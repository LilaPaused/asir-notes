# VNC con Vino en GNOME

## Qué es VNC

VNC permite conectarse al escritorio gráfico de una máquina remota.

En Ubuntu Desktop puede usarse con Vino o con la función de compartición de escritorio.

## Puerto habitual

```text
5900/TCP
```

## Importante: Xorg vs Wayland

Algunas herramientas antiguas o clientes VNC tienen problemas con Wayland.

En laboratorio puede ser necesario iniciar sesión con Xorg en vez de Wayland.

## Instalar Vino

```bash
sudo apt update
sudo apt install vino
```

## Configurar desde interfaz gráfica

En Ubuntu GNOME:

```text
Configuración -> Compartición -> Compartición de escritorio
```

Activar:

- Compartición de escritorio.
- Control remoto.
- Contraseña de acceso.

## Configurar desde terminal

Desactivar requisito de cifrado si el cliente VNC no lo soporta:

```bash
gsettings set org.gnome.Vino require-encryption false
```

Permitir conexión VNC:

```bash
gsettings set org.gnome.Vino enabled true
```

Configurar método de autenticación:

```bash
gsettings set org.gnome.Vino authentication-methods "['vnc']"
```

## Asignar contraseña VNC

La contraseña debe configurarse desde la interfaz gráfica o con `gsettings`, según versión.

En prácticas puede dejarse definida desde la configuración de escritorio remoto.

## Iniciar Vino manualmente

```bash
/usr/lib/vino/vino-server &
```

## Abrir puerto con UFW

```bash
sudo ufw allow 5900/tcp
sudo ufw status
```

## Conexión desde mRemoteNG

Configurar:

| Campo | Valor |
|---|---|
| Protocolo | VNC |
| Puerto | 5900 |
| Hostname/IP | IP del Ubuntu destino |
| Password | contraseña VNC |

## Problemas comunes

### Pantalla negra

Puede estar relacionado con Wayland, sesión bloqueada o incompatibilidad del servidor VNC.

### Error de cifrado

Probar:

```bash
gsettings set org.gnome.Vino require-encryption false
```

### No conecta

Revisar:

- Vino instalado.
- Servicio iniciado.
- Puerto 5900 abierto.
- IP correcta.
- Sesión gráfica iniciada.
