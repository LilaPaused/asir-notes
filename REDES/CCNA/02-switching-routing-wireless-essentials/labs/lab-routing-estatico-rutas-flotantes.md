# Lab - Routing estático y rutas flotantes

## Objetivo

Configurar rutas estáticas y una ruta flotante como backup.

## Ruta estática principal

```bash
ip route 192.168.20.0 255.255.255.0 10.0.0.2
```

## Ruta flotante

```bash
ip route 192.168.20.0 255.255.255.0 10.0.1.2 10
```

## Explicación

La ruta principal tiene AD 1.

La ruta flotante tiene AD 10.

Mientras la ruta principal esté disponible, la ruta flotante no aparece en la tabla de routing.

## Verificación

```bash
show ip route
ping 192.168.20.1
traceroute 192.168.20.1
```

## Prueba de fallo

1. Apagar la interfaz principal.
2. Revisar tabla de rutas.
3. Confirmar que entra la ruta flotante.
4. Restaurar interfaz principal.
5. Confirmar que vuelve la ruta principal.

## Regla práctica

Una ruta flotante solo debe entrar cuando la ruta principal deja de estar disponible.
