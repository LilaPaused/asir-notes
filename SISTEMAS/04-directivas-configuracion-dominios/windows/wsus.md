# WSUS - Windows Server Update Services

## Qué es WSUS

WSUS permite centralizar las actualizaciones de Windows dentro de una organización.

En vez de que cada cliente descargue actualizaciones directamente desde Internet, los equipos del dominio consultan al servidor WSUS.

## Ventajas

- control centralizado de actualizaciones
- aprobación manual de parches
- ahorro de ancho de banda
- separación por grupos de equipos
- integración con GPO

## 1. Instalar rol WSUS

En Windows Server:

Administrador del servidor
Agregar roles y características
Windows Server Update Services

Durante la instalación se debe indicar una ruta para almacenar las actualizaciones.

Ejemplo:

\\wserver12\Updates12

También puede usarse ruta local:

J:\Updates12

## 2. Preparar carpeta de actualizaciones

Crear carpeta para almacenar actualizaciones.

Ejemplo:

J:\Updates12

Compartirla si se usa ruta UNC.

Debe tener permisos suficientes para que WSUS pueda escribir.

## 3. Configurar WSUS

Después de instalar, abrir el asistente de configuración de WSUS.

Opciones habituales:

- sincronizar desde Microsoft Update
- elegir idiomas
- elegir productos
- elegir clasificaciones
- configurar horario de sincronización

## 4. Idiomas

Seleccionar solo los idiomas necesarios.

Ejemplo:

- English
- Spanish

Esto evita descargar actualizaciones innecesarias.

## 5. Productos

No conviene marcar todo Windows porque descarga demasiado.

Para una práctica con Windows 10:

- desmarcar Windows general
- marcar solo Windows 10

## 6. Clasificaciones

Según la práctica, pueden dejarse las preseleccionadas o elegir:

- Critical Updates
- Security Updates
- Updates
- Upgrades

## 7. Crear grupo de equipos

En la consola WSUS:

Computers
All Computers
Add Computer Group

Ejemplo:

equipswsus12

## 8. Crear GPO para clientes WSUS

Abrir:

gpmc.msc

Crear GPO vinculada al dominio o a la OU de clientes.

Ejemplo:

WSUS

## 9. Configurar actualizaciones automáticas

Ruta:

Configuración del equipo
Plantillas administrativas
Componentes de Windows
Windows Update
Configurar Actualizaciones automáticas

Estado:

Habilitada

Opción típica:

3 - Descargar automáticamente y notificar instalación

## 10. Especificar servidor WSUS interno

Ruta:

Configuración del equipo
Plantillas administrativas
Componentes de Windows
Windows Update
Especificar la ubicación del servicio Windows Update en la intranet

Habilitar e indicar:

http://wserver12.cacheconleche.es:8530

Tanto para detección como para estadísticas.

## 11. Habilitar destinatarios del lado cliente

Ruta:

Configuración del equipo
Plantillas administrativas
Componentes de Windows
Windows Update
Habilitar destinatarios del lado cliente

Habilitar e indicar el grupo WSUS:

equipswsus12

## 12. Aprobar actualizaciones

En WSUS:

Updates
Seleccionar actualización
Approve
Elegir grupo
Install

## 13. Comprobar en cliente

Actualizar directivas:

gpupdate /force

Ver GPO aplicada al equipo:

gpresult /r /scope computer

En Windows Update debería aparecer un aviso similar a:

Algunas opciones las administra la organización.

## Importante

gpresult /r puede no mostrar la GPO si esta afecta al equipo.

Usar:

gpresult /r /scope computer

## Problemas comunes

### El cliente no aparece en WSUS

Revisar:

- GPO aplicada al equipo
- nombre correcto del grupo WSUS
- URL con puerto 8530
- DNS funcional
- conectividad al servidor

### Windows Update sigue usando Internet

Revisar la directiva:

Especificar la ubicación del servicio Windows Update en la intranet

Debe estar habilitada con la URL correcta.

### No aparecen actualizaciones

Revisar:

- productos seleccionados
- clasificaciones
- sincronización completada
- actualizaciones aprobadas
