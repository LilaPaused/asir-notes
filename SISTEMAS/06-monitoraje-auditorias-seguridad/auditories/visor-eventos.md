# Visor de eventos

## Qué es

El Visor de eventos permite consultar registros generados por Windows.

Se abre con:

    eventvwr.msc

## Registro de seguridad

Las auditorías suelen aparecer en:

    Registros de Windows -> Seguridad

## Filtrar eventos

Para encontrar auditorías concretas, conviene usar filtros.

Se puede filtrar por:

- nivel
- origen
- fecha
- ID de evento
- usuario

## Eventos de acceso a objetos

Cuando un usuario intenta acceder a una carpeta auditada, el evento puede incluir:

- usuario
- dominio
- nombre del objeto
- ruta afectada
- tipo de acceso solicitado
- si fue correcto o fallido

## Información útil dentro del evento

Campos importantes:

- SubjectUserName
- ObjectName
- AccessList
- AccessMask
- Failure Reason

## Ejemplo

Si un usuario intenta crear un fichero sin permisos en una carpeta auditada, el Visor de eventos puede mostrar la ruta del objeto, el usuario y el tipo de acceso fallido.

## Problemas comunes

Si no aparece nada:

- la GPO no se aplicó
- falta ejecutar `gpupdate /force`
- no se habilitó auditoría de acceso a objetos
- la carpeta no tiene entrada de auditoría
- se auditó el grupo equivocado
- se espera un evento de un usuario que no forma parte del grupo auditado
