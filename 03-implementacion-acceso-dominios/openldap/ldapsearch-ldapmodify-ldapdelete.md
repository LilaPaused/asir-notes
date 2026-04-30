# ldapsearch, ldapmodify y ldapdelete

## ldapsearch

`ldapsearch` permite consultar objetos LDAP.

Consulta simple:

```bash
ldapsearch -x
```

Consulta con base:

```bash
ldapsearch -x -LLL -b "dc=sis12,dc=et"
```

Mostrar solo DN:

```bash
ldapsearch -x -LLL -b "dc=sis12,dc=et" "(objectClass=*)" dn
```

## Buscar OUs

```bash
ldapsearch -x -LLL -b "dc=sis12,dc=et" "(objectClass=organizationalUnit)" dn
```

## Buscar grupos

```bash
ldapsearch -x -LLL -b "dc=sis12,dc=et" "(objectClass=posixGroup)" dn cn gidNumber
```

## Buscar usuarios

```bash
ldapsearch -x -LLL -b "dc=sis12,dc=et" "(objectClass=posixAccount)" dn uid uidNumber gidNumber
```

## Buscar por atributo

Por correo:

```bash
ldapsearch -x -LLL -b "dc=sis12,dc=et" "(mail=usuario@dominio.local)"
```

Por móvil:

```bash
ldapsearch -x -LLL -b "dc=sis12,dc=et" "(mobile=*)"
```

## ldapmodify

`ldapmodify` modifica objetos existentes.

Ejemplo: cambiar `gidNumber` de un grupo.

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

## Cambiar atributo de usuario

```ldif
dn: uid=enito,ou=primera,dc=pf32,dc=et
changetype: modify
replace: gidNumber
gidNumber: 1999
```

## Mover usuario de OU

```ldif
dn: uid=enito,ou=primera,dc=pf32,dc=et
changetype: modrdn
newrdn: uid=enito
deleteoldrdn: 1
newsuperior: ou=segona,dc=pf32,dc=et
```

## Añadir atributos

```ldif
dn: uid=a1201,ou=sis1,ou=asix,dc=sis12,dc=et
changetype: modify
add: mail
mail: a1201@sis12.et
-
add: mobile
mobile: 600000000
```

## ldapdelete

Eliminar objeto:

```bash
ldapdelete -x -D "cn=admin,dc=sis12,dc=et" -W "uid=a1201,ou=sis1,ou=asix,dc=sis12,dc=et"
```

## Buenas prácticas

- Consultar antes de modificar.
- Guardar LDIF de cambios.
- Verificar después con ldapsearch.
- Cuidado con DN exactos.
- No borrar objetos sin comprobar dependencias.

## Flujo recomendado

1. `ldapsearch` para localizar el objeto.
2. Crear fichero `.ldif` de modificación.
3. Ejecutar `ldapmodify`.
4. Comprobar con `ldapsearch`.

## Resumen rápido

- `ldapsearch`: buscar.
- `ldapadd`: crear.
- `ldapmodify`: modificar.
- `ldapdelete`: eliminar.
