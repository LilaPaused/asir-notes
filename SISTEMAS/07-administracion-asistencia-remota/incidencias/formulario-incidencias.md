# Formulario de incidencias

## Objetivo

Un formulario de incidencias permite que el usuario comunique un problema de forma ordenada.

Debe ser simple. Si se piden demasiados datos, el usuario lo rellenará mal o directamente no lo usará.

## Campos para el usuario

### Apartado de contacto

- ID de empleado.
- Correo electrónico.

### Apartado del dispositivo averiado

- Código del dispositivo.
- Descripción del problema.
- Si tiene datos para recuperar.

## Ejemplo de campos

| Campo | Obligatorio | Motivo |
|---|---|---|
| ID empleado | Sí | Identificar quién reporta |
| Correo | Sí | Contacto rápido |
| Código dispositivo | Sí | Localizar equipo afectado |
| Descripción | Sí | Entender el problema |
| Datos a recuperar | Sí | Evitar pérdida de información |

## Campos para el técnico

Cuando el técnico recibe la incidencia:

- número de ticket
- fecha de recepción
- técnico asignado
- categoría
- diagnóstico inicial
- actuación remota o presencial

Cuando la resuelve:

- fecha de resolución
- solución aplicada
- piezas usadas
- equipo sustituido
- garantía reclamada
- datos recuperados
- observaciones

## Recomendación de diseño

Separar el formulario en bloques:

1. Contacto.
2. Dispositivo.
3. Problema.
4. Datos importantes.
5. Envío.

## Criterio importante

El usuario no debería decidir la urgencia técnica si no tiene contexto.

La prioridad real debería asignarla el técnico o el sistema según impacto:

- usuario único afectado
- departamento afectado
- servicio crítico caído
- pérdida potencial de datos
- problema de seguridad
