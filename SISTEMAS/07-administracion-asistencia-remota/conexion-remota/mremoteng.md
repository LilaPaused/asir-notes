# mRemoteNG

## Qué es

mRemoteNG es una herramienta para centralizar conexiones remotas desde Windows.

Permite guardar conexiones de distintos protocolos en una misma interfaz.

Protocolos habituales:

- RDP
- SSH
- VNC
- Telnet
- RAW

## Para qué sirve

Sirve para tener ordenadas varias conexiones a servidores y clientes.

Ejemplo de organización:

- SERVERS
  - wserver
  - userver
- CLIENTS
  - wclient
  - uclient

## Crear una carpeta de conexiones

1. Abrir mRemoteNG.
2. Crear una carpeta nueva.
3. Poner un nombre claro.
4. Crear conexiones dentro.

Ejemplo:

- Ubuntu Desktop 12
- Windows Servers
- Linux Servers
- Clientes

## Crear una conexión

Datos mínimos:

- Nombre de la conexión
- IP o hostname
- Protocolo
- Puerto
- Usuario
- Contraseña, si la práctica lo pide

## Ejemplo RDP

Para conectar a Windows:

- Protocolo: RDP
- Puerto: 3389
- Hostname/IP: IP del Windows destino
- Usuario: usuario autorizado
- Contraseña: la del usuario

## Ejemplo SSH

Para conectar a Ubuntu Server:

- Protocolo: SSH version 2
- Puerto: 22
- Hostname/IP: IP del servidor
- Usuario: usuario Linux
- Contraseña: contraseña del usuario

## Ejemplo VNC

Para conectar a Ubuntu Desktop por VNC:

- Protocolo: VNC
- Puerto: 5900
- Hostname/IP: IP del cliente Ubuntu
- Password: contraseña VNC configurada

## Comprobaciones

Antes de crear conexiones en mRemoteNG, probar:

- ping al destino
- servicio remoto activo
- firewall permitiendo el puerto

## Problemas comunes

### No conecta por RDP

Revisar:

- Escritorio remoto habilitado.
- Usuario autorizado.
- Firewall permitiendo RDP.
- IP correcta.

### No conecta por SSH

Revisar:

- openssh-server instalado.
- servicio ssh activo.
- puerto 22 permitido.
- usuario y contraseña correctos.

### No conecta por VNC

Revisar:

- sesión Xorg en vez de Wayland si hay incompatibilidad.
- Vino instalado.
- contraseña VNC configurada.
- cifrado desactivado si el cliente no soporta el método.
- puerto 5900 permitido.
