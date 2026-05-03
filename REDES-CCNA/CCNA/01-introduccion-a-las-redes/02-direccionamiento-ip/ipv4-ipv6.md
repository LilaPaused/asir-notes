# Direccionamiento IPv4 e IPv6

## Sistemas numéricos

### Decimal

Sistema base 10.

### Hexadecimal

Sistema base 16.

Usa valores del 0 al 9 y de la A a la F.

### Binario

Sistema base 2.

Usa únicamente 0 y 1.

---

# IPv4

## Estructura

IPv4 utiliza direcciones de 32 bits divididas en 4 octetos.

Ejemplo:

```text
192.168.1.1
```

## CIDR

El CIDR indica cuántos bits pertenecen a la parte de red.

Ejemplo:

```text
192.168.1.0/24
```

## Partes de una dirección IPv4

Una dirección IPv4 se divide en:

```text
ID de red + ID de host
```

## IP de red

Identifica la red.

Tiene todos los bits de host en 0.

## Broadcast

Dirección usada para comunicarse con todos los dispositivos de una red.

Tiene todos los bits de host en 1.

## IP útil

Dirección asignable a un host.

No puede ser ni la IP de red ni la de broadcast.

## Clases tradicionales

| Clase | Rango | Máscara por defecto |
|---|---|---|
| A | 0.0.0.0 - 127.255.255.255 | /8 |
| B | 128.0.0.0 - 191.255.255.255 | /16 |
| C | 192.0.0.0 - 223.255.255.255 | /24 |
| D | 224.0.0.0 - 239.255.255.255 | Multicast |
| E | 240.0.0.0 - 255.255.255.255 | Reservado |

## Direcciones privadas

| Rango | CIDR |
|---|---|
| 10.0.0.0 - 10.255.255.255 | 10.0.0.0/8 |
| 172.16.0.0 - 172.31.255.255 | 172.16.0.0/12 |
| 192.168.0.0 - 192.168.255.255 | 192.168.0.0/16 |

## APIPA

Rango:

```text
169.254.0.0/16
```

Se asigna automáticamente cuando DHCP falla.

No es enrutable y no sirve para salir a Internet.

## Loopback

Rango:

```text
127.0.0.0/8
```

Se usa para pruebas internas del propio equipo.

---

# IPv6

## Estructura

IPv6 utiliza 128 bits representados en hexadecimal.

Tiene 8 bloques de 16 bits.

Ejemplo:

```text
2001:0000:0000:0000:0000:0000:0000:0017
```

## Reglas de simplificación

1. Se eliminan ceros a la izquierda.
2. Una única secuencia continua de bloques `0000` puede sustituirse por `::`.

Ejemplo:

```text
2001:0000:0000:0000:0000:0000:0000:0017
2001::17
```

La doble abreviación `::` solo puede usarse una vez en una dirección.

## Tipos principales

### Loopback

```text
::1
```

### Link-local

```text
FE80::/10
```

- Se genera automáticamente.
- Solo funciona en la red local.
- No sale a Internet.

### ULA

```text
FC00::/7
```

Equivalente a direccionamiento privado.

### Global Unicast

```text
2000::/3
```

Equivalente a una dirección pública.

## Tipos de comunicación IPv6

- Unicast
- Multicast
- Anycast

En IPv6 no existe broadcast.

## ICMPv6

ICMPv6 se usa para:

- Echo request / echo reply
- Mensajes de error
- Neighbor Discovery
- Autoconfiguración

## MTU en IPv6

Los routers no fragmentan paquetes IPv6.

Si el paquete es demasiado grande, se genera un mensaje ICMPv6 de tipo Packet Too Big.
