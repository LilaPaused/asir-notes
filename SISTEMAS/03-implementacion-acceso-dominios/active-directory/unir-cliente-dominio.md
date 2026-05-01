# Unir un cliente Windows al dominio

## Requisitos previos

Antes de unir un cliente Windows al dominio:

1. El cliente debe tener IP correcta.
2. El cliente debe hacer ping al servidor.
3. El DNS del cliente debe apuntar al controlador de dominio.
4. El dominio debe resolver por DNS.
5. Debe existir conectividad con el DC.

## Configuración IP básica

Ejemplo:

- Cliente: `192.168.12.100/24`
- Servidor DC: `192.168.12.1/24`
- DNS del cliente: `192.168.12.1`

## Comprobaciones antes de unir

```cmd
ipconfig /all
ping 192.168.12.1
ping wserver12.midom12.et
nslookup wserver12.midom12.et
```

Si falla DNS, no sigas. Primero arregla DNS.

## Unir desde entorno gráfico

Ruta:

- Este equipo
- Propiedades
- Cambiar configuración
- Cambiar
- Miembro de dominio
- Escribir dominio

Ejemplo:

```text
midom12.et
pf3112.dom
```

Después pedirá credenciales con permiso para unir equipos al dominio.

## Credenciales

Normalmente se usa:

- Administrador del dominio
- usuario autorizado para unir ese equipo

En algunos ejercicios se crea previamente una cuenta de equipo y se indica qué usuario puede vincularla.

## Reinicio

Después de unir el equipo correctamente, Windows pedirá reiniciar.

Es normal.

## Iniciar sesión en dominio

Formato:

```text
DOMINIO\usuario
```

Ejemplo:

```text
MIDOM12\jmonfort
PF3112\ucopia
```

También puede funcionar con UPN:

```text
jmonfort@pf3112.dom
```

## Error típico: el usuario no puede unir el equipo

Si un usuario no autorizado intenta unir un equipo al dominio, Windows puede mostrar un error de permisos.

Causas:

- el usuario no tiene permisos
- la cuenta de equipo estaba precreada para otro usuario
- el equipo ya existe en AD

## Caso de cuenta de equipo precreada

Se puede crear un equipo en AD:

- nombre: `myclient`
- usuario autorizado para vincularlo: `jmonfort`

En ese caso, `ucopia` no podrá unir el equipo si no tiene permisos.

## Comprobación final

En el servidor:

- abrir Usuarios y equipos de Active Directory
- buscar el equipo cliente
- comprobar que aparece en la OU correcta

En el cliente:

```cmd
whoami
hostname
```

## Resumen rápido

- Sin DNS correcto, no hay unión al dominio.
- El cliente debe apuntar al DC como DNS.
- Se necesita usuario con permisos.
- Tras unir, reiniciar.
- Validar con inicio de sesión de dominio.
