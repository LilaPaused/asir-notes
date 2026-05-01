# Backups y restauración

## Objetivo

Crear copias de seguridad de carpetas y restaurarlas si se eliminan datos.

## Windows: xcopy

Copiar directorio con contenido:

- `xcopy origen destino /E /I`

Opciones:

- `/E` copia subdirectorios, incluso vacíos
- `/I` asume que el destino es un directorio

## Windows: robocopy

Herramienta más robusta para copias grandes.

Copia normal:

- `robocopy origen destino /E`

Copia espejo:

- `robocopy origen destino /MIR`

Copiar atributos:

- `robocopy origen destino /E /COPYALL`

Ventajas:

- muestra informe final
- soporta reintentos
- útil para restauraciones grandes

## Linux: rsync

Copia conservando estructura:

- `rsync -a origen/ destino/`

Restauración con salida detallada:

- `rsync -av backup/ destino/`

## Diferencia importante

Con barra final:

- `origen/` copia el contenido de origen

Sin barra final:

- `origen` copia la carpeta origen dentro del destino

## Buenas prácticas

- Comprobar origen y destino antes de ejecutar.
- Cuidado con `/MIR`, porque puede borrar en destino lo que no exista en origen.
- Usar `rsync -av` para ver qué se copia.
- Hacer pruebas con carpetas pequeñas antes de usar datos importantes.
