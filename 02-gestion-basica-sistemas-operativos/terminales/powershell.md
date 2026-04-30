# PowerShell

## Qué es

PowerShell es una consola avanzada de Windows orientada a administración del sistema.

Trabaja con objetos, no solo con texto, y permite automatizar tareas con scripts.

## Comandos básicos

| Acción | PowerShell |
|---|---|
| Listar contenido | Get-ChildItem |
| Crear elemento | New-Item |
| Copiar | Copy-Item |
| Mover | Move-Item |
| Renombrar | Rename-Item |
| Borrar | Remove-Item |
| Ver contenido | Get-Content |
| Escribir contenido | Set-Content |
| Añadir contenido | Add-Content |

## Alias comunes

| Alias | Comando real |
|---|---|
| ls | Get-ChildItem |
| dir | Get-ChildItem |
| cat | Get-Content |
| cp | Copy-Item |
| mv | Move-Item |
| rm | Remove-Item |

Aunque funcionen alias de CMD, en prácticas de PowerShell conviene usar comandos propios de PowerShell.

## Crear directorios

    New-Item -ItemType Directory -Path .\viatges\asia\fotos
    New-Item -ItemType Directory -Path .\viatges\asia\textos

Crear varias rutas:

    New-Item -ItemType Directory -Path .\viatges\asia\fotos, .\viatges\asia\textos

## Copiar directorios

    Copy-Item .\viatges\asia -Destination .\viatges\africa -Recurse

Copiar con fuerza si existe:

    Copy-Item .\viatges\asia -Destination .\viatges\africa -Recurse -Force

## Iterar con ForEach-Object

Ejemplo para copiar una estructura base a varios continentes:

    ".\viatges\africa", ".\viatges\america", ".\viatges\europa", ".\viatges\oceania" | ForEach-Object { Copy-Item .\viatges\asia -Destination $_ -Recurse -Force }

## Mostrar estructura recursiva

    Get-ChildItem -Recurse .\viatges

Si se quiere salida tipo árbol, puede usarse tree, aunque realmente es comando heredado de CMD:

    tree .\viatges /f

## Renombrar

    Rename-Item -Path .\viatges\america -NewName nord_america

## Mover archivos

    Move-Item -Path .\Desktop\PT4\*.jpg -Destination .\viatges\europa\fotos

## Ver contenido de archivos

    Get-Content .\viatges\europa\textos\*.txt

Paginar salida:

    Get-Content .\viatges\europa\textos\*.txt | Out-Host -Paging

## Rango de nombres

PowerShell permite patrones como:

    Get-Content .\viatges\nord_america\textos\newyork[34].txt

Esto permite seleccionar newyork3.txt y newyork4.txt en una sola orden.

## Añadir contenido de un archivo a otro

    Add-Content -Path .\newyork3.txt -Value (Get-Content .\newyork4.txt)

Alternativa rápida:

    Get-Content .\newyork4.txt >> .\newyork3.txt

## Crear archivo con contenido

    Set-Content -Path .\sidney1.txt -Value "L'opera de Sidney"

## Buscar archivos

Buscar archivos que contengan una letra o en el nombre:

    Get-ChildItem -Path .\viatges -Recurse -File -Filter "*o*"

## Borrar directorios

Sin confirmación:

    Remove-Item .\viatges\africa -Recurse -Force

Con confirmación:

    Remove-Item .\viatges\asia -Recurse -Confirm

## Crear enlace simbólico

    New-Item -ItemType SymbolicLink -Path .\Desktop\myfavoriteplace.jpg -Target C:\Users\alumne\viatges\europa\fotos\paris1.jpg

Nota: puede requerir PowerShell como administrador.

## Cuándo usar PowerShell

PowerShell es ideal para:

- administración Windows moderna
- automatizar tareas
- gestionar red y firewall
- gestionar discos
- gestionar roles de servidor
- trabajar con objetos del sistema
