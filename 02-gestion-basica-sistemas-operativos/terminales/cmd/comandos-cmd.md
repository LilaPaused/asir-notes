# Comandos básicos de CMD

## Directorios

Crear directorio:

- `mkdir carpeta`

Crear estructura:

- `mkdir viatges\africa\fotos viatges\africa\textos`

Mostrar árbol:

- `tree viatges /F`

Mostrar recursivamente:

- `dir viatges /S`

Renombrar:

- `ren america nord_america`

Copiar estructura vacía:

- `xcopy origen destino /T /E`

Copiar estructura con contenido:

- `xcopy origen destino /E /I`

Eliminar directorio con contenido sin preguntar:

- `rmdir /S /Q carpeta`

Eliminar preguntando:

- `rmdir /S carpeta`

## Ficheros

Mostrar contenido:

- `type archivo.txt`

Crear archivo con texto:

- `echo texto > archivo.txt`

Añadir contenido:

- `type origen.txt >> destino.txt`

Eliminar archivo:

- `del archivo.txt`

Mover archivo:

- `move origen destino`

## Backup

Copia robusta:

- `robocopy origen destino /MIR`

Copiar todo conservando más información:

- `robocopy origen destino /E /COPYALL`

## Enlaces simbólicos

Crear enlace simbólico a archivo:

- `mklink destino origen`

Requiere terminal con privilegios de administrador o modo desarrollador activo.
