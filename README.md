# ASIX Notes

Repositorio personal de apuntes, prácticas y documentación técnica del CFGS ASIX (Administración de Sistemas Informáticos en Red).

La idea de este repositorio no es guardar PDFs sin más, sino reorganizar el contenido de clase para que sea fácil de consultar, reutilizar y enseñar.

Actualmente el repositorio está separado en dos grandes bloques:

- **SISTEMAS**: prácticas de implantación, administración, monitorización y soporte de sistemas operativos.
- **REDES/CCNA**: espacio preparado para apuntes y prácticas de redes basadas en CCNA.

---

## 🔗 Apuntes originales en la nube

Aquí puedes añadir los enlaces a las carpetas donde tienes guardados los PDFs originales.

### SISTEMAS

- Tema 1 - Fundamentos de sistemas operativos: [LINK_AQUI]
- Tema 2 - Gestión básica de sistemas operativos: [LINK_AQUI]
- Tema 3 - Implementación y acceso a dominios: [LINK_AQUI]
- Tema 4 - Directivas de configuración de dominios: [LINK_AQUI]
- Tema 5 - Gestión de la información en red: [LINK_AQUI]
- Tema 6 - Monitorización y auditorías de seguridad: [LINK_AQUI]
- Tema 7 - Administración y asistencia remota: [LINK_AQUI]

### REDES / CCNA

- CCNA - Introducción a las redes: [LINK_AQUI]

---

## 📂 Estructura del repositorio

```text
asix-notes/
├── README.md
├── SISTEMAS/
│   ├── 01-fundamentos-sistemas-operativos/
│   ├── 02-gestion-basica-sistemas-operativos/
│   ├── 03-implementacion-acceso-dominios/
│   ├── 04-directivas-configuracion-dominios/
│   ├── 05-gestion-informacion-red/
│   ├── 06-monitoraje-auditorias-seguridad/
│   └── 07-administracion-asistencia-remota/
│
└── REDES/
    └── CCNA/
```

---

# SISTEMAS

Bloque dedicado a sistemas operativos, administración de servidores, dominios, almacenamiento, monitorización, auditorías y soporte remoto.

## Tema 1 - Fundamentos de sistemas operativos

Ruta:

```text
SISTEMAS/01-fundamentos-sistemas-operativos/
```

Contenido principal:

- Virtualización con VirtualBox
- Instalación de Windows y Linux
- Dual boot
- GRUB
- Ventoy
- Arquitectura de Von Neumann
- Gestión de memoria
- Proceso de arranque

Prácticas relacionadas:

- PT1 - Virtualización
- PT2 - Instalación de sistemas operativos
- PT3 - Dual boot, GRUB y arranque
- PF1 - Repaso / examen de fundamentos

---

## Tema 2 - Gestión básica de sistemas operativos

Ruta:

```text
SISTEMAS/02-gestion-basica-sistemas-operativos/
```

Contenido principal:

- Terminales: CMD, PowerShell y Bash
- Ficheros y directorios
- Rutas y comodines
- Redirecciones
- Discos y particiones
- Red interna
- IP estática
- Firewall
- DNS básico en Windows Server y Ubuntu Server

Prácticas relacionadas:

- PT4 - Gestión de ficheros y directorios
- PT5 - Discos y particiones
- PT6 - Red interna y DNS
- PF2 - Repaso / examen de gestión básica

---

## Tema 3 - Implementación y acceso a dominios

Ruta:

```text
SISTEMAS/03-implementacion-acceso-dominios/
```

Contenido principal:

- Active Directory
- Controlador de dominio
- Usuarios, grupos y unidades organizativas
- Recursos compartidos
- Permisos NTFS
- Perfiles móviles
- Carpetas personales
- OpenLDAP
- LDIF
- phpLDAPadmin
- NFS para perfiles Linux

Prácticas relacionadas:

- PT7 - Active Directory
- PT8 - Recursos compartidos y perfiles
- PT9 - OpenLDAP
- PF3 - Repaso / examen de dominios

---

## Tema 4 - Directivas de configuración de dominios

Ruta:

```text
SISTEMAS/04-directivas-configuracion-dominios/
```

Contenido principal:

- GPOs
- Fondo de pantalla obligatorio
- Bloqueo de personalización
- Instalación de software por GPO
- WSUS
- AppLocker
- Ansible
- Inventarios
- Playbooks
- Repositorio local APT con apt-mirror y Apache2

Prácticas relacionadas:

- PT10 - GPO, WSUS, AppLocker y Ansible
- PF4 - Repaso / examen de directivas y automatización

---

## Tema 5 - Gestión de la información en red

Ruta:

```text
SISTEMAS/05-gestion-informacion-red/
```

Contenido principal:

- RAID
- Storage Spaces
- Hot Spare
- RAID en Linux con mdadm
- Copias de seguridad en Windows Server
- Backups con rsync y cron
- Restauración
- Cuotas de disco
- FSRM
- SMB
- NFS
- Permisos NTFS
- Permisos Linux
- CREATOR OWNER
- Sticky bit

Prácticas relacionadas:

- PT11 - RAID, backups y cuotas
- PT12 - Recursos compartidos SMB/NFS
- PF5 - Repaso / examen de gestión de información

---

## Tema 6 - Monitorización y auditorías de seguridad

Ruta:

```text
SISTEMAS/06-monitoraje-auditorias-seguridad/
```

Contenido principal:

- Monitor de confiabilidad
- Administrador de tareas
- Monitor de recursos
- Monitor de rendimiento
- Recopiladores de datos
- Alertas de rendimiento
- Monitorización Linux
- uptime
- top
- ps
- mpstat
- vmstat
- free
- df
- iostat
- Auditorías Windows con GPO
- Visor de eventos
- auditd
- ausearch
- aureport

Prácticas relacionadas:

- PT13 - Monitorización de sistemas operativos
- PT14 - Auditorías de sistemas operativos
- PF6 - Repaso / examen de monitorización y auditorías

---

## Tema 7 - Administración y asistencia remota

Ruta:

```text
SISTEMAS/07-administracion-asistencia-remota/
```

Contenido principal:

- Conexiones remotas
- mRemoteNG
- RDP
- SSH
- VNC
- OpenSSH Server
- Vino
- UFW
- Firewall Windows
- rdesktop
- Incidencias informáticas
- Protocolo de incidencias
- Formulario de incidencias

Prácticas relacionadas:

- PT15 - Conexiones remotas
- Actividades RA8 - Incidencias y protocolos
- PF7 - Repaso / examen de administración remota

---

# REDES / CCNA

Bloque preparado para apuntes y prácticas de redes.

Ruta prevista:

```text
REDES/CCNA/
```

Contenido previsto:

- Fundamentos de redes
- Modelos OSI y TCP/IP
- Ethernet
- Switching
- Direccionamiento IPv4 e IPv6
- Subnetting
- Routing
- VLANs
- Seguridad básica
- Packet Tracer
- Prácticas del curso CCNA: Introducción a las redes

---

## 💻 Tecnologías trabajadas

- Windows Server
- Active Directory
- GPO
- WSUS
- AppLocker
- Linux Ubuntu
- Arch Linux
- VirtualBox
- CMD
- PowerShell
- Bash
- SSH
- RDP
- VNC
- mRemoteNG
- DNS / Bind9
- OpenLDAP
- NFS
- SMB
- RAID / Storage Spaces
- mdadm
- rsync
- cron
- Ansible
- UFW
- Firewall de Windows
- auditd

---

## 🎯 Objetivo del repositorio

- Tener apuntes técnicos claros y estructurados.
- Poder consultar prácticas rápidamente.
- Reutilizar comandos, procedimientos y soluciones.
- Preparar exámenes.
- Construir un portfolio técnico real.
- Mostrar trabajo práctico relacionado con sistemas y redes.

---

## 🧠 Nota personal

Gran parte del contenido original estaba organizado en PDFs y entregas de clase, con nombres tipo PT, PF y capturas.

Este repositorio reorganiza ese trabajo por áreas técnicas para que sea más fácil de entender, buscar y reutilizar.
