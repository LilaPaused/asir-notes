# Comandos básicos de monitorización en Linux

## uptime

Muestra:

- hora actual
- tiempo encendido del sistema
- usuarios conectados
- carga media del sistema

Comando:

    uptime

La carga media suele mostrarse para:

- último minuto
- últimos 5 minutos
- últimos 15 minutos

## top

Muestra procesos en tiempo real.

Comando:

    top

Para salir:

    q

## ps

Muestra procesos.

Ejemplo básico:

    ps

Ejemplo más completo:

    ps aux

## df

Muestra uso de sistemas de archivos.

Ejemplo:

    df -h -l

Donde:

- `-h` muestra tamaños en formato legible.
- `-l` muestra solo sistemas de archivos locales.

## free

Muestra uso de memoria RAM y swap.

    free -h

## sysstat

Paquete que incluye herramientas como `mpstat` e `iostat`.

Instalación:

    sudo apt install sysstat

## Resumen rápido

| Comando | Uso |
|---|---|
| uptime | carga media y tiempo encendido |
| top | procesos en tiempo real |
| ps | lista de procesos |
| df | uso de discos |
| free | memoria RAM y swap |
| mpstat | CPU |
| vmstat | memoria y sistema |
| iostat | disco y transferencias |
