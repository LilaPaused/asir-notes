# Conceptos de discos y particiones

## Disco

Un disco es un dispositivo de almacenamiento.

Puede ser:

- HDD
- SSD
- disco virtual VDI, VHD, VMDK
- USB

## Partición

Una partición es una división lógica dentro de un disco.

Permite separar espacios para distintos usos.

## Tabla de particiones

Define cómo se organizan las particiones del disco.

Tipos comunes:

- MBR
- GPT

## MBR

Sistema antiguo.

Limitaciones:

- máximo 4 particiones primarias
- peor soporte para discos grandes

## GPT

Sistema moderno.

Ventajas:

- soporta discos grandes
- soporta más particiones
- es el estándar en sistemas actuales con UEFI

## Sistema de archivos

Formato que permite guardar datos dentro de una partición.

Ejemplos:

- NTFS en Windows
- FAT32 o exFAT en USB
- ext4 en Linux

## Etiqueta

Nombre visible de una partición o volumen.

Ejemplos:

- backup
- wdisc1121
- udisc1222

## Letra de unidad en Windows

Windows usa letras:

- C:
- D:
- E:

Linux no usa letras; monta sistemas en rutas.

## Montaje en Linux

Linux accede a particiones mediante puntos de montaje.

Ejemplos:

- /home
- /mnt/datos
- /media/usuario/USB

## Flujo típico para preparar un disco

1. Añadir disco
2. Inicializar disco
3. Crear tabla de particiones
4. Crear particiones
5. Formatear
6. Etiquetar
7. Montar o asignar letra
8. Comprobar que se puede guardar información
