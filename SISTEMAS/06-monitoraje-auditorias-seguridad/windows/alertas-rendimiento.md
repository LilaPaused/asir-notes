# Alertas de rendimiento

## Qué son

Una alerta de rendimiento permite ejecutar una acción cuando una métrica supera un umbral.

Ejemplo:

- si la CPU supera el 80%
- iniciar un recopilador de datos
- registrar información para análisis posterior

## Ejemplo

Crear un recopilador llamado:

    CPUXX

Que recoja:

    % de tiempo de procesador

Con intervalo de muestra:

    5 segundos

## Crear alerta

Nombre recomendado:

    myCPUalertXX

Condición:

    CPU > 80%

Acción:

    lanzar el recopilador CPUXX

## Prueba de carga

Para probar una alerta de CPU se puede abrir software pesado o ejecutar tareas que generen carga.

En laboratorio también se puede usar un bucle o herramienta de estrés, pero hay que hacerlo con cuidado.

## Para qué sirve

Permite capturar información justo cuando se produce un problema.

Esto es mejor que mirar el sistema después, cuando quizá el problema ya ha desaparecido.

## Idea clave

Monitorizar es observar.

Alertar es reaccionar cuando algo supera un límite.
