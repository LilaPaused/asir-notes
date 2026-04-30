# Red interna y pruebas de ping

## Objetivo

Antes de configurar administración remota, hay que comprobar que las máquinas se ven entre sí.

En las prácticas se trabaja con una red interna donde cada máquina tiene una IP fija.

## Ejemplo de esquema

| Máquina | Rol | IP ejemplo |
|---|---|---|
| winadm | Equipo administrador | 192.168.12.X |
| wserver | Windows Server | 192.168.12.1 |
| userver | Ubuntu Server | 192.168.12.2 |
| wclient | Cliente Windows | 192.168.12.100 |
| uclient | Cliente Ubuntu | 192.168.12.200 |

En el examen también aparece una red del tipo:

| Máquina | IP |
|---|---|
| w10-2425 | 172.16.XX.100 |
| ud-2425 | 172.16.XX.200 |

## Probar conectividad desde Windows

Comando:

```cmd
ping 192.168.12.1
ping 192.168.12.2
```

Para ver configuración IP:

```cmd
ipconfig
```

## Probar conectividad desde Linux

Comando:

```bash
ping 172.16.12.100
ping 172.16.12.200
```

Para ver configuración IP:

```bash
ip a
```

## Si el ping falla

Revisar:

1. Que las máquinas estén en la misma red interna.
2. Que la IP esté bien configurada.
3. Que la máscara sea correcta.
4. Que no haya IP duplicada.
5. Que el firewall permita ICMP.
6. Que el adaptador correcto esté activo.

## Importante

Que el ping funcione no significa que RDP, SSH o VNC funcionen.

El ping solo demuestra conectividad básica. Después hay que comprobar servicios y puertos.
