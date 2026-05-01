# Reparar GRUB manualmente

## Cuándo usar este procedimiento

Se usa cuando GRUB ha sido sobrescrito o dañado.

Caso típico:

Instalo Linux -> Instalo Windows después -> Windows pisa GRUB

## Necesitas

- una ISO Live de Linux
- acceso a terminal
- saber en qué partición está instalado Linux

## 1. Arrancar desde Live ISO

Iniciar la máquina desde una ISO Live.

Abrir terminal.

## 2. Localizar particiones

sudo fdisk -l

Buscar la partición donde está instalado Linux.

Ejemplo:

- /dev/sda1 -> Linux
- /dev/sda2 -> Windows

## 3. Montar el sistema Linux

Ejemplo si Linux está en /dev/sda1:

sudo mount /dev/sda1 /mnt

## 4. Montar directorios necesarios

sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys

Si existe partición EFI, también puede ser necesario montarla:

sudo mount /dev/sdaX /mnt/boot/efi

Sustituir /dev/sdaX por la partición EFI real.

## 5. Entrar con chroot

sudo chroot /mnt

Ahora la terminal trabaja como si estuviera dentro del Linux instalado.

## 6. Reinstalar GRUB

En BIOS/MBR:

grub-install /dev/sda

En UEFI puede variar, pero un ejemplo común sería:

grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=GRUB

## 7. Regenerar configuración

En Debian/Ubuntu:

update-grub

Alternativa:

grub-mkconfig -o /boot/grub/grub.cfg

## 8. Salir y desmontar

exit
sudo umount -R /mnt
reboot

## 9. Comprobar

Al reiniciar debería aparecer GRUB con las entradas de Linux y Windows.

## Problemas comunes

### Windows no aparece

Activar os-prober en:

/etc/default/grub

Añadir o modificar:

GRUB_DISABLE_OS_PROBER=false

Luego:

sudo update-grub

### Error al montar

Revisar partición correcta:

sudo fdisk -l
lsblk

## Resumen rápido

sudo fdisk -l
sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
grub-install /dev/sda
update-grub
exit
sudo umount -R /mnt
reboot
