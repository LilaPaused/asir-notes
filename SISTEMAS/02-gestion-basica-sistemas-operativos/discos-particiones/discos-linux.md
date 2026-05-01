# Gestión de discos en Linux

## Objetivo

Inicializar discos, crear particiones, formatearlas y etiquetarlas en Linux.

## Ver discos

- `lsblk`
- `sudo fdisk -l`
- `sudo fdisk -l | grep sd`

## GParted

Pasos:

1. Seleccionar disco correcto.
2. Crear tabla de particiones GPT.
3. Crear particiones.
4. Elegir sistema de archivos ext4.
5. Añadir etiqueta.
6. Aplicar cambios.
7. Cerrar GParted para liberar el disco.

## fdisk

Abrir disco:

- `sudo fdisk /dev/sdX`

Crear tabla GPT:

- `g`

Crear partición:

- `n`

Escribir cambios:

- `w`

## Formatear en ext4

- `sudo mkfs.ext4 /dev/sdX1`
- `sudo mkfs.ext4 /dev/sdX2`

## Etiquetar particiones

- `sudo e2label /dev/sdX1 "udisc2121"`
- `sudo e2label /dev/sdX2 "udisc2122"`

## Comprobar

- `lsblk -f`

## Buenas prácticas

- Revisar muy bien el disco antes de formatear.
- No trabajar sobre `/dev/sda` si es el disco del sistema.
- Cerrar GParted si las particiones no aparecen.
- Usar etiquetas para identificar particiones rápido.
