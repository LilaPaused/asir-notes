# Recopiladores de datos

## Qué son

Un recopilador de datos permite guardar métricas del sistema durante un periodo de tiempo.

A diferencia del gráfico en tiempo real, el recopilador puede programarse y generar informes.

## Ejemplo de recopilador personal

Nombre recomendado:

    personalXX

Contadores útiles:

- % de tiempo de procesador
- MB disponibles de memoria
- MB disponibles del disco de datos

## Crear recopilador

Ruta general:

    Monitor de rendimiento -> Conjuntos de recopiladores de datos -> Definido por el usuario

Pasos:

1. Crear nuevo conjunto recopilador.
2. Elegir creación manual.
3. Añadir contadores.
4. Elegir intervalo de muestreo.
5. Elegir ubicación de guardado.
6. Configurar programación.

## Programación laboral

Ejemplo de programación:

- lunes a viernes
- inicio a las 09:00
- duración de 8 horas

Esto simula una jornada laboral.

## Retención de datos

Si solo se quieren conservar los últimos 5 días:

- limitar la cantidad de recopilaciones guardadas
- eliminar las más antiguas antes de iniciar una nueva

## System Diagnostics

Windows incluye recopiladores del sistema como:

    System Diagnostics

Este genera un informe amplio con información sobre:

- CPU
- memoria
- servicios
- configuración del sistema
- diagnósticos
- advertencias

## Uso práctico

Un recopilador de datos sirve cuando quieres estudiar el rendimiento durante horas o días, no solo en un momento puntual.
