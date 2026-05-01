# CPU con mpstat

## Qué es

`mpstat` permite ver estadísticas de uso del procesador.

Forma parte del paquete `sysstat`.

Instalación:

    sudo apt install sysstat

## Ejecutar mpstat

    mpstat

Muestra porcentajes de uso de CPU en distintos estados.

## Columnas importantes

| Columna | Significado |
|---|---|
| %usr | tiempo usado por procesos de usuario |
| %sys | tiempo usado por el kernel |
| %idle | tiempo ocioso de CPU |
| %iowait | espera por operaciones de disco |
| %nice | procesos con prioridad nice |

## %nice

`%nice` indica el porcentaje de CPU usado por procesos con prioridad modificada mediante `nice`.

Los procesos con valor nice alto tienen menos prioridad.

## CPU ociosa

La columna `%idle` indica cuánto tiempo está la CPU libre.

Si `%idle` es muy alto, la CPU no está siendo el cuello de botella.

## Tomar muestras

Formato:

    mpstat intervalo numero_muestras

Ejemplo para 30 muestras cada 2 segundos:

    mpstat 2 30 > cpustatus.txt

Tiempo total:

    2 * 30 = 60 segundos

## Uso práctico

Sirve para observar si la CPU se carga cuando abrimos programas, copiamos archivos o ejecutamos tareas pesadas.

También permite generar datos para graficarlos luego en Calc o similar.
