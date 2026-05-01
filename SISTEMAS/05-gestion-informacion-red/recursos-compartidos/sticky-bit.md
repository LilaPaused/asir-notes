# Sticky bit

## Qué es

El sticky bit es un permiso especial de Linux.

En directorios compartidos, permite que varios usuarios creen archivos, pero evita que un usuario borre o modifique archivos de otros si no es propietario.

## Ejemplo típico

El directorio /tmp usa sticky bit.

Permisos habituales:

    drwxrwxrwt

La t final indica sticky bit.

## Para qué sirve

Sirve para carpetas colaborativas.

Ejemplo:

- alumnos pueden entregar archivos
- cada alumno puede tocar lo suyo
- no pueden borrar entregas de otros
- el profesor puede tener permisos superiores

## Activar sticky bit

    sudo chmod +t directorio

Ejemplo:

    sudo chmod +t /shared/Compartido/Moduls/Apunts

## Permisos habituales

Para una carpeta donde todos pueden crear pero no borrar lo de otros:

    sudo chmod 1777 carpeta

El primer 1 activa sticky bit.

## Verificar

    ls -ld carpeta

Debe verse algo como:

    drwxrwxrwt

## Diferencia con permisos normales

Sin sticky bit:

- si un usuario tiene escritura en el directorio, puede borrar archivos de otros

Con sticky bit:

- puede crear
- puede borrar lo suyo
- no puede borrar lo de otros

## Comparación con CREATOR OWNER

En Windows se usa CREATOR OWNER para escenarios parecidos.

En Linux se usa sticky bit combinado con permisos de usuario/grupo.

## Resumen

El sticky bit es fundamental en carpetas compartidas donde muchos usuarios escriben pero no deben pisarse entre ellos.
