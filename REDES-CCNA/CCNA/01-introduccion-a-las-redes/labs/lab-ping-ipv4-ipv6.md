# Laboratorio - Ping IPv4 e IPv6 con router Linux

## Objetivo

Comprobar conectividad IPv4 e IPv6 entre dos redes usando un equipo Debian como router.

## Topología

```text
Windows Cliente --- Debian Router --- Debian Server
192.168.1.1       192.168.1.254
                  192.168.2.254       192.168.2.1
```

IPv6:

```text
Windows Cliente --- Debian Router --- Debian Server
2001:1::2         2001:1::1
                  2001:2::1           2001:2::2
```

## Configuración en Windows

Ver interfaces:

```cmd
netsh interface ipv4 show interfaces
```

Asignar IPv4:

```cmd
netsh interface ipv4 set address name="Ethernet" static 192.168.1.1 255.255.255.0 192.168.1.254
```

Asignar IPv6:

```cmd
netsh interface ipv6 add address "Ethernet" 2001:1::2
```

## Configuración en Debian Router

Interfaz hacia Windows:

```bash
sudo ip addr add 192.168.1.254/24 dev enp0s3
sudo ip -6 addr add 2001:1::1/64 dev enp0s3
```

Interfaz hacia Debian Server:

```bash
sudo ip addr add 192.168.2.254/24 dev enp0s8
sudo ip -6 addr add 2001:2::1/64 dev enp0s8
```

Activar forwarding IPv4:

```bash
sudo sysctl -w net.ipv4.ip_forward=1
```

## Configuración en Debian Server

```bash
sudo ip addr add 192.168.2.1/24 dev enp0s3
sudo ip -6 addr add 2001:2::2/64 dev enp0s3
sudo ip route add default via 192.168.2.254
```

## Pruebas

Desde Windows:

```cmd
ping 192.168.1.254
ping 192.168.2.254
tracert 192.168.2.1
```

Desde Debian Server:

```bash
ping 192.168.2.254
ping 192.168.1.254
traceroute 192.168.1.1
```

IPv6:

```cmd
tracert -6 2001:2::2
```

```bash
traceroute6 2001:1::2
```
