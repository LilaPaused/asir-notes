# Lab - STP

## Objetivo

Interpretar el comportamiento de STP en una topología redundante.

## Conceptos

- Root Bridge.
- Root Port.
- Designated Port.
- Alternate / Backup.
- Blocking y Forwarding.

## Pasos de análisis

1. Identificar el Root Bridge.
2. Marcar todos los puertos del root como Designated Forwarding.
3. Elegir el Root Port de cada switch no-root.
4. Elegir el Designated Port de cada segmento.
5. Marcar el resto como Alternate/Backup.

## Comando principal

```bash
show spanning-tree
```

## Configurar root primary

```bash
conf t
spanning-tree vlan 10 root primary
end
wr
```

## Revisar prioridad

```bash
show spanning-tree vlan 10
```

## Errores típicos

- Confundir Root Bridge con Root Port.
- Pensar que todos los enlaces redundantes están activos.
- No tener en cuenta costes.
- Resolver empates sin mirar BID o Port ID.
