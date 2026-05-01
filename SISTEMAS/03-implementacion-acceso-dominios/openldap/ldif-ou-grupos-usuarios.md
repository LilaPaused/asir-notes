# LDIF: crear OUs, grupos y usuarios

## Qué es LDIF

LDIF significa LDAP Data Interchange Format.

Es un formato de texto usado para crear, modificar o eliminar objetos LDAP.

## Crear una OU

Ejemplo:

```ldif
dn: ou=asix,dc=sis12,dc=et
objectClass: organizationalUnit
ou: asix
description: Administracio de sistemes informatics en xarxa
```

Cargar:

```bash
ldapadd -x -D "cn=admin,dc=sis12,dc=et" -W -f 01_ou_asix.ldif
```

## Crear varias OUs hijas

```ldif
dn: ou=sis1,ou=asix,dc=sis12,dc=et
objectClass: organizationalUnit
ou: sis1
description: Estudiants Sistemes informatics superiors 1

dn: ou=sis3,ou=asix,dc=sis12,dc=et
objectClass: organizationalUnit
ou: sis3
description: Estudiants Sistemes informatics superiors 3
```

Importante: dejar una línea en blanco entre entradas.

## Crear grupo posixGroup

```ldif
dn: cn=students1,ou=sis1,ou=asix,dc=sis12,dc=et
objectClass: posixGroup
cn: students1
gidNumber: 3121
```

Cargar:

```bash
ldapadd -x -D "cn=admin,dc=sis12,dc=et" -W -f grupo.ldif
```

## Crear usuario POSIX

Ejemplo:

```ldif
dn: uid=a1201,ou=sis1,ou=asix,dc=sis12,dc=et
objectClass: inetOrgPerson
objectClass: posixAccount
objectClass: shadowAccount
cn: Elias Vidal
sn: Vidal
uid: a1201
uidNumber: 1201
gidNumber: 3121
homeDirectory: /home/ldapusers/a1201
loginShell: /bin/bash
userPassword: {SSHA}HASH_DE_CONTRASEÑA
```

## Atributos importantes

| Atributo | Función |
|---|---|
| dn | ubicación única del objeto |
| objectClass | tipo de objeto |
| ou | unidad organizativa |
| cn | nombre común |
| uid | login del usuario |
| uidNumber | identificador numérico de usuario |
| gidNumber | grupo principal |
| homeDirectory | ruta home |
| loginShell | shell de inicio |

## Comprobar OUs

```bash
ldapsearch -x -LLL -b "dc=sis12,dc=et" "(objectClass=organizationalUnit)" dn
```

## Comprobar grupos

```bash
ldapsearch -x -LLL -b "dc=sis12,dc=et" "(objectClass=posixGroup)" dn
```

## Comprobar usuarios

```bash
ldapsearch -x -LLL -b "dc=sis12,dc=et" "(objectClass=posixAccount)" dn
```

## Errores comunes

### Falta línea en blanco entre entradas

LDAP interpreta mal el fichero.

Solución:

- separar cada objeto con una línea vacía.

### Atributo mal escrito

Ejemplo:

- `descripton` en vez de `description`

Solución:

- corregir el atributo.

### DN incorrecto

Si intentas crear un objeto dentro de una OU que no existe, fallará.

Solución:

- crear primero las OUs padre.

## Orden correcto de importación

1. OUs
2. Grupos
3. Usuarios

Los usuarios dependen de las OUs y de los grupos.
