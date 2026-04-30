# Monitor de confiabilidad

## Qué es

El Monitor de confiabilidad de Windows permite ver la estabilidad del sistema a lo largo del tiempo.

Se abre con:

    perfmon /rel

Muestra un índice de estabilidad y registra problemas de hardware, software, errores de Windows, instalaciones, desinstalaciones y otros cambios relevantes.

## Índice de estabilidad

El índice de estabilidad es una puntuación que resume cómo de estable ha sido el sistema.

Baja cuando aparecen eventos críticos como:

- errores de aplicación
- cierres inesperados
- fallos de Windows
- problemas de hardware
- errores durante instalaciones o actualizaciones

## Tipos de eventos

El gráfico puede mostrar eventos como:

- errores críticos
- advertencias
- eventos informativos
- instalaciones de software
- actualizaciones
- errores de aplicaciones

## Uso práctico

Sirve para responder preguntas como:

- desde cuándo falla el sistema
- qué aplicación empezó a dar problemas
- si una actualización coincide con un fallo
- si el equipo se ha vuelto inestable después de instalar algo

## Comando rápido

    perfmon /rel

## Relación con otras herramientas

El Monitor de confiabilidad da una vista histórica y resumida.

Para análisis más técnico se complementa con:

- Visor de eventos
- Monitor de rendimiento
- Administrador de tareas
- Monitor de recursos
