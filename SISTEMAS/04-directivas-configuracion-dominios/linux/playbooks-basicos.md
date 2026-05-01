# Playbooks básicos de Ansible

## Qué es un playbook

Un playbook es un fichero YAML que define tareas que Ansible ejecutará en uno o varios equipos.

Sirve para automatizar configuraciones.

## Estructura básica

Un playbook suele tener:

- hosts
- become
- tasks

Ejemplo conceptual:

- hosts: clients12
  become: yes
  tasks:
    - name: Instalar paquete
      apt:
        name: cowsay
        state: present

## Revisar sintaxis

Antes de ejecutar:

ansible-playbook --syntax-check -i /etc/ansible/hosts/hosts.ini playbook.yml

## Ejecutar playbook

ansible-playbook -i /etc/ansible/hosts/hosts.ini playbook.yml -u sisadmin

## Playbook para instalar cowsay

Archivo:

/etc/ansible/playbooks/instala12.yml

Contenido orientativo:

- hosts: clients12
  become: yes
  tasks:
    - name: Instalar cowsay
      apt:
        name: cowsay
        state: present
        update_cache: yes

## Comprobación en cliente

En el cliente:

cowsay "Hola Rafa"

## Playbook para montar recurso NFS

Objetivo:

- crear punto de montaje
- montar recurso compartido
- hacerlo permanente en fstab

Tareas habituales:

- file para crear directorio
- mount para montar recurso
- lineinfile o mount con state mounted/present para fstab

## Playbook para fondo de pantalla en Linux

La práctica plantea configurar un fondo desde un recurso compartido.

La idea general:

1. Montar recurso NFS.
2. Asegurar permisos de acceso.
3. Copiar o referenciar la imagen.
4. Modificar configuración del entorno gráfico.
5. Bloquear cambios si el entorno lo permite.

## Buenas prácticas

- Revisar sintaxis antes de ejecutar.
- Ejecutar primero en un solo cliente.
- Usar nombres claros.
- Guardar playbooks en una carpeta ordenada.
- Documentar qué hace cada tarea.

## Comandos útiles

Probar ping:

ansible all -i /etc/ansible/hosts/hosts.ini -m ping -u sisadmin

Ejecutar playbook:

ansible-playbook -i /etc/ansible/hosts/hosts.ini /etc/ansible/playbooks/instala12.yml -u sisadmin

Revisar sintaxis:

ansible-playbook --syntax-check -i /etc/ansible/hosts/hosts.ini /etc/ansible/playbooks/instala12.yml
