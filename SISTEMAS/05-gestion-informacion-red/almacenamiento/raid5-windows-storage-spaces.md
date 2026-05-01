# RAID 5 en Windows con Storage Spaces

## Objetivo

Crear un sistema redundante en Windows Server usando Storage Spaces.

En la práctica se planifica un RAID 5 con Hot Spare:

- Disco 1: 100 GB
- Disco 2: 100 GB
- Disco 3: 100 GB
- Disco Hot Spare: 100 GB

Capacidad útil aproximada:

- 200 GB útiles
- 100 GB equivalentes para paridad
- 100 GB como reserva activa

## Requisito en VirtualBox

Para que Windows Server detecte correctamente los discos en Storage Spaces, puede ser necesario añadirlos bajo un controlador LsiLogic SAS.

Sin ese controlador, los discos pueden no aparecer correctamente en el panel de almacenamiento.

## Ruta en Windows Server

Desde el Administrador del servidor:

Servicios de archivos y almacenamiento -> Volúmenes -> Grupos de almacenamiento

## Crear la pool

Pasos:

1. Añadir los discos a la máquina virtual.
2. Arrancar Windows Server.
3. Abrir Administrador del servidor.
4. Entrar en Servicios de archivos y almacenamiento.
5. Ir a Grupos de almacenamiento.
6. Crear un nuevo grupo.
7. Seleccionar los discos físicos.
8. Marcar uno como Reserva activa si se quiere Hot Spare.
9. Finalizar la creación.

## Crear el disco virtual

Dentro de la pool:

1. Seleccionar la pool.
2. Crear nuevo disco virtual.
3. Elegir distribución Parity.
4. Seleccionar aprovisionamiento fijo.
5. Usar el tamaño máximo disponible.
6. Crear el disco virtual.

En Windows, Parity equivale a un comportamiento tipo RAID 5.

## Problema habitual

Puede ocurrir que el asistente gráfico falle al crear el disco virtual.

En ese caso, se puede terminar de crear desde PowerShell. Lo importante es entender que el problema no es de diseño del RAID, sino de la interfaz gráfica.

## Inicializar y formatear

Después de crear el disco virtual:

1. Abrir Administración de discos.
2. Inicializar el disco.
3. Usar GPT.
4. Crear un volumen simple.
5. Asignar letra.
6. Formatear en NTFS.

## Comprobaciones

Comprobar:

- que el disco aparece en el explorador
- que tiene la capacidad esperada
- que permite crear archivos
- que Storage Spaces lo muestra como correcto
- que los discos físicos están integrados en la pool

## Comandos útiles

Ver discos físicos desde PowerShell:

    Get-PhysicalDisk

Ver pools:

    Get-StoragePool

Ver discos virtuales:

    Get-VirtualDisk

## Resumen

Storage Spaces permite crear pools de discos y discos virtuales con redundancia. Para un escenario tipo RAID 5 se usa Parity. Si se añade Hot Spare, el sistema puede reconstruirse automáticamente cuando falla un disco.
