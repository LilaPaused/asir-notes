# PF6 - Repaso de monitorización y auditorías

## Windows: carpeta compartida solo lectura

Para compartir ACADEMY con usuarios del dominio solo lectura:

1. Propiedades de carpeta.
2. Compartir.
3. Añadir `Usuarios del dominio`.
4. Permiso: lectura.
5. En NTFS, asegurar lectura y ejecución.
6. No permitir escritura/modificación.

## Windows: GPO de auditoría

Crear GPO:

    auditoriesXX

Vincularla al dominio.

Ruta:

    Configuración del equipo
    Configuración de Windows
    Configuración de seguridad
    Directivas locales
    Directiva de auditoría

Habilitar:

    Auditar el acceso a objetos

Marcar:

- Correcto
- Error

## Windows: auditoría de errores sobre carpeta

En ACADEMY:

1. Seguridad.
2. Opciones avanzadas.
3. Auditoría.
4. Añadir grupo `angles`.
5. Tipo: Error.
6. Acceso: Modificar / Escritura.
7. Aplicar a esta carpeta, subcarpetas y archivos.

## Comprobación

Usuario `ang1`:

- intenta crear carpeta
- falla
- aparece evento en Seguridad

Usuario `pmat`:

- también puede fallar por permisos
- pero no genera evento si no pertenece al grupo auditado

## Visor de eventos

Ruta:

    Visor de eventos -> Registros de Windows -> Seguridad

Buscar eventos de auditoría y revisar:

- SubjectUserName
- ObjectName
- AccessList
- Failure Reason

## Linux: instalar auditd

    sudo apt install auditd audispd-plugins

## Linux: directorio de prueba

Crear directorio:

    sudo mkdir /OSCAR_PETA

Ver permisos:

    ls -ld /OSCAR_PETA

Cambiar propietario y grupo:

    sudo chown enito:grupB /OSCAR_PETA

Asignar permisos:

    sudo chmod 750 /OSCAR_PETA

## Linux: auditoría persistente

Editar:

    sudo nano /etc/audit/rules.d/audit.rules

Añadir:

    -w /OSCAR_PETA -p w -k clauXX

Cargar reglas:

    sudo augenrules --load

Comprobar:

    sudo auditctl -l

## Linux: pruebas de escritura

Casos típicos:

- `enito` puede crear porque es propietario.
- `eteck` no puede escribir si solo tiene permisos de grupo `r-x`.
- `kjones` no puede acceder si no es propietario ni grupo.
- `sisadmin` con sudo puede forzar creación.

## Linux: buscar eventos

Por clave:

    sudo ausearch -k clauXX -i

Informe:

    sudo aureport -k -i > auditreportXX.log

## Monitorización Windows

Herramientas clave:

- `taskmgr`
- `resmon`
- `perfmon`
- `perfmon /rel`

## Monitorización Linux

Comandos clave:

- `uptime`
- `top`
- `ps aux`
- `mpstat`
- `vmstat`
- `free`
- `df -h -l`
- `iostat`

## Fallos típicos

- No ejecutar `gpupdate /force` después de cambiar una GPO.
- Auditar el grupo equivocado.
- Esperar eventos de usuarios que no están dentro del grupo auditado.
- Crear reglas con `auditctl` y olvidarse de hacerlas persistentes.
- Confundir permisos con auditoría.
- No usar `sudo` con comandos de auditd.
