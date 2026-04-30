# GPO - Fondo de pantalla obligatorio

## Objetivo

Aplicar un fondo de pantalla obligatorio a los usuarios del dominio y bloquear que puedan cambiarlo.

Este caso se trabaja creando una carpeta compartida accesible para los clientes, copiando la imagen dentro y configurando una GPO.

## 1. Crear carpeta compartida

En el servidor, crear una carpeta en la raíz del disco.

Ejemplo:

C:\Compartit12

Compartirla con lectura y escritura para los usuarios del dominio, según lo que pida la práctica.

Ruta UNC esperada:

\\VM_WINPDC4\Compartit12

O con el nombre real del servidor:

\\NOMBRE_SERVIDOR\Compartit12

## 2. Copiar la imagen

Copiar dentro la imagen que se usará como wallpaper.

Ejemplo:

C:\Compartit12\mywallpaper.jpg

Desde los clientes debe usarse ruta UNC, no ruta local.

Correcto:

\\VM_WINPDC4\Compartit12\mywallpaper.jpg

Incorrecto:

C:\Compartit12\mywallpaper.jpg

## 3. Crear la GPO

Abrir:

gpmc.msc

Crear una nueva GPO vinculada al dominio.

Ejemplo:

fons12

## 4. Configurar fondo de escritorio

Editar la GPO:

Configuración de usuario
Plantillas administrativas
Escritorio
Escritorio activo
Tapiz del escritorio

Habilitar la directiva e indicar la ruta UNC del wallpaper.

Ejemplo:

\\VM_WINPDC4\Compartit12\mywallpaper.jpg

## 5. Bloquear el cambio de fondo

Editar:

Configuración de usuario
Plantillas administrativas
Panel de control
Personalización
Impedir cambiar el fondo de escritorio

Estado:

Habilitada

## 6. Aplicar en cliente

En el cliente:

gpupdate /force

Cerrar sesión y volver a entrar si hace falta.

## 7. Comprobar

Entrar con un usuario del dominio.

Debe verse:

- fondo aplicado
- mensaje indicando que algunas opciones están administradas por la organización
- imposibilidad de cambiar el fondo desde Configuración

## Problemas comunes

### El fondo no aparece

Comprobar:

- que la ruta sea UNC
- que el cliente puede acceder a la carpeta compartida
- que el archivo existe
- que la GPO está vinculada donde toca
- que el usuario está dentro del ámbito de la GPO

### La GPO no aparece en gpresult

Si es configuración de usuario:

gpresult /r

Si es configuración de equipo:

gpresult /r /scope computer

### El usuario puede cambiar el fondo

Revisar la directiva de personalización:

Impedir cambiar el fondo de escritorio

Debe estar habilitada.
