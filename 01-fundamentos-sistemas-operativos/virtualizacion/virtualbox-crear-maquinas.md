# Crear máquinas virtuales con VirtualBox

## Objetivo

Crear máquinas virtuales preparadas para instalar distintos sistemas operativos.

En este bloque se trabaja con:

- Windows 10
- Windows Server
- Ubuntu Desktop
- Ubuntu Server

## Máquinas creadas

| Máquina | Sistema previsto | RAM | CPU | Disco |
|---|---|---:|---:|---:|
| mv_w10 | Windows 10 | 6 GB | 4 cores | 50 GB + 100 GB |
| mv_w2019 / mv_w2022 | Windows Server | 8 GB | 6 cores | 50 GB + 100 GB |
| mv_ud24.04 | Ubuntu Desktop | 4 GB | 2 cores | 50 GB + 100 GB |
| mv_us24.04 | Ubuntu Server | 2 GB | 2 cores | 50 GB + 100 GB |

## Recomendación de configuración

### Sistema

- Asignar RAM suficiente.
- No usar más núcleos de los necesarios.
- Activar EFI si el sistema lo requiere.
- Comprobar que la virtualización está activa en BIOS/UEFI del host.

### Almacenamiento

Cada máquina debe tener dos discos:

- disco principal para el sistema
- disco secundario para datos, prácticas o particiones específicas

Ejemplo:

- Disco 1: 50 GB
- Disco 2: 100 GB

### Red

Para prácticas iniciales, usar NAT.

Ventajas de NAT:

- conexión a Internet fácil
- no requiere configuración extra
- suficiente para instalar paquetes y actualizaciones

## Pasos generales

1. Abrir VirtualBox.
2. Crear nueva máquina.
3. Elegir tipo de sistema operativo.
4. Asignar memoria RAM.
5. Asignar CPUs.
6. Crear disco virtual principal.
7. Añadir segundo disco.
8. Configurar red en NAT.
9. Montar ISO cuando toque instalar.
10. Comprobar que arranca.

## Buenas prácticas

- Usar nombres claros.
- No mezclar ISOs, discos y snapshots sin orden.
- Crear snapshots después de cada instalación limpia.
- Guardar las máquinas en una carpeta identificable.
- Documentar errores reales.

## Ejemplo de nombres

- mv_w10
- mv_w2022
- mv_ud24.04
- mv_us24.04

## Conceptos relacionados

- [Instalar Windows y Linux](./instalar-windows-linux.md)
- [Errores comunes en VirtualBox](./errores-virtualbox.md)
