# Instalar Windows y Linux en VirtualBox

## Objetivo

Instalar sistemas operativos dentro de las máquinas virtuales creadas previamente.

Sistemas trabajados:

- Windows 10
- Windows Server
- Ubuntu Desktop
- Ubuntu Server

## Instalación de Windows 10

### Versión recomendada

Usar Windows 10 Pro.

Motivos:

- permite unirse a dominio
- incluye Escritorio Remoto
- permite BitLocker
- incluye editor de directivas
- es más adecuada para prácticas de sistemas

## Disco de instalación

Instalar Windows en el disco de 50 GB.

El disco de 100 GB queda libre para prácticas posteriores.

## Tipo de instalación

Seleccionar instalación personalizada.

Esto permite elegir manualmente el disco donde se instalará el sistema.

## Configuración inicial

Durante el primer arranque:

- seleccionar idioma
- seleccionar distribución de teclado
- evitar vincular cuenta Microsoft si la práctica pide usuario local
- crear usuario requerido
- comprobar conexión a Internet

## Instalación de Windows Server

Usar versión con experiencia de escritorio si se quiere entorno gráfico.

En prácticas de administración puede interesar instalar también versiones sin GUI para trabajar desde PowerShell.

## Instalación de Ubuntu Desktop

En Ubuntu se puede separar:

- / en el disco principal
- /home en el segundo disco

Esto permite separar el sistema de los datos de usuario.

## Instalación de Ubuntu Server

En Ubuntu Server el particionado suele hacerse desde el instalador en modo texto.

Puntos importantes:

- asignar hostname correcto
- crear usuario administrador
- comprobar red
- instalar OpenSSH si se necesita administración remota

## Comprobaciones finales

Después de instalar cualquier sistema:

- comprobar hostname
- comprobar usuario
- comprobar dirección IP
- comprobar conexión a Internet

En Windows:

- whoami
- hostname
- ipconfig

En Linux:

- whoami
- hostname
- ip a

## Snapshots

Después de instalar un sistema limpio, es recomendable crear una instantánea.

Nombre recomendado:

Recien instalado

Esto permite volver a un estado funcional si una práctica rompe la máquina.

## Buenas prácticas

- No instalar cosas innecesarias antes del snapshot inicial.
- Comprobar red antes de continuar.
- Documentar errores.
- Mantener nombres de máquinas coherentes.
- Separar sistema y datos cuando sea posible.
