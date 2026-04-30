# Rutas, comodines y redirecciones

## Rutas absolutas

Indican la ubicación completa desde la raíz del sistema.

Windows:

- `C:\Users\usuario\Documents`

Linux:

- `/home/usuario/Documents`

## Rutas relativas

Dependen de la carpeta actual.

Ejemplos:

- `..` sube un nivel
- `.` representa la carpeta actual
- `Docs\archivo.txt`
- `../Pictures/imagen.jpg`

## Comodines

Permiten seleccionar varios archivos.

| Comodín | Significado |
|---|---|
| `*` | Cualquier cantidad de caracteres |
| `?` | Un solo carácter |
| `[3,4]` | Valores concretos en PowerShell/Bash |
| `[a-z]` | Rango de caracteres |

Ejemplos:

- `*.txt`
- `newyork[3,4].txt`
- `*o*`

## Redirecciones

Sobrescribir archivo:

- Windows / Linux: `>`

Añadir al final:

- Windows / Linux: `>>`

Ejemplos:

- `echo Hola > archivo.txt`
- `type origen.txt >> destino.txt`
- `cat origen.txt >> destino.txt`

## Pipes

Un pipe pasa la salida de un comando a otro.

Windows / Linux:

- `|`

Ejemplos:

- `dir /s | more`
- `cat *.txt | more`
- `Get-Content *.txt | Out-Host -Paging`
