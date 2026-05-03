# STP

## Problema que resuelve

La redundancia física entre switches puede crear bucles de capa 2.

Un bucle puede provocar:

- Tormentas de broadcast.
- Duplicación de tramas.
- Saturación de la red.
- Inestabilidad de la tabla MAC.

STP evita estos bucles bloqueando enlaces redundantes.

## Versiones

| Protocolo | Estándar | Característica |
|---|---|---|
| STP | IEEE 802.1D | Versión clásica |
| RSTP | IEEE 802.1w | Convergencia más rápida |

## Root Bridge

El Root Bridge es el switch principal dentro del árbol STP.

Se elige por el Bridge ID más bajo.

El Bridge ID se compone de:

- Prioridad
- MAC

## Roles de puertos

### Root Port

Puerto que llega al Root Bridge por el mejor camino.

### Designated Port

Puerto elegido para reenviar tráfico en un segmento.

### Alternate / Backup

Puerto bloqueado para evitar bucles.

## Estados de puertos

- Blocking
- Listening
- Learning
- Forwarding

## Costes habituales

| Velocidad | Coste |
|---|---|
| 10 Mbps | 100 |
| 100 Mbps | 19 |
| 1 Gbps | 4 |

## Pasos para resolver STP en examen

1. Elegir Root Bridge.
2. Todos los puertos del Root Bridge son Designated Forwarding.
3. Elegir un Root Port en cada switch no-root.
4. Elegir un Designated Port en cada segmento.
5. Bloquear el resto de puertos.

## Desempates

Si hay empate:

1. Menor coste al root.
2. Menor Bridge ID del vecino.
3. Menor Port ID.

## PVST

PVST permite tener una instancia de STP por VLAN.

Esto permite balancear tráfico entre switches usando roots diferentes por VLAN.

## Configuración básica

Elegir root primario:

```bash
conf t
spanning-tree vlan 10,20,30 root primary
end
wr
```

Configurar prioridad manual:

```bash
conf t
spanning-tree vlan 10 priority 4096
end
wr
```

Activar PortFast en puertos de acceso:

```bash
conf t
interface fa0/1
 spanning-tree portfast
end
wr
```

## Verificación

```bash
show spanning-tree
show spanning-tree vlan 10
```

## Regla rápida

Si hay un Root Port, el puerto opuesto en el mismo segmento suele ser Designated Port.
