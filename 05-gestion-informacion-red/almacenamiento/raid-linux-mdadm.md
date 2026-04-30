# RAID en Linux con mdadm

## Qué es mdadm

mdadm es la herramienta habitual en Linux para crear y administrar RAIDs por software.

Permite crear dispositivos como:

- /dev/md0
- /dev/md1
- /dev/md2

## Ver discos disponibles

    lsblk

También se puede usar:

    sudo fdisk -l

## RAID 1 básico

RAID 1 replica datos entre dos discos.

Ejemplo con dos discos:

- /dev/sdb
- /dev/sdc

Crear RAID 1:

    sudo mdadm --create /dev/md1 --level=1 --raid-devices=2 /dev/sdb /dev/sdc

Ver estado:

    cat /proc/mdstat

## Formatear el RAID

Una vez creado el RAID:

    sudo mkfs.ext4 /dev/md1

## Crear punto de montaje

    sudo mkdir /myRAID12

Montar:

    sudo mount /dev/md1 /myRAID12

Comprobar:

    df -hT

## Hacer el RAID persistente

Guardar configuración de mdadm:

    sudo mdadm --detail --scan | sudo tee -a /etc/mdadm/mdadm.conf

Actualizar initramfs:

    sudo update-initramfs -u

## Hacer el montaje persistente

Obtener UUID:

    sudo blkid /dev/md1

Editar fstab:

    sudo nano /etc/fstab

Ejemplo de entrada:

    UUID=xxxx-xxxx /myRAID12 ext4 defaults,nofail,discard 0 0

Probar:

    sudo mount -a

## Cambiar propietario

Si el directorio fue creado con sudo, puede que el usuario normal no pueda escribir.

Ejemplo:

    sudo chown usuario:usuario /myRAID12

## RAID 0+1 en Linux

En la práctica también se trabaja un RAID 0+1:

1. Crear dos RAID 0.
2. Crear un RAID superior usando esos dos RAID como espejo.
3. Formatear solo el RAID final.
4. Montarlo.
5. Guardarlo en mdadm.conf y fstab.

## Comandos útiles

Ver estado:

    cat /proc/mdstat

Ver detalle:

    sudo mdadm --detail /dev/md1

Parar RAID:

    sudo mdadm --stop /dev/md1

Ensamblar RAIDs detectados:

    sudo mdadm --assemble --scan

## Nota importante

Si un RAID no está correctamente guardado en mdadm.conf y fstab, puede no montarse después de reiniciar.

Por eso hay dos persistencias distintas:

- persistencia del RAID en mdadm.conf
- persistencia del montaje en fstab
