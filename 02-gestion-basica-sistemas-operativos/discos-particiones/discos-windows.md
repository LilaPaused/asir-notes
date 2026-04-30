# Gestión de discos en Windows

## Objetivo

Inicializar discos, crear particiones, formatearlas y asignar letras de unidad.

## Entorno gráfico

Abrir administración de discos:

- `Win + X`
- Administración de discos

Pasos:

1. Seleccionar disco nuevo.
2. Inicializar disco.
3. Elegir GPT.
4. Crear nuevo volumen simple.
5. Asignar tamaño.
6. Asignar letra.
7. Formatear en NTFS.
8. Poner etiqueta.

## GPT vs MBR

| Tipo | Uso |
|---|---|
| MBR | Antiguo, más limitado |
| GPT | Moderno, recomendado |

## Diskpart

Abrir:

- `diskpart`

Comandos básicos:

- `list disk`
- `select disk N`
- `clean`
- `convert gpt`
- `create partition primary size=5111`
- `format fs=ntfs quick label=wdisc2121`
- `assign letter=G`
- `list volume`

## PowerShell

Ver discos:

- `Get-Disk`

Inicializar:

- `Initialize-Disk -Number N -PartitionStyle GPT`

Crear partición:

- `New-Partition -DiskNumber N -Size 5GB -DriveLetter G`

Formatear:

- `Format-Volume -DriveLetter G -FileSystem NTFS -NewFileSystemLabel "wdisc2121"`

Ver particiones:

- `Get-Partition`

## Buenas prácticas

- Confirmar número de disco antes de usar `clean`.
- No tocar el disco del sistema.
- Usar etiquetas claras.
- Comprobar resultado en el explorador de archivos.
