# Troubleshooting básico

## Windows

Ver configuración IP:

```cmd
ipconfig /all
```

Ping:

```cmd
ping 192.168.1.1
```

Traceroute:

```cmd
tracert 192.168.1.1
```

Borrar tabla ARP:

```cmd
arp -d
```

## Linux

Ver direcciones:

```bash
ip a
```

Ver rutas:

```bash
ip route
```

Ping:

```bash
ping 192.168.1.1
```

Traceroute:

```bash
traceroute 192.168.1.1
```

Capturar ICMP:

```bash
sudo tcpdump -i enp0s8 icmp
```

## Cisco IOS

Ver interfaces:

```bash
show ip interface brief
```

Ver configuración:

```bash
show running-config
```

Ver rutas:

```bash
show ip route
```
