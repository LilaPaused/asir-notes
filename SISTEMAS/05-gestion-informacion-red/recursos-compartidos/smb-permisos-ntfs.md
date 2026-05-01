# SMB y permisos NTFS

## Qué es SMB

SMB es el protocolo usado por Windows para compartir carpetas en red.

Ejemplo de ruta UNC:

    \\wserver12\Empresa

## Dos capas de permisos

En Windows hay dos capas:

1. Permisos de recurso compartido
2. Permisos NTFS

El permiso efectivo será la combinación más restrictiva.

## Permisos de recurso compartido

Se configuran al compartir la carpeta.

Permisos típicos:

- lectura
- cambiar
- control total

## Permisos NTFS

Se configuran en la pestaña Seguridad.

Permiten afinar mucho más.

Ejemplos:

- leer
- escribir
- modificar
- eliminar
- crear archivos
- crear carpetas
- atravesar carpeta
- leer datos

## Regla práctica

En entornos administrados suele ser mejor:

- dar permisos amplios en Share
- afinar realmente en NTFS

Ejemplo:

Share:

- Usuarios del dominio: Cambiar y Leer

NTFS:

- permisos concretos por grupo

## Denegar permisos

El permiso Denegar tiene prioridad sobre Permitir.

Hay que usarlo con cuidado.

Sirve para escenarios donde quieres impedir explícitamente una acción.

## Ejemplo: carpeta Empresa

Objetivo:

- Dirección puede crear, modificar y eliminar.
- Resto de departamentos solo leen.
- Resto de departamentos no pueden crear ni eliminar.

Grupos:

- GG_DIR_All_W -> escritura
- GG_DIR_All_R -> lectura
- GG_SYS_All_R -> lectura
- GG_SYS_All_W -> denegar escritura
- GG_SEG_All_R -> lectura
- GG_SEG_All_W -> denegar escritura
- GG_RED_All_R -> lectura
- GG_RED_All_W -> denegar escritura
- GG_SOP_All_R -> lectura
- GG_SOP_All_W -> denegar escritura

## Ejemplo: carpeta Academy

Objetivo:

- todos pueden ver estructura
- usuarios normales no pueden crear ni modificar en la raíz

Se puede denegar escritura a Usuarios del dominio solo en la carpeta raíz y archivos, evitando afectar subcarpetas que se configurarán aparte.

## Comprobación

Siempre probar con usuarios reales:

- usuario que debe poder escribir
- usuario que solo debe leer
- usuario que no debe acceder
- usuario que puede crear solo en su zona

## Errores comunes

- configurar solo el Share y olvidar NTFS
- aplicar Denegar demasiado arriba
- heredar permisos sin revisar
- dejar Usuarios del dominio con permisos excesivos
- no probar desde cliente

## Resumen

SMB publica el recurso. NTFS decide realmente quién puede hacer qué. Para permisos finos, la clave es diseñar grupos y aplicar permisos con herencia controlada.
