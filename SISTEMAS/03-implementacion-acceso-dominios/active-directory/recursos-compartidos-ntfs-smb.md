# Recursos compartidos SMB y permisos NTFS

## Qué es un recurso compartido

Un recurso compartido es una carpeta accesible por red.

En Windows se accede mediante ruta UNC.

Ejemplo:

```text
\\wserver12\Empresa
\\wserver12\Home$
\\wserver12\Profiles$
```

## Ruta UNC

UNC significa Universal Naming Convention.

Formato:

```text
\\servidor\recurso
```

Ejemplo:

```text
\\MYPDC\PM12
```

## Permisos SHARE vs NTFS

Hay dos capas de permisos:

1. Permisos de recurso compartido.
2. Permisos NTFS.

La práctica recomendada es:

- SHARE amplio y simple.
- NTFS afinado y específico.

## Permisos SHARE

En Compartir avanzado se puede permitir acceso al recurso.

Ejemplo habitual:

- Usuarios del dominio: Cambiar + Leer
- Administradores: Control total

## Permisos NTFS

Los permisos NTFS determinan realmente qué puede hacer cada grupo dentro de la carpeta.

Ejemplos:

- Lectura
- Modificar
- Control total

## Carpetas ocultas con $

Un recurso terminado en `$` queda oculto al navegar la red.

Ejemplos:

- `Profiles$`
- `Home$`

No significa que sea seguro por sí solo; solo oculta el recurso en exploraciones normales.

## Estructura recomendada

Ejemplo para empresa:

```text
J:\Compartido\Empresa
J:\Compartido\Direccion
J:\Compartido\Sistemas
J:\Compartido\Redes
J:\Compartido\Seguridad
J:\Compartido\Soporte
J:\CoreData\Profiles
J:\CoreData\HomeFolders
```

## Crear carpeta con PowerShell

```powershell
New-Item -ItemType Directory -Path "J:\Compartido\Empresa"
```

## Compartir carpeta

```powershell
New-SmbShare -Name "Empresa" -Path "J:\Compartido\Empresa" -ChangeAccess "Usuarios del dominio"
```

## Asignar permisos NTFS con icacls

Lectura:

```powershell
icacls "J:\Compartido\Empresa" /grant "CACHECONLECHE\GG_SYS_All_R:(OI)(CI)R"
```

Modificar:

```powershell
icacls "J:\Compartido\Empresa" /grant "CACHECONLECHE\GG_DIR_All_W:(OI)(CI)M"
```

## Significado de OI, CI y M

- OI: Object Inherit. Los permisos heredan a ficheros.
- CI: Container Inherit. Los permisos heredan a subcarpetas.
- R: Read.
- M: Modify.

## Comprobar recursos compartidos

```powershell
Get-SmbShare
```

## Buen diseño de permisos

Ejemplo:

- Dirección escribe en Empresa.
- Otros departamentos leen Empresa.
- Cada departamento escribe en su área.
- Jefes pueden escribir en carpetas específicas.
- Usuarios no reciben permisos directos.

## Errores comunes

### Dar permisos directamente a usuarios

Mala práctica.

Mejor usar grupos.

### Afinar solo SHARE y olvidar NTFS

El permiso efectivo será el más restrictivo entre SHARE y NTFS.

### Usar Everyone sin pensar

En laboratorio puede funcionar, pero en empresa real no es lo ideal.

## Resumen rápido

- UNC: `\\servidor\recurso`.
- SHARE: acceso de red.
- NTFS: permisos reales.
- `$`: recurso oculto.
- Grupos: forma correcta de asignar permisos.
