# PF4 - Repaso

## Preguntas teóricas

### Construcción de repositorio local Ubuntu Server

Pasos:

1. Instalar apt-mirror en el servidor.
2. Preparar una ruta con espacio suficiente para guardar paquetes.
3. Configurar /etc/apt/mirror.list.
4. Ejecutar apt-mirror para descargar paquetes.
5. Publicar el repositorio con Apache2.
6. Comprobar desde cliente por navegador o curl.
7. Modificar sources.list del cliente para usar el servidor local.
8. Ejecutar apt update en cliente.
9. Instalar un paquete de prueba.

En clientes se debe configurar APT para que use el repositorio local en vez de los repositorios externos.

### Convertir Windows Server en WSUS

Pasos:

1. Instalar rol WSUS.
2. Indicar carpeta de almacenamiento.
3. Configurar asistente de WSUS.
4. Elegir idiomas.
5. Elegir productos.
6. Elegir clasificaciones.
7. Sincronizar con Microsoft Update.
8. Crear grupo de equipos.
9. Crear GPO para clientes.
10. Configurar servidor WSUS interno con puerto 8530.
11. Habilitar destinatarios del lado cliente.
12. Aprobar actualizaciones.
13. Comprobar en cliente.

### AppLocker

AppLocker permite crear reglas para permitir o bloquear aplicaciones.

Tipos de reglas:

- ejecutables
- instaladores Windows
- scripts
- aplicaciones empaquetadas
- DLLs

Condiciones:

- editor
- ruta
- hash

## Práctica Windows: fondo obligatorio

Pasos:

1. Crear carpeta CompartitXX.
2. Compartirla con usuarios del dominio.
3. Copiar wallpaper.jpg en la carpeta.
4. Crear GPO fonsXX vinculada al dominio.
5. Configurar Tapiz del escritorio usando ruta UNC.
6. Bloquear cambio de fondo desde Panel de control > Personalización.
7. Aplicar gpupdate /force.
8. Comprobar con usu1 y usu2.

## Práctica Windows: instalación de Notepad++

Pasos:

1. Copiar notepadpp.msi en una carpeta compartida.
2. Crear GPO instalaXX vinculada a la OU segunda.
3. Editar Instalación de software.
4. Añadir paquete desde ruta UNC.
5. Dejarlo como asignado.
6. Iniciar sesión con usu1 y comprobar que no se instala.
7. Iniciar sesión con usu2 y comprobar que sí se instala.

## Práctica Linux: Ansible

Pasos:

1. Instalar ansible en el servidor.
2. Crear inventario con grupo clientsXX.
3. Crear usuario sisadmin en clientes.
4. Dar sudo sin contraseña.
5. Instalar openssh-server en clientes.
6. Crear clave RSA en servidor.
7. Copiar clave a clientes con ssh-copy-id.
8. Probar ansible ping.

Comando de prueba:

ansible all -i /etc/ansible/hosts/hosts.ini -m ping -u sisadmin

## Playbook instalaXX

Objetivo:

- instalar cowsay en clientes

Comprobar:

cowsay "Hola Rafa"

## Repositorio local APT

Puntos clave:

- apt-mirror descarga paquetes.
- Apache2 publica el repositorio.
- El cliente debe cambiar sources.list.
- Ansible puede automatizar la configuración del cliente.

## Comandos útiles

Aplicar GPO:

gpupdate /force

Ver GPOs de usuario:

gpresult /r

Ver GPOs de equipo:

gpresult /r /scope computer

Instalar Ansible:

sudo apt install ansible

Probar Ansible:

ansible all -i /etc/ansible/hosts/hosts.ini -m ping -u sisadmin

Instalar apt-mirror:

sudo apt install apt-mirror

Ejecutar mirror:

sudo apt-mirror
