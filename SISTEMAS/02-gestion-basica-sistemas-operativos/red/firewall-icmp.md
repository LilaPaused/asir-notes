# Firewall e ICMP

## Problema

En Windows, aunque las máquinas estén en la misma red, el ping puede fallar por el firewall.

El ping usa ICMP.

## Regla PowerShell para permitir ping entrante

- `New-NetFirewallRule -Name "Permitir-Ping-Entrada" -DisplayName "Permitir ping entrada" -Protocol ICMPv4 -IcmpType 8 -Direction Inbound -Action Allow`

## Regla para salida

- `New-NetFirewallRule -Name "Permitir-Ping-Salida" -DisplayName "Permitir ping salida" -Protocol ICMPv4 -Direction Outbound -Action Allow`

## Recomendación

No deshabilitar el firewall entero.

Mejor crear reglas concretas.

## Comprobación

Desde otra máquina:

- `ping 192.168.12.1`

Desde Windows:

- `ping 192.168.12.100`

## Linux

Normalmente no hace falta tocar reglas para permitir ping en prácticas básicas, salvo que haya firewall configurado.
