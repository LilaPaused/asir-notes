# Auditoría de acceso a objetos

## Qué es

La auditoría de acceso a objetos permite registrar acciones sobre carpetas o archivos.

Ejemplo:

- un usuario intenta crear un fichero donde no tiene permisos
- un usuario intenta borrar una carpeta
- un usuario modifica un archivo sensible

## Paso 1: habilitar auditoría por GPO

Ruta:

    Configuración del equipo
    Configuración de Windows
    Configuración de seguridad
    Directivas locales
    Directiva de auditoría
    Auditar el acceso a objetos

Marcar:

- Correcto
- Error

Según el caso práctico, puede bastar con Error.

## Paso 2: configurar auditoría en la carpeta

Ruta:

    Propiedades de carpeta
    Seguridad
    Opciones avanzadas
    Auditoría

Añadir el grupo que se quiere auditar.

Ejemplo:

    grupo angles

Tipo:

    Error

Permisos auditados:

- escribir
- modificar
- crear archivos
- crear carpetas
- eliminar

Aplicar a:

    esta carpeta, subcarpetas y archivos

## Ejemplo práctico

Si una carpeta ACADEMY es solo de lectura y se auditan los errores de escritura del grupo `angles`, cuando el usuario `ang1` intente crear una carpeta se generará evento.

Si otro usuario que no pertenece a `angles` intenta lo mismo, puede fallar igual, pero no aparecerá en la auditoría configurada para `angles`.

## Idea clave

La auditoría no es lo mismo que el permiso.

El permiso decide si se puede hacer la acción.

La auditoría decide si esa acción queda registrada.
