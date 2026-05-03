# ICMP, ARP y análisis con Wireshark

## ARP

ARP relaciona una dirección IPv4 con una dirección MAC dentro de una red local.

La tabla ARP solo tiene sentido dentro de la misma red local.

## Funcionamiento de ARP

### ARP Request

Se envía en broadcast.

Pregunta:

```text
¿Quién tiene esta IP?
```

### ARP Reply

Se responde en unicast.

Indica:

```text
Esta IP pertenece a esta MAC
```

## ICMP

ICMP se usa para diagnóstico y control.

El uso más común es `ping`.

## Ping

Ping comprueba conectividad mediante:

- Echo Request
- Echo Reply

Si hay respuesta, existe conectividad a nivel de red.

## Mensajes comunes

- Echo Request
- Echo Reply
- Destination Unreachable
- Time Exceeded

## TTL

TTL significa Time To Live.

Indica cuántos saltos puede atravesar un paquete antes de descartarse.

## Wireshark

En una captura de ping IPv4 se pueden observar:

- Tramas ARP iniciales
- Paquetes ICMP Echo Request
- Paquetes ICMP Echo Reply
- Cabecera Ethernet II
- Cabecera IPv4
- Cabecera ICMP

## Cabeceras en un ping IPv4

| Capa | Cabecera | Función |
|---|---|---|
| Enlace | Ethernet II | MAC origen y destino |
| Red | IPv4 | IP origen, IP destino, TTL |
| Control | ICMP | Echo request / reply |

## tcpdump

En Linux se puede capturar tráfico ICMP con:

```bash
sudo tcpdump -i enp0s8 icmp
```

## Regla práctica

Si se borra la tabla ARP antes de hacer ping, en Wireshark se verá primero ARP y luego ICMP.
