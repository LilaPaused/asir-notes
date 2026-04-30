# OpenLDAP: instalación y configuración base

## Qué es OpenLDAP

OpenLDAP es una implementación libre del protocolo LDAP.

Permite crear un servicio de directorio en Linux para almacenar objetos como:

- usuarios
- grupos
- unidades organizativas
- atributos de identificación

## Paquetes necesarios

En Ubuntu Server:

```bash
sudo apt install slapd ldap-utils
```

- `slapd`: servidor OpenLDAP.
- `ldap-utils`: herramientas cliente como ldapsearch, ldapadd, ldapmodify.

## Comprobar servicio

```bash
sudo systemctl status slapd.service
```

Debe aparecer como:

```text
active (running)
```

## Reconfigurar slapd

```bash
sudo dpkg-reconfigure slapd
```

Opciones típicas:

- Omitir configuración inicial: No
- Dominio DNS: `sis12.et`
- Organización: `sis12`
- Contraseña de administrador: la definida en la práctica
- Base de datos: MDB o HDB según versión/práctica
- Purgar base de datos al eliminar slapd: No
- Mover base de datos antigua: Sí

## BASE y URI

Editar:

```bash
sudo nano /etc/ldap/ldap.conf
```

Ejemplo:

```text
BASE dc=sis12,dc=et
URI ldap://ldap.sis12.et
```

## Resolución simple con /etc/hosts

Si no hay DNS, se puede usar `/etc/hosts`.

Ejemplo:

```text
192.168.12.2 userver12 ldap.sis12.et
```

## Comprobar conexión

```bash
ldapsearch -x
```

Si funciona, devuelve entradas del dominio.

## Ver base de datos completa

```bash
sudo slapcat
```

Esto muestra el contenido de la base LDAP desde el servidor.

## Administrador del dominio LDAP

El administrador suele tener DN parecido a:

```text
cn=admin,dc=sis12,dc=et
```

## Eliminar configuración previa de Bind9

Si venías de práctica DNS y quieres empezar limpio:

```bash
sudo apt purge --autoremove bind9
```

## Resumen rápido

```bash
sudo apt install slapd ldap-utils
sudo systemctl status slapd.service
sudo dpkg-reconfigure slapd
sudo nano /etc/ldap/ldap.conf
sudo nano /etc/hosts
ldapsearch -x
sudo slapcat
```
