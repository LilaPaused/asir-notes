# Gestión de ficheros y directorios

## Objetivo

Saber crear, copiar, mover, renombrar, listar y eliminar ficheros y directorios desde terminal.

## Operaciones principales

| Acción | CMD | PowerShell | Bash |
|---|---|---|---|
| Crear carpeta | `mkdir` | `New-Item -ItemType Directory` | `mkdir` |
| Copiar carpeta | `xcopy /E /I` | `Copy-Item -Recurse` | `cp -r` |
| Mover | `move` | `Move-Item` | `mv` |
| Renombrar | `ren` | `Rename-Item` | `mv` |
| Eliminar | `rmdir /S` | `Remove-Item -Recurse` | `rm -r` |
| Ver archivo | `type` | `Get-Content` | `cat` |

## Árbol de directorios

En CMD:

- `tree viatges /F`

En Linux:

- `tree -a -A viatges`

En PowerShell se puede usar `Get-ChildItem -Recurse`, aunque visualmente no queda igual que `tree`.

## Buenas prácticas

- Usar rutas relativas cuando estás cerca del destino.
- Usar rutas absolutas cuando no quieres depender de la ubicación actual.
- Usar comodines para evitar repetir comandos.
- No usar administrador/root si no hace falta.
- Antes de borrar, comprobar con `dir`, `ls` o `Get-ChildItem`.

## Ejemplo de estructura

- `viatges/africa/fotos`
- `viatges/africa/textos`
- `viatges/europa/fotos`
- `viatges/europa/textos`
- `viatges/oceania/fotos`
- `viatges/oceania/textos`
