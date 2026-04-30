# GPO - Instalación de software

## Objetivo

Instalar software automáticamente en clientes del dominio usando una GPO.

En la práctica se usa un instalador MSI, como Notepad++.

## Requisito importante

La instalación por GPO funciona correctamente con paquetes MSI.

No se debe seleccionar el instalador desde una ruta local del servidor.

Debe usarse una ruta UNC accesible por los clientes.

Correcto:

\\SERVIDOR\Compartit12\notepadpp.msi

Incorrecto:

C:\Compartit12\notepadpp.msi

## 1. Preparar punto de distribución

Crear una carpeta compartida.

Ejemplo:

C:\Compartit12

Copiar dentro el instalador:

notepadpp-v8.6.4.msi

Compartir la carpeta con permisos suficientes para que los clientes puedan leer el MSI.

## 2. Crear la GPO

Abrir:

gpmc.msc

Crear una GPO vinculada a la OU que debe recibir el software.

Ejemplo:

instala12 vinculada a la OU segunda

## 3. Añadir paquete

Editar la GPO:

Configuración de usuario
Configuración de software
Instalación de software
Nuevo
Paquete

Seleccionar el MSI usando la ruta UNC.

Ejemplo:

\\VM_WINPDC4\Compartit12\notepadpp-v8.6.4.msi

## 4. Elegir modo

Modos habituales:

### Asignado

El programa se instala automáticamente.

Puede instalarse al iniciar sesión o al arrancar, dependiendo de si se aplica a usuario o equipo.

### Publicado

El programa queda disponible para instalar desde el Panel de control.

No se instala directamente.

## 5. Comprobar aplicación

En el cliente:

gpupdate /force

Cerrar sesión o reiniciar si lo pide.

Después iniciar sesión con un usuario de la OU afectada.

Comprobar en:

- menú inicio
- aplicaciones instaladas
- panel de control

## Caso de prueba

Si la GPO está vinculada a la OU segunda:

- usu1 en OU primera: no debería recibir la instalación
- usu2 en OU segunda: sí debería recibir la instalación

## Desinstalar software por GPO

En la GPO:

Instalación de software
Seleccionar paquete
Quitar

Opciones:

- desinstalar inmediatamente de usuarios/equipos
- permitir que los usuarios sigan usando el software pero impedir nuevas instalaciones

## Problemas comunes

### No se instala

Revisar:

- ruta UNC
- permisos de lectura en carpeta compartida
- que el MSI sea válido
- que la GPO esté vinculada a la OU correcta
- si afecta a usuario o equipo
- si hace falta cerrar sesión o reiniciar

### El usuario no tiene acceso al MSI

Probar desde el cliente:

\\SERVIDOR\Compartit12

Si no puede acceder, la GPO tampoco podrá instalar el paquete.

## Buenas prácticas

- Crear una carpeta solo para paquetes MSI.
- Usar nombres claros.
- No usar rutas locales.
- Probar con una OU pequeña.
- Documentar si el paquete es asignado o publicado.
