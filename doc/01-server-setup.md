\# 1. Configuración del Servidor y Red



\## Configuración de Interfaces de Red

Verificación de las interfaces en el servidor DHCP (`dhcp`):



```bash

$ ip a

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:8d:c0:4d brd ff:ff:ff:ff:ff:ff
    altname enp0s3
    inet 10.0.2.15/24 brd 10.0.2.255 scope global dynamic eth0
       valid_lft 86171sec preferred_lft 86171sec
    inet6 fd00::a00:27ff:fe8d:c04d/64 scope global dynamic mngtpmaddr 
       valid_lft 86170sec preferred_lft 14170sec
    inet6 fe80::a00:27ff:fe8d:c04d/64 scope link 
       valid_lft forever preferred_lft forever
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:a8:b4:d4 brd ff:ff:ff:ff:ff:ff
    altname enp0s8
    inet 192.168.68.59/22 brd 192.168.71.255 scope global dynamic eth1
       valid_lft 6979sec preferred_lft 6979sec
    inet6 fe80::a00:27ff:fea8:b4d4/64 scope link 
       valid_lft forever preferred_lft forever
4: eth2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:5e:63:53 brd ff:ff:ff:ff:ff:ff
    altname enp0s9
    inet 192.168.57.10/24 brd 192.168.57.255 scope global eth2
       valid_lft forever preferred_lft forever
    inet6 fe80::a00:27ff:fe5e:6353/64 scope link 
       valid_lft forever preferred_lft forever
