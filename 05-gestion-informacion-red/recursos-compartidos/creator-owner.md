# CREATOR OWNER

## Qué es

CREATOR OWNER es una entidad especial de Windows.

Representa al usuario que crea un archivo o carpeta.

Permite aplicar permisos dinámicos al propietario real del objeto creado.

## Para qué sirve

Sirve en carpetas colaborativas donde varios usuarios pueden crear contenido, pero no deberían modificar el contenido de otros.

Ejemplo:

- Josep crea una carpeta.
- Guillermina crea otra carpeta.
- Josep puede modificar lo suyo.
- Josep no puede borrar ni modificar lo de Guillermina.

## Escenario típico

Carpeta:

    \\wserver12\Direccion

Objetivo:

- todos los usuarios de Dirección pueden leer
- varios grupos pueden crear contenido en la raíz
- cada usuario solo puede modificar lo que él mismo crea

## Configuración conceptual

En la raíz:

- grupos de escritura: crear archivos y carpetas
- grupo general de lectura: leer y atravesar
- CREATOR OWNER: modificar sobre subcarpetas y archivos

## Aplicación correcta

CREATOR OWNER normalmente se aplica a:

- solo subcarpetas y archivos

No tiene sentido aplicarlo como permiso normal a la raíz para todo.

## Equivalencia mental con Linux

CREATOR OWNER se parece a una idea tipo sticky bit de Linux, aunque no es lo mismo.

En ambos casos se busca que un usuario no pueda borrar o modificar lo de otro en una carpeta compartida.

## Caso de entregas

En una carpeta de entregas:

- estudiantes pueden crear archivos
- estudiantes solo modifican los suyos
- profesores pueden modificar todos

Para eso:

- estudiantes: crear y leer
- CREATOR OWNER: modificar sus propios objetos
- profesores: control total o modificar

## Comprobaciones

Probar con dos usuarios:

1. Usuario A crea archivo.
2. Usuario B intenta modificarlo.
3. Usuario B debe fallar.
4. Usuario B crea su propio archivo.
5. Usuario B sí puede modificar el suyo.

## Resumen

CREATOR OWNER es clave cuando necesitas una carpeta donde todos puedan entregar o crear, pero nadie pueda tocar el trabajo de otro.
