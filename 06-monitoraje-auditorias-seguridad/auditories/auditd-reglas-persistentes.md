# Reglas persistentes con auditd

## Problema

Las reglas creadas con `auditctl` se pierden al reiniciar.

Para hacerlas permanentes hay que guardarlas en un fichero de reglas.

## Archivo de reglas

Ruta habitual:

    /etc/audit/rules.d/audit.rules

También se pueden usar archivos separados dentro de:

    /etc/audit/rules.d/

## Ejemplo de regla persistente

Auditar intentos de escritura sobre un directorio:

    -w /OSCAR_PETA -p w -k clau12

## Cargar reglas

Después de modificar reglas:

    sudo augenrules --load

Comprobar:

    sudo auditctl -l

## Ejemplo práctico

Crear directorio:

    sudo mkdir /OSCAR_PETA

Cambiar propietario y grupo:

    sudo chown enito:grupB /OSCAR_PETA

Permisos:

    sudo chmod 750 /OSCAR_PETA

Regla persistente:

    -w /OSCAR_PETA -p w -k clau12

## Permisos del ejemplo

Con permisos `750`:

- propietario: lectura, escritura y ejecución
- grupo: lectura y ejecución
- otros: sin acceso

Si `enito` es propietario, puede escribir.

Si `eteck` pertenece al grupo pero no es propietario, puede entrar pero no escribir.

Si `kjones` no pertenece, no puede acceder.

Un usuario con `sudo` puede forzar la creación.

## Idea clave

Auditd registra intentos según la regla, pero los permisos del sistema siguen siendo los que permiten o bloquean la acción.
