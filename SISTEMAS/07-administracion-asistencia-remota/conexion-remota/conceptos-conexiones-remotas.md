# Conceptos de conexiones remotas

## Qué es una conexión remota

Una conexión remota permite administrar o utilizar un equipo desde otro dispositivo a través de la red.

Puede ser de dos tipos principales:

- Terminal remota: se trabaja con comandos.
- Escritorio remoto: se controla el entorno gráfico.

## Protocolos habituales

| Protocolo | Uso principal | Puerto habitual |
|---|---|---:|
| RDP | Escritorio remoto Windows | 3389 |
| SSH | Terminal remota Linux/Unix | 22 |
| VNC | Escritorio remoto multiplataforma | 5900 |

## Diferencia entre RDP, SSH y VNC

### RDP

RDP está pensado para acceder gráficamente a sistemas Windows.

Permite abrir una sesión de escritorio remoto con usuario y contraseña.

### SSH

SSH permite administrar un equipo desde terminal de forma segura.

Es ideal para servidores Linux porque no requiere entorno gráfico.

### VNC

VNC permite ver y controlar el escritorio gráfico de otro equipo.

En Linux puede usarse con herramientas como Vino, aunque hay que vigilar compatibilidad con Wayland/Xorg.

## Flujo básico de una conexión remota

1. Comprobar conectividad IP.
2. Activar el servicio remoto en el equipo destino.
3. Abrir el puerto correspondiente en el firewall.
4. Crear o configurar usuario autorizado.
5. Crear la conexión desde el equipo administrador.
6. Probar acceso.
7. Documentar configuración y credenciales usadas en laboratorio.

## Buenas prácticas

- No exponer RDP, SSH o VNC directamente a Internet sin protección.
- Usar contraseñas fuertes.
- Limitar usuarios autorizados.
- Usar VPN si se administra desde fuera de la red.
- No guardar contraseñas en texto plano si no es estrictamente necesario.
- Documentar IP, protocolo, puerto y usuario usado.

## Resumen

Las conexiones remotas son básicas para administración de sistemas, pero deben configurarse con criterio: servicio activo, puerto permitido, usuario autorizado y pruebas de conectividad.
