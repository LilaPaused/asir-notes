# RAID: conceptos base

## Qué es RAID

RAID significa Redundant Array of Independent Disks.

Es una técnica que permite combinar varios discos físicos para conseguir uno o varios objetivos:

- más rendimiento
- más tolerancia a fallos
- más capacidad útil
- mejor disponibilidad

## RAID no es backup

RAID ayuda a mantener el servicio funcionando si falla un disco, pero no sustituye una copia de seguridad.

Un RAID no te protege de:

- borrado accidental
- ransomware
- corrupción de datos
- errores humanos
- incendio o pérdida del servidor

## RAID 0

RAID 0 reparte datos entre varios discos.

Ventaja:

- mejora rendimiento
- suma capacidad

Desventaja:

- no hay redundancia
- si falla un disco, se pierde todo

## RAID 1

RAID 1 replica los datos en dos o más discos.

Ventaja:

- tolerancia a fallos
- si cae un disco, el otro conserva los datos

Desventaja:

- se pierde capacidad útil porque se duplica información

Ejemplo con 2 discos de 100 GB:

- capacidad total física: 200 GB
- capacidad útil: 100 GB

## RAID 5

RAID 5 usa paridad distribuida.

Requiere mínimo 3 discos.

Ventaja:

- tolera el fallo de un disco
- aprovecha mejor la capacidad que RAID 1

Desventaja:

- penaliza escritura
- si fallan dos discos, se pierden datos

Ejemplo con 3 discos de 100 GB:

- capacidad total física: 300 GB
- capacidad útil aproximada: 200 GB
- 100 GB equivalentes se usan para paridad

## RAID 0+1

RAID 0+1 combina striping y espejo.

Primero se crean conjuntos RAID 0 y luego se espejan entre sí.

Ejemplo con 4 discos de 100 GB:

- capacidad total física: 400 GB
- capacidad útil aproximada: 200 GB

## Hot Spare

Un Hot Spare es un disco de reserva.

No cuenta como capacidad útil mientras todo funciona bien.

Su función es entrar automáticamente cuando un disco del RAID falla.

Ejemplo:

- 3 discos para RAID 5
- 1 disco Hot Spare

Si falla un disco del RAID, el Hot Spare pasa a ocupar su lugar.

## Resumen rápido

| Tipo | Mínimo discos | Tolerancia a fallos | Capacidad útil aproximada |
|---|---:|---:|---|
| RAID 0 | 2 | 0 discos | suma total |
| RAID 1 | 2 | 1 disco | 50% |
| RAID 5 | 3 | 1 disco | total - 1 disco |
| RAID 0+1 | 4 | depende del fallo | 50% |

## Regla mental

- RAID 0: velocidad, pero peligro.
- RAID 1: espejo simple.
- RAID 5: equilibrio entre capacidad y tolerancia.
- Hot Spare: disco de reemplazo automático.
- Backup: recuperación real ante desastre.
