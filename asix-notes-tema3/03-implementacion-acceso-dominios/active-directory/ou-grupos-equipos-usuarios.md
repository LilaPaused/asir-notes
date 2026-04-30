# OUs, grupos, equipos y usuarios en Active Directory

## Unidad Organizativa

Una OU es un contenedor lógico dentro de Active Directory.

Sirve para organizar objetos y aplicar administración de forma ordenada.

Puede contener:

- usuarios
- grupos
- equipos
- otras OUs

## Buen diseño de OUs

No conviene crear OUs sin sentido.

Una estructura simple y clara para una PYME puede ser:

- OU raíz de empresa
- OUs por departamento
- objetos dentro de cada departamento

Ejemplo:

- `CacheConLeche`
  - `Direccion`
  - `Sistemas_Infraestructura`
  - `Redes_Conectividad`
  - `Seguridad_Tecnologica`
  - `Soporte_Tecnico`

## Usuarios

Los usuarios representan cuentas de personas o servicios.

Atributos importantes:

- nombre
- apellidos
- login
- contraseña
- departamento
- empresa
- grupos
- perfil móvil
- carpeta personal
- equipos permitidos para iniciar sesión

## Equipos

Los equipos representan ordenadores unidos o preparados para unirse al dominio.

Ejemplos de nomenclatura:

- `lap-DIR01`
- `desk-SYS01`
- `lap-RED01`

Una nomenclatura útil indica:

- tipo de equipo: portátil o escritorio
- departamento
- número

## Grupos

Los grupos permiten asignar permisos sin tocar usuario por usuario.

Regla importante:

No se dan permisos directamente a usuarios salvo casos muy concretos.

Se dan permisos a grupos y se meten usuarios en esos grupos.

## Estrategia AGGP

AGGP significa:

- Accounts
- Global Groups
- Permissions

Flujo:

Usuario -> Grupo Global -> Permiso sobre recurso

Es una estrategia simple y válida para una PYME o laboratorio con un solo dominio.

## Nomenclatura de grupos

Ejemplo:

- `GG_DIR_All_R`
- `GG_DIR_All_W`
- `GG_SYS_R_Servidores`
- `GG_SYS_W_Servidores`

Interpretación:

- `GG`: Global Group
- `DIR` o `SYS`: departamento
- `R`: lectura
- `W`: escritura
- parte final: rol o recurso

## Lectura vs escritura

Separar lectura y escritura evita dar más permisos de los necesarios.

Ejemplo:

- `GG_RED_R_Comunicaciones`: puede leer.
- `GG_RED_W_Comunicaciones`: puede modificar.

## Grupos globales

Para AGGP en un entorno sencillo:

- ámbito: Global
- tipo: Seguridad

## Equipos y usuarios permitidos

En las propiedades de un usuario se puede limitar desde qué equipos puede iniciar sesión.

Esto es útil para:

- usuarios con portátil asignado
- laboratorios de examen
- control de acceso por puesto

## Resumen rápido

- OU: organiza objetos.
- Usuario: cuenta de persona o servicio.
- Equipo: ordenador del dominio.
- Grupo: mecanismo correcto para permisos.
- AGGP: usuarios dentro de grupos y grupos asignados a permisos.
