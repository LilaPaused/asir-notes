# ausearch y aureport

## ausearch

`ausearch` permite buscar eventos de auditoría.

Buscar por clave:

    sudo ausearch -k clau12

Buscar por fichero:

    sudo ausearch -f /OSCAR_PETA

Buscar eventos de credenciales adquiridas:

    sudo ausearch -m CRED_ACQ -i

Buscar eventos de credenciales liberadas:

    sudo ausearch -m CRED_DISP -i

## Opción -i

La opción `-i` interpreta valores numéricos y los muestra de forma más legible.

Ejemplo:

    sudo ausearch -k clau12 -i

## aureport

`aureport` genera informes a partir de los logs de auditoría.

Ejemplo de informe de claves:

    sudo aureport -k -i

Guardar informe:

    sudo aureport -k -i > auditreport12.log

## Información útil en auditoría

En una entrada de auditoría interesa identificar:

- usuario
- comando
- fichero o directorio afectado
- resultado
- hora
- clave de auditoría

## Ejemplo de uso

Después de auditar `/OSCAR_PETA`, crear ficheros con varios usuarios y buscar:

    sudo ausearch -k clau12 -i

Así se puede ver qué usuario generó cada intento de escritura.

## CRED_ACQ y CRED_DISP

`CRED_ACQ` suele aparecer cuando un usuario adquiere credenciales al iniciar sesión o cambiar de usuario.

`CRED_DISP` aparece cuando esas credenciales se liberan, por ejemplo al cerrar sesión.

## Idea clave

`ausearch` sirve para investigar eventos concretos.

`aureport` sirve para resumir y generar informes.
