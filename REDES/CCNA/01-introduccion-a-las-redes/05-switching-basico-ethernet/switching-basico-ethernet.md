# Switching básico y Ethernet

## Switch

Un switch trabaja principalmente en capa 2 y conmuta tramas usando direcciones MAC.

## Tabla CAM

La tabla CAM relaciona:

```text
MAC -> Puerto
```

Reglas:

- Una MAC solo puede estar asociada a un puerto.
- Un puerto puede tener muchas MAC.

## Funcionamiento básico

1. El switch recibe una trama.
2. Aprende la MAC origen.
3. Busca la MAC destino en la tabla CAM.
4. Si conoce el puerto destino, reenvía por ese puerto.
5. Si no conoce el destino, hace flood.

## Flood

Reenvío por todos los puertos excepto por el puerto de entrada.

## Dominios

### Dominio de colisión

Zona donde pueden ocurrir colisiones.

### Dominio de broadcast

Zona donde se propaga broadcast.

## Store and Forward

El switch recibe la trama completa, verifica FCS y luego reenvía.

Es más seguro, pero más lento.

## Cut Through

El switch empieza a reenviar antes de recibir toda la trama.

Es más rápido, pero menos seguro.

## Encapsulación

Cada capa añade información propia.

| Capa | Unidad |
|---|---|
| Aplicación | Datos |
| Transporte | Segmento |
| Red | Paquete |
| Enlace | Trama |
| Física | Bits |
