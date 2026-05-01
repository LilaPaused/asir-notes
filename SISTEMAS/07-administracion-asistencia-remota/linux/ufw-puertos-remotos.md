# UFW y puertos remotos

## Qué es UFW

UFW es una interfaz sencilla para gestionar reglas de firewall en Ubuntu.

## Ver estado

```bash
sudo ufw status
```

Si está inactivo:

```bash
sudo ufw enable
```

## Permitir SSH

```bash
sudo ufw allow 22/tcp
```

## Permitir VNC

```bash
sudo ufw allow 5900/tcp
```

## Ver reglas

```bash
sudo ufw status numbered
```

## Borrar regla

```bash
sudo ufw delete NUMERO
```

## Reglas típicas de laboratorio

```bash
sudo ufw allow 22/tcp
sudo ufw allow 5900/tcp
sudo ufw status
```

## Tabla rápida

| Servicio | Puerto | Protocolo |
|---|---:|---|
| SSH | 22 | TCP |
| VNC | 5900 | TCP |
| RDP | 3389 | TCP |

## Cuidado

Antes de activar UFW en una máquina remota, asegúrate de permitir SSH.

Si activas firewall sin permitir SSH, puedes bloquear tu propia conexión.
