# Conceptos DNS

## Qué es DNS

DNS traduce nombres a direcciones IP.

Ejemplo:

    servidor.empresa.local -> 192.168.12.1

## Zona directa

Permite resolver nombre a IP.

Ejemplo:

    wserver12.sis -> 192.168.12.1

## Zona inversa

Permite resolver IP a nombre.

Ejemplo:

    192.168.12.1 -> wserver12.sis

## Registro A

Asocia un nombre con una IPv4.

Ejemplo:

    wserver12 IN A 192.168.12.1

## Registro CNAME

Crea un alias hacia otro nombre.

Ejemplo:

    servidor IN CNAME wserver12

## Registro PTR

Usado en zona inversa.

Asocia una IP con un nombre.

## nslookup

Consultar DNS:

    nslookup wserver12.sis

Consulta inversa:

    nslookup 192.168.12.1

## dig

Herramienta común en Linux:

    dig userver12.sis
    dig -x 192.168.12.2

## DNS local

En una LAN privada, un servidor DNS puede resolver nombres internos que no existen en Internet.

Ejemplo:

    wserver12.sis
    userver12.sis

## Idea clave

DNS no es solo Internet. También se usa dentro de redes privadas para identificar servidores, clientes y servicios.
