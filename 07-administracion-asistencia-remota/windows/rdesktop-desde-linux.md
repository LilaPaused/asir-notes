# Conexión RDP desde Linux con rdesktop

## Qué es rdesktop

`rdesktop` es una herramienta de Linux para conectarse por RDP a equipos Windows.

Permite abrir una sesión gráfica remota desde Ubuntu hacia Windows.

## Instalar rdesktop

En Ubuntu/Debian:

```bash
sudo apt update
sudo apt install rdesktop
```

## Sintaxis básica

```bash
rdesktop -u usuario IP_DEL_WINDOWS
```

Ejemplo:

```bash
rdesktop -u alumne 172.16.12.100
```

Después pedirá la contraseña del usuario.

## Pasar contraseña en el comando

También existe opción para pasar contraseña, pero no es recomendable:

```bash
rdesktop -u usuario -p contraseña IP_DEL_WINDOWS
```

No es profesional porque deja la contraseña visible en historial o procesos.

## Buenas prácticas

Usar:

```bash
rdesktop -u usuario IP_DEL_WINDOWS
```

Y escribir la contraseña cuando la pida.

## Requisitos en Windows

Antes de conectar desde Linux:

- RDP debe estar habilitado.
- El usuario debe tener permisos.
- Firewall debe permitir RDP.
- El equipo debe tener IP accesible.

## Problemas comunes

### Certificado no confiable

Puede aparecer un aviso porque el certificado del servidor no está validado por una CA confiable.

En laboratorio se puede aceptar si se confirma que la IP es correcta.

### No conecta

Revisar:

```bash
ping IP_DEL_WINDOWS
```

Y en Windows revisar:

- Escritorio remoto.
- Firewall.
- Usuario.
