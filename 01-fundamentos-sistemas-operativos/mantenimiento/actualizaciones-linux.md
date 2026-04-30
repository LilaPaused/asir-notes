# Actualizaciones en Linux

## Qué es

Actualizar Linux consiste en sincronizar repositorios e instalar nuevas versiones de paquetes.

En sistemas basados en Debian/Ubuntu se usa apt.

## Actualizar lista de paquetes

sudo apt update

Este comando no instala actualizaciones.

Solo actualiza la información de los repositorios.

## Ver paquetes actualizables

apt list --upgradable

## Instalar actualizaciones

sudo apt upgrade

## Actualización más completa

sudo apt full-upgrade

Puede instalar o eliminar paquetes si es necesario para resolver dependencias.

## Limpiar paquetes innecesarios

sudo apt autoremove

## Buscar paquete

apt search nombre-paquete

## Ver si un paquete está instalado

apt list --installed | grep nombre-paquete

Ejemplo:

apt list --installed | grep firefox

## Instalar paquete

sudo apt install nombre-paquete

Ejemplo:

sudo apt install wine64

## Ver dependencias de un paquete

apt depends nombre-paquete

Ejemplo:

apt depends wine64

## Guardar lista de paquetes instalados

apt list --installed > listaSW.txt

## Flujo recomendado

sudo apt update
apt list --upgradable
sudo apt upgrade
sudo apt autoremove

## Diferencia entre update y upgrade

| Comando | Qué hace |
|---|---|
| apt update | Actualiza la lista de paquetes |
| apt upgrade | Instala actualizaciones disponibles |
| apt full-upgrade | Actualiza resolviendo cambios de dependencias |
| apt autoremove | Elimina paquetes que ya no hacen falta |

## Buenas prácticas

- Ejecutar apt update antes de instalar software.
- Leer qué paquetes se instalarán o eliminarán.
- En servidores, evitar actualizar sin plan.
- Reiniciar si se actualiza kernel o servicios críticos.
