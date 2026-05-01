# Dual boot Windows/Linux

## Qué es

Un dual boot permite tener dos sistemas operativos instalados y elegir cuál arrancar al encender la máquina.

Ejemplo:

Windows + Linux

## Gestor de arranque

El gestor de arranque permite elegir el sistema.

Los más comunes son:

- Windows Boot Manager
- GRUB

En sistemas Linux, GRUB suele ser la opción más habitual.

## Modo fácil

Instalar primero Windows y después Linux.

### Por qué es más fácil

Linux suele detectar Windows durante la instalación y añade automáticamente una entrada en GRUB.

Flujo:

Instalar Windows -> Dejar espacio libre -> Instalar Linux -> GRUB detecta Windows

## Modo difícil

Instalar primero Linux y después Windows.

### Problema

Windows suele sobrescribir el gestor de arranque.

Resultado:

Linux instalado -> Windows instalado -> Windows Boot Manager pisa GRUB

Después suele ser necesario reparar GRUB.

## Esquema recomendado

Disco 100 GB:

- Windows: 50 GB
- Linux: 50 GB

## Comprobaciones

Desde Linux:

sudo fdisk -l

Actualizar GRUB:

sudo update-grub

En algunas distribuciones:

sudo grub-mkconfig -o /boot/grub/grub.cfg

## OS Prober

os-prober permite detectar otros sistemas instalados.

En algunas distribuciones modernas puede venir desactivado.

Archivo habitual:

/etc/default/grub

Línea útil:

GRUB_DISABLE_OS_PROBER=false

Después:

sudo update-grub

## Buenas prácticas

- Instalar Windows primero si se puede.
- Dejar espacio libre para Linux.
- Tener una ISO Live preparada.
- Saber reparar GRUB manualmente.
- Crear snapshots si se trabaja en VirtualBox.

## Conceptos relacionados

- [GRUB](./grub.md)
- [Reparar GRUB](./reparar-grub.md)
- [Boot Repair](./bootrepair.md)
