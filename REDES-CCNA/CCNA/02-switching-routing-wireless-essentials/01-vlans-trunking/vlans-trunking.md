# VLANs y trunking

## Concepto de VLAN

Una VLAN separa lógicamente una red física.

Permite dividir una infraestructura común en varias redes virtuales independientes.

## Para qué sirve

- Separar departamentos.
- Reducir dominios de broadcast.
- Aislar tráfico.
- Organizar la red.
- Mejorar seguridad y administración.

## Puertos access

Un puerto access pertenece a una sola VLAN.

Se usa normalmente para conectar:

- PCs
- impresoras
- teléfonos IP
- dispositivos finales

Ejemplo:

```bash
conf t
vlan 10
 name USERS
exit

interface fa0/1
 description PC VLAN 10
 switchport mode access
 switchport access vlan 10
 spanning-tree portfast
end
wr
```

## Puertos trunk

Un trunk transporta varias VLANs por un mismo enlace.

Se usa normalmente entre:

- Switch a switch
- Switch a router
- Switch a switch multicapa
- Switch a port-channel

Ejemplo:

```bash
conf t
interface g0/1
 description TRUNK hacia S2
 switchport mode trunk
 switchport trunk allowed vlan 10,20,30,99
 switchport trunk native vlan 99
end
wr
```

## Etiquetado 802.1Q

El trunk identifica a qué VLAN pertenece cada trama mediante una etiqueta.

La etiqueta VLAN se añade a la cabecera de Ethernet.

## VLAN nativa

La VLAN nativa es la VLAN que viaja sin etiqueta en un enlace trunk.

Debe coincidir en ambos extremos del trunk.

Si no coincide, pueden aparecer errores y comportamientos inseguros.

## Tagged y untagged

- Tagged: trama etiquetada con VLAN.
- Untagged: trama sin etiqueta, asociada a la VLAN nativa.

## VLAN estática

El puerto tiene asignada una VLAN fija.

## VLAN dinámica

La VLAN se asigna según una condición, por ejemplo una MAC.

## VLAN de voz

Un puerto access puede transportar una VLAN de datos y una VLAN de voz.

Ejemplo:

```bash
interface fa0/13
 description PC + telefono IP
 switchport mode access
 switchport access vlan 10
 switchport voice vlan 150
 spanning-tree portfast
```

## Comandos de verificación

```bash
show vlan brief
show interfaces trunk
show run interface fa0/1
show interfaces fa0/1 switchport
```

## Errores típicos

- Crear VLAN en un switch, pero no en el resto de switches que la transportan.
- Olvidar configurar el enlace como trunk.
- VLAN nativa diferente en ambos extremos.
- Restringir VLANs permitidas y olvidar añadir una VLAN necesaria.
- Pensar que una VLAN enruta por sí sola.

## Regla rápida

Las VLANs separan redes.

Para comunicar VLANs diferentes hace falta routing.
