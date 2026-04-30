# PF3 OpenLDAP - Repaso

## Bases de datos de OpenLDAP

OpenLDAP puede usar más de una base de datos o backend.

En una instalación típica hay:

- base de configuración: `cn=config`
- base de datos del dominio: por ejemplo `dc=sis12,dc=et`

La primera guarda configuración del servidor.

La segunda guarda los objetos del dominio LDAP.

## NSS y PAM

### NSS

NSS permite que Linux consulte usuarios y grupos en LDAP además de en archivos locales.

Prueba clave:

```bash
getent passwd
getent group
```

### PAM

PAM gestiona autenticación y sesiones.

Permite iniciar sesión con usuarios LDAP y crear su home al primer login si está configurado.

## Datos básicos del servidor

Comandos útiles:

```bash
hostname
ip a
cat /etc/ldap/ldap.conf
sudo slapcat
```

Datos típicos:

- hostname
- IP
- BASE
- URI
- administrador del dominio

Administrador típico:

```text
cn=admin,dc=pf32,dc=et
```

## Importar LDIFs

Orden correcto:

1. OUs
2. grupos
3. usuarios

Comandos:

```bash
ldapadd -x -D "cn=admin,dc=pf32,dc=et" -W -f ous.ldif
ldapadd -x -D "cn=admin,dc=pf32,dc=et" -W -f grups.ldif
ldapadd -x -D "cn=admin,dc=pf32,dc=et" -W -f usuaris.ldif
```

## Errores típicos en LDIF

- atributo mal escrito
- falta línea en blanco entre objetos
- DN padre inexistente
- UID duplicado
- `gidNumber` mal asignado
- objectClass incompleto

## Buscar solo entradas

OUs:

```bash
ldapsearch -x -LLL -b "dc=pf32,dc=et" "(objectClass=organizationalUnit)" dn
```

Grupos:

```bash
ldapsearch -x -LLL -b "dc=pf32,dc=et" "(objectClass=posixGroup)" dn
```

Usuarios:

```bash
ldapsearch -x -LLL -b "dc=pf32,dc=et" "(objectClass=posixAccount)" dn
```

## Configurar cliente en LAN

Netplan:

- IP del cliente
- máscara
- DNS si procede
- ruta si hace falta

Hosts:

```text
192.168.100.100 ldap.pf32.et ldap
```

Comprobar:

```bash
ping 192.168.100.100
ping ldap.pf32.et
```

## Configurar ldap.conf en cliente

```text
BASE dc=pf32,dc=et
URI ldap://ldap.pf32.et
```

Comprobar:

```bash
ldapsearch -x
```

## Modificar gidNumber de grupo

LDIF:

```ldif
dn: cn=grupA,ou=primera,dc=pf32,dc=et
changetype: modify
replace: gidNumber
gidNumber: 1999
```

Aplicar:

```bash
ldapmodify -x -D "cn=admin,dc=pf32,dc=et" -W -f modify_group.ldif
```

Si algún usuario tenía el `gidNumber` antiguo, hay que actualizarlo también.

## Mover usuario de OU

LDIF:

```ldif
dn: uid=enito,ou=primera,dc=pf32,dc=et
changetype: modrdn
newrdn: uid=enito
deleteoldrdn: 1
newsuperior: ou=segona,dc=pf32,dc=et
```

## phpLDAPadmin

Crear usuario:

- elegir OU correcta
- Generic User Account
- nombre y login
- grupo principal
- uidNumber 3004 si lo pide el examen
- revisar atributos después de crear

## NFS para perfiles

Servidor:

```bash
sudo exportfs -v
ls -ld /perfilsldap
```

Cliente:

```bash
sudo apt install nfs-common
sudo mkdir -p /home/users
sudo mount IP_SERVIDOR:/perfilsldap /home/users
```

Persistente en `/etc/fstab`:

```text
IP_SERVIDOR:/perfilsldap /home/users nfs defaults 0 0
```

## NSS y PAM para login LDAP

Instalar paquetes necesarios, reconfigurar ldap-auth-config y revisar:

```text
/etc/nsswitch.conf
/etc/pam.d/common-session
```

Línea útil para crear home:

```text
session optional pam_mkhomedir.so skel=/etc/skel umask=077
```

## Prueba final

```bash
getent passwd usuarioLDAP
su - usuarioLDAP
pwd
```

Comprobar en servidor que se ha creado el perfil/home en `/perfilsldap`.

## Checklist rápido

- LDIFs importados.
- ldapsearch funciona.
- cliente resuelve servidor LDAP.
- ldap.conf correcto.
- gidNumber corregido.
- usuario movido de OU.
- phpLDAPadmin funciona.
- NFS montado.
- NSS muestra usuarios LDAP.
- PAM permite login.
- home se crea en servidor.
