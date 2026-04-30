# Comandos básicos de PowerShell

## Directorios

Crear directorio:

- `New-Item -ItemType Directory -Path carpeta`

Listar recursivamente:

- `Get-ChildItem -Recurse`

Copiar:

- `Copy-Item -Path origen -Destination destino -Recurse`

Mover:

- `Move-Item -Path origen -Destination destino`

Renombrar:

- `Rename-Item -Path antiguo -NewName nuevo`

Eliminar:

- `Remove-Item -Path carpeta -Recurse -Force`

Eliminar con confirmación:

- `Remove-Item -Path carpeta -Recurse -Confirm`

## Ficheros

Mostrar contenido:

- `Get-Content archivo.txt`

Crear o sobrescribir:

- `Set-Content -Path archivo.txt -Value "texto"`

Añadir contenido:

- `Add-Content -Path destino.txt -Value (Get-Content origen.txt)`

Paginar salida:

- `Get-Content archivo.txt | Out-Host -Paging`

Buscar archivos:

- `Get-ChildItem -Path . -Recurse -File -Filter "*o*"`

## Descargar archivos

- `Invoke-WebRequest -Uri "URL" -OutFile "archivo.jpg"`

`curl` puede funcionar como alias de `Invoke-WebRequest` en PowerShell.

## Enlaces simbólicos

- `New-Item -ItemType SymbolicLink -Path destino -Target origen`

Puede requerir permisos de administrador.
