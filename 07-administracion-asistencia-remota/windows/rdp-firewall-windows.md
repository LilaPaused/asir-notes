# Firewall y reglas RDP en Windows

## Objetivo

Para aceptar conexiones RDP, Windows debe tener habilitado el servicio y permitir tráfico en el firewall.

## Puerto RDP

```text
3389/TCP
```

## Reglas de firewall

En el Firewall de Windows con seguridad avanzada, revisar reglas de entrada relacionadas con:

```text
Escritorio remoto
Remote Desktop
RDP
```

Deben estar habilitadas para el perfil de red correspondiente.

## Habilitar desde interfaz gráfica

1. Abrir Firewall de Windows con seguridad avanzada.
2. Ir a Reglas de entrada.
3. Buscar reglas de Escritorio remoto.
4. Habilitar las necesarias.

## Comprobar desde PowerShell

Listar reglas relacionadas con Remote Desktop:

```powershell
Get-NetFirewallRule | Where-Object DisplayName -like "*Remote Desktop*"
```

Habilitar reglas:

```powershell
Enable-NetFirewallRule -DisplayGroup "Remote Desktop"
```

## Probar desde otro equipo

Desde Windows:

```cmd
mstsc
```

Desde Linux con rdesktop:

```bash
rdesktop -u usuario IP_DEL_WINDOWS
```

## Error típico

Si el ping responde pero RDP no conecta, normalmente el problema es:

- Escritorio remoto no habilitado.
- Firewall bloqueando 3389.
- Usuario sin permisos.
- Servicio no activo.

## Recomendación

En laboratorio se permite abrir RDP, pero en producción no debería exponerse a redes no confiables. Mejor usar VPN, segmentación y reglas de firewall restrictivas.
