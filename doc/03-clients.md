\# 3. Configuración de Clientes, Leases y NAT



\## Cliente Dinámico (`c1`)

Verificación de la dirección IP obtenida dinámicamente desde el servidor DHCP:



```bash

$ ip a



1: lo: <LOOPBACK,UP,LOWER\_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000

&#x20;   link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00

&#x20;   inet 127.0.0.1/8 scope host lo

&#x20;      valid\_lft forever preferred\_lft forever

&#x20;   inet6 ::1/128 scope host noprefixroute 

&#x20;      valid\_lft forever preferred\_lft forever

2: eth0: <BROADCAST,MULTICAST,UP,LOWER\_UP> mtu 1500 qdisc fq\_codel state UP group default qlen 1000

&#x20;   link/ether 08:00:27:8d:c0:4d brd ff:ff:ff:ff:ff:ff

&#x20;   altname enp0s3

&#x20;   inet 10.0.2.15/24 brd 10.0.2.255 scope global dynamic eth0

&#x20;      valid\_lft 84286sec preferred\_lft 84286sec

&#x20;   inet6 fd00::a00:27ff:fe8d:c04d/64 scope global dynamic mngtpmaddr 

&#x20;      valid\_lft 86169sec preferred\_lft 14169sec

&#x20;   inet6 fe80::a00:27ff:fe8d:c04d/64 scope link 

&#x20;      valid\_lft forever preferred\_lft forever

3: eth1: <BROADCAST,MULTICAST,UP,LOWER\_UP> mtu 1500 qdisc fq\_codel state UP group default qlen 1000

&#x20;   link/ether 08:00:27:db:55:61 brd ff:ff:ff:ff:ff:ff

&#x20;   altname enp0s8

&#x20;   inet 192.168.57.20/24 brd 192.168.57.255 scope global dynamic eth1

&#x20;      valid\_lft 85895sec preferred\_lft 85895sec

&#x20;   inet6 fe80::a00:27ff:fedb:5561/64 scope link 

&#x20;      valid\_lft forever preferred\_lft forever







\## Cliente Dinámico (`printer`)

Verificación de la dirección IP obtenida dinámicamente desde el servidor DHCP:





$ ip a



1: lo: <LOOPBACK,UP,LOWER\_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000

&#x20;   link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00

&#x20;   inet 127.0.0.1/8 scope host lo

&#x20;      valid\_lft forever preferred\_lft forever

&#x20;   inet6 ::1/128 scope host noprefixroute 

&#x20;      valid\_lft forever preferred\_lft forever

2: eth0: <BROADCAST,MULTICAST,UP,LOWER\_UP> mtu 1500 qdisc fq\_codel state UP group default qlen 1000

&#x20;   link/ether 08:00:27:8d:c0:4d brd ff:ff:ff:ff:ff:ff

&#x20;   altname enp0s3

&#x20;   inet 10.0.2.15/24 brd 10.0.2.255 scope global dynamic eth0

&#x20;      valid\_lft 84330sec preferred\_lft 84330sec

&#x20;   inet6 fd00::a00:27ff:fe8d:c04d/64 scope global dynamic mngtpmaddr 

&#x20;      valid\_lft 86343sec preferred\_lft 14343sec

&#x20;   inet6 fe80::a00:27ff:fe8d:c04d/64 scope link 

&#x20;      valid\_lft forever preferred\_lft forever

3: eth1: <BROADCAST,MULTICAST,UP,LOWER\_UP> mtu 1500 qdisc fq\_codel state UP group default qlen 1000

&#x20;   link/ether 08:00:27:ef:4b:7e brd ff:ff:ff:ff:ff:ff

&#x20;   altname enp0s8

&#x20;   inet 192.168.57.100/24 brd 192.168.57.255 scope global dynamic eth1

&#x20;      valid\_lft 6865sec preferred\_lft 6865sec

&#x20;   inet6 fe80::a00:27ff:feef:4b7e/64 scope link 

&#x20;      valid\_lft forever preferred\_lft forever



$ ping -c 4 8.8.8.8



1: lo: <LOOPBACK,UP,LOWER\_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000

&#x20;   link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00

&#x20;   inet 127.0.0.1/8 scope host lo

&#x20;      valid\_lft forever preferred\_lft forever

&#x20;   inet6 ::1/128 scope host noprefixroute 

&#x20;      valid\_lft forever preferred\_lft forever

2: eth0: <BROADCAST,MULTICAST,UP,LOWER\_UP> mtu 1500 qdisc fq\_codel state UP group default qlen 1000

&#x20;   link/ether 08:00:27:8d:c0:4d brd ff:ff:ff:ff:ff:ff

&#x20;   altname enp0s3

&#x20;   inet 10.0.2.15/24 brd 10.0.2.255 scope global dynamic eth0

&#x20;      valid\_lft 84330sec preferred\_lft 84330sec

&#x20;   inet6 fd00::a00:27ff:fe8d:c04d/64 scope global dynamic mngtpmaddr 

&#x20;      valid\_lft 86343sec preferred\_lft 14343sec

&#x20;   inet6 fe80::a00:27ff:fe8d:c04d/64 scope link 

&#x20;      valid\_lft forever preferred\_lft forever

3: eth1: <BROADCAST,MULTICAST,UP,LOWER\_UP> mtu 1500 qdisc fq\_codel state UP group default qlen 1000

&#x20;   link/ether 08:00:27:ef:4b:7e brd ff:ff:ff:ff:ff:ff

&#x20;   altname enp0s8

&#x20;   inet 192.168.57.100/24 brd 192.168.57.255 scope global dynamic eth1

&#x20;      valid\_lft 6865sec preferred\_lft 6865sec

&#x20;   inet6 fe80::a00:27ff:feef:4b7e/64 scope link 

&#x20;      valid\_lft forever preferred\_lft forever



vagrant@server:\~$ cat /proc/sys/net/ipv4/ip\_forward

0



$ ip r



\- \*\*`eth0` (`10.0.2.0/24`)\*\*: Red NAT de Vagrant para gestión SSH y salida a Internet.

\- \*\*`eth1` (`192.168.68.0/22`)\*\*: Interfaz pública en modo puente (\*bridge\*).

\- \*\*`eth2` (`192.168.57.0/24`)\*\*: Red interna (`intnet`) donde el servidor tiene la IP estática `192.168.57.10` y atiende las peticiones DHCP de los clientes.



