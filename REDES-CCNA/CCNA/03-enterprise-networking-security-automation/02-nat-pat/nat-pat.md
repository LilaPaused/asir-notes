# NAT y PAT

## Concepto

NAT traduce direcciones IP.

Se usa para permitir que redes privadas puedan comunicarse con redes públicas.

## Redes privadas RFC1918

| Rango | CIDR |
|---|---|
| 10.0.0.0 - 10.255.255.255 | 10.0.0.0/8 |
| 172.16.0.0 - 172.31.255.255 | 172.16.0.0/12 |
| 192.168.0.0 - 192.168.255.255 | 192.168.0.0/16 |

## SNAT

Source NAT.

Traduce la IP origen.

Uso típico:

```text
Red privada -> Internet
```

## PAT

Port Address Translation.

Permite que muchos hosts usen una misma IP pública diferenciando conexiones por puertos.

También se conoce como NAT overload.

## DNAT

Destination NAT.

Traduce la IP destino.

Uso típico:

```text
Internet -> servidor interno
```

Se usa para publicar servicios.

## NAT estático

Traducción fija entre IP privada e IP pública.

```bash
ip nat inside source static 192.168.1.10 209.165.201.10
```

## Port forwarding

```bash
ip nat inside source static tcp 192.168.1.10 80 209.165.201.10 80
```

## NAT dinámico con pool

```bash
access-list 1 permit 172.16.10.0 0.0.0.255
access-list 1 permit 172.16.11.0 0.0.0.255

ip nat pool PUBLIC_POOL 209.165.200.226 209.165.200.230 netmask 255.255.255.224
ip nat inside source list 1 pool PUBLIC_POOL overload

interface g0/0
 ip nat inside

interface s0/0/0
 ip nat outside
```

## PAT con interfaz

```bash
access-list 1 permit 192.168.1.0 0.0.0.255

ip nat inside source list 1 interface s0/0/0 overload

interface g0/0
 ip nat inside

interface s0/0/0
 ip nat outside
```

## Inside y outside

- `ip nat inside`: interfaz hacia la red privada.
- `ip nat outside`: interfaz hacia la red pública o ISP.

## Verificación

```bash
show ip nat translations
show ip nat statistics
show run | section ip nat
```

## Idea clave

Para tráfico iniciado desde dentro hacia fuera se usa SNAT/PAT.

Para acceder desde fuera a un servidor privado interno hace falta DNAT, NAT estático o port forwarding.

## ISP en laboratorios

En muchos labs, el ISP no hace NAT.

El NAT se configura en el router frontera del cliente.

## Errores típicos

- Marcar mal inside/outside.
- ACL de NAT incorrecta.
- No tener ruta por defecto hacia el ISP.
- No tener ruta de vuelta.
- Intentar acceder desde fuera sin DNAT.
