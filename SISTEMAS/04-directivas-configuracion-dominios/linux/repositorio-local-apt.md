# Repositorio local APT

## Qué es

Un repositorio local APT permite que los clientes Ubuntu descarguen paquetes desde un servidor interno en vez de usar directamente Internet.

En la práctica se puede montar con:

- apt-mirror
- Apache2
- Ansible para configurar clientes

## Para qué sirve

Ventajas:

- ahorrar ancho de banda
- controlar fuentes de paquetes
- acelerar instalaciones internas
- mantener un espejo local de repositorios

## 1. Preparar disco para repositorio

Conviene usar un disco grande.

El repositorio puede ocupar más de 150 GB dependiendo de los paquetes sincronizados.

Montaje recomendado:

/srv/apt-mirror

## 2. Montar disco en fstab

Crear partición y sistema de archivos.

Montar en:

/srv/apt-mirror

Añadir entrada en /etc/fstab para que sea persistente.

Después:

sudo mount -a

## 3. Instalar apt-mirror

sudo apt update
sudo apt install apt-mirror

## 4. Configurar mirror.list

Archivo habitual:

/etc/apt/mirror.list

Aquí se define:

- ruta base de descarga
- repositorios origen
- arquitectura
- distribución
- componentes

Ejemplo de elementos:

set base_path /srv/apt-mirror
deb http://archive.ubuntu.com/ubuntu noble main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu noble-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu noble-security main restricted universe multiverse

## 5. Descargar repositorio

sudo apt-mirror

Esto puede tardar bastante y consumir mucho espacio.

## 6. Publicar con Apache2

Instalar Apache:

sudo apt install apache2

Crear enlace simbólico al repositorio dentro del DocumentRoot de Apache.

Ejemplo:

sudo ln -s /srv/apt-mirror/mirror/archive.ubuntu.com/ubuntu /var/www/html/ubuntu

Ajustar permisos si hace falta.

## 7. Comprobar desde cliente

Desde navegador:

http://IP_SERVIDOR/ubuntu

Debe verse el árbol del repositorio.

## 8. Configurar cliente

Modificar sources.list para usar el repositorio local.

Ejemplo:

deb http://192.168.100.100/ubuntu noble main restricted universe multiverse
deb http://192.168.100.100/ubuntu noble-updates main restricted universe multiverse
deb http://192.168.100.100/ubuntu noble-security main restricted universe multiverse

Después:

sudo apt update

## 9. Automatizar con Ansible

Un playbook puede:

- hacer backup de sources.list
- escribir nuevas fuentes APT
- eliminar configuraciones que bloqueen el repo local
- ejecutar apt update
- instalar un paquete de prueba como VLC

## Problemas comunes

### El cliente sigue usando Internet

Revisar:

- sources.list
- archivos en /etc/apt/sources.list.d/
- prioridad de repositorios

### Apache no muestra el repo

Revisar:

- enlace simbólico
- permisos
- ruta real donde apt-mirror descargó los paquetes
- servicio apache2 activo

### apt update falla

Revisar:

- distribución correcta
- componentes correctos
- URL accesible desde cliente
- estructura del repositorio
