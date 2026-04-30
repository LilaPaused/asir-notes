# PF2 - Repaso

## Bloque CMD

Situarse en una ruta:

- `cd C:\arbolito\Docs`

Mostrar árbol desde ruta relativa:

- `tree .. /F`

Mover imágenes y textos en máximo dos comandos:

- `move C:\arbolito\*.jpg C:\arbolito\Pictures`
- `move C:\arbolito\*.txt C:\arbolito\Docs`

Crear archivo sin editor:

- `echo Jose Monfort > mjose12.txt`

Abrir editor:

- `notepad telefono.txt`

Añadir contenido:

- `type telefono.txt >> mjose12.txt`

Borrar archivo:

- `del telefono.txt`

## Disco backup en Windows

Crear disco en VirtualBox.

En Windows:

1. Administración de discos.
2. Inicializar GPT.
3. Nuevo volumen simple.
4. Letra B.
5. NTFS.
6. Etiqueta backup.

## Backup con robocopy

Crear directorio:

- `mkdir B:\arbolito2`

Copiar:

- `robocopy C:\arbolito B:\arbolito2 /MIR`

Ver recursivo:

- `dir B:\arbolito2 /S`

## Enlace simbólico

- `mklink C:\Users\alumne\Desktop\puente.jpg C:\arbolito\Pictures\puente.jpg`

## Red Windows

Configurar IP estática por comandos o entorno gráfico.

Permitir ping creando reglas ICMP en firewall.

## DNS Windows

Pasos:

1. Servidor con IP estática.
2. DNS primario del servidor: `127.0.0.1`.
3. Instalar rol DNS.
4. Crear zona directa.
5. Crear zona inversa.
6. Crear registros A.
7. Crear PTR automático.
8. Cliente usa IP del servidor como DNS.
9. Probar con `nslookup` y `ping`.

## Usuarios Linux

Crear usuario:

- `sudo useradd -m -c "Pepito Perez" pepito`
- `sudo passwd pepito`

Crear grupo:

- `sudo groupadd -g 2000 grupito`

Añadir a grupo:

- `sudo usermod -aG grupito pepito`

Comprobar:

- `id pepito`
- `cat /etc/group`
