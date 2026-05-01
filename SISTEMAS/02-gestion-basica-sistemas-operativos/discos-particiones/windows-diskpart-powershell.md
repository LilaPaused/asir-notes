# Gestión de discos en Windows

## Entorno gráfico

Abrir Administración de discos:

    Win + X -> Administración de discos

Desde ahí se puede:

- inicializar discos
- elegir MBR o GPT
- crear volúmenes simples
- asignar letra
- formatear en NTFS
- poner etiqueta

## Crear volumen simple

Pasos:

1. Clic derecho sobre espacio no asignado
2. Nuevo volumen simple
3. Elegir tamaño
4. Asignar letra
5. Formatear en NTFS
6. Poner etiqueta

## Diskpart

Abrir diskpart:

    diskpart

Listar discos:

    list disk

Seleccionar disco:

    select disk 3

Limpiar disco:

    clean

Convertir a GPT:

    convert gpt

Crear partición primaria:

    create partition primary size=5111

Formatear:

    format fs=ntfs quick label="wdisc2121"

Asignar letra:

    assign letter=G

Ver volúmenes:

    list volume

## PowerShell

Ver discos:

    Get-Disk

Inicializar disco:

    Initialize-Disk -Number 3 -PartitionStyle GPT

Crear partición:

    New-Partition -DiskNumber 3 -Size 5GB -DriveLetter G

Formatear volumen:

    Format-Volume -DriveLetter G -FileSystem NTFS -NewFileSystemLabel "wdisc2121"

Ver particiones:

    Get-Partition

## Comandos útiles

Ver volúmenes:

    Get-Volume

Ver particiones de un disco:

    Get-Partition -DiskNumber 3

## Precaución

El comando clean de diskpart borra la tabla de particiones del disco seleccionado.

Antes de usarlo, comprobar muy bien el número de disco.
