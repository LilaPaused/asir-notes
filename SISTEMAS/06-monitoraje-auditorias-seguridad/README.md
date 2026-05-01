# Monitoraje y auditorias de seguridad

Este bloque recoge apuntes sobre monitorización de sistemas operativos y auditorías de seguridad.

El objetivo es saber supervisar el rendimiento de un sistema, detectar cuellos de botella, recopilar datos, generar informes y auditar acciones relevantes sobre usuarios, procesos, objetos y ficheros.

## Contenido

### Windows

- [Monitor de confiabilidad](./windows/monitor-confiabilidad.md)
- [Administrador de tareas](./windows/administrador-tareas.md)
- [Monitor de recursos](./windows/monitor-recursos.md)
- [Monitor de rendimiento](./windows/monitor-rendimiento.md)
- [Recopiladores de datos](./windows/recopiladores-datos.md)
- [Alertas de rendimiento](./windows/alertas-rendimiento.md)

### Linux

- [Comandos básicos de monitorización](./linux/comandos-monitorizacion.md)
- [Procesos con top y ps](./linux/top-ps-procesos.md)
- [CPU con mpstat](./linux/mpstat-cpu.md)
- [Memoria con vmstat y free](./linux/vmstat-free-memoria.md)
- [Disco con df e iostat](./linux/df-iostat-discos.md)

### Auditorías

- [Auditorías en Windows](./auditories/auditorias-windows.md)
- [Auditoría de acceso a objetos](./auditories/auditoria-acceso-objetos.md)
- [Visor de eventos](./auditories/visor-eventos.md)
- [Auditd en Linux](./auditories/auditd-linux.md)
- [Reglas persistentes con auditd](./auditories/auditd-reglas-persistentes.md)
- [Informes con ausearch y aureport](./auditories/ausearch-aureport.md)

### Exámenes

- [PF6 - Repaso](./examenes/pf6-repaso.md)

## Ideas clave

Monitorizar no es solo mirar si algo funciona. Es observar métricas como CPU, memoria, disco, red, procesos y eventos para entender el estado real de un sistema.

Auditar consiste en registrar acciones importantes para poder responder preguntas como:

- quién intentó acceder
- cuándo ocurrió
- qué objeto fue afectado
- si la acción fue correcta o fallida
- qué usuario o proceso la provocó

En Windows se trabaja mucho con el Visor de eventos, GPOs, directivas de auditoría y auditoría sobre objetos NTFS. En Linux se trabaja con herramientas como `auditd`, `auditctl`, `ausearch` y `aureport`.
