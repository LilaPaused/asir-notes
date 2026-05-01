# Memoria con vmstat y free

## vmstat

`vmstat` muestra estadísticas de memoria, swap, procesos, CPU y E/S.

Ejemplo:

    vmstat 1 10

Esto toma una muestra cada segundo durante 10 segundos.

## vmstat -s

Muestra estadísticas acumuladas:

    vmstat -s

Puede incluir:

- memoria total
- memoria usada
- memoria libre
- swap
- páginas de memoria
- interrupciones
- cambios de contexto

## free

`free` muestra un resumen de RAM y swap.

    free -h

Columnas habituales:

- total
- used
- free
- shared
- buff/cache
- available

## Diferencia entre vmstat y free

`free` es más directo y resumido.

`vmstat` aporta más detalle sobre comportamiento del sistema.

## Uso práctico

Si un sistema va lento:

1. mirar `free -h`
2. comprobar si falta RAM
3. usar `vmstat` para ver si hay presión de memoria o uso de swap

## Señales de problema

Puede haber problema si:

- hay poca memoria disponible
- se usa mucha swap
- aumenta mucho el intercambio con disco
- el sistema empieza a responder lentamente
