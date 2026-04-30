# Monitor de recursos

## Qué es

El Monitor de recursos ofrece una vista más detallada que el Administrador de tareas.

Se puede abrir desde el Administrador de tareas o ejecutando:

    resmon

## Pestañas disponibles

Las pestañas principales son:

- Información general
- CPU
- Memoria
- Disco
- Red

## Información general

Resume el uso de CPU, disco, red y memoria.

En cada gráfico suelen aparecer indicadores de colores para mostrar actividad y capacidad.

## CPU

Permite ver qué procesos consumen procesador.

También permite:

- finalizar procesos
- suspender procesos
- analizar esperas

## Memoria

Permite ver la memoria utilizada, disponible y reservada.

Sirve para detectar procesos que consumen demasiada RAM o situaciones en las que el sistema empieza a depender demasiado del disco.

## Disco

Muestra actividad de lectura y escritura.

Sirve para detectar qué proceso está generando muchas operaciones de disco.

## Red

Muestra conexiones, puertos y procesos que usan red.

Es útil para detectar tráfico inesperado o comprobar qué aplicación está usando la conexión.

## Ejemplo de uso

Si el sistema va lento:

1. Abrir `resmon`.
2. Revisar CPU.
3. Revisar Memoria.
4. Revisar Disco.
5. Localizar el proceso con mayor consumo.

## Diferencia con taskmgr

`taskmgr` da una vista rápida.

`resmon` permite investigar con más detalle qué proceso está usando cada recurso.
