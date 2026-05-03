# Fundamentos de red

## Qué es una red

Una red es un conjunto de nodos interconectados que permiten compartir información.

## Dispositivos habituales

- PC
- Servidor
- Router
- Switch
- Access Point

## Nodo

Un nodo es un dispositivo conectado a la red.

## NIC

La NIC, Network Interface Card, es la tarjeta o interfaz de red que permite que un dispositivo se comunique en una red.

Permite asociar el dispositivo a una dirección física y enviar o recibir información.

## Dirección IP

Identificador lógico de un dispositivo dentro de una red.

## Dirección MAC

Identificador físico asociado a la interfaz de red.

## Gateway

Dispositivo al que se envía el tráfico cuando el destino no está en la red local.

## Máscara de red

Indica qué parte de una dirección IP corresponde a la red y qué parte corresponde al host.

Sin máscara, los dispositivos no sabrían si otro host pertenece a su misma red local.

## DHCP

Servicio que asigna automáticamente configuración IP a los dispositivos.

Puede entregar:

- Dirección IP
- Máscara
- Gateway
- DNS

## DNS

Servicio que traduce nombres de dominio a direcciones IP.

## Servidor

Dispositivo o sistema que responde a peticiones de otros dispositivos.

## Dispositivos finales

- PC
- Portátil
- Servidor
- Impresora
- Teléfono IP

## Dispositivos de red

### Hub

- Trabaja en capa 1.
- No interpreta IP ni MAC.
- Reenvía la señal por todos los puertos.
- No separa dominios de colisión.

### Switch

- Trabaja principalmente en capa 2.
- Usa direcciones MAC.
- Aprende direcciones mediante la tabla CAM.
- Separa dominios de colisión por puerto.

### Router

- Trabaja en capa 3.
- Usa direcciones IP.
- Interconecta redes diferentes.
- Separa dominios de broadcast.

## Resumen rápido

| Dispositivo | Capa | Usa | Función |
|---|---|---|---|
| Hub | 1 | Señal | Reenvía bits |
| Switch | 2 | MAC | Conmuta tramas |
| Router | 3 | IP | Enruta paquetes |
