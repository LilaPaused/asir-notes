# Administración de Active Directory con PowerShell y CSVDE

## Por qué automatizar

Crear objetos desde GUI está bien para aprender, pero no escala.

Cuando tienes muchas OUs, grupos, usuarios o equipos, es mejor usar:

- PowerShell
- CSVDE
- ficheros CSV

## PowerShell para OUs

Crear OU:

```powershell
New-ADOrganizationalUnit -Name "CacheConLeche" -Path "DC=cacheconleche,DC=es" -ProtectedFromAccidentalDeletion $true
```

Comprobar:

```powershell
Get-ADOrganizationalUnit -Filter *
```

Crear OU con descripción:

```powershell
New-ADOrganizationalUnit -Name "PF31" -Path "DC=pf3112,DC=dom" -Description "Unitat Organitzativa de la prova"
```

## PowerShell para grupos

Crear grupo global de seguridad:

```powershell
New-ADGroup -Name "GG_DIR_All_R" -SamAccountName "GG_DIR_All_R" -GroupCategory Security -GroupScope Global -Path "OU=Direccion,OU=CacheConLeche,DC=cacheconleche,DC=es"
```

Crear grupo dominio local de seguridad:

```powershell
New-ADGroup -Name "GrupA" -SamAccountName "GrupA" -GroupCategory Security -GroupScope DomainLocal -Path "OU=PF31,DC=pf3112,DC=dom"
```

Comprobar:

```powershell
Get-ADGroup -Filter *
```

## PowerShell para equipos

Crear equipo:

```powershell
New-ADComputer -Name "lap-DIR01" -Path "OU=Direccion,OU=CacheConLeche,DC=cacheconleche,DC=es"
```

Comprobar:

```powershell
Get-ADComputer -Filter *
```

## PowerShell para usuarios

Crear usuario básico:

```powershell
New-ADUser -Name "Jose Monfort" -GivenName "Jose" -Surname "Monfort" -SamAccountName "jmonfort" -UserPrincipalName "jmonfort@pf3112.dom" -Path "OU=PF31,DC=pf3112,DC=dom" -Enabled $true
```

Añadir a grupo:

```powershell
Add-ADGroupMember -Identity "GrupA" -Members "jmonfort"
```

Asignar atributos:

```powershell
Set-ADUser -Identity "jmonfort" -Department "Informática" -Company "ET"
```

Comprobar grupos del usuario:

```powershell
Get-ADPrincipalGroupMembership jmonfort
```

## CSVDE

CSVDE permite importar y exportar objetos de Active Directory usando CSV.

Exportar grupo:

```powershell
csvde -f grupA.csv -r "(cn=GrupA)"
```

Importar objetos:

```powershell
csvde -i -f grupB.csv
```

Usar `-k` para ignorar errores no críticos o entradas ya existentes:

```powershell
csvde -i -f usuarios.csv -k
```

## Limitaciones de CSVDE

CSVDE sirve bien para:

- OUs
- grupos
- usuarios básicos
- equipos

Pero tiene limitaciones:

- no asigna contraseñas de forma cómoda
- no añade usuarios a grupos mediante `memberOf`
- para permisos SMB/NTFS no es la herramienta adecuada

Para tareas más avanzadas conviene usar PowerShell.

## Campos típicos en CSVDE

OU:

```csv
dn,objectClass,ou
"OU=PF31,DC=pf3112,DC=dom",organizationalUnit,PF31
```

Grupo:

```csv
dn,objectClass,cn,sAMAccountName,groupType
"CN=GrupB,OU=PF31,DC=pf3112,DC=dom",group,GrupB,GrupB,-2147483644
```

## Resumen rápido

- GUI: bien para entender.
- PowerShell: mejor para administración real.
- CSVDE: útil para importaciones masivas simples.
- CSVDE no sustituye a PowerShell para todo.
