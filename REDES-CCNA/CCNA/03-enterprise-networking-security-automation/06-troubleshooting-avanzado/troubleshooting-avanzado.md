# Troubleshooting avanzado

## Interfaces

```bash
show ip interface brief
show interfaces
```

## Routing

```bash
show ip route
show ip protocols
traceroute
ping
```

## OSPF

```bash
show ip ospf neighbor
show ip ospf interface brief
show ip ospf database
show ip route ospf
show run | section router ospf
```

Comprobar:

- Vecinos.
- Área.
- Router ID.
- Wildcard.
- Interfaces pasivas.
- Redes anunciadas.

## NAT

```bash
show ip nat translations
show ip nat statistics
show run | section ip nat
```

Comprobar:

- ACL de NAT.
- Inside/outside.
- Ruta por defecto.
- Traducciones activas.
- Port forwarding.

## FHRP

```bash
show standby
show standby brief
```

Comprobar:

- Router activo.
- Router standby.
- IP virtual.
- Prioridad.
- Preempt.

## CDP

```bash
show cdp neighbors
show cdp neighbors detail
```

## Regla de diagnóstico

1. Capa física.
2. Dirección IP.
3. Gateway.
4. Routing.
5. ACL/NAT/firewall.
6. Servicio final.

## Errores típicos

- Revisar OSPF antes de comprobar interfaces.
- Configurar NAT sin ruta por defecto.
- Configurar gateway físico en lugar de IP virtual FHRP.
- Anunciar mal una red por wildcard.
- No verificar ruta de retorno.
