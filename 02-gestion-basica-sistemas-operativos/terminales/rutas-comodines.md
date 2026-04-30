# Rutas y comodines

## Ruta absoluta

Una ruta absoluta empieza desde la raíz del sistema.

En Windows:

    C:\Users\alumne\Desktop

En Linux:

    /home/alumne/Desktop

## Ruta relativa

Una ruta relativa depende de la ubicación actual.

Ejemplo en Windows, estando en:

    C:\arbolito\Docs

Para referirse a C:\arbolito:

    ..

Para ir a Pictures:

    ..\Pictures

En Linux sería:

    ../Pictures

## Cuándo usar cada una

Ruta absoluta:

- cuando quieres evitar dudas
- cuando estás moviendo archivos entre ubicaciones lejanas
- en scripts que deben ejecutarse desde cualquier lugar

Ruta relativa:

- cuando trabajas dentro de una estructura concreta
- cuando el enunciado te obliga a no moverte de un directorio
- cuando quieres comandos más cortos

## Comodín asterisco

El asterisco sustituye cualquier cantidad de caracteres.

Ejemplos:

    *.txt
    *.jpg
    newyork*.txt
    *o*

## Comodín interrogante

El interrogante sustituye un solo carácter.

Ejemplo:

    foto?.jpg

Coincide con:

    foto1.jpg
    foto2.jpg

Pero no con:

    foto10.jpg

## Rangos

En Bash y PowerShell se pueden usar patrones de rango.

Ejemplo:

    newyork[34].txt

Coincide con:

    newyork3.txt
    newyork4.txt

## Llaves en Bash

Bash permite expansión con llaves.

Ejemplo:

    mkdir -p viatges/{africa,asia,europa}/{fotos,textos}

Crea varias rutas de golpe.

## Comodines útiles por sistema

| Acción | CMD | PowerShell | Bash |
|---|---|---|---|
| Todos los TXT | *.txt | *.txt | *.txt |
| Contiene o | *o* | *o* | *o* |
| Rango 3 o 4 | limitado | [34] | [34] |
| Varias opciones | no cómodo | arrays/listas | {a,b,c} |

## Consejo

Antes de mover o borrar con comodines, prueba listando primero.

Ejemplo:

    dir *o*
    Get-ChildItem *o*
    ls *o*

Luego ejecutas move, Move-Item o mv.
