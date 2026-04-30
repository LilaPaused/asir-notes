# PF5 Linux: RAID, NFS, cuotas y permisos

## Bloques principales

En la parte Linux se trabaja:

- RAID con mdadm
- montaje permanente
- NFS
- permisos Linux
- sticky bit
- cuotas de disco
- comprobación con usuarios LDAP

## RAID 1

Crear RAID 1:

    sudo mdadm --create /dev/md1 --level=1 --raid-devices=2 /dev/sdb /dev/sdc

Ver estado:

    cat /proc/mdstat

Formatear:

    sudo mkfs.ext4 /dev/md1

Montar:

    sudo mkdir /myRAID12
    sudo mount /dev/md1 /myRAID12

Persistencia:

    sudo mdadm --detail --scan | sudo tee -a /etc/mdadm/mdadm.conf
    sudo update-initramfs -u

fstab:

    UUID=xxxx /myRAID12 ext4 defaults,nofail,discard 0 0

## Comprobar tras reinicio

    df -hT
    cat /proc/mdstat

## NFS

Servidor:

    sudo apt install nfs-kernel-server

Editar exports:

    /myRAID12 192.168.100.0/24(rw,sync,no_subtree_check)

Aplicar:

    sudo exportfs -ra

Cliente:

    sudo apt install nfs-common
    showmount -e IP_SERVIDOR
    sudo mount IP_SERVIDOR:/myRAID12 /RecursosSRV

## Permisos Linux

Caso ShareResources:

- /ShareResources -> 755 root root
- /ShareResources/First -> permisos específicos
- /ShareResources/Second -> permisos específicos
- /ShareResources/Third -> sticky bit

## Caso First

Objetivo:

- propietario: amenta
- grupo: grupA
- propietario total
- grupo solo acceso/lectura
- otros sin acceso

Comandos:

    sudo chown amenta:grupA /ShareResources/First
    sudo chmod 750 /ShareResources/First

## Caso Second

Objetivo:

- propietario: eteck
- grupo: grupB
- propietario total
- grupo solo lectura/acceso
- otros sin acceso

Comandos:

    sudo chown eteck:grupB /ShareResources/Second
    sudo chmod 750 /ShareResources/Second

## Caso Third

Objetivo:

- usuarios pueden crear
- no pueden borrar o modificar lo que no es suyo
- propietario y grupo con más permisos

Sticky bit:

    sudo chmod +t /ShareResources/Third

Ejemplo habitual:

    sudo chmod 1777 /ShareResources/Third

## Cuotas Linux

Instalar:

    sudo apt install quota quotatool

fstab:

    defaults,usrquota,grpquota

Inicializar:

    sudo quotacheck -cum /myRAID12
    sudo quotacheck -cgm /myRAID12
    sudo quotaon /myRAID12

Editar usuario:

    sudo edquota -u ulocal

Ver:

    sudo repquota /myRAID12

## Pruebas de cuota

Crear archivos:

    for i in {1..12}; do touch file$i; done

Comprobar que al superar el límite flexible aparece el estado de gracia.

## getent

Para comprobar usuarios y grupos del dominio LDAP:

    getent passwd
    getent group

## Fallos a evitar

- no guardar mdadm.conf
- no actualizar initramfs
- montar en fstab sin probar
- exportar NFS sin permisos locales
- olvidar usrquota,grpquota
- no activar quotaon
- probar permisos solo con un usuario
