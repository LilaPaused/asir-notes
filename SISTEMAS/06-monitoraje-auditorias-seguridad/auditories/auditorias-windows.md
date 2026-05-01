# Auditorías en Windows

## Qué son

Las auditorías de Windows permiten registrar eventos de seguridad.

Sirven para saber qué usuario hizo una acción, cuándo ocurrió y si fue correcta o fallida.

## Configuración por GPO

Ruta habitual:

    Administración de directivas de grupo
    Configuración del equipo
    Configuración de Windows
    Configuración de seguridad
    Directivas locales
    Directiva de auditoría

## Auditoría de inicio de sesión

Permite registrar intentos de inicio de sesión correctos o erróneos.

Ejemplo:

- usuario no autorizado intenta iniciar sesión
- contraseña incorrecta
- acceso denegado al servidor

## Auditoría de acceso a objetos

Permite auditar acceso a ficheros, carpetas y otros objetos.

Normalmente se habilita primero por GPO y luego se configura la auditoría concreta en el objeto NTFS.

## Correcto y Error

Se puede auditar:

- Correcto: cuando la acción se permite.
- Error: cuando la acción falla.

## Buenas prácticas

No auditar todo sin criterio.

Auditar demasiados eventos puede generar ruido y llenar registros rápidamente.

Mejor auditar acciones importantes:

- intentos fallidos de acceso
- cambios en carpetas sensibles
- borrado de archivos críticos
- escritura en recursos restringidos
- conexión de almacenamiento externo
