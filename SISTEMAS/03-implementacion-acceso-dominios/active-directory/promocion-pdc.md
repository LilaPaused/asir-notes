# Promocionar un servidor a controlador de dominio

## Qué significa promocionar un servidor

Promocionar un servidor significa convertirlo en controlador de dominio.

En Windows Server, esto se hace instalando el rol de Active Directory Domain Services y completando después el asistente de promoción.

Un servidor promocionado pasa a gestionar objetos del dominio como:

- usuarios
- grupos
- equipos
- unidades organizativas
- políticas
- autenticación
- servicios de directorio

## Roles necesarios

Para un dominio básico necesitas:

- Active Directory Domain Services (AD DS)
- DNS Server

DNS es obligatorio en la práctica porque los clientes localizan el dominio y los controladores de dominio mediante resolución de nombres.

## Preparación recomendada

Antes de promocionar:

1. IP estática configurada.
2. DNS primario apuntando al propio servidor.
3. Hostname correcto.
4. Conectividad comprobada.
5. Snapshot de la máquina virtual.

## Eliminar DNS anterior

Si ya había una práctica DNS previa, conviene quitar el rol DNS o borrar zonas antiguas para evitar configuraciones residuales.

Ruta gráfica:

- Administrador del servidor
- Administrar
- Quitar roles y características
- Desmarcar Servidor DNS

## Instalar AD DS y DNS

Ruta gráfica:

- Administrador del servidor
- Administrar
- Agregar roles y características
- Instalación basada en características o roles
- Seleccionar servidor
- Marcar Servicios de dominio de Active Directory
- Marcar Servidor DNS
- Instalar

## Promocionar el servidor

Después de instalar el rol:

- Abrir notificación del Administrador del servidor.
- Seleccionar Promover este servidor a controlador de dominio.

Para crear el primer dominio:

- Agregar un nuevo bosque.
- Nombre de dominio raíz: ejemplo `midom12.et` o `pf3112.dom`.

## Opciones importantes

En el asistente:

- Servidor DNS: activado.
- Catálogo Global: activado si es el primer DC del bosque.
- RODC: desactivado si es un DC normal.
- Contraseña DSRM: contraseña de recuperación de servicios de directorio.

## Advertencia DNS

Es normal que aparezca una advertencia sobre delegación DNS cuando se crea un dominio nuevo en laboratorio.

No suele impedir la promoción.

## Comprobaciones después del reinicio

### Login

Después de reiniciar, el login ya debería mostrar el dominio:

- `MIDOM12\Administrador`
- `PF3112\Administrador`

### Administrador del servidor

Deben aparecer paneles como:

- AD DS
- DNS

Ambos deberían estar en verde si no hay errores críticos.

### DNS

En Herramientas > DNS debe existir una zona directa con el nombre del dominio.

Ejemplo:

- `midom12.et`
- `pf3112.dom`

También debería existir un registro A del servidor.

### Cliente

Desde el cliente Windows:

- DNS primario apuntando al servidor.
- ping al servidor por nombre.
- nslookup al FQDN del servidor.

Comandos útiles:

```powershell
ipconfig /all
nslookup wserver12.midom12.et
ping wserver12.midom12.et
```

## Errores comunes

### El cliente no resuelve el dominio

Causa probable:

- DNS del cliente apunta a NAT, router o Internet en vez de al DC.

Solución:

- Poner como DNS primario la IP del controlador de dominio.

### El panel DNS muestra zonas antiguas

Causa probable:

- Quedaron zonas de una práctica anterior.

Solución:

- Borrar zonas antiguas que no pertenezcan al dominio actual.

### No aparece el dominio al iniciar sesión

Causa probable:

- Promoción incompleta o inicio con usuario local.

Solución:

- Verificar que AD DS está instalado y que el servidor se reinició correctamente.
