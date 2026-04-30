# Windows Update

## Qué es

Windows Update es el sistema de Microsoft para descargar e instalar actualizaciones del sistema operativo.

Sirve para instalar:

- parches de seguridad
- actualizaciones de calidad
- actualizaciones de drivers
- nuevas versiones de componentes del sistema

## Windows Update en entorno gráfico

Ruta habitual:

Configuración -> Windows Update

Desde ahí se puede:

- buscar actualizaciones
- pausar temporalmente actualizaciones
- ver historial
- configurar horas activas
- reiniciar cuando sea necesario

## Limitación importante

En Windows cliente no siempre se puede elegir con precisión cuándo descargar o instalar actualizaciones.

Normalmente Windows permite pausar o retrasar, pero no da control total desde la interfaz básica.

## Servicio de Windows Update

El servicio principal se llama:

wuauserv

## Deshabilitar Windows Update

No es recomendable en producción, pero en práctica se puede probar.

Desde CMD como administrador:

sc config wuauserv start= disabled

Reiniciar y comprobar estado:

sc query wuauserv

## Volver a habilitar Windows Update

sc config wuauserv start= demand

O automático:

sc config wuauserv start= auto

## Windows Update desde PowerShell

En Windows Server sin entorno gráfico puede ser útil usar PowerShell.

Una opción habitual es instalar el módulo:

Install-Module PSWindowsUpdate

Importar módulo:

Import-Module PSWindowsUpdate

Buscar actualizaciones:

Get-WindowsUpdate

Instalar todas:

Install-WindowsUpdate -AcceptAll -AutoReboot

Instalar una KB concreta:

Install-WindowsUpdate -KBArticleID KBXXXXXXX -AcceptAll -AutoReboot

## Buenas prácticas

- No deshabilitar Windows Update permanentemente salvo caso muy justificado.
- En servidores, controlar ventanas de mantenimiento.
- Revisar actualizaciones antes de instalarlas.
- Crear snapshots antes de actualizaciones importantes en entornos de laboratorio.

## Resumen rápido

CMD:

- sc query wuauserv
- sc config wuauserv start= disabled
- sc config wuauserv start= demand

PowerShell:

- Install-Module PSWindowsUpdate
- Get-WindowsUpdate
- Install-WindowsUpdate -AcceptAll -AutoReboot
