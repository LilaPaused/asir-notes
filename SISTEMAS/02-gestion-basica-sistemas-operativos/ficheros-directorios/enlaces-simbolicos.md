# Enlaces simbólicos

## Qué es un enlace simbólico

Un enlace simbólico es un acceso directo avanzado que apunta a otro archivo o directorio.

No contiene los datos reales, solo una referencia al destino.

## Windows CMD

Crear enlace simbólico a un archivo:

- `mklink destino origen`

Ejemplo:

- `mklink C:\Users\alumno\Desktop\myfavoriteplace.jpg C:\Users\alumno\viatges\europa\fotos\paris.jpg`

Puede requerir permisos de administrador.

## PowerShell

Crear enlace simbólico:

- `New-Item -ItemType SymbolicLink -Path destino -Target origen`

## Linux

Crear enlace simbólico:

- `ln -s origen destino`

Ejemplo:

- `ln -s ~/viatges/europa/fotos/paris.jpg ~/Desktop/myfavoriteplace.jpg`

## Comprobar enlace

En CMD:

- `dir`

En PowerShell:

- `Get-ChildItem`

En Linux:

- `ls -l`

## Diferencia con copia

Una copia duplica el archivo.

Un enlace apunta al archivo original.

Si el original se elimina o se mueve, el enlace puede romperse.
