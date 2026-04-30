# Comandos básicos de Bash

## Directorios

Crear directorio:

- `mkdir carpeta`

Crear estructura completa:

- `mkdir -p viatges/africa/{fotos,textos}`

Listar:

- `ls`

Listar recursivo:

- `ls -R`

Árbol visual:

- `tree`

Árbol con archivos y ASCII:

- `tree -a -A`

Copiar:

- `cp -r origen destino`

Mover o renombrar:

- `mv origen destino`

Eliminar directorio con contenido sin preguntar:

- `rm -rf carpeta`

Eliminar preguntando:

- `rm -ri carpeta`

## Ficheros

Mostrar contenido:

- `cat archivo.txt`

Paginar:

- `cat archivo.txt | more`

Crear archivo con texto:

- `echo "texto" > archivo.txt`

Añadir contenido:

- `cat origen.txt >> destino.txt`

Buscar archivos:

- `find viatges -type f -name "*o*"`

Descargar archivo:

- `wget -P destino URL`

## Backup

Copia con rsync:

- `rsync -a origen/ destino/`

Restaurar mostrando detalle:

- `rsync -av backup/ destino/`

## Enlaces simbólicos

- `ln -s origen destino`
