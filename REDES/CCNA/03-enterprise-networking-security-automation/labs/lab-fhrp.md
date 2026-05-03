# Lab - FHRP con HSRP

## Objetivo

Crear una puerta de enlace virtual redundante.

## Escenario

```text
Host -> Switch -> R1
              -> R2
```

Los hosts usan como gateway una IP virtual.

## R1

```bash
conf t
interface g0/1
 standby version 2
 standby 1 ip 192.168.1.254
 standby 1 priority 150
 standby 1 preempt
end
wr
```

## R2

```bash
conf t
interface g0/1
 standby version 2
 standby 1 ip 192.168.1.254
end
wr
```

## Verificación

```bash
show standby
show standby brief
```

## Prueba de fallo

1. Apagar R1 o su interfaz LAN.
2. Verificar que R2 pasa a activo.
3. Restaurar R1.
4. Verificar recuperación si `preempt` está configurado.

## Error típico

Configurar en los hosts la IP física del router en lugar de la IP virtual.
