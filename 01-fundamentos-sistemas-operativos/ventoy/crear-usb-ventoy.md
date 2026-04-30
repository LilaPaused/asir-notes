# Crear USB con Ventoy

## Qué es Ventoy

Ventoy es una herramienta que permite crear un USB booteable donde puedes copiar varias imágenes ISO.

No hace falta flashear cada ISO por separado.

Simplemente:

1. instalas Ventoy en el USB
2. copias las ISOs dentro
3. arrancas desde el USB
4. eliges la ISO desde el menú

## Ventajas

- Permite tener varias ISOs en un mismo USB.
- Es fácil de organizar por carpetas.
- Ahorra tiempo.
- Funciona con muchas distribuciones Linux y Windows.

## Crear unidad Ventoy en Linux

Descargar Ventoy desde su web oficial.

Extraer el archivo.

Entrar en la carpeta:

cd ventoy-x.x.xx

Identificar el USB:

lsblk

Ejemplo:

/dev/sdb

Instalar Ventoy en el USB:

sudo sh Ventoy2Disk.sh -i /dev/sdb

## Reinstalar Ventoy

Si el USB ya tiene Ventoy y quieres reinstalar:

sudo sh Ventoy2Disk.sh -I /dev/sdb

Cuidado: esto puede borrar datos.

## Organización recomendada

Dentro del USB puedes crear carpetas:

- Linux/
- Windows/
- Recovery/
- Herramientas/

Ejemplo:

- Linux/debian.iso
- Linux/archlinux.iso
- Windows/windows10.iso
- Recovery/bootrepair.iso

## Comprobación

Después de copiar una ISO:

1. reiniciar el equipo
2. elegir arrancar desde USB
3. comprobar que Ventoy muestra la ISO
4. arrancar la ISO

## Buenas prácticas

- Revisar bien el nombre del dispositivo antes de ejecutar el comando.
- No confundir /dev/sdb con el disco principal.
- Mantener las ISOs ordenadas por carpetas.
- Guardar también herramientas de recuperación.
