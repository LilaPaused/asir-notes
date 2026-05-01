# CMD

## Qué es

CMD es la consola clásica de Windows. Permite ejecutar comandos para gestionar archivos, directorios, red, discos y procesos básicos del sistema.

No es tan potente como PowerShell, pero sigue siendo muy útil para administración básica y exámenes.

## Comandos básicos

| Acción | Comando |
|---|---|
| Ver ruta actual | cd |
| Cambiar de directorio | cd ruta |
| Listar contenido | dir |
| Crear directorio | mkdir nombre |
| Borrar directorio vacío | rmdir nombre |
| Borrar directorio con contenido | rmdir /s nombre |
| Borrar sin preguntar | rmdir /s /q nombre |
| Copiar archivo | copy origen destino |
| Mover archivo | move origen destino |
| Renombrar | ren antiguo nuevo |
| Mostrar contenido | type archivo.txt |
| Ver árbol | tree ruta |
| Ver árbol con archivos | tree ruta /f |

## Crear estructura de directorios

Ejemplo:

    mkdir viatges\africa\fotos viatges\africa\textos

También se puede crear más de una ruta en el mismo comando.

## Copiar estructura sin archivos

    xcopy origen destino /T /E

Opciones:

- /T copia solo estructura de carpetas
- /E incluye carpetas vacías

## Copiar estructura con archivos

    xcopy origen destino /E /I

Opciones:

- /E copia subdirectorios, incluidos vacíos
- /I asume que el destino es un directorio si hay duda

## Mostrar árbol de directorios

    tree viatges

Con archivos:

    tree viatges /f

Con caracteres ASCII para guardarlo correctamente en TXT:

    tree viatges /f /a > estructura.txt

## Mostrar contenido de archivos

Mostrar un archivo:

    type archivo.txt

Mostrar varios:

    type archivo1.txt archivo2.txt

Mostrar todos los TXT de un directorio:

    type *.txt

Paginar salida:

    type *.txt | more

## Redirecciones

Sobrescribir archivo:

    echo Texto > archivo.txt

Añadir al final:

    echo Texto >> archivo.txt

Añadir contenido de un archivo a otro:

    type origen.txt >> destino.txt

## Buscar archivos con comodines

Listar archivos con una letra concreta:

    dir viatges\*o* /S /B /A:-D

Opciones:

- /S busca recursivamente
- /B muestra salida simple
- /A:-D muestra solo archivos, no directorios

## Borrar directorios

Borrar sin confirmación:

    rmdir /s /q viatges\africa

Borrar pidiendo confirmación:

    rmdir /s viatges\asia

## Enlace simbólico

Crear enlace simbólico a un archivo:

    mklink destino origen

Ejemplo:

    mklink C:\Users\alumne\Desktop\myfavoriteplace.jpg C:\Users\alumne\viatges\europa\fotos\paris1.jpg

Nota: normalmente requiere CMD como administrador.

## Cuándo usar CMD

CMD es buena opción para:

- prácticas básicas
- rutas Windows
- copiar y mover archivos
- tree
- robocopy
- diskpart
- comandos rápidos de red
