# DNS en Ubuntu Server con Bind9

## Objetivo

Configurar Ubuntu Server como servidor DNS en una LAN privada.

## Instalar paquetes

- `sudo apt update`
- `sudo apt install bind9 bind9utils dnsutils`

## Configurar IP y DNS local

En Netplan, el servidor debe tener IP estática.

Además, puede usar como DNS:

- `127.0.0.1`

Aplicar:

- `sudo netplan apply`

## resolv.conf

En algunas instalaciones, `/etc/resolv.conf` es un enlace gestionado por systemd-resolved.

Hay que asegurarse de que el sistema consulta al DNS correcto.

## named.conf.local

Archivo:

- `/etc/bind/named.conf.local`

Ejemplo de zonas:

- zona directa: `userver12.sis`
- zona inversa: `12.168.192.in-addr.arpa`

## Archivos de zona

Se pueden crear copiando la plantilla:

- `/etc/bind/db.local`

Ejemplo:

- `/etc/bind/directa.userver12.sis.db`
- `/etc/bind/inversa.userver12.sis.db`

## Registros habituales

### A

- `userver12 IN A 192.168.12.2`

### CNAME

- `servidor IN CNAME userver12`

### PTR

- `2 IN PTR userver12.userver12.sis.`

## Comprobar configuración

Comprobar configuración global:

- `sudo named-checkconf`

Comprobar zona directa:

- `sudo named-checkzone userver12.sis /etc/bind/directa.userver12.sis.db`

Comprobar zona inversa:

- `sudo named-checkzone 12.168.192.in-addr.arpa /etc/bind/inversa.userver12.sis.db`

## Reiniciar servicio

- `sudo systemctl restart bind9`
- `sudo systemctl status bind9`

## Pruebas

- `nslookup userver12.userver12.sis`
- `nslookup servidor.userver12.sis`
- `dig -x 192.168.12.2`
- `ping userver12.userver12.sis`
