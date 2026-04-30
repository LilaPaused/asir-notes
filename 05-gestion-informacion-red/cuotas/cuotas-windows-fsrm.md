# Cuotas en Windows Server con FSRM

## Qué son las cuotas

Las cuotas limitan cuánto espacio puede usar una carpeta o usuario.

En Windows Server se gestionan con el Administrador de recursos del servidor de archivos.

También se conoce como FSRM.

## Instalar característica

Desde Administrador del servidor:

Agregar roles y características -> Servicios de archivos y almacenamiento -> Administrador de recursos del servidor de archivos

## Tipos de cuota

### Cuota rígida

No permite superar el límite.

Ejemplo:

- límite 10 GB
- si se llega a 10 GB, no se puede escribir más

### Cuota flexible

Permite superar el límite, pero registra avisos o ejecuta acciones.

Sirve para monitorizar sin bloquear.

## Plantillas de cuota

Una plantilla permite reutilizar configuraciones.

Ejemplos:

- Recursos compartidos: 5 GB
- Homes de usuario: 10 GB
- Pruebas: 222 MB

## Umbrales

Se pueden definir avisos al llegar a un porcentaje.

Ejemplo:

- 90% -> registrar evento
- 95% -> enviar correo
- 100% -> bloquear escritura

## Crear una cuota

Pasos:

1. Abrir Administrador de recursos del servidor de archivos.
2. Ir a Administración de cuotas.
3. Crear plantilla si hace falta.
4. Crear cuota.
5. Seleccionar carpeta.
6. Elegir plantilla.
7. Aplicar.

## Aplicar cuotas a subcarpetas

Para carpetas Home puede interesar aplicar una plantilla automáticamente a subcarpetas existentes y nuevas.

Esto permite que cada usuario tenga su propio límite.

## Comprobar cuotas

Se puede probar creando archivos grandes.

Ejemplo en PowerShell:

    fsutil file createnew archivo3GB.bin 3221225472

Para crear 5 GB:

    fsutil file createnew archivo5GB.bin 5368709120

## Qué comprobar

- porcentaje usado
- límite aplicado
- si se bloquea al superar límite
- si aparece evento en el Visor de eventos
- si el usuario cliente recibe error

## Caso de examen

Una cuota de 222 MB sobre una carpeta compartida puede mostrar:

- porcentaje usado tras copiar file1
- aviso al superar el 90%
- bloqueo cuando se intenta copiar un archivo que supera el límite

## Resumen

FSRM permite controlar uso de disco por carpeta. Es especialmente útil en carpetas compartidas, homes de usuarios y entornos multiusuario.
