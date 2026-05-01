# DNS en Windows Server

## Objetivo

Configurar un servidor Windows Server como servidor DNS para una LAN privada.

## 1. Configurar DNS del propio servidor

El servidor DNS debe apuntarse a sí mismo.

DNS primario:

    127.0.0.1

O también puede usar su IP interna según caso.

## 2. Instalar rol DNS

Desde Administrador del servidor:

    Administrar -> Agregar roles y características -> Servidor DNS

Después:

    Herramientas -> DNS

## 3. Crear zona directa

Ejemplo:

    wserver12.sis

Tipo:

    Zona principal

Actualizaciones dinámicas:

    No permitir

## 4. Crear zona inversa

Ejemplo de red:

    192.168.12.0/24

Zona inversa:

    12.168.192.in-addr.arpa

## 5. Crear registros

Registro A:

    wserver12 -> 192.168.12.1

CNAME:

    servidor -> wserver12

PTR:

    192.168.12.1 -> wserver12.sis

## 6. Configurar cliente

En Windows 10, configurar DNS primario:

    192.168.12.1

## 7. Probar desde cliente

    nslookup wserver12.sis
    nslookup servidor.wserver12.sis
    nslookup 192.168.12.1
    ping wserver12.sis
    ping servidor.wserver12.sis

## Problema típico con NAT

Si la máquina tiene adaptador NAT y adaptador interno, puede usar el DNS del NAT en vez del DNS interno.

Soluciones:

- desconectar NAT para probar
- priorizar adaptador interno
- configurar DNS correctamente en el adaptador adecuado

## Registro nuevo de cliente

Crear registro A:

    wclient12 -> 192.168.12.100

Marcar opción para crear PTR automáticamente si la zona inversa existe.

## Buenas prácticas

- Crear zona directa e inversa.
- Probar A, CNAME y PTR.
- No desactivar firewall sin necesidad.
- Documentar IPs y nombres.
