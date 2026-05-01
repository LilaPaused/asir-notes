# Red interna e IP estática

## Objetivo

Configurar varias máquinas virtuales en una LAN privada usando red interna.

## VirtualBox

Todas las máquinas deben usar el mismo nombre de red interna.

Ejemplo:

- Adaptador 2
- Red interna
- Nombre: `interna`

Si el nombre no coincide, las máquinas no se ven.

## Esquema de ejemplo

| Máquina | Rol | IP |
|---|---|---|
| Windows Server | Servidor Windows | 192.168.12.1 |
| Ubuntu Server | Servidor Linux | 192.168.12.2 |
| Windows 10 | Cliente Windows | 192.168.12.100 |
| Ubuntu Desktop | Cliente Linux | 192.168.12.200 |

## Windows gráfico

Abrir adaptadores:

- `Win + R`
- `ncpa.cpl`

Configurar IPv4 manualmente:

- IP
- máscara
- puerta de enlace si aplica
- DNS si aplica

## Windows PowerShell

Desactivar DHCP:

- `Set-NetIPInterface -InterfaceAlias "Ethernet_int" -Dhcp Disabled`

Asignar IP:

- `New-NetIPAddress -InterfaceAlias "Ethernet_int" -IPAddress 192.168.12.1 -PrefixLength 24`

## Ubuntu Desktop gráfico

Ajustes de red:

- IPv4 manual
- IP
- máscara
- DNS si aplica

## Ubuntu Server con Netplan

Editar YAML en:

- `/etc/netplan/`

Aplicar:

- `sudo netplan apply`

Comprobar:

- `ip a`

## Ping

Comprobar conectividad:

- `ping IP`

En Windows puede hacer falta permitir ICMP en firewall.
