# Restauración de backups

## Idea clave

Un backup que no se ha probado no es un backup fiable.

La restauración es la parte que confirma que una copia sirve de verdad.

## Restauración en Windows Server

En un escenario de fallo grave:

1. Insertar ISO de Windows Server.
2. Arrancar desde la ISO.
3. Elegir Reparar el equipo.
4. Buscar una imagen de sistema.
5. Seleccionar el backup más reciente.
6. Iniciar restauración.
7. Esperar al reinicio.
8. Verificar que los datos han vuelto.

## Qué se puede recuperar

Según el tipo de copia:

- servidor completo
- volúmenes
- archivos
- carpetas
- estado del sistema

## Simulación de fallo

En laboratorio se puede probar eliminando:

- una OU de Active Directory
- archivos de prueba
- carpetas compartidas

Después se restaura y se comprueba que todo vuelve.

## Riesgo

No conviene probar restauraciones destructivas en producción sin plan.

Primero se prueban en laboratorio.

## Restauración en Linux con rsync

Si se tiene una copia completa:

    sudo rsync -a /mnt/raid01/backups/fulls/ /shared/

Si se tiene una incremental concreta:

    sudo rsync -a /mnt/raid01/backups/incrementales/2026-02-24/ /shared/

## Comprobaciones tras restaurar

Verificar:

- permisos
- propietario y grupo
- contenido
- rutas
- servicios afectados
- acceso desde clientes

## Resumen

Restaurar no es solo copiar datos de vuelta. También hay que comprobar que permisos, rutas, servicios y accesos siguen funcionando.
