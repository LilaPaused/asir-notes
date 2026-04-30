# Auditd en Linux

## Qué es

`auditd` es el sistema de auditoría de Linux.

Permite registrar acciones a nivel de sistema, especialmente sobre ficheros, comandos, usuarios y eventos del kernel.

## Instalación

En Ubuntu/Debian:

    sudo apt install auditd audispd-plugins

## Servicio

Comprobar estado:

    sudo systemctl status auditd

## Configuración principal

Archivo:

    /etc/audit/auditd.conf

Controla aspectos como:

- ubicación de logs
- formato de logs
- rotación
- tamaño máximo de archivos
- comportamiento si se llena el disco

## Ver reglas activas

    sudo auditctl -l

## Crear regla temporal

Ejemplo para auditar escritura sobre un fichero:

    sudo auditctl -w /ruta/prova_auditoria -p w -k modprova

Donde:

- `-w`: objeto vigilado
- `-p w`: permiso auditado, en este caso escritura
- `-k`: clave para buscar eventos

## Eliminar una regla

    sudo auditctl -W /ruta/prova_auditoria -p w -k modprova

## Eliminar todas las reglas

    sudo auditctl -D

## Buscar eventos

Por fichero:

    sudo ausearch -f /ruta/prova_auditoria

Por clave:

    sudo ausearch -k modprova

## Idea clave

Las reglas creadas con `auditctl` son temporales. Si reinicias, se pierden salvo que las guardes como reglas persistentes.
