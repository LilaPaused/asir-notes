# Usuarios, grupos y políticas básicas

## Usuarios en Linux

Crear usuario con `useradd`:

- `sudo useradd -m -c "Pepito Perez" pepito`

Asignar contraseña:

- `sudo passwd pepito`

Ver usuarios:

- `cat /etc/passwd`

Las contraseñas cifradas se guardan en:

- `/etc/shadow`

## Grupos en Linux

Crear grupo con GID concreto:

- `sudo groupadd -g 2000 grupito`

Añadir usuario a grupo secundario:

- `sudo usermod -aG grupito pepito`

Comprobar:

- `cat /etc/group`
- `id pepito`

## Política de contraseñas en Ubuntu

Archivo habitual con pwquality:

- `/etc/security/pwquality.conf`

Parámetros importantes:

- `minlen`
- `minclass`
- `dcredit`
- `ucredit`
- `lcredit`
- `ocredit`

Ejemplo de requisitos:

- longitud mínima 8
- mínimo 3 clases de caracteres
- créditos para caracteres no alfanuméricos

## Bloqueo de cuenta en Windows

Política:

- Umbral de bloqueo de cuenta

Ruta típica:

- `gpedit.msc`
- Configuración del equipo
- Configuración de Windows
- Configuración de seguridad
- Directivas de cuenta
- Directiva de bloqueo de cuenta

## Desbloquear usuario en Windows

Desde administración de equipos:

- Usuarios y grupos locales
- Usuarios
- Propiedades del usuario
- desbloquear cuenta

## Intentos de login en Ubuntu

Puede configurarse con PAM/faillock o según práctica mediante parámetros del sistema.

Comandos útiles:

- `faillock --user usuario`
- `faillock --user usuario --reset`
