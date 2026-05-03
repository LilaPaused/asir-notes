# Laboratorio - ICMP con Wireshark

## Objetivo

Analizar el tráfico generado por un ping usando Wireshark.

## Pasos

1. Comprobar conectividad entre las máquinas.
2. Borrar la tabla ARP en Windows.
3. Iniciar captura con Wireshark.
4. Ejecutar ping desde Windows hacia Debian.
5. Identificar tramas ARP e ICMP.

## Borrar tabla ARP en Windows

Ejecutar CMD como administrador:

```cmd
arp -d
```

## Qué se espera ver

Primero aparecen tramas ARP:

- ARP Request
- ARP Reply

Después aparecen paquetes ICMP:

- Echo Request
- Echo Reply

## Cabeceras importantes

### Ethernet II

Contiene:

- MAC origen
- MAC destino

### IPv4

Contiene:

- IP origen
- IP destino
- TTL
- Protocolo

### ICMP

Contiene:

- Tipo
- Código
- Identificador
- Número de secuencia

## tcpdump en Linux

```bash
sudo tcpdump -i enp0s8 icmp
```

## Conclusión

Ping no solo genera ICMP.

Si la MAC destino no está en la tabla ARP, antes del ICMP se genera tráfico ARP para resolver la dirección física.
