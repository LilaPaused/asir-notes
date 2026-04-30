# Actualizaciones en Arch Linux

## Gestor de paquetes

Arch Linux usa pacman como gestor de paquetes oficial.

## Actualizar el sistema

sudo pacman -Syu

Este comando:

- sincroniza bases de datos
- descarga paquetes nuevos
- actualiza el sistema

## Instalar un paquete

sudo pacman -S nombre-paquete

Ejemplo:

sudo pacman -S git

## Buscar paquete

pacman -Ss nombre-paquete

## Ver paquetes instalados

pacman -Q

## Eliminar paquete

sudo pacman -R nombre-paquete

Eliminar paquete y dependencias que ya no se usan:

sudo pacman -Rns nombre-paquete

## Limpiar caché

sudo pacman -Sc

## Advertencia

Arch es una distribución rolling release.

Eso significa que las actualizaciones son continuas.

No conviene actualizar a ciegas después de mucho tiempo sin hacerlo.

## Flujo básico recomendado

sudo pacman -Syu

Si se usa AUR con yay:

yay

## Diferencia entre pacman y yay

| Herramienta | Función |
|---|---|
| pacman | Gestiona paquetes oficiales |
| yay | Gestiona paquetes oficiales y AUR |

## Buenas prácticas

- Leer los mensajes antes de confirmar.
- No cortar una actualización a mitad.
- Revisar la Arch Wiki ante errores.
- Tener snapshots o backups si el sistema es importante.
- No instalar paquetes AUR sin revisar.
