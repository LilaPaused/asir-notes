# Perfiles móviles y carpetas Home

## Perfil móvil

Un perfil móvil permite que el perfil del usuario se guarde en el servidor.

Así, cuando el usuario inicia sesión desde distintos equipos, puede conservar su entorno.

Ejemplos de datos que pueden seguir al usuario:

- escritorio
- documentos del perfil
- configuración básica de usuario

## Cuándo usar perfiles móviles

Tiene sentido cuando:

- varios usuarios comparten equipos
- los usuarios no tienen equipo fijo
- se quiere centralizar el perfil

No siempre es buena idea en entornos grandes o modernos, porque puede ralentizar inicios de sesión.

## Carpeta Home

La carpeta Home es una carpeta personal del usuario en el servidor.

Sirve para guardar documentos personales.

Ejemplo:

```text
\\wserver12\Home$\jmonfort
```

## Diferencia entre perfil móvil y Home

| Elemento | Función |
|---|---|
| Perfil móvil | Guarda configuración y perfil de usuario |
| Home directory | Carpeta personal para datos del usuario |

## Rutas típicas

Perfil móvil:

```text
\\wserver12\Profiles$\%username%
```

Home:

```text
\\wserver12\Home$\%username%
```

En Windows AD se puede usar `%username%` para que cada usuario genere su propia ruta.

## Configurar desde GUI

En Usuarios y equipos de Active Directory:

- Usuario
- Propiedades
- Perfil
- Ruta de perfil
- Carpeta particular

## Configurar perfil móvil con PowerShell

```powershell
Set-ADUser -Identity "jmonfort" -ProfilePath "\\wserver12\Profiles$\jmonfort"
```

## Configurar Home con PowerShell

```powershell
Set-ADUser -Identity "jmonfort" -HomeDirectory "\\wserver12\Home$\jmonfort" -HomeDrive "H:"
```

## Aplicar a varios usuarios

Ejemplo conceptual:

```powershell
Get-ADUser -Filter * -SearchBase "OU=PF31,DC=pf3112,DC=dom" | ForEach-Object {
    Set-ADUser $_ -ProfilePath "\\MYPDC\PM12$($_.SamAccountName)"
}
```

## Permisos recomendados

Para carpetas de perfiles:

- SYSTEM: Control total
- Administradores: Control total
- Usuario propietario: Control total sobre su carpeta

No debería poder entrar cualquier usuario en perfiles de otros.

## Comprobación

Después de iniciar sesión con el usuario de dominio:

1. Entrar en el servidor.
2. Revisar la carpeta de perfiles.
3. Confirmar que se creó una carpeta con el login.
4. Crear un fichero en el cliente y comprobar si aparece en el servidor si corresponde.

## Errores comunes

### Perfil no se crea

Causas posibles:

- ruta UNC incorrecta
- permisos SHARE incorrectos
- permisos NTFS incorrectos
- usuario no tiene acceso

### El usuario no puede iniciar sesión

Causas posibles:

- cuenta deshabilitada
- contraseña caducada
- usuario limitado a otro equipo
- equipo no unido correctamente al dominio

## Resumen rápido

- Perfil móvil: configuración del usuario en servidor.
- Home: carpeta personal de datos.
- Las rutas UNC deben ser correctas.
- Los permisos son la parte crítica.
