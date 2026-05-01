# Gestión de memoria

## Qué es

La gestión de memoria es la función del sistema operativo encargada de administrar la memoria principal.

El sistema operativo decide:

- qué procesos se cargan en memoria
- cuánto espacio ocupa cada proceso
- qué zonas están libres
- qué zonas están ocupadas
- cómo se traduce una dirección lógica a una dirección física

## Tipos principales

Hay dos métodos importantes:

1. Paginación
2. Segmentación

## Paginación

La paginación divide la memoria en bloques de tamaño fijo.

- La memoria lógica se divide en páginas.
- La memoria física se divide en marcos.
- Las páginas se colocan dentro de marcos.

## Ventajas de la paginación

- Permite usar memoria no contigua.
- Evita la fragmentación externa.
- Facilita la gestión automática de memoria.
- Es muy usada en sistemas modernos.

## Inconvenientes de la paginación

- Puede generar fragmentación interna.
- Requiere tablas de páginas.
- La traducción de direcciones añade complejidad.

## Fragmentación interna

Ocurre cuando un bloque reservado no se aprovecha por completo.

Ejemplo:

- marco de 4 KB
- proceso usa 3 KB
- sobra 1 KB dentro del marco

Ese espacio sobra, pero queda reservado.

## Segmentación

La segmentación divide la memoria en bloques de tamaño variable llamados segmentos.

Cada segmento representa una parte lógica del programa.

Ejemplos:

- código
- datos
- pila
- heap

## Ventajas de la segmentación

- Se adapta mejor a la estructura lógica de los programas.
- Permite separar partes del proceso.
- Facilita ciertos controles de permisos.

## Inconvenientes de la segmentación

- Puede generar fragmentación externa.
- Es más difícil encontrar huecos disponibles.
- Puede requerir compactación de memoria.

## Fragmentación externa

Ocurre cuando hay memoria libre, pero está repartida en huecos pequeños.

Puede haber 6 MB libres en total, pero si están separados en huecos pequeños, un proceso que necesita 5 MB contiguos no podrá cargarse.

## Comparación rápida

| Método | Tamaño de bloques | Fragmentación típica | Idea principal |
|---|---|---|---|
| Paginación | Fijo | Interna | Divide en páginas y marcos |
| Segmentación | Variable | Externa | Divide según partes lógicas |

## Para examen

La paginación divide la memoria en bloques fijos y evita la fragmentación externa, aunque puede producir fragmentación interna. La segmentación divide la memoria en bloques variables según partes lógicas del programa, pero puede producir fragmentación externa.
