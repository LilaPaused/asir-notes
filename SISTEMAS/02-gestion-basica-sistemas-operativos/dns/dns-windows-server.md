# DNS en Windows Server

## Objetivo

Configurar Windows Server como servidor DNS dentro de una LAN privada.

## Paso 1: DNS del servidor

En el servidor, establecer como DNS principal:

- `127.0.0.1`

Esto indica que el servidor se consulte a sí mismo.

## Paso 2: instalar rol DNS

En Administrador del servidor:

- Administrar
- Agregar roles y características
- Servidor DNS
- Instalar

## Paso 3: abrir consola DNS

Ruta:

- Herramientas
- DNS

## Paso 4: zona directa

Crear zona de búsqueda directa.

Ejemplo:

- `wserver12.sis`
- tipo: principal
- sin actualizaciones dinámicas

## Paso 5: zona inversa

Crear zona inversa para la red.

Ejemplo:

- red `192.168.12.0`
- zona `12.168.192.in-addr.arpa`

## Registros

### A

Nombre:

- `wserver12`

IP:

- `192.168.12.1`

### CNAME

Alias:

- `servidor`

Destino:

- `wserver12.wserver12.sis`

### PTR

Resolución inversa de IP a nombre.

## Cliente Windows

Configurar DNS del cliente:

- DNS primario: IP del servidor DNS

Ejemplo:

- `192.168.12.1`

## Pruebas

- `nslookup wserver12.wserver12.sis`
- `nslookup servidor.wserver12.sis`
- `nslookup 192.168.12.1`
- `ping wserver12.wserver12.sis`
