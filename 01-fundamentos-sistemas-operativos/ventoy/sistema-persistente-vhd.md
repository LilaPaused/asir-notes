# Sistema persistente con VHD/VToy

## Objetivo

Crear un sistema que pueda arrancar desde un USB Ventoy y conservar los cambios.

En vez de arrancar una ISO live sin persistencia, se usa un disco virtual.

## Idea principal

Se crea una máquina virtual con un disco .vhd.

Después se prepara con vtoyboot, se copia al USB Ventoy y se renombra como .vtoy.

## Qué significa persistente

Un sistema persistente conserva cambios.

Ejemplos:

- archivos creados
- paquetes instalados
- configuraciones
- usuarios
- cambios en el escritorio

Si apagas y vuelves a arrancar, todo sigue ahí.

## Crear máquina virtual

En VirtualBox:

- sistema: Arch Linux
- disco: VHD
- tamaño: 30 GB o 50 GB
- pre-allocated
- EFI activado si la práctica lo requiere

## Preparar vtoyboot

Descargar vtoyboot.

Montar la ISO:

sudo mount vtoyboot-x.x.xx.iso /mnt/ISOS

Extraer el contenido necesario.

Ejecutar el script dentro del sistema instalado:

sudo sh vtoyboot.sh

El script adapta el sistema para poder arrancar desde Ventoy.

## Copiar al USB

Apagar la máquina virtual.

Localizar el disco .vhd.

Copiarlo al USB Ventoy.

Renombrar:

Ventoy_ARCH.vhd -> Ventoy_ARCH.vhd.vtoy

## Arranque

Arrancar desde el USB Ventoy y seleccionar el archivo .vtoy.

Si todo está bien, cargará el sistema instalado.

## Comprobar persistencia

Crear un archivo:

mkdir -p ~/Documents
echo "He booteado desde Ventoy" > ~/Documents/prueba.txt

Apagar.

Arrancar de nuevo.

Comprobar:

cat ~/Documents/prueba.txt

## Ventajas

- Sistema portable.
- Conserva cambios.
- No depende de una instalación en el disco interno.
- Útil para laboratorio, recuperación o pruebas.

## Limitaciones

- El rendimiento depende del USB.
- Las escrituras pueden ser más lentas.
- No todos los equipos arrancan igual.
- Puede haber problemas con drivers según hardware.

## Resumen rápido

Crear VM con VHD -> Instalar sistema -> Ejecutar vtoyboot.sh -> Copiar VHD al USB Ventoy -> Renombrar a .vtoy -> Arrancar desde Ventoy
