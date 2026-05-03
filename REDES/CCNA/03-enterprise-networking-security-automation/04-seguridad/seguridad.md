# Seguridad básica de red

## Objetivo

Aplicar controles básicos para limitar tráfico, segmentar redes y reducir exposición.

## Principios

- Permitir solo el tráfico necesario.
- Separar redes por función.
- Evitar administración insegura.
- Proteger accesos remotos.
- Verificar configuraciones.

## Segmentación

La segmentación separa dispositivos o servicios en redes diferentes.

Ejemplos:

- VLAN de usuarios.
- VLAN de servidores.
- VLAN de administración.
- VLAN de voz.
- Red de invitados.

## ACL

Una ACL filtra tráfico según condiciones.

Puede filtrar por:

- IP origen.
- IP destino.
- Protocolo.
- Puerto.
- Dirección del tráfico.

## Buenas prácticas

- Usar SSH en lugar de Telnet.
- Proteger líneas VTY.
- Usar contraseñas cifradas.
- Deshabilitar servicios innecesarios.
- Limitar acceso a la gestión.
- Documentar cambios.
- Verificar con comandos antes y después.

## Comandos base de protección

```bash
service password-encryption
enable secret class
no ip domain-lookup
banner motd #Acceso autorizado solamente#
```

## SSH básico

```bash
conf t
hostname S1
ip domain-name ccna.local
username admin privilege 15 secret cisco123
crypto key generate rsa
ip ssh version 2

line vty 0 15
 login local
 transport input ssh
end
wr
```

## Error común

Abrir servicios de administración a toda la red sin filtrar origen.
