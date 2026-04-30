# Escritorio remoto RDP en Windows

## Qué es RDP

RDP es el protocolo de escritorio remoto de Microsoft.

Permite conectarse gráficamente a un equipo Windows desde otro equipo.

## Puerto habitual

RDP usa normalmente el puerto:

```text
3389/TCP
```

## Habilitar Escritorio remoto

Ruta habitual en Windows:

```text
Configuración -> Sistema -> Escritorio remoto
```

Activar:

```text
Habilitar Escritorio remoto
```

Confirmar la advertencia.

## Usuarios autorizados

Para entrar por RDP, el usuario debe tener permisos.

Normalmente pueden entrar:

- Administradores locales.
- Usuarios añadidos al grupo de Escritorio remoto.

## Conectarse desde Windows

Comando:

```cmd
mstsc
```

Luego introducir:

- IP del equipo destino.
- Usuario.
- Contraseña.

## Conectarse desde mRemoteNG

Configuración típica:

| Campo | Valor |
|---|---|
| Protocolo | RDP |
| Puerto | 3389 |
| Hostname/IP | IP del Windows destino |
| Usuario | Usuario autorizado |
| Contraseña | Contraseña del usuario |

## Prueba correcta

Una prueba correcta es que aparezca la ventana de credenciales de Windows y, al autenticar, se abra el escritorio remoto.

## Problemas comunes

### No aparece pantalla de login

Revisar:

- IP correcta.
- RDP habilitado.
- Firewall.
- Adaptador de red.

### Usuario no autorizado

Añadir el usuario al grupo correspondiente o usar un administrador local.

### Error de certificado

En entornos de laboratorio puede aparecer aviso de certificado. No siempre es un problema real; hay que verificar que se conecta al equipo correcto.
