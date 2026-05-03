# Routing estático

## Concepto

El routing estático consiste en crear rutas manualmente.

## Tabla RIB

La tabla RIB contiene las rutas conocidas por el router.

Campos habituales:

- Red destino.
- Máscara.
- Interfaz de salida.
- Next Hop.
- Distancia administrativa.
- Métrica.

## Next Hop

Router siguiente al que se envía el paquete.

## Ruta por defecto

```text
0.0.0.0/0
```

Se usa cuando no existe una ruta más específica.

## Longest Prefix Match

El router elige la ruta más específica.

Ejemplo:

```text
192.168.2.0/24
192.168.2.0/23
```

Para un destino dentro de `192.168.2.0/24`, gana `/24`.

## Distancia administrativa

Indica la preferencia de la ruta.

| Ruta | AD |
|---|---|
| Conectada | 0 |
| Estática | 1 |
| OSPF | 110 |
| RIP | 120 |

## Ruta estática básica

```bash
ip route 192.168.20.0 255.255.255.0 10.0.0.2
```

## Ruta por defecto

```bash
ip route 0.0.0.0 0.0.0.0 10.0.0.2
```

## Ruta flotante

Ruta estática con AD más alta.

Sirve como backup.

```bash
ip route 192.168.20.0 255.255.255.0 10.0.0.2 10
```

## Punto a punto y broadcast

En punto a punto se puede usar interfaz de salida.

En redes broadcast es recomendable usar next hop.

## Supernetting

Agrupa varias rutas en una sola.

Ejemplo:

```text
192.168.2.0/24
192.168.3.0/24
```

Resumen:

```text
192.168.2.0/23
```

## Verificación

```bash
show ip route
show running-config | include ip route
ping
traceroute
```

## Errores típicos

- Configurar la ruta en un router, pero no la ruta de vuelta.
- Usar una máscara incorrecta.
- Poner mal el next hop.
- Usar una interfaz de salida en red broadcast sin next hop.
- Olvidar que la default route es la última opción.
