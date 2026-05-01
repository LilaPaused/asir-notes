# PF5 Windows: RAID, cuotas, backups y SMB

## Bloques principales

En la parte Windows del tema se trabaja:

- cuotas de disco
- copias de seguridad
- RAID con Storage Spaces
- recursos compartidos SMB
- permisos NTFS avanzados
- comprobaciones desde cliente

## Cuotas de disco

Preguntas típicas:

- nombre de la cuota
- ruta donde se aplica
- límite máximo
- umbrales configurados
- acciones al superar un porcentaje
- comportamiento desde cliente

## Caso de cuota

Ejemplo:

- carpeta: D:\CarpetaProves
- límite: 222 MB
- aviso: 90%
- acción: registrar evento

Comprobaciones:

1. Copiar file1.
2. Ver porcentaje usado.
3. Copiar file2.
4. Comprobar evento.
5. Copiar file3.
6. Ver error al superar límite.

## Backups Windows Server

Preguntas típicas:

- instalar característica de copias de seguridad
- configurar copia incremental diaria
- cambiar programación desde el Programador de tareas
- crear tarea con .bat para backup completo
- comprobar destino

Destino de ejemplo:

    \\Winclient\b

## RAID Windows

Preguntas típicas:

- nombre de la pool
- cantidad de discos
- capacidad total
- nombre del disco virtual
- tipo de RAID
- capacidad útil
- función del Hot Spare

Ejemplo:

- pool: mypool
- 4 discos de 100 GB
- disco virtual: myVD
- distribución: Parity
- equivalente: RAID 5
- capacidad útil: unos 200 GB
- Hot Spare: reserva activa

## Fallo de disco

Al quitar un disco del RAID:

- la pool entra en advertencia
- los datos siguen accesibles
- el Hot Spare entra automáticamente
- habría que reemplazar el disco físico y añadir nuevo Hot Spare

## SMB y permisos NTFS

Escenarios:

- ACADEMY: todos leen, nadie crea en raíz
- LENGUAGES: grupos de idiomas acceden, materias no accede
- GERMAN: solo grupo alemán accede
- RESOURCES: profes escriben, alumnos leen
- DELIVERIES: alumnos crean y solo modifican lo suyo; profes modifican todo
- NOTICES: profesores crean/modifican sin borrar; estudiantes solo leen

## CREATOR OWNER en examen

Se usa cuando:

- varios alumnos entregan archivos
- cada alumno solo modifica lo suyo
- el profesor puede modificar todos

## Comprobaciones importantes

Siempre probar con usuarios concretos:

- profesor de la materia
- alumno de la materia
- usuario de otro grupo
- otro alumno del mismo grupo

## Comandos útiles

Ver árbol de carpetas en PowerShell:

    tree X:

Crear archivo grande:

    fsutil file createnew archivo.bin 100000000

Ver GPO o sesión no aplica aquí, pero sí comprobar usuario:

    whoami

## Fallos a evitar

- confundir permisos Share con NTFS
- aplicar Denegar demasiado arriba
- olvidar CREATOR OWNER
- no probar con usuarios distintos
- no comprobar eventos de cuota
- pensar que RAID sustituye backup
