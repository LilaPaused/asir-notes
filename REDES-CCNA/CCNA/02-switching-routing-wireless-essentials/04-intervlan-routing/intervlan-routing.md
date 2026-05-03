# Inter-VLAN Routing

## Concepto

Las VLANs separan redes.

Para que dos VLANs se comuniquen, hace falta routing.

Formas habituales:

- Router-on-a-stick.
- Switch multicapa mediante SVIs.

---

## Router-on-a-stick

Se usa un router con subinterfaces.

El switch envía varias VLANs al router por un trunk.

### Switch

```bash
conf t
interface g0/1
 description TRUNK hacia R1
 switchport mode trunk
 switchport trunk native vlan 99
 switchport trunk allowed vlan 10,20,30,99
end
wr
```

### Router

```bash
conf t
interface g0/0
 description Enlace trunk hacia switch
 no shutdown
exit

interface g0/0.10
 description Gateway VLAN 10
 encapsulation dot1Q 10
 ip address 192.168.10.1 255.255.255.0
exit

interface g0/0.20
 description Gateway VLAN 20
 encapsulation dot1Q 20
 ip address 192.168.20.1 255.255.255.0
exit

interface g0/0.99
 description VLAN nativa
 encapsulation dot1Q 99 native
 ip address 192.168.99.1 255.255.255.0
end
wr
```

## Switch multicapa

Un switch multicapa enruta mediante interfaces VLAN.

### Activar routing

```bash
conf t
ip routing
end
wr
```

### Crear SVIs

```bash
conf t
interface vlan 10
 description Gateway VLAN 10
 ip address 192.168.10.254 255.255.255.0
 no shutdown
exit

interface vlan 20
 description Gateway VLAN 20
 ip address 192.168.20.254 255.255.255.0
 no shutdown
end
wr
```

## Routed port

En un switch multicapa, un puerto puede actuar como puerto de router.

```bash
conf t
interface g0/2
 no switchport
 ip address 10.10.0.2 255.255.255.252
 no shutdown
end
wr
```

## SVI de gestión en switch capa 2

```bash
conf t
vlan 99
 name Management

interface vlan 99
 ip address 192.168.99.11 255.255.255.0
 no shutdown

ip default-gateway 192.168.99.254
end
wr
```

## Condiciones para que una SVI esté activa

- La VLAN existe.
- La interfaz VLAN tiene `no shutdown`.
- Hay un puerto activo en esa VLAN o un trunk que la transporte.

## Verificación

```bash
show ip interface brief
show vlan brief
show interfaces trunk
show run interface vlan 10
```

## Errores típicos

- Olvidar `ip routing` en un MLS.
- Crear las SVIs pero no transportar las VLANs por trunk.
- No configurar gateway en los hosts.
- No activar la interfaz física del router en router-on-a-stick.
