# Administrador de tareas

## Qué es

El Administrador de tareas permite ver de forma rápida qué procesos están ejecutándose y qué recursos consumen.

Se abre con:

    taskmgr

## Pestañas principales

Las pestañas habituales son:

- Procesos
- Rendimiento
- Usuarios
- Detalles
- Servicios

## Procesos

Muestra aplicaciones y procesos en ejecución.

Métricas habituales:

- CPU
- Memoria
- Disco
- Red
- Estado
- Nombre del proceso

Se pueden añadir más columnas haciendo clic derecho sobre la cabecera de la tabla.

## Rendimiento

Muestra gráficos de uso de:

- CPU
- memoria
- disco
- red

En máquinas virtuales algunas métricas pueden no aparecer, por ejemplo ciertos datos de caché del procesador.

## Detalles

Muestra información más técnica de los procesos.

Aquí se ve el ejecutable real, el PID y otros datos.

## Servicios

Permite ver servicios activos o detenidos.

Desde aquí se puede comprobar si un servicio está en ejecución o detenido.

## Ver PID de un proceso

Ejemplo con Bloc de notas:

1. Abrir Bloc de notas.
2. Ir a Procesos.
3. Clic derecho sobre el proceso.
4. Ir a detalles.
5. Leer el PID.

## Finalizar proceso por PID

Desde CMD:

    taskkill /F /PID 3252

Donde:

- `/F` fuerza el cierre.
- `/PID` indica el identificador del proceso.

## Uso práctico

Sirve para detectar procesos que consumen demasiada CPU, demasiada RAM o que se han quedado bloqueados.
