# Montaje permanente con fstab

## Qué es fstab

/etc/fstab define sistemas de archivos que se montan automáticamente al arrancar.

Se usa para:

- discos locales
- RAIDs
- recursos NFS
- particiones externas

## Ver discos y UUID

    lsblk
    sudo blkid

## Montar RAID local

Ejemplo:

    UUID=xxxx-xxxx /myRAID12 ext4 defaults,nofail,discard 0 0

## Montar recurso NFS

Ejemplo:

    192.168.100.100:/ShareResources /RecursosSRV nfs defaults 0 0

## Probar fstab

Después de editar:

    sudo mount -a

Si no da error, la entrada es válida.

## Comprobar

    df -hT

## Opción nofail

nofail permite que el sistema arranque aunque el montaje no esté disponible.

Es útil en discos secundarios o recursos de red.

## Errores comunes

- usar ruta de montaje inexistente
- escribir mal el UUID
- olvidar instalar nfs-common
- no probar con mount -a
- bloquear el arranque por una entrada incorrecta

## Buenas prácticas

Antes de reiniciar:

1. hacer copia de fstab
2. editar con cuidado
3. ejecutar mount -a
4. verificar con df -hT

Copia:

    sudo cp /etc/fstab /etc/fstab.bak

## Resumen

fstab es simple, pero un error puede impedir un arranque limpio. Siempre se prueba antes de reiniciar.
