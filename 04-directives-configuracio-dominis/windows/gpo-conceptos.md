# GPO - Conceptos básicos

## Qué es una GPO

Una GPO, o Group Policy Object, es una directiva de grupo usada en dominios Active Directory.

Permite aplicar configuraciones centralizadas a:

- usuarios
- equipos
- dominios completos
- unidades organizativas
- grupos concretos mediante filtrado de seguridad

## Para qué sirve

Las GPOs permiten administrar equipos del dominio sin tener que configurarlos uno por uno.

Ejemplos:

- establecer un fondo de pantalla obligatorio
- bloquear cambios de personalización
- instalar programas automáticamente
- configurar Windows Update contra un WSUS interno
- aplicar reglas de AppLocker
- ejecutar scripts de inicio o cierre de sesión

## Dónde se gestionan

La herramienta habitual es:

gpmc.msc

Nombre completo:

Administración de directivas de grupo

## Vinculación

Una GPO no hace nada solo por existir.

Debe estar vinculada a:

- dominio
- OU
- sitio

Ejemplo:

Si una GPO se vincula al dominio, puede afectar a todos los usuarios/equipos del dominio.

Si se vincula a una OU llamada segunda, solo afectará a los objetos que estén dentro de esa OU, salvo herencias o bloqueos.

## Configuración de equipo y usuario

Dentro de una GPO hay dos ramas principales.

### Configuración de equipo

Se aplica al equipo.

Ejemplos:

- WSUS
- instalación de software asignada al equipo
- AppLocker
- servicios del sistema
- scripts de inicio

### Configuración de usuario

Se aplica al usuario que inicia sesión.

Ejemplos:

- fondo de pantalla
- restricciones de panel de control
- redirección de carpetas
- scripts de inicio de sesión
- software publicado al usuario

## Aplicar cambios

En cliente Windows:

gpupdate /force

Ver directivas aplicadas al usuario:

gpresult /r

Ver directivas aplicadas al equipo:

gpresult /r /scope computer

También puede usarse:

rsop.msc

## Error típico

Un error muy común es mirar solo gpresult /r y pensar que no se ha aplicado una GPO.

Si la GPO es de equipo, hay que revisar:

gpresult /r /scope computer

## Orden de aplicación

Orden típico:

1. Local
2. Site
3. Domain
4. OU

La OU más cercana al objeto suele tener prioridad, salvo configuraciones especiales como bloqueo de herencia o forzar vínculo.

## Buenas prácticas

- No tocar la Default Domain Policy sin necesidad.
- Crear GPOs separadas por objetivo.
- Usar nombres claros.
- Documentar a qué OU se vincula cada GPO.
- Probar primero con una OU pequeña.
- No mezclar muchas configuraciones distintas dentro de una sola GPO.

## Ejemplo de nombres

- GPO-Fondo-Corporativo
- GPO-WSUS-Clientes
- GPO-Instalar-NotepadPP
- GPO-Bloquear-AppLocker
