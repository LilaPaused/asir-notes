# Dominios, bosques, árboles y tipos de controlador

## Dominio

Un dominio es una estructura lógica que centraliza la administración de objetos de una red.

Objetos típicos:

- usuarios
- grupos
- equipos
- impresoras
- unidades organizativas
- recursos compartidos

Ejemplo:

- `midom12.et`
- `cacheconleche.es`
- `pf3112.dom`

## Controlador de dominio

Un controlador de dominio es un servidor que almacena y gestiona la base de datos del dominio.

Funciones principales:

- autenticar usuarios
- validar equipos
- aplicar políticas
- resolver objetos del directorio
- replicar información con otros DCs

## PDC

PDC significa Primary Domain Controller.

En prácticas se suele usar para referirse al primer controlador de dominio del entorno.

En Active Directory moderno ya no funciona exactamente como en NT clásico, pero sigue siendo útil como forma de decir: servidor principal del dominio.

## Bosque

Un bosque es el contenedor lógico de mayor nivel en Active Directory.

Puede contener uno o varios árboles de dominios.

Ejemplo:

- Bosque: `midom12.et`
- Árbol principal: `midom12.et`
- Otro árbol dentro del bosque: `otrodom.sis`

## Árbol de dominios

Un árbol es un conjunto de dominios que comparten un espacio de nombres continuo.

Ejemplo:

- `midom12.et`
- `subdom.midom12.et`

Aquí `subdom.midom12.et` cuelga del dominio padre `midom12.et`.

## Nuevo árbol dentro de un bosque

Un dominio como `otrodom.sis` puede estar en el mismo bosque, pero ser raíz de otro árbol.

Eso significa que comparte bosque, pero no comparte el mismo espacio de nombres que `midom12.et`.

## Catálogo Global

El Catálogo Global almacena una copia parcial de objetos del bosque.

Sirve para búsquedas rápidas y autenticación en entornos con varios dominios.

En el primer controlador de dominio de un bosque normalmente se activa.

## RODC

RODC significa Read Only Domain Controller.

Es un controlador de dominio de solo lectura.

Se usa cuando interesa tener autenticación local en una sede, pero sin exponer una copia editable de la base de datos del dominio.

## Tipos habituales en prácticas

| Tipo | Descripción |
|---|---|
| DC normal | Controlador de dominio con escritura |
| PDC inicial | Primer controlador del dominio/bosque |
| GC | DC con catálogo global |
| RODC | DC de solo lectura |
| Subdominio | Dominio hijo dentro del mismo árbol |
| Nuevo árbol | Dominio raíz distinto dentro del mismo bosque |

## Ejemplo práctico de laboratorio

Dominio padre:

- `midomZZ.et`

Subdominio:

- `subdom.midomZZ.et`

Otro árbol:

- `otrodom.sis`

RODC adicional:

- controlador de solo lectura del dominio `midomZZ.et`

## Resumen rápido

- Dominio: estructura administrativa centralizada.
- DC: servidor que controla el dominio.
- Bosque: conjunto máximo de árboles de dominio.
- Árbol: dominios con espacio de nombres relacionado.
- GC: catálogo global para búsquedas en el bosque.
- RODC: controlador de dominio de solo lectura.
