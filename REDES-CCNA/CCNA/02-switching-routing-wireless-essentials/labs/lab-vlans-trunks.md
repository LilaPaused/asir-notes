# Lab - VLANs y trunks

## Objetivo

Crear VLANs, asignar puertos access y transportar varias VLANs entre switches mediante trunk.

## Topología

```text
PC VLAN 10 --- S1 ===== S2 --- PC VLAN 10
PC VLAN 20 --- S1      S2 --- PC VLAN 20
```

## Configuración VLANs

```bash
conf t
vlan 10
 name USERS
vlan 20
 name ADMIN
vlan 99
 name MANAGEMENT
end
wr
```

## Puertos access

```bash
conf t
interface fa0/1
 switchport mode access
 switchport access vlan 10
 spanning-tree portfast

interface fa0/2
 switchport mode access
 switchport access vlan 20
 spanning-tree portfast
end
wr
```

## Trunk

```bash
conf t
interface g0/1
 switchport mode trunk
 switchport trunk native vlan 99
 switchport trunk allowed vlan 10,20,99
end
wr
```

## Verificación

```bash
show vlan brief
show interfaces trunk
ping
```

## Errores típicos

- VLAN no creada en ambos switches.
- Trunk no configurado.
- VLAN no permitida en el trunk.
- VLAN nativa diferente.
