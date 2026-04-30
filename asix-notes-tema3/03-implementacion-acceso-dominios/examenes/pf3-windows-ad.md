# PF3 Windows AD - Repaso

## Concepto de dominio

Un dominio es una estructura lógica que centraliza la administración de usuarios, equipos, grupos y recursos de una red.

En Windows Server, el dominio se gestiona mediante Active Directory Domain Services.

## LDAP en AD

LDAP significa Lightweight Directory Access Protocol.

Datos clave:

| Elemento | Valor |
|---|---|
| Protocolo | LDAP |
| Capa aproximada | Aplicación |
| Versión habitual | LDAPv3 |
| Puerto | TCP/389 |
| LDAP sobre SSL | TCP/636 |

## Ver configuración IP con PowerShell

```powershell
Get-NetIPConfiguration
```

Para ver más detalle:

```powershell
Get-NetIPAddress
Get-DnsClientServerAddress
```

## Instalar roles para PDC

Roles:

- Active Directory Domain Services
- DNS Server

Desde GUI:

- Administrador del servidor
- Agregar roles y características
- AD DS
- DNS
- Instalar

## Promocionar dominio

Ejemplo:

- nuevo bosque
- dominio: `pf3112.dom`
- DNS activado
- Catálogo Global activado
- RODC desactivado

## Comprobar DNS del dominio

En DNS Manager:

- zona directa del dominio
- registro A del servidor

Comandos desde cliente:

```cmd
nslookup mypdc.pf3112.dom
ping mypdc.pf3112.dom
```

## Crear OU con PowerShell

```powershell
New-ADOrganizationalUnit -Name "PF31" -Path "DC=pf3112,DC=dom" -Description "Unitat Organitzativa de la prova"
```

## Crear grupo desde GUI

En Usuarios y equipos de Active Directory:

- OU PF31
- Nuevo
- Grupo
- Nombre: GrupA
- Ámbito: Dominio local
- Tipo: Seguridad

## Exportar grupo con CSVDE

```powershell
csvde -f grupA.csv -r "(cn=GrupA)"
```

## Importar grupo con CSVDE

```powershell
csvde -i -f grupB.csv
```

## Crear usuario desde GUI

Crear usuario en OU PF31 con:

- nombre y apellidos
- login correspondiente
- contraseña
- marcar contraseña nunca caduca si lo pide el enunciado

## Añadir usuario a grupo y atributos

```powershell
Add-ADGroupMember -Identity "GrupA" -Members "jmonfort"
Set-ADUser -Identity "jmonfort" -Department "Informàtica" -Company "ET"
```

## Copiar usuario

Desde GUI:

- clic derecho sobre usuario
- Copiar
- nuevo nombre: Usuario Copia
- login: `ucopia`

Al copiar se conservan algunos atributos, pero conviene comprobarlos.

## Crear recurso compartido

Ejemplo:

- carpeta: `C:\PM12`
- recurso: `PM12`
- ruta UNC: `\\MYPDC\PM12`

## Perfil móvil

Ruta ejemplo:

```text
\\MYPDC\PM12\%username%
```

## Crear cuenta de equipo

En OU PF31:

- Nuevo
- Equipo
- nombre: `myclient`
- usuario autorizado para unirlo: `jmonfort`

## Configurar cliente

Cliente:

- IP de la red del servidor
- DNS primario: IP del DC

Comprobar:

```cmd
ping IP_SERVIDOR
ping mypdc.pf3112.dom
```

## Unir cliente al dominio

Si se precreó el equipo y se autorizó a un usuario concreto:

- `ucopia` puede fallar si no tiene permiso.
- `jmonfort` debería poder unirlo si fue autorizado.

## Verificar perfil móvil

1. Iniciar sesión con usuario de dominio.
2. Cerrar sesión.
3. Comprobar en el servidor que se creó carpeta de perfil.

## Checklist rápido

- IP y DNS correctos.
- AD DS y DNS instalados.
- Dominio promovido.
- Zona DNS creada.
- OU creada.
- Grupo creado.
- Usuario creado.
- Usuario añadido al grupo.
- Recurso compartido creado.
- Perfil móvil configurado.
- Cliente unido al dominio.
