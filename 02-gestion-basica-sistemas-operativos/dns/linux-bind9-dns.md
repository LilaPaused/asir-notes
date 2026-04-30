# DNS en Ubuntu Server con Bind9

## Objetivo

Configurar Ubuntu Server como servidor DNS usando Bind9.

## Instalar paquetes

    sudo apt update
    sudo apt install bind9 bind9-utils

## Configurar IP y DNS del servidor

En netplan, el servidor puede apuntarse a sí mismo:

    nameservers:
      addresses: [127.0.0.1]

Aplicar:

    sudo netplan apply

## resolv.conf persistente

En Ubuntu, resolv.conf puede estar gestionado por systemd-resolved.

Revisar:

    ls -l /etc/resolv.conf

Puede ser necesario ajustar systemd-resolved para que use el DNS deseado.

Reiniciar servicio:

    sudo systemctl restart systemd-resolved

## Archivo de zonas

Editar:

    sudo nano /etc/bind/named.conf.local

Ejemplo:

    zone "userver12.sis" {
        type master;
        file "/etc/bind/directa.userver12.sis.db";
    };

    zone "12.168.192.in-addr.arpa" {
        type master;
        file "/etc/bind/inversa.userver12.sis.db";
    };

Comprobar sintaxis:

    sudo named-checkconf

## Crear archivos de zona

Usar plantilla:

    sudo cp /etc/bind/db.local /etc/bind/directa.userver12.sis.db
    sudo cp /etc/bind/db.local /etc/bind/inversa.userver12.sis.db

## Zona directa

Ejemplo básico:

    $TTL 604800
    @ IN SOA userver12.sis. admin.userver12.sis. (
        2
        604800
        86400
        2419200
        604800 )
    @ IN NS userver12.sis.
    userver12 IN A 192.168.12.2
    servidor IN CNAME userver12

Comprobar:

    sudo named-checkzone userver12.sis /etc/bind/directa.userver12.sis.db

## Zona inversa

Ejemplo:

    $TTL 604800
    @ IN SOA userver12.sis. admin.userver12.sis. (
        2
        604800
        86400
        2419200
        604800 )
    @ IN NS userver12.sis.
    2 IN PTR userver12.sis.

Comprobar:

    sudo named-checkzone 12.168.192.in-addr.arpa /etc/bind/inversa.userver12.sis.db

## Reiniciar Bind9

    sudo systemctl restart bind9
    sudo systemctl status bind9

## Probar

    nslookup userver12.sis
    nslookup servidor.userver12.sis
    dig userver12.sis
    dig -x 192.168.12.2

## Añadir cliente

Zona directa:

    uclient12 IN A 192.168.12.200

Zona inversa:

    200 IN PTR uclient12.userver12.sis.

Después:

    sudo named-checkconf
    sudo systemctl restart bind9

## Idea clave

Bind9 funciona por archivos. Si un carácter está mal, el servicio puede fallar. Por eso hay que usar named-checkconf y named-checkzone antes de reiniciar.
