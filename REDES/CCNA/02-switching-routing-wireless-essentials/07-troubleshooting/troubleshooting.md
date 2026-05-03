# Troubleshooting CCNA 2

## Interfaces

```bash
show ip interface brief
show interfaces status
```

## VLANs

```bash
show vlan brief
```

## Trunks

```bash
show interfaces trunk
show run interface g0/1
```

## STP

```bash
show spanning-tree
show spanning-tree vlan 10
```

## EtherChannel

```bash
show etherchannel summary
show run interface port-channel 1
```

## Inter-VLAN

```bash
show ip interface brief
show run interface vlan 10
show run interface g0/0.10
show ip route
```

## Routing estático

```bash
show ip route
show running-config | include ip route
ping
traceroute
```

## Reglas rápidas

- Si dos VLANs no se comunican, revisar gateway y routing.
- Si una VLAN no cruza a otro switch, revisar trunk y allowed VLANs.
- Si STP bloquea un enlace, comprobar root bridge, costes y Port ID.
- Si EtherChannel no levanta, revisar que los puertos físicos tengan la misma configuración.
- Si la ruta flotante entra antes de tiempo, revisar la distancia administrativa.
