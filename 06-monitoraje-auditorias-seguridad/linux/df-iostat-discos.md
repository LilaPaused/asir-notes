# Disco con df e iostat

## df

`df` muestra el espacio usado y disponible en los sistemas de archivos.

Ejemplo:

    df -h -l

Opciones:

- `-h`: formato legible para humanos.
- `-l`: solo sistemas de archivos locales.

## iostat

`iostat` permite ver estadísticas de E/S de disco.

Forma parte del paquete `sysstat`.

Instalación:

    sudo apt install sysstat

## iostat -dpm

    iostat -dpm

Opciones:

- `-d`: muestra dispositivos, no CPU.
- `-p`: muestra particiones.
- `-m`: muestra datos en MB/s.

## Muestras recurrentes

Ejemplo para tomar datos cada 3 segundos, 15 veces:

    iostat -dkp 3 15

Tiempo total:

    3 * 15 = 45 segundos

## Qué observar

En una prueba de disco se puede observar:

- lecturas
- escrituras
- dispositivos con actividad
- picos al copiar, mover o descargar archivos

## Uso práctico

Si un servidor va lento, `iostat` ayuda a saber si el disco es el cuello de botella.

Si hay muchas escrituras o lecturas, se puede identificar qué disco o partición está trabajando más.
