# Bash

## Qué es

Bash es una shell común en sistemas Linux. Permite gestionar archivos, directorios, permisos, procesos, red, paquetes y servicios.

## Comandos básicos

| Acción | Comando |
|---|---|
| Ver ruta actual | pwd |
| Listar | ls |
| Listar recursivo | ls -R |
| Crear directorio | mkdir |
| Crear ruta completa | mkdir -p |
| Copiar archivo | cp |
| Copiar directorio | cp -r |
| Mover o renombrar | mv |
| Borrar archivo | rm |
| Borrar directorio vacío | rmdir |
| Borrar directorio con contenido | rm -r |
| Ver contenido | cat |
| Paginar | more o less |
| Buscar archivos | find |
| Crear enlace simbólico | ln -s |

## Crear estructura de directorios

Crear rutas completas:

    mkdir -p viatges/africa/{fotos,textos}

Crear varios continentes:

    mkdir -p viatges/{africa,asia,america,europa,oceania}/{fotos,textos}

## Mostrar árbol

En Linux puede que tree no venga instalado.

Instalar en Debian/Ubuntu:

    sudo apt install tree

Usar:

    tree viatges

Con archivos:

    tree -a viatges

Con salida ASCII:

    tree -a -A viatges

Guardar en archivo:

    tree -a -A viatges > estructura.txt

## Copiar directorios

    cp -r origen destino

Ejemplo:

    cp -r viatges/nord_america viatges/sud_america

## Mover archivos con comodines

Mover todas las imágenes JPG:

    mv *.jpg destino/

Mover varios patrones:

    mv {ams*.j*,lon*.j*,par*.j*,vie*.j*} viatges/europa/fotos/

Mover textos:

    mv {ams*.t*,lon*.t*,par*.t*,vie*.t*} viatges/europa/textos/

## Mostrar contenido

Un archivo:

    cat archivo.txt

Todos los TXT:

    cat *.txt

Paginar:

    cat *.txt | more

## Seleccionar archivos por patrón

Ejemplo:

    cat newyork[34].txt

Esto selecciona newyork3.txt y newyork4.txt.

## Redirecciones

Crear o sobrescribir:

    echo "texto" > archivo.txt

Añadir al final:

    echo "texto" >> archivo.txt

Añadir archivo a otro:

    cat origen.txt >> destino.txt

## Descargar archivo

    wget -P destino URL

## Buscar archivos

Buscar archivos con o en el nombre:

    find viatges -type f -name '*o*'

Opciones:

- -type f busca solo ficheros
- -name aplica patrón de nombre

## Borrar directorios

Sin preguntar:

    rm -rf viatges/africa

Preguntando:

    rm -ri viatges/asia

## Crear enlace simbólico

    ln -s origen destino

Ejemplo:

    ln -s ~/viatges/europa/fotos/paris1.jpg ~/Desktop/myfavoriteplace

## Buenas prácticas

- Revisar bien rutas antes de usar rm -rf.
- Usar tabulador para autocompletar.
- Usar comillas si hay espacios en rutas.
- Usar find para búsquedas potentes.
- Usar rsync para backups serios.
