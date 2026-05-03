# FHRP

## Concepto

FHRP, First Hop Redundancy Protocol, permite tener redundancia en la puerta de enlace.

El objetivo es que los hosts usen una IP virtual como gateway.

Si el router activo cae, otro router asume el rol.

## Protocolos

| Protocolo | Tipo | Roles |
|---|---|---|
| HSRP | Cisco | Active / Standby |
| VRRP | Estándar | Master / Backup |
| GLBP | Cisco | Balanceo de carga |

## Problema que resuelve

Si los hosts tienen como gateway un único router y ese router cae, pierden salida.

FHRP evita este punto único de fallo.

## Funcionamiento

- Se configura una IP virtual.
- Los hosts usan esa IP como gateway.
- Un router actúa como activo.
- Otro router queda en standby.
- Si el activo cae, el standby toma el control.

## HSRP básico

### Router activo

```bash
conf t
interface g0/1
 standby version 2
 standby 1 ip 192.168.1.254
 standby 1 priority 150
 standby 1 preempt
end
wr
```

### Router standby

```bash
conf t
interface g0/1
 standby version 2
 standby 1 ip 192.168.1.254
end
wr
```

## Preempt

Permite que el router con mayor prioridad recupere el rol activo cuando vuelve a estar disponible.

## Verificación

```bash
show standby
show standby brief
```

## Gateway en los hosts

Los hosts deben usar la IP virtual.

Ejemplo:

```text
192.168.1.254
```

## Errores típicos

- Configurar como gateway la IP física del router.
- No activar preempt cuando se espera recuperación automática.
- Usar grupos HSRP diferentes entre routers.
- Configurar mal la IP virtual.
