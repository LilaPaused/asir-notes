# phpLDAPadmin

## Qué es phpLDAPadmin

phpLDAPadmin es una interfaz web para administrar OpenLDAP.

Permite crear, editar y eliminar objetos LDAP desde navegador.

## Acceso

Normalmente se accede desde el navegador usando la IP o nombre del servidor.

Ejemplo:

```text
http://ldap.sis12.et/phpldapadmin
```

## Login

DN típico de administrador:

```text
cn=admin,dc=sis12,dc=et
```

## Crear una OU

Pasos:

1. Seleccionar el contenedor padre.
2. Create a child entry.
3. Elegir Generic: Organisational Unit.
4. Escribir nombre de la OU.
5. Confirmar con Commit.

## Añadir descripción

Una vez creada la OU:

1. Abrir el objeto.
2. Add new attribute.
3. Seleccionar `description`.
4. Añadir texto.
5. Update Object.

## Crear grupo posixGroup

Para crear un grupo con `gidNumber`, conviene usar plantilla Default.

Pasos:

1. Create a child entry.
2. Elegir Default.
3. objectClass: `posixGroup`.
4. RDN: `cn`.
5. Rellenar `cn`.
6. Rellenar `gidNumber`.
7. Saltar atributos que no interesan si phpLDAPadmin los propone.
8. Commit.

## Crear usuario

Pasos:

1. Elegir OU correcta.
2. Create a child entry.
3. Generic: User Account.
4. Rellenar nombre, login y contraseña.
5. Revisar atributos POSIX.
6. Ajustar `uidNumber` si la plantilla lo genera automáticamente.
7. Confirmar.

## uidNumber automático

En algunas plantillas, phpLDAPadmin bloquea o genera automáticamente el `uidNumber`.

Solución:

- crear el usuario
- entrar al atributo `uidNumber`
- modificarlo
- guardar con Update Object

## Ventajas

- Visual.
- Útil para comprobar estructura.
- Facilita crear objetos sin escribir LDIF desde cero.

## Desventajas

- Es fácil crear objetos con atributos inconsistentes si no se entiende LDAP.
- Para cargas masivas es peor que LDIF.
- Algunas plantillas no encajan exactamente con la práctica.

## Comprobación desde terminal

Después de crear algo en phpLDAPadmin:

```bash
ldapsearch -x -LLL -b "dc=sis12,dc=et" "(objectClass=*)" dn
```

## Resumen rápido

phpLDAPadmin es cómodo para visualizar y editar, pero en una práctica seria conviene combinarlo con LDIF y comandos LDAP.
