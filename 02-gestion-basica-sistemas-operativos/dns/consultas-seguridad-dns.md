# Consultas y seguridad DNS

## Consulta recursiva

El cliente pide la respuesta final al servidor DNS.

El servidor DNS se encarga de preguntar a otros servidores hasta conseguir la respuesta.

Flujo:

- Cliente
- DNS local
- Root
- TLD
- Autoritativo
- Cliente

Idea clave:

- trabaja el servidor DNS

## Consulta iterativa

El cliente va recibiendo referencias y hace varias consultas hasta llegar al servidor autoritativo.

Idea clave:

- trabaja más el cliente

## Diferencia principal

| Tipo | Quién resuelve |
|---|---|
| Recursiva | Servidor DNS |
| Iterativa | Cliente siguiendo referencias |

## DNSSEC

Añade firmas digitales a los registros DNS.

Ayuda a evitar:

- falsificación de respuestas
- cache poisoning
- manipulación de registros

## DNSCurve

Cifra comunicaciones DNS usando criptografía.

Ayuda contra:

- espionaje
- ataques Man-in-the-Middle

## FCrDNS

Forward Confirmed reverse DNS.

Compara resolución directa e inversa.

Sirve para verificar que una IP y un dominio coinciden.

Muy usado contra:

- spam
- suplantación
- servidores mal configurados
