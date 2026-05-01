# PF1 - Repaso de Sistemas Operativos

## Parte teórica

### 1. Arquitectura de Von Neumann

La arquitectura de Von Neumann se compone de:

- CPU
- memoria principal
- entrada/salida
- bus de datos
- bus de direcciones
- bus de control

Respuesta corta:

Es un modelo de arquitectura donde la CPU, la memoria principal y los dispositivos de entrada/salida se comunican mediante buses.

## 2. Gestión de memoria

Tipos principales:

1. Paginación
2. Segmentación

### Paginación

Divide memoria lógica y física en bloques de tamaño fijo.

Ventaja:

- evita fragmentación externa

Inconveniente:

- puede provocar fragmentación interna

### Segmentación

Divide la memoria en bloques de tamaño variable según partes lógicas del programa.

Ventaja:

- se adapta mejor a la estructura del programa

Inconveniente:

- puede provocar fragmentación externa

## 3. Proceso de arranque

Pasos:

1. Power On
2. BIOS/UEFI
3. POST
4. Búsqueda de dispositivo de arranque
5. Lectura de MBR/GPT
6. Carga del Boot Manager
7. Arranque del sistema operativo

Respuesta corta:

Al encender el equipo, se alimenta el hardware, se ejecuta BIOS/UEFI, se comprueba el sistema con POST, se busca un dispositivo arrancable, se lee MBR/GPT, se carga el gestor de arranque y finalmente toma el control el sistema operativo.

## Parte práctica

### Crear máquina virtual con disco existente

1. Crear nueva máquina.
2. Asignar nombre requerido.
3. Asignar CPU y RAM.
4. Usar disco existente .vdi.
5. Arrancar.
6. Comprobar nombre del equipo.

En Windows:

- hostname
- whoami

## Dual boot con discos ya instalados

Caso:

- disco 1: Windows 10
- disco 2: Ubuntu Desktop

Objetivo:

- tener GRUB funcional para elegir sistema

Método rápido:

1. Añadir ambos discos a la máquina virtual.
2. Montar ISO de Boot Repair.
3. Arrancar desde Boot Repair.
4. Aplicar reparación.
5. Reiniciar.
6. Comprobar GRUB.

## Backup de drivers en Windows

Comando recomendado desde CMD o PowerShell como administrador:

dism /online /export-driver /destination:%USERPROFILE%\Desktop\drivers_cnom

Ejemplo:

dism /online /export-driver /destination:C:\Users\ASIX1\Desktop\drivers_mjose

## Información hardware en Ubuntu en HTML

Instalar si hace falta:

sudo apt install lshw

Crear HTML:

sudo lshw -html > /home/asix1/Escritorio/hw_cnom.html

Ejemplo:

sudo lshw -html > /home/asix1/Escritorio/hw_mjose.html

Abrir con navegador:

firefox /home/asix1/Escritorio/hw_mjose.html

## Lista de software instalado en Ubuntu

apt list --installed > /home/asix1/Escritorio/llistaSW.txt

Buscar un paquete concreto:

apt list --installed | grep firefox

## Instalar wine64

sudo apt update
sudo apt install wine64

Durante la instalación, apt mostrará cuántos paquetes nuevos se instalarán.

## Ver dependencias de wine64

apt depends wine64

## Windows Update desde PowerShell

Instalar módulo:

Install-Module PSWindowsUpdate

Buscar actualizaciones:

Get-WindowsUpdate

Instalar todas:

Install-WindowsUpdate -AcceptAll -AutoReboot

Instalar una KB concreta:

Install-WindowsUpdate -KBArticleID KBXXXXXXX -AcceptAll -AutoReboot

## Fallos a evitar

- No dejar preguntas teóricas sin responder.
- No olvidar comprobar hostname.
- No olvidar capturar evidencia del GRUB.
- No hacer comandos sin privilegios de administrador.
- No confundir ruta de Escritorio en Linux.
- No desactivar Windows Update sin saber cómo volver a activarlo.
