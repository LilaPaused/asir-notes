# Lab - OSPF básico

## Objetivo

Configurar OSPF entre routers y verificar adyacencias.

## Configuración base

```bash
conf t
router ospf 1
 router-id 1.1.1.1
 network 10.0.0.0 0.0.0.255 area 0
end
wr
```

## Interfaz pasiva

```bash
router ospf 1
 passive-interface g0/0
```

## Verificación

```bash
show ip ospf neighbor
show ip route ospf
show ip protocols
show ip ospf interface brief
```

## Problemas típicos

- Área diferente entre routers.
- Wildcard incorrecta.
- Interfaz apagada.
- Passive-interface en enlace entre routers.
- Router ID duplicado.
