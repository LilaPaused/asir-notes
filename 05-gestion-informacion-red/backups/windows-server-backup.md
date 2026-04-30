# Backups en Windows Server

## Herramienta

Windows Server incluye la característica Copias de seguridad de Windows Server.

Sirve para programar y ejecutar copias de seguridad del servidor.

## Instalación

Desde Administrador del servidor:

Agregar roles y características -> Características -> Copias de seguridad de Windows Server

## Tipos de copia

Se puede configurar:

- copia del servidor completo
- copia personalizada
- copia programada
- copia única manual

## Copia del servidor completo

Es útil cuando se quiere poder restaurar el sistema completo.

Incluye:

- sistema
- configuración
- servicios
- datos seleccionados según el tipo de copia

## Destinos posibles

Windows Server permite guardar backups en:

- disco dedicado
- volumen
- carpeta compartida remota

## Disco dedicado

Ventaja:

- opción recomendada para backups del servidor
- Windows puede gestionar el disco para copias

Desventaja:

- puede quedar reservado para el sistema de backup
- no se usa como disco normal desde el explorador

## Carpeta compartida remota

Puede usarse una ruta UNC.

Ejemplo:

    \\winclient\b

Sirve si se quiere guardar el backup en otro equipo o recurso compartido.

## Copias incrementales

Una copia incremental guarda solo los cambios desde la copia anterior.

Ventajas:

- menos espacio
- menos tiempo

Desventaja:

- la restauración depende de la cadena de copias

## Programar una copia

Pasos generales:

1. Abrir Copias de seguridad de Windows Server.
2. Elegir Programación de copia de seguridad.
3. Seleccionar servidor completo o personalizada.
4. Elegir frecuencia.
5. Elegir hora.
6. Seleccionar destino.
7. Confirmar.

## Copia manual

Se puede lanzar una copia de una vez para comprobar que todo funciona.

Esto es útil antes de simular fallos.

## Comprobación

Hay que revisar:

- estado de la última copia
- destino donde se ha guardado
- logs o eventos
- espacio disponible
- posibilidad de restauración

## Buenas prácticas

- No guardar la única copia en el mismo volumen que los datos críticos.
- Probar restauraciones.
- Documentar frecuencia y destino.
- Usar incrementales para copias frecuentes.
- Mantener copias completas periódicas.
