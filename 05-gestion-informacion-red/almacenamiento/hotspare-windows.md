# Hot Spare en Windows

## Qué es un Hot Spare

Un Hot Spare es un disco de reserva que queda preparado para sustituir automáticamente a un disco fallido.

No forma parte de la capacidad útil mientras no hay fallos.

## Caso práctico

Escenario:

- RAID 5 con tres discos de 100 GB
- un cuarto disco de 100 GB como Hot Spare

Capacidad útil aproximada:

- 200 GB

## Cómo comprobarlo

Para probar el Hot Spare en laboratorio:

1. Apagar la máquina virtual.
2. Quitar un disco que forme parte del RAID.
3. No quitar el disco marcado como reserva activa.
4. Arrancar la máquina.
5. Revisar Storage Spaces.
6. Comprobar que el disco de reserva entra en funcionamiento.

## Resultado esperado

Al retirar un disco del RAID:

- la pool muestra advertencia
- los datos siguen accesibles
- el Hot Spare pasa a sustituir el disco perdido
- el volumen sigue montado

No debería aparecer como pérdida total de datos.

## Qué hacer en un caso real

En producción, después de que el Hot Spare entre en funcionamiento:

1. identificar el disco físico averiado
2. reemplazarlo por un disco nuevo
3. añadir el nuevo disco a la pool
4. dejarlo como nuevo Hot Spare
5. comprobar que la pool vuelve a estado saludable

## Diferencia entre advertencia y error

Una advertencia indica que el sistema sigue funcionando pero ha perdido margen de seguridad.

Un error grave indicaría que el volumen ya no puede mantener la integridad o disponibilidad.

## Resumen

El Hot Spare no evita que un disco falle, pero reduce el tiempo de exposición. El sistema no necesita esperar a que un técnico añada un disco para empezar la reconstrucción.
