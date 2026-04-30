# Cuotas en Linux

## Qué son

Las cuotas de disco limitan el uso de espacio o el número de archivos que puede crear un usuario o grupo.

En Linux pueden aplicarse por:

- usuario
- grupo
- bloques de disco
- inodos

## Paquetes

Instalar:

    sudo apt install quota quotatool

## Activar cuotas en fstab

En la partición o punto de montaje donde se quieren cuotas, añadir opciones:

    usrquota,grpquota

Ejemplo:

    /dev/md1 /myRAID12 ext4 defaults,usrquota,grpquota 0 0

Remontar:

    sudo mount -o remount /myRAID12

O:

    sudo mount -a

## Inicializar cuotas

Ejecutar:

    sudo quotacheck -cum /myRAID12
    sudo quotacheck -cgm /myRAID12

Activar:

    sudo quotaon /myRAID12

## Ver estado

    sudo repquota /myRAID12

## Editar cuota de usuario

    sudo edquota -u usuario

## Límites

Hay dos tipos de límite:

### Soft limit

Límite flexible.

El usuario puede superarlo temporalmente durante el periodo de gracia.

### Hard limit

Límite máximo.

No se puede superar.

## Periodo de gracia

Permite definir cuánto tiempo puede estar un usuario por encima del soft limit.

Ejemplo:

- soft limit de 10 archivos
- grace period de 2 días

## Cuotas por inodos

Si quieres limitar cantidad de archivos o directorios, usas inodos.

Ejemplo de examen:

- usuario ulocal
- máximo flexible de 10 elementos
- 2 días para corregir

## Comprobación

Crear archivos en bucle desde cliente:

    touch file1 file2 file3 file4 file5

O:

    for i in {1..12}; do touch file$i; done

Luego revisar:

    quota -u usuario
    sudo repquota /myRAID12

## Problemas comunes

- no poner usrquota,grpquota en fstab
- no remontar el sistema de archivos
- no ejecutar quotacheck
- no activar quotaon
- aplicar cuotas en una ruta que no es punto de montaje
- usar NFS y no comprobar cómo se mapean usuarios

## Resumen

En Linux las cuotas dependen del sistema de archivos y del montaje. No basta con instalar paquetes: hay que activar opciones, generar ficheros de control, encender las cuotas y probarlas.
