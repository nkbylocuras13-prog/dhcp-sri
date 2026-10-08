\# 1. Configuración del Servidor y Red



\## Configuración de Interfaces de Red

Verificación de las interfaces en el servidor DHCP (`dhcp`):



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

&#x20;      valid\_lft 86171sec preferred\_lft 86171sec

&#x20;   inet6 fd00::a00:27ff:fe8d:c04d/64 scope global dynamic mngtpmaddr 

&#x20;      valid\_lft 86170sec preferred\_lft 14170sec

&#x20;   inet6 fe80::a00:27ff:fe8d:c04d/64 scope link 

&#x20;      valid\_lft forever preferred\_lft forever

3: eth1: <BROADCAST,MULTICAST,UP,LOWER\_UP> mtu 1500 qdisc fq\_codel state UP group default qlen 1000

&#x20;   link/ether 08:00:27:a8:b4:d4 brd ff:ff:ff:ff:ff:ff

&#x20;   altname enp0s8

&#x20;   inet 192.168.68.59/22 brd 192.168.71.255 scope global dynamic eth1

&#x20;      valid\_lft 6979sec preferred\_lft 6979sec

&#x20;   inet6 fe80::a00:27ff:fea8:b4d4/64 scope link 

&#x20;      valid\_lft forever preferred\_lft forever

4: eth2: <BROADCAST,MULTICAST,UP,LOWER\_UP> mtu 1500 qdisc fq\_codel state UP group default qlen 1000

&#x20;   link/ether 08:00:27:5e:63:53 brd ff:ff:ff:ff:ff:ff

&#x20;   altname enp0s9

&#x20;   inet 192.168.57.10/24 brd 192.168.57.255 scope global eth2

&#x20;      valid\_lft forever preferred\_lft forever

&#x20;   inet6 fe80::a00:27ff:fe5e:6353/64 scope link 

&#x20;      valid\_lft forever preferred\_lft forever

