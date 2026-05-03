# OSPF

## Concepto

OSPF, Open Shortest Path First, es un protocolo de routing dinámico de estado de enlace.

Es un IGP, por lo que se usa dentro de un sistema autónomo.

## Características

- Usa el algoritmo SPF.
- Se basa en Dijkstra.
- Tiene convergencia rápida.
- Usa coste como métrica.
- Soporta áreas.
- No sumariza automáticamente por defecto.
- Mantiene una base de datos de estado de enlace.

## Estado de enlace

Los routers OSPF no envían toda la tabla de routing constantemente.

Intercambian información de enlaces para construir una visión común de la topología.

## LSDB

Link-State Database.

Base de datos con la información de topología OSPF.

## SPF

Algoritmo usado para calcular el camino más corto.

## Router ID

Identificador único del router en OSPF.

Se elige así:

1. Router ID configurado manualmente.
2. IP más alta de una loopback.
3. IP más alta de una interfaz activa.

## Áreas

OSPF puede dividir la red en áreas.

El área principal es:

```text
area 0
```

## Tipos de router

### Internal Router

Todas sus interfaces OSPF están en la misma área.

### ABR

Area Border Router.

Conecta áreas diferentes.

### ASBR

Autonomous System Boundary Router.

Conecta OSPF con otro protocolo de routing, rutas externas o salida hacia otro dominio.

## DR y BDR

En redes broadcast se eligen:

- DR: Designated Router.
- BDR: Backup Designated Router.

Sirven para reducir el número de adyacencias.

No se usan en enlaces punto a punto.

## Elección DR/BDR

1. Mayor prioridad OSPF.
2. En empate, mayor Router ID.

Prioridad 0:

```bash
interface g0/0
 ip ospf priority 0
```

Ese router no será DR ni BDR.

## Tipos de paquetes OSPF

| Tipo | Nombre | Función |
|---|---|---|
| 1 | Hello | Descubrir vecinos |
| 2 | DBD | Resumen de base de datos |
| 3 | LSR | Solicitar información |
| 4 | LSU | Enviar información |
| 5 | LSAck | Confirmar recepción |

## LSA básicos

| Tipo | Nombre | Generado por |
|---|---|---|
| 1 | Router LSA | Cada router |
| 2 | Network LSA | DR |
| 3 | Summary LSA | ABR |

## Configuración básica

```bash
conf t
router ospf 1
 router-id 1.1.1.1
 network 192.168.1.0 0.0.0.255 area 0
end
wr
```

## Wildcard mask

La wildcard es la inversa de la máscara.

| CIDR | Máscara | Wildcard |
|---|---|---|
| /24 | 255.255.255.0 | 0.0.0.255 |
| /30 | 255.255.255.252 | 0.0.0.3 |
| /29 | 255.255.255.248 | 0.0.0.7 |
| /23 | 255.255.254.0 | 0.0.1.255 |
| /22 | 255.255.252.0 | 0.0.3.255 |

## Interfaces pasivas

Una interfaz pasiva:

- Anuncia la red.
- No envía Hellos.
- No forma vecinos.

Uso típico:

- PCs.
- Servidores.
- Switches L2.
- Redes finales.

```bash
router ospf 1
 passive-interface g0/0
```

## Ruta por defecto en OSPF

```bash
router ospf 1
 default-information originate
```

Si no hay ruta por defecto instalada:

```bash
router ospf 1
 default-information originate always
```

## Verificación

```bash
show ip ospf neighbor
show ip route ospf
show ip protocols
show ip ospf
show ip ospf interface
show ip ospf interface brief
show ip ospf database
```

## Reinicio del proceso

```bash
clear ip ospf process
```

No borra configuración, pero reinicia vecinos, LSDB y cálculo SPF.

## Errores típicos

- Wildcard incorrecta.
- Área incorrecta.
- Router ID duplicado.
- Interfaz pasiva hacia otro router.
- No anunciar una red conectada.
- No tener área 0 en diseños multiárea.
