# Implementación y acceso a dominios

Este bloque recoge la administración de servicios de directorio en Windows Server y Ubuntu Server.

El objetivo no es memorizar asistentes, sino entender qué se está construyendo: un dominio, sus objetos, sus servicios de nombre, sus permisos y la forma en la que los clientes acceden a esos recursos.

## Contenido

### Active Directory

- [Promocionar servidor a controlador de dominio](./active-directory/promocion-pdc.md)
- [Dominios, bosques, árboles y tipos de controlador](./active-directory/dominios-bosques-arboles-dc.md)
- [OUs, grupos, equipos y usuarios](./active-directory/ou-grupos-equipos-usuarios.md)
- [Administración con PowerShell y CSVDE](./active-directory/csvde-powershell-ad.md)
- [Recursos compartidos SMB y permisos NTFS](./active-directory/recursos-compartidos-ntfs-smb.md)
- [Perfiles móviles y carpetas Home](./active-directory/perfiles-moviles-home-directories.md)
- [Unir cliente Windows al dominio](./active-directory/unir-cliente-dominio.md)

### OpenLDAP

- [Instalación y configuración base](./openldap/openldap-instalacion-base.md)
- [LDIF: OUs, grupos y usuarios](./openldap/ldif-ou-grupos-usuarios.md)
- [ldapsearch, ldapmodify y ldapdelete](./openldap/ldapsearch-ldapmodify-ldapdelete.md)
- [phpLDAPadmin](./openldap/phpldapadmin.md)
- [NSS y PAM con LDAP](./openldap/nss-pam-autenticacion-ldap.md)
- [NFS para perfiles LDAP](./openldap/nfs-perfiles-ldap.md)

### Repaso de examen

- [PF3 Windows AD](./examenes/pf3-windows-ad.md)
- [PF3 OpenLDAP](./examenes/pf3-openldap.md)

## Ideas clave

Un dominio centraliza usuarios, grupos, equipos y permisos.

Active Directory implementa servicios de directorio en Windows usando LDAP, DNS, Kerberos y otros componentes.

OpenLDAP permite construir un servicio de directorio en Linux, normalmente gestionado mediante ficheros LDIF, comandos LDAP y herramientas como phpLDAPadmin.

## Mapa mental rápido

- AD DS: servicio de directorio de Windows.
- DNS: imprescindible para localizar servicios del dominio.
- DC: controlador de dominio.
- GC: catálogo global.
- RODC: controlador de dominio de solo lectura.
- OU: contenedor lógico para organizar objetos.
- Grupo: mecanismo para asignar permisos de forma ordenada.
- SMB: compartición de carpetas en Windows.
- NTFS: permisos reales sobre archivos/carpetas.
- LDAP: protocolo de consulta y modificación de directorios.
- LDIF: formato de texto para crear o modificar objetos LDAP.
- NSS/PAM: integración de usuarios LDAP con el inicio de sesión Linux.
