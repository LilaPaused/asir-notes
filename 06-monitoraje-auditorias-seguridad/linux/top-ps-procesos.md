# Procesos con top y ps

## top

`top` es una herramienta interactiva para ver procesos en tiempo real.

    top

## Primera línea

La primera línea muestra información similar a `uptime`:

- hora
- tiempo encendido
- usuarios conectados
- carga media

## Tasks

La línea `Tasks` muestra cuántos procesos hay y en qué estado están.

Estados habituales:

- running
- sleeping
- stopped
- zombie

## Proceso zombie

Un proceso zombie es un proceso hijo que ya ha terminado, pero cuyo proceso padre todavía no ha recogido su estado de finalización.

No está ejecutando trabajo útil, pero sigue apareciendo en la tabla de procesos.

## Filtrar por usuario

Dentro de `top` se puede pulsar:

    u

Y escribir el nombre del usuario.

Esto muestra solo procesos de ese usuario.

## Matar un proceso desde top

Dentro de `top`:

1. Pulsar `k`.
2. Escribir el PID.
3. Confirmar la señal.

## ps

`ps` muestra procesos lanzados desde la sesión actual.

    ps

Columnas típicas:

| Columna | Significado |
|---|---|
| PID | identificador del proceso |
| TTY | terminal asociada |
| TIME | tiempo de CPU usado |
| CMD | comando ejecutado |

## ps aux

Muestra muchos más procesos del sistema:

    ps aux

Es útil para buscar procesos concretos:

    ps aux | grep firefox

## Uso práctico

Si un programa se queda colgado:

1. localizar PID con `top` o `ps aux`
2. cerrarlo con `kill`

Ejemplo:

    kill PID

Forzar:

    kill -9 PID
