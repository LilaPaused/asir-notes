# Lab - NAT/PAT

## Objetivo

Configurar salida a Internet mediante PAT y publicar un servicio interno mediante port forwarding.

## PAT de salida

```bash
access-list 1 permit 192.168.1.0 0.0.0.255

ip nat inside source list 1 interface s0/0/0 overload

interface g0/0
 ip nat inside

interface s0/0/0
 ip nat outside
```

## Ruta por defecto

```bash
ip route 0.0.0.0 0.0.0.0 s0/0/0
```

## Port forwarding

```bash
ip nat inside source static tcp 192.168.1.10 80 209.165.201.10 80
```

## Verificación

```bash
show ip nat translations
show ip nat statistics
show run | section ip nat
```

## Errores típicos

- ACL incorrecta.
- Falta ruta por defecto.
- Inside/outside invertidos.
- No generar tráfico para crear traducciones.
