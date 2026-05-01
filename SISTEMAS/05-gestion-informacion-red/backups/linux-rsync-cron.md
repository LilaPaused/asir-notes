# Backups en Linux con rsync y cron

## Objetivo

Crear copias de seguridad automáticas usando rsync y cron.

En la práctica se trabaja con:

- copias completas
- copias incrementales
- limpieza de incrementales antiguas

## Estructura recomendada

Ejemplo:

    /mnt/raid01/backups/fulls/
    /mnt/raid01/backups/incrementales/

Crear directorios:

    sudo mkdir -p /mnt/raid01/backups/fulls
    sudo mkdir -p /mnt/raid01/backups/incrementales

## Copia completa

Ejemplo:

    rsync -a --delete /shared/ /mnt/raid01/backups/fulls/

Qué hace:

- copia el contenido de /shared/
- conserva permisos y estructura
- elimina del destino lo que ya no existe en origen

## Copia incremental

Ejemplo:

    rsync -a --link-dest=/mnt/raid01/backups/fulls/ /shared/ /mnt/raid01/backups/incrementales/$(date +\%F)/

La opción --link-dest permite usar la última completa como referencia.

Así se ahorra espacio porque no se duplica todo.

## Programar con cron

Editar crontab:

    crontab -e

Ejemplo de política:

- copia completa cada lunes
- incrementales de martes a domingo
- limpieza de incrementales antiguas

Ejemplo:

    0 2 * * 1 rsync -a --delete /shared/ /mnt/raid01/backups/fulls/
    0 2 * * 2-7 rsync -a --link-dest=/mnt/raid01/backups/fulls/ /shared/ /mnt/raid01/backups/incrementales/$(date +\%F)/
    0 3 * * * find /mnt/raid01/backups/incrementales/ -type d -mtime +14 -exec rm -rf {} \;

## Explicación

Primera línea:

- se ejecuta a las 02:00 los lunes
- hace copia completa
- usa --delete para mantener una única completa limpia

Segunda línea:

- se ejecuta de martes a domingo
- crea incrementales por fecha

Tercera línea:

- se ejecuta cada día a las 03:00
- borra incrementales con más de 14 días

## Cuidado con el porcentaje

En cron, el símbolo % tiene significado especial.

Por eso en date se usa:

    \%F

No:

    %F

## Comprobaciones

Ver contenido:

    ls -lah /mnt/raid01/backups

Ver incrementales:

    ls -lah /mnt/raid01/backups/incrementales

Lanzar manualmente una prueba antes de depender de cron.

## Buenas prácticas

- Revisar logs.
- Comprobar restauraciones.
- No guardar copias solo en el mismo disco.
- Limpiar incrementales antiguas.
- Documentar la política de backup.
