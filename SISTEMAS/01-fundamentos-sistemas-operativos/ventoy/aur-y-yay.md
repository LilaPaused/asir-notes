# AUR y yay

## Qué es AUR

AUR significa Arch User Repository.

Es un repositorio comunitario donde usuarios de Arch publican paquetes que no están necesariamente en los repositorios oficiales.

## Importante

AUR no es lo mismo que los repositorios oficiales de Arch.

Los paquetes de AUR deben revisarse antes de instalarse.

## Relación con Git

Muchos paquetes de AUR se descargan como repositorios Git.

Por eso normalmente necesitas instalar git:

sudo pacman -S git

## Instalación manual desde AUR

Ejemplo genérico:

git clone URL_DEL_PAQUETE
cd paquete
makepkg -si

## Problema de instalación manual

Los paquetes instalados manualmente desde AUR no se actualizan directamente con:

sudo pacman -Syu

Para gestionarlos mejor se usa un helper.

## Qué es yay

yay significa Yet Another Yogurt.

Es un helper de AUR.

Permite:

- buscar paquetes en AUR
- instalar paquetes AUR
- actualizar paquetes oficiales
- actualizar paquetes AUR

## Instalar yay

1. Instalar git:

sudo pacman -S git

2. Clonar yay:

git clone https://aur.archlinux.org/yay.git

3. Entrar en la carpeta:

cd yay

4. Compilar e instalar:

makepkg -si

## Usar yay

Buscar paquete:

yay nombre-paquete

Instalar paquete:

yay -S nombre-paquete

Actualizar sistema completo:

yay

También se puede usar:

yay -Syu

## Diferencia entre pacman y yay

| Herramienta | Repos oficiales | AUR |
|---|---|---|
| pacman | Sí | No |
| yay | Sí | Sí |

## Advertencias

- No instalar paquetes AUR sin revisar.
- Leer los PKGBUILD si el paquete es sensible.
- AUR es útil, pero no todo es igual de fiable.
- Evitar instalar software innecesario.

## Resumen rápido

sudo pacman -S git
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si
yay
