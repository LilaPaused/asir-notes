# GRUB

## Qué es

GRUB significa GNU GRand Unified Bootloader.

Es un gestor de arranque usado habitualmente en sistemas Linux.

Permite cargar:

- Linux
- Windows
- otros sistemas operativos
- opciones avanzadas de recuperación

## Función principal

GRUB aparece al arrancar el equipo y permite seleccionar qué sistema iniciar.

Ejemplo:

- Debian GNU/Linux
- Advanced options for Debian
- Windows 10

## Archivos importantes

### Configuración principal

/etc/default/grub

Aquí se configuran opciones generales.

Ejemplos:

- GRUB_TIMEOUT=10
- GRUB_DEFAULT=0
- GRUB_DISABLE_OS_PROBER=false

### Scripts de generación

/etc/grub.d/

Contiene scripts que generan las entradas del menú.

Ejemplos:

- /etc/grub.d/10_linux
- /etc/grub.d/30_os-prober
- /etc/grub.d/40_custom

## Actualizar GRUB

En Debian/Ubuntu:

sudo update-grub

En otras distribuciones:

sudo grub-mkconfig -o /boot/grub/grub.cfg

## Entrada personalizada

Se puede añadir una entrada manual en:

/etc/grub.d/40_custom

Después hay que regenerar GRUB.

## os-prober

os-prober detecta sistemas operativos instalados en otras particiones.

Comando:

sudo os-prober

Si no detecta Windows, revisar:

/etc/default/grub

Y activar:

GRUB_DISABLE_OS_PROBER=false

Luego:

sudo update-grub

## Problemas comunes

- Windows no aparece en GRUB.
- Windows sobrescribe GRUB.
- GRUB arranca pero no carga Linux.
- Error por particiones mal identificadas.
- os-prober desactivado.

## Resumen

GRUB es una pieza clave en dual boot. Si se rompe, normalmente se puede reparar desde una Live ISO montando el sistema y reinstalando el cargador.
