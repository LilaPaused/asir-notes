# Permisos Linux para recursos compartidos

## Estructura básica

Linux usa permisos para:

- propietario
- grupo
- otros

Cada uno puede tener:

- lectura
- escritura
- ejecución

## Significado en archivos

r:

- leer contenido

w:

- modificar contenido

x:

- ejecutar archivo

## Significado en directorios

r:

- listar contenido

w:

- crear, borrar o renombrar entradas

x:

- entrar o atravesar el directorio

En directorios, x es clave para poder acceder.

## Notación octal

| Octal | Permisos |
|---:|---|
| 7 | rwx |
| 6 | rw- |
| 5 | r-x |
| 4 | r-- |
| 0 | --- |

Ejemplos:

    chmod 755 carpeta
    chmod 770 carpeta
    chmod 1777 carpeta

## Cambiar propietario

    sudo chown usuario:grupo carpeta

Ejemplo:

    sudo chown amenta:grupA /ShareResources/First

## Casos típicos

### Solo propietario total, grupo lectura, otros nada

    sudo chmod 750 carpeta

### Propietario y grupo total, otros nada

    sudo chmod 770 carpeta

### Todos pueden crear, pero sticky bit

    sudo chmod 1777 carpeta

## Caso First

Objetivo:

- propietario amenta
- grupo grupA
- propietario puede todo
- grupo solo lectura/acceso
- otros sin acceso

Comandos:

    sudo chown amenta:grupA /ShareResources/First
    sudo chmod 750 /ShareResources/First

## Caso Third con sticky bit

Objetivo:

- propietario y grupo con permisos totales
- resto puede acceder y crear
- nadie puede borrar lo que no es suyo

Ejemplo:

    sudo chmod 1777 /ShareResources/Third

Dependiendo del diseño también se puede ajustar propietario y grupo.

## Comprobaciones

Usar usuarios distintos:

    su - amenta
    su - kjones

Probar:

    cd /ShareResources/First
    touch prueba.txt
    rm archivo_de_otro_usuario.txt

## Resumen

En Linux, compartir por NFS no sirve de nada si los permisos del sistema de archivos no están bien diseñados.
