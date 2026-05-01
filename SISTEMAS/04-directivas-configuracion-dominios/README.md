# Directivas de configuración de dominios

Este bloque recoge apuntes sobre gestión centralizada de equipos mediante directivas de dominio.

El tema se divide en dos mundos:

- Windows Server y Active Directory: GPO, WSUS, instalación de software y AppLocker.
- Linux: Ansible, repositorios APT locales, NFS y playbooks para configuración centralizada.

## Contenido

### Windows / Active Directory

- [Conceptos de GPO](./windows/gpo-conceptos.md)
- [Fondo de pantalla obligatorio](./windows/gpo-fondo-pantalla.md)
- [Instalación de software por GPO](./windows/gpo-instalacion-software.md)
- [WSUS](./windows/wsus.md)
- [AppLocker](./windows/applocker.md)

### Linux

- [Ansible Server](./linux/ansible-server.md)
- [Playbooks básicos](./linux/playbooks-basicos.md)
- [Repositorio local APT](./linux/repositorio-local-apt.md)

### Repaso

- [PF4 - Repaso](./examenes/pf4-repaso.md)

## Idea clave

Una directiva de dominio permite aplicar una configuración a varios usuarios o equipos desde un punto central.

En Windows esto se trabaja principalmente con GPOs dentro de Active Directory.

En Linux, una forma equivalente de automatizar configuraciones es usar Ansible junto con SSH, inventarios y playbooks.
