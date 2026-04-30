# NFS en Linux

## Qué es NFS

NFS permite compartir directorios entre sistemas Linux/Unix en red.

Es una alternativa habitual a SMB en entornos Linux.

## Paquetes

En servidor:

    sudo apt install nfs-kernel-server

En cliente:

    sudo apt install nfs-common

## Compartir un directorio

Editar:

    sudo nano /etc/exports

Ejemplo:

    /ShareResources 192.168.100.0/24(rw,sync,no_subtree_check)

Aplicar cambios:

    sudo exportfs -ra

Ver exportaciones:

    sudo exportfs -v

## Permisos del directorio

NFS no sustituye permisos Linux.

Aunque exportes con rw, si el sistema de archivos no permite escribir, el cliente no podrá escribir.

Ejemplo:

    sudo chown nobody:nogroup /myRAID12
    sudo chmod 777 /myRAID12

Esto se usa en prácticas para permitir escritura general, aunque en producción se afina más.

## Mostrar recursos desde cliente

    showmount -e IP_SERVIDOR

## Montar recurso

Crear punto de montaje:

    sudo mkdir /RecursosSRV

Montar:

    sudo mount IP_SERVIDOR:/ShareResources /RecursosSRV

Comprobar:

    df -hT

## Montaje permanente

Editar:

    sudo nano /etc/fstab

Ejemplo:

    192.168.100.100:/ShareResources /RecursosSRV nfs defaults 0 0

Probar:

    sudo mount -a

## Problemas comunes

- permisos locales incorrectos
- /etc/exports mal escrito
- no ejecutar exportfs -ra
- firewall bloqueando NFS
- usuarios y grupos no coinciden entre cliente y servidor
- no usar no_root_squash cuando el escenario de laboratorio lo necesita

## no_root_squash

Por defecto, NFS puede mapear root del cliente a un usuario sin privilegios.

En laboratorio puede usarse no_root_squash para evitar problemas de permisos, pero en producción debe usarse con mucho cuidado.

## Resumen

NFS comparte rutas, pero los permisos reales siguen dependiendo del propietario, grupo, modo octal, UID/GID y opciones de exportación.
