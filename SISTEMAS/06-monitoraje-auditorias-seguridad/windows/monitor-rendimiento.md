# Monitor de rendimiento

## Qué es

El Monitor de rendimiento permite supervisar métricas concretas del sistema mediante contadores.

Se abre con:

    perfmon

## Contadores

Un contador mide un aspecto concreto del sistema.

Ejemplos:

- tiempo de procesador
- bytes de lectura de disco
- bytes de escritura de disco
- memoria disponible
- espacio libre en disco

## Añadir contadores

Pasos:

1. Abrir `perfmon`.
2. Ir a Monitor de rendimiento.
3. Clic derecho sobre el gráfico.
4. Agregar contadores.
5. Seleccionar el objeto que se quiere medir.
6. Añadir los contadores necesarios.

## Contadores de disco

Para ver actividad de disco se pueden usar:

- Bytes de lectura de disco
- Bytes de escritura de disco

Esto permite ver picos cuando se abren, crean, modifican o guardan archivos.

## Modos de visualización

El Monitor de rendimiento permite varios modos:

- línea
- histograma
- informe

## Uso práctico

Sirve para:

- detectar cuellos de botella
- medir rendimiento en tiempo real
- comprobar si una aplicación dispara el uso de disco
- crear recopiladores de datos
- crear alertas automáticas

## Diferencia con Monitor de recursos

El Monitor de recursos es más directo y visual.

El Monitor de rendimiento es más flexible y permite elegir exactamente qué métricas recoger.
