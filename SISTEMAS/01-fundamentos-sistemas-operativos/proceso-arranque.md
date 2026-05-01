# Proceso de arranque

## Qué es

El proceso de arranque es la secuencia que sigue un ordenador desde que se pulsa el botón de encendido hasta que el sistema operativo toma el control.

## Resumen rápido

Power On -> BIOS/UEFI -> POST -> MBR/GPT -> Boot Manager -> Sistema Operativo

## 1. Power On

El usuario pulsa el botón de encendido.

La fuente de alimentación empieza a proporcionar corriente a la placa base, CPU, memoria, discos y demás componentes.

Cuando la alimentación es estable, se genera la señal de encendido correcto.

## 2. BIOS o UEFI

La BIOS o UEFI es el firmware de la placa base.

Su función es inicializar el hardware y preparar el equipo para buscar un sistema arrancable.

### BIOS

Sistema tradicional de firmware.

Suele trabajar con MBR.

### UEFI

Sistema moderno que sustituye a BIOS.

Ventajas:

- soporte para discos grandes
- arranque más flexible
- Secure Boot
- mejor integración con GPT

## 3. POST

POST significa Power On Self Test.

Es una comprobación inicial del hardware.

Comprueba elementos como:

- memoria RAM
- CPU
- tarjeta gráfica
- teclado
- dispositivos conectados
- discos

Si hay un error grave, el sistema puede mostrar un mensaje o emitir pitidos.

## 4. Búsqueda de dispositivo de arranque

El firmware busca un dispositivo desde el que arrancar.

Ejemplos:

- disco duro
- SSD
- USB
- DVD
- red PXE

El orden de búsqueda depende de la configuración de BIOS/UEFI.

## 5. MBR o GPT

El sistema localiza la información de particionado y arranque.

### MBR

Master Boot Record.

Sistema antiguo de particiones.

Limitaciones:

- máximo 4 particiones primarias
- problemas con discos grandes

### GPT

GUID Partition Table.

Sistema moderno de particiones usado normalmente con UEFI.

Ventajas:

- más particiones
- soporte para discos grandes
- mayor fiabilidad

## 6. Boot Manager

El Boot Manager permite cargar un sistema operativo.

Ejemplos:

- Windows Boot Manager
- GRUB
- systemd-boot

En un dual boot, el gestor de arranque permite escoger entre varios sistemas.

## 7. Sistema Operativo

Cuando se selecciona un sistema, el Boot Manager carga el kernel o cargador correspondiente.

A partir de este momento, el sistema operativo toma el control.

## Ejemplo en dual boot

UEFI -> GRUB -> Elegir Linux o Windows -> Arranca el sistema elegido

## Para examen

Al encender el equipo se alimenta la placa base, se ejecuta BIOS/UEFI, se realiza el POST, se busca un dispositivo arrancable, se lee MBR/GPT, se carga el Boot Manager y finalmente el sistema operativo toma el control.
