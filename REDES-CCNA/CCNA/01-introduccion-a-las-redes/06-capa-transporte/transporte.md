# Capa de transporte

## Protocolos principales

- TCP
- UDP

## Puertos

Permiten multiplexar conexiones.

### Rangos

| Rango | Uso |
|---|---|
| 0 - 1023 | Bien conocidos |
| 1024 - 49151 | Registrados |
| 49152 - 65535 | Dinámicos |

## Socket

```text
IP + Puerto
```

Permite distinguir conexiones.

## TCP

Características:

- Orientado a conexión.
- Fiable.
- Usa ACK.
- Control de flujo.
- Control de errores.

### 3-Way Handshake

1. SYN
2. SYN-ACK
3. ACK

## UDP

Características:

- No orientado a conexión.
- No fiable.
- Más rápido.
- No usa ACK.

## Comparación

| Característica | TCP | UDP |
|---|---|---|
| Conexión | Sí | No |
| Fiabilidad | Sí | No |
| ACK | Sí | No |
| Velocidad | Menor | Mayor |
