# Errores comunes en VirtualBox

## Error: VirtualBox can't operate in VMX root mode

### Síntoma

Al iniciar una máquina virtual aparece un error parecido a:

VirtualBox can't operate in VMX root mode.
Please disable the KVM kernel extension, recompile your kernel and reboot.

## Causa

VirtualBox entra en conflicto con módulos KVM cargados en el host Linux.

No se puede usar VirtualBox y KVM sobre la misma virtualización hardware al mismo tiempo sin ajustar módulos.

## Solución temporal

### Intel

sudo modprobe -r kvm_intel

### AMD

sudo modprobe -r kvm_amd

Después, volver a abrir la máquina virtual.

## Solución más permanente

Crear una blacklist del módulo correspondiente.

Ejemplo para Intel:

echo "blacklist kvm_intel" | sudo tee /etc/modprobe.d/blacklist-kvm.conf

Ejemplo para AMD:

echo "blacklist kvm_amd" | sudo tee /etc/modprobe.d/blacklist-kvm.conf

Reiniciar el equipo.

## Error: Windows no detecta red en VirtualBox

### Síntoma

Windows arranca, pero no tiene conexión a Internet.

Puede ocurrir porque no reconoce el adaptador de red virtual.

## Solución

En VirtualBox:

Configuración -> Red -> Avanzado -> Tipo de adaptador

Seleccionar:

Intel PRO/1000 MT Desktop

Comprobar también:

- Adaptador habilitado
- Conectado a NAT
- Cable conectado activado

## Comandos de comprobación

En Windows:

- ipconfig
- ping 8.8.8.8

En Linux:

- ip a
- ping 8.8.8.8

## Recomendaciones

- Usar NAT para prácticas simples.
- Cambiar el tipo de adaptador si Windows no detecta red.
- Crear snapshot antes de modificar mucho el sistema.
- Documentar el error y la solución.
