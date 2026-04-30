# AppLocker

## Qué es AppLocker

AppLocker es una función de Windows que permite controlar qué aplicaciones pueden ejecutarse en los equipos.

Se puede usar para permitir o bloquear software según reglas.

## Para qué sirve

Ejemplos:

- bloquear una aplicación concreta
- impedir ejecutar programas fuera de rutas permitidas
- permitir solo software firmado
- controlar qué grupos pueden usar ciertos ejecutables

## Tipos de reglas

AppLocker puede crear reglas para:

- Ejecutables
- Instaladores de Windows
- Scripts
- Aplicaciones empaquetadas
- DLLs

## Condiciones de regla

Las reglas pueden basarse en:

### Editor

Se basa en la firma digital del software.

Ejemplo:

Permitir aplicaciones firmadas por Microsoft.

### Ruta de acceso

Se basa en una ruta concreta.

Ejemplo:

Bloquear C:\Program Files\App\programa.exe

### Hash de archivo

Se basa en el hash del archivo.

Es útil si el ejecutable no está firmado, pero cambia si el archivo se actualiza.

## 1. Crear GPO

Abrir:

gpmc.msc

Crear GPO.

Ejemplo:

LimitarSW

Vincularla al dominio o a una OU concreta.

## 2. Activar servicio Identidad de aplicación

AppLocker necesita que el servicio Identidad de aplicación esté activo.

Dentro de la GPO:

Configuración del equipo
Configuración de Windows
Configuración de seguridad
Servicios del sistema
Identidad de aplicación

Configurar como automático.

## 3. Configurar AppLocker

Ruta:

Configuración del equipo
Configuración de Windows
Configuración de seguridad
Directivas de control de aplicaciones
AppLocker

Activar las reglas necesarias.

## 4. Crear regla

Ejemplo:

Reglas de ejecutables
Crear nueva regla

Elegir:

- Acción: Denegar
- Usuario o grupo afectado
- Condición: Ruta de acceso
- Ruta del ejecutable bloqueado

## 5. Crear reglas predeterminadas

Cuando AppLocker lo pida, conviene crear las reglas predeterminadas.

Esto evita bloquear accidentalmente todo el sistema.

## 6. Aplicar en cliente

En cliente:

gpupdate /force

Ver GPO:

gpresult /r /scope computer

## 7. Comprobar

Entrar con un usuario afectado por la regla.

Intentar abrir la aplicación.

Resultado esperado:

- el usuario afectado no puede abrirla
- un usuario no afectado sí puede abrirla

## Problemas comunes

### La regla no se aplica

Revisar:

- servicio Identidad de aplicación
- GPO vinculada correctamente
- si afecta al equipo o al usuario
- grupo de seguridad correcto
- ruta real del ejecutable

### Se bloquea más de lo esperado

Revisar reglas predeterminadas.

Sin reglas predeterminadas, AppLocker puede ser demasiado restrictivo.

## Buenas prácticas

- Probar primero en modo auditoría si es posible.
- No aplicar directamente a todo el dominio.
- Crear reglas predeterminadas.
- Documentar qué aplicación se bloquea y a qué grupo afecta.
