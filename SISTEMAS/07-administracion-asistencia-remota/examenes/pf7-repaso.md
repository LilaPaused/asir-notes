# PF7 - Repaso

## Parte teórica

### Qué es una incidencia informática

Una incidencia informática es un reporte de mal funcionamiento de un elemento tecnológico del entorno de trabajo.

Ejemplos:

- ordenador lento
- aplicación que no abre
- error de red
- teclado roto
- pérdida de acceso
- pantalla defectuosa

## Campos mínimos de un formulario de usuario

- ID de empleado.
- Correo o teléfono.
- Código del dispositivo.
- Descripción de la incidencia.
- Si hay datos que recuperar.

## Campos del técnico

Al recibir:

- técnico asignado
- fecha de recepción
- diagnóstico inicial
- tipo de actuación

Al cerrar:

- fecha de resolución
- solución aplicada
- piezas usadas
- equipo sustituido
- garantía
- datos recuperados

## Protocolo de actuación

Preguntas clave:

1. ¿Se puede solucionar remotamente?
2. ¿Se puede solucionar en el sitio?
3. ¿El equipo tiene garantía?
4. ¿Hay que comprar piezas?
5. ¿Es viable reparar?
6. ¿Hay datos para recuperar?

## Parte práctica: red interna

Ejemplo:

| Máquina | IP |
|---|---|
| w10-2425 | 172.16.XX.100 |
| ud-2425 | 172.16.XX.200 |

Comprobar conectividad:

```cmd
ping 172.16.XX.200
```

```bash
ping 172.16.XX.100
```

## SSH en Ubuntu

Instalar:

```bash
sudo apt install openssh-server
```

Activar:

```bash
sudo systemctl enable ssh
sudo systemctl start ssh
```

Conectar desde mRemoteNG:

- Protocolo: SSH version 2
- IP: 172.16.XX.200
- Usuario: alumne
- Puerto: 22

Instalar paquete remotamente:

```bash
sudo apt install rdesktop
```

## VNC en Ubuntu

Instalar Vino:

```bash
sudo apt install vino
```

Permitir puerto:

```bash
sudo ufw allow 5900/tcp
```

Desactivar cifrado si el cliente no lo soporta:

```bash
gsettings set org.gnome.Vino require-encryption false
```

Iniciar servidor:

```bash
/usr/lib/vino/vino-server &
```

Conectar desde mRemoteNG:

- Protocolo: VNC
- IP: 172.16.XX.200
- Puerto: 5900
- Contraseña: la configurada en el escritorio remoto

## RDP en Windows

En Windows:

1. Activar Escritorio remoto.
2. Permitir conexiones remotas.
3. Revisar firewall.
4. Asegurar usuario autorizado.

Desde Linux:

```bash
rdesktop -u alumne 172.16.XX.100
```

## Comandos importantes

### Linux

```bash
ip a
ping IP
sudo apt install openssh-server
sudo systemctl enable ssh
sudo systemctl start ssh
sudo ufw allow 22/tcp
sudo ufw allow 5900/tcp
sudo ufw status
rdesktop -u usuario IP
```

### Windows

```cmd
ipconfig
ping IP
mstsc
```

## Errores típicos

### SSH no conecta

Revisar:

- openssh-server instalado
- servicio iniciado
- firewall
- IP correcta
- usuario correcto

### VNC no conecta

Revisar:

- Vino instalado
- puerto 5900 abierto
- sesión Xorg
- contraseña correcta
- cifrado compatible

### RDP no conecta

Revisar:

- RDP activado
- firewall
- usuario autorizado
- IP correcta

## Resumen rápido

- RDP: escritorio remoto Windows.
- SSH: terminal remota segura.
- VNC: escritorio gráfico remoto.
- mRemoteNG: gestor centralizado de conexiones.
- Incidencia: problema reportado por usuario que debe registrarse, diagnosticarse y cerrarse correctamente.
