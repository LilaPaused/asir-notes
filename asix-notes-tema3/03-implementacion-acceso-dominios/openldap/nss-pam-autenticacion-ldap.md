# NSS y PAM con LDAP

## Objetivo

Configurar un cliente Linux para que pueda ver usuarios LDAP e iniciar sesión con ellos.

Para eso intervienen dos piezas:

- NSS
- PAM

## NSS

NSS significa Name Service Switch.

Permite que el sistema consulte usuarios y grupos en distintas fuentes.

Fuentes típicas:

- archivos locales: `/etc/passwd`, `/etc/group`
- LDAP

Cuando NSS está bien configurado, comandos como estos muestran usuarios LDAP:

```bash
getent passwd
getent group
```

## PAM

PAM significa Pluggable Authentication Modules.

Gestiona autenticación y sesiones.

Permite que un usuario LDAP pueda iniciar sesión en el sistema.

También puede crear automáticamente el home del usuario al primer login.

## Paquetes habituales

```bash
sudo apt install libnss-ldap libpam-ldap ldap-auth-config nscd
```

Según la versión de Ubuntu, pueden variar los paquetes.

## Reconfigurar ldap-auth-config

```bash
sudo dpkg-reconfigure ldap-auth-config
```

Datos típicos:

- URI: `ldap://ldap.sis12.et`
- Base: `dc=sis12,dc=et`
- Versión LDAP: 3
- Cuenta root LDAP: `cn=admin,dc=sis12,dc=et`

## Configurar NSS

Archivo:

```text
/etc/nsswitch.conf
```

Líneas importantes:

```text
passwd:         files ldap
group:          files ldap
shadow:         files ldap
```

## Comprobar NSS

```bash
getent passwd
getent group
```

Si no aparecen usuarios LDAP, revisar:

- conexión al servidor
- `/etc/ldap/ldap.conf`
- `/etc/nsswitch.conf`
- servicio nscd
- datos de ldap-auth-config

## Configurar PAM para crear home

Archivo habitual:

```text
/etc/pam.d/common-session
```

Añadir o comprobar:

```text
session optional pam_mkhomedir.so skel=/etc/skel umask=077
```

Esto crea el home del usuario cuando inicia sesión por primera vez.

## Cambiar contraseña LDAP

Para que los usuarios puedan cambiar contraseña, PAM debe estar correctamente configurado.

Comando:

```bash
passwd
```

## Prueba de login

Desde terminal:

```bash
su - usuarioLDAP
```

O desde login gráfico:

- Not Listed
- escribir UID
- contraseña LDAP

## Problema típico: getent no muestra usuarios

Solución posible:

```bash
sudo dpkg-reconfigure ldap-auth-config
sudo systemctl restart nscd
```

También revisar que el cliente resuelve el servidor LDAP.

## Resumen rápido

- NSS hace visibles usuarios y grupos LDAP al sistema.
- PAM permite autenticarlos.
- `pam_mkhomedir` crea el home al primer inicio.
- `getent passwd` es la prueba clave de NSS.
- `su - usuario` es la prueba rápida de autenticación.
