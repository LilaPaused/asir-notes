# Firewall y conectividad ICMP

## Problema típico

Las máquinas están en la misma red, tienen IP correcta, pero el ping falla.

En Windows suele deberse al firewall bloqueando ICMP.

## ICMP

ICMP es el protocolo usado por ping.

Permitir ping no significa abrir todos los puertos. Solo se permite responder o enviar paquetes ICMP.

## Regla en PowerShell

Permitir ping de entrada:

    New-NetFirewallRule -Name "Permitir-Ping-Entrada" -DisplayName "Permitir ping entrada" -Protocol ICMPv4 -IcmpType 8 -Direction Inbound -Action Allow

Permitir ping de salida:

    New-NetFirewallRule -Name "Permitir-Ping-Salida" -DisplayName "Permitir ping salida" -Protocol ICMPv4 -Direction Outbound -Action Allow

## Comprobar ping

    ping 192.168.12.1

## No desactivar firewall

En prácticas es tentador desactivar el firewall, pero no es buena práctica.

Lo correcto es crear reglas concretas.

## Linux

En Ubuntu básico normalmente ping funciona sin tocar reglas.

Si hay firewall activo, revisar ufw:

    sudo ufw status

## Diagnóstico rápido

1. Comprobar IP
2. Comprobar máscara
3. Comprobar que están en la misma red interna
4. Comprobar firewall
5. Probar ping en ambos sentidos

## TTL orientativo

En ping, Windows suele responder con TTL=128 y Linux con TTL=64.

Esto puede ayudar a identificar el tipo de sistema remoto.
