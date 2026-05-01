# Ansible Server

## Qué es Ansible

Ansible es una herramienta de automatización que permite administrar varios equipos desde un servidor central.

Funciona normalmente por SSH y no requiere instalar un agente propio en los clientes.

## Para qué sirve

En este tema se usa Ansible para:

- comprobar conectividad con clientes
- instalar paquetes
- configurar repositorios
- montar recursos NFS
- modificar ficheros de configuración
- aplicar cambios en varios equipos a la vez

## 1. Instalar Ansible en el servidor

En Ubuntu Server:

sudo apt update
sudo apt install ansible

## 2. Preparar estructura

Crear carpetas para inventarios y playbooks:

sudo mkdir -p /etc/ansible/hosts
sudo mkdir -p /etc/ansible/playbooks

## 3. Crear inventario

Archivo:

/etc/ansible/hosts/hosts.ini

Ejemplo:

[clients12]
192.168.100.1
192.168.100.2

## 4. Preparar usuario administrador en clientes

En cada cliente crear usuario:

sisadmin

Contraseña:

adminsis

Añadirlo a sudo:

sudo usermod -aG sudo sisadmin

## 5. Permitir sudo sin contraseña

Editar con visudo:

sudo visudo

Añadir:

sisadmin ALL=(ALL) NOPASSWD:ALL

## 6. Instalar SSH en clientes

En cada cliente:

sudo apt update
sudo apt install openssh-server

Comprobar servicio:

sudo systemctl status ssh

## 7. Generar clave en servidor

En el servidor Ansible:

ssh-keygen -t rsa -b 4096

No poner passphrase si la práctica pide conexión sin contraseña.

## 8. Copiar clave a clientes

Desde el servidor:

ssh-copy-id sisadmin@192.168.100.1
ssh-copy-id sisadmin@192.168.100.2

## 9. Probar conexión SSH

ssh sisadmin@192.168.100.1

Si entra sin pedir contraseña, está correcto.

## 10. Probar Ansible

ansible all -i /etc/ansible/hosts/hosts.ini -m ping -u sisadmin

Resultado esperado:

SUCCESS

## Problemas comunes

### Pide contraseña

Revisar:

- ssh-copy-id realizado
- usuario correcto
- clave en ~/.ssh/authorized_keys
- permisos de .ssh

### Falla sudo

Revisar:

sisadmin ALL=(ALL) NOPASSWD:ALL

### Ansible no conecta

Revisar:

- IPs del inventario
- servicio SSH activo
- conectividad con ping
- usuario correcto
