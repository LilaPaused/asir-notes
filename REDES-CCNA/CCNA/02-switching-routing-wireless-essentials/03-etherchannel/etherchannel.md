# EtherChannel

## Concepto

EtherChannel agrupa varios enlaces físicos en un único enlace lógico.

El enlace lógico se llama Port-Channel.

## Ventajas

- Aumenta ancho de banda.
- Aporta redundancia.
- Evita que STP bloquee enlaces físicos individuales.
- STP ve el Port-Channel como un solo enlace.

## Modos

### Estático

No usa protocolo de negociación.

```text
mode on
```

### LACP

Estándar IEEE 802.3ad.

Modos:

- active
- passive

Al menos un lado debe estar en active.

### PAgP

Propietario Cisco.

Modos:

- desirable
- auto

Al menos un lado debe estar en desirable.

## Requisitos

Los enlaces físicos deben tener la misma configuración:

- Velocidad.
- Dúplex.
- Modo access o trunk.
- VLAN nativa.
- VLANs permitidas.
- Misma configuración de capa 2.

## Configuración LACP

```bash
conf t
interface range fa0/23 - 24
 description Miembros EtherChannel Po1
 channel-group 1 mode active
exit

interface port-channel 1
 description Port-Channel trunk
 switchport mode trunk
 switchport trunk native vlan 99
 switchport trunk allowed vlan 10,20,30,99
end
wr
```

## Verificación

```bash
show etherchannel summary
show interfaces trunk
show run interface port-channel 1
```

## Estados importantes

- `Po1(SU)`: correcto, capa 2 y en uso.
- `Po1(SD)`: creado, pero down.
- `P`: puerto físico integrado correctamente en el canal.

## Regla práctica

Si hay EtherChannel, la configuración trunk debe aplicarse al Port-Channel.
