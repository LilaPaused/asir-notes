# SSH con OpenSSH Server

## Qué es SSH

SSH permite conectarse de forma remota a una terminal de otro equipo.

Es el método más común para administrar servidores Linux.

## Instalar OpenSSH Server

En Ubuntu/Debian:

```bash
sudo apt update
sudo apt install openssh-server
```

## Activar servicio

```bash
sudo systemctl enable ssh
sudo systemctl start ssh
```

Comprobar estado:

```bash
sudo systemctl status ssh
```

## Conectar desde Linux

```bash
ssh usuario@IP_DEL_SERVIDOR
```

Ejemplo:

```bash
ssh alumne@172.16.12.200
```

## Conectar desde mRemoteNG

Configurar:

| Campo | Valor |
|---|---|
| Protocolo | SSH version 2 |
| Puerto | 22 |
| Hostname/IP | IP del Ubuntu destino |
| Usuario | usuario Linux |
| Contraseña | contraseña del usuario |

## Primer acceso

En el primer acceso, SSH puede mostrar una advertencia sobre la clave del host.

Si la IP es correcta y estamos en laboratorio, se acepta para guardar la huella del servidor.

## Instalar paquetes remotamente

Una vez conectado por SSH se puede administrar el sistema:

```bash
sudo apt install rdesktop
```

## Abrir puerto con UFW

Si UFW está activo:

```bash
sudo ufw allow 22/tcp
sudo ufw status
```

## Buenas prácticas

- No permitir login directo de root.
- Usar usuarios normales con sudo.
- Usar claves SSH en entornos reales.
- Limitar acceso por firewall.
- Cambiar contraseñas por defecto.
