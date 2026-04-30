# Gestión de discos en Linux

## Herramientas usadas

- GParted para entorno gráfico
- fdisk para terminal
- mkfs.ext4 para formatear
- e2label para etiquetar

## Ver discos

    lsblk

Otra opción:

    sudo fdisk -l

Filtrar discos sd:

    sudo fdisk -l | grep sd

## GParted

Pasos generales:

1. Seleccionar disco correcto
2. Crear tabla de particiones GPT
3. Crear primera partición
4. Crear segunda partición
5. Elegir ext4
6. Asignar etiqueta
7. Aplicar cambios
8. Cerrar GParted

Nota importante: si GParted sigue abierto, puede mantener el disco ocupado y no aparecer montado en el sistema.

## fdisk

Abrir disco:

    sudo fdisk /dev/sdd

Crear tabla GPT:

    g

Crear partición:

    n

Aceptar valores por defecto o asignar tamaño, por ejemplo:

    +5G

Guardar cambios:

    w

## Formatear en ext4

    sudo mkfs.ext4 /dev/sdd1
    sudo mkfs.ext4 /dev/sdd2

## Etiquetar particiones

    sudo e2label /dev/sdd1 "udisc2121"
    sudo e2label /dev/sdd2 "udisc2122"

## Comprobar

    lsblk -f

O desde el explorador de archivos, en Other Locations.

## Flujo completo rápido

    sudo fdisk -l
    sudo fdisk /dev/sdd
    sudo mkfs.ext4 /dev/sdd1
    sudo mkfs.ext4 /dev/sdd2
    sudo e2label /dev/sdd1 "udisc2121"
    sudo e2label /dev/sdd2 "udisc2122"
    lsblk -f

## Precaución

Nunca ejecutes fdisk o mkfs sobre un disco si no estás seguro de cuál es.

mkfs formatea y borra el contenido de la partición.
