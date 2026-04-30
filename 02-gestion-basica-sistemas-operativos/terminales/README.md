# Terminales

## Objetivo

Conocer las diferencias básicas entre CMD, PowerShell y Bash.

## CMD

Terminal clásica de Windows.

Útil para:

- comandos simples
- scripts `.bat`
- gestión básica de archivos
- herramientas como `tree`, `dir`, `type`, `copy`, `xcopy`, `robocopy`

## PowerShell

Shell moderna de Windows basada en objetos.

Útil para:

- administración de sistema
- automatización
- gestión de servicios
- red
- discos
- Active Directory
- Windows Server

## Bash

Shell habitual en Linux.

Útil para:

- administración de sistema
- scripts `.sh`
- gestión de archivos
- permisos
- procesos
- red

## Comparación rápida

| Acción | CMD | PowerShell | Bash |
|---|---|---|---|
| Listar | `dir` | `Get-ChildItem` | `ls` |
| Crear carpeta | `mkdir` | `New-Item -ItemType Directory` | `mkdir` |
| Copiar | `copy` / `xcopy` | `Copy-Item` | `cp` |
| Mover | `move` | `Move-Item` | `mv` |
| Borrar | `del` / `rmdir` | `Remove-Item` | `rm` |
| Mostrar texto | `type` | `Get-Content` | `cat` |
