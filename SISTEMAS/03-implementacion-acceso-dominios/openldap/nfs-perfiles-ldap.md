# NFS para perfiles LDAP

## Objetivo

Guardar los perfiles o homes de usuarios LDAP en el servidor y montarlos desde el cliente.

Esto permite que los usuarios LDAP tengan su directorio personal centralizado.

## Servidor NFS

Instalar:

```bash
sudo apt install nfs-kernel-server
```

Crear carpeta:

```bash
sudo mkdir -p /perfilsldap
```

Asignar permisos de laboratorio:

```bash
sudo chown nobody:nogroup /perfilsldap
sudo chmod 777 /perfilsldap
```

En entorno real habría que afinar permisos, pero en laboratorio se usa para simplificar.

## Exportar carpeta

Editar:

```bash
sudo nano /etc/exports
```

Ejemplo:

```text
/perfilsldap 192.168.100.0/24(rw,sync,no_subtree_check,no_root_squash)
```

Aplicar:

```bash
sudo exportfs -ra
sudo systemctl restart nfs-kernel-server
```

Comprobar exports:

```bash
sudo exportfs -v
```

## Cliente NFS

Instalar:

```bash
sudo apt install nfs-common
```

Crear punto de montaje:

```bash
sudo mkdir -p /home/users
```

Montar:

```bash
sudo mount 192.168.100.100:/perfilsldap /home/users
```

Comprobar:

```bash
df -h
```

## Montaje persistente

Editar:

```bash
sudo nano /etc/fstab
```

Añadir:

```text
192.168.100.100:/perfilsldap /home/users nfs defaults 0 0
```

Probar:

```bash
sudo mount -a
```

## Crear prueba

Desde cliente:

```bash
echo "Jose Monfort" > /home/users/prova.txt
```

Desde servidor:

```bash
cat /perfilsldap/prova.txt
```

## Relación con LDAP

Los usuarios LDAP deben tener `homeDirectory` apuntando a una ruta que exista o que se pueda crear.

Ejemplo:

```text
homeDirectory: /home/users/jmonfort
```

Con NFS montado, ese home realmente se almacena en el servidor.

## Errores comunes

### Permission denied

Causas:

- permisos de carpeta insuficientes
- export mal definido
- falta `no_root_squash` en laboratorio
- cliente fuera de la red permitida

### No monta al reiniciar

Causas:

- línea de fstab incorrecta
- red no lista durante arranque
- servidor NFS apagado

### Home no se crea

Causas:

- PAM no tiene `pam_mkhomedir`
- ruta homeDirectory incorrecta
- permisos NFS incorrectos

## Resumen rápido

Servidor:

```bash
sudo apt install nfs-kernel-server
sudo mkdir -p /perfilsldap
sudo chown nobody:nogroup /perfilsldap
sudo chmod 777 /perfilsldap
sudo nano /etc/exports
sudo exportfs -ra
```

Cliente:

```bash
sudo apt install nfs-common
sudo mkdir -p /home/users
sudo mount IP_SERVIDOR:/perfilsldap /home/users
```
