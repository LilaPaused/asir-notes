# Gestión de la información en una red

Este bloque recoge apuntes y prácticas sobre almacenamiento seguro, recursos compartidos, permisos, copias de seguridad, cuotas y sistemas redundantes de discos.

No está organizado como “PT11”, “PT12” o “PF5”, sino por conceptos técnicos reales.

## Contenido

### Almacenamiento

- [RAID: conceptos base](./almacenamiento/raid-conceptos.md)
- [RAID 5 en Windows con Storage Spaces](./almacenamiento/raid5-windows-storage-spaces.md)
- [Hot Spare en Windows](./almacenamiento/hotspare-windows.md)
- [RAID en Linux con mdadm](./almacenamiento/raid-linux-mdadm.md)

### Copias de seguridad

- [Backups en Windows Server](./backups/windows-server-backup.md)
- [Backups en Linux con rsync y cron](./backups/linux-rsync-cron.md)
- [Restauración de backups](./backups/restauracion-backups.md)

### Cuotas

- [Cuotas en Windows Server](./cuotas/cuotas-windows-fsrm.md)
- [Cuotas en Linux](./cuotas/cuotas-linux.md)

### Recursos compartidos

- [SMB y permisos NTFS](./recursos-compartidos/smb-permisos-ntfs.md)
- [CREATOR OWNER](./recursos-compartidos/creator-owner.md)
- [NFS en Linux](./recursos-compartidos/nfs-linux.md)
- [Sticky bit](./recursos-compartidos/sticky-bit.md)

### Linux

- [Permisos Linux para recursos compartidos](./linux/permisos-linux-recursos.md)
- [Montaje permanente con fstab](./linux/fstab-montajes.md)

### Exámenes

- [PF5 Windows: RAID, cuotas, backups y SMB](./examenes/pf5-windows.md)
- [PF5 Linux: RAID, NFS, cuotas y permisos](./examenes/pf5-linux.md)

## Ideas clave

La gestión de la información en red no consiste solo en crear carpetas compartidas. También hay que pensar en:

- disponibilidad de los datos
- tolerancia a fallos
- recuperación ante errores humanos
- permisos correctos por usuario o grupo
- límites de uso mediante cuotas
- acceso desde clientes Windows y Linux
- comprobaciones reales desde usuarios distintos

Este tema mezcla administración Windows Server y Linux Server, por eso está dividido por tecnologías y no por práctica.
