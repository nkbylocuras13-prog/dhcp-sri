# 3. Configuración de Clientes, Leases y NAT

## Cliente Dinámico (`c1`)
Verificación de la dirección IP obtenida dinámicamente desde el servidor DHCP:

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
       valid_lft 84286sec preferred_lft 84286sec
    inet6 fd00::a00:27ff:fe8d:c04d/64 scope global dynamic mngtpmaddr 
       valid_lft 86169sec preferred_lft 14169sec
    inet6 fe80::a00:27ff:fe8d:c04d/64 scope link 
       valid_lft forever preferred_lft forever
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:db:55:61 brd ff:ff:ff:ff:ff:ff
    altname enp0s8
    inet 192.168.57.20/24 brd 192.168.57.255 scope global dynamic eth1
       valid_lft 85895sec preferred_lft 85895sec
    inet6 fe80::a00:27ff:fedb:5561/64 scope link 
       valid_lft forever preferred_lft forever

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
       valid_lft 84330sec preferred_lft 84330sec
    inet6 fd00::a00:27ff:fe8d:c04d/64 scope global dynamic mngtpmaddr 
       valid_lft 86343sec preferred_lft 14343sec
    inet6 fe80::a00:27ff:fe8d:c04d/64 scope link 
       valid_lft forever preferred_lft forever
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:ef:4b:7e brd ff:ff:ff:ff:ff:ff
    altname enp0s8
    inet 192.168.57.100/24 brd 192.168.57.255 scope global dynamic eth1
       valid_lft 6865sec preferred_lft 6865sec
    inet6 fe80::a00:27ff:feef:4b7e/64 scope link 
       valid_lft forever preferred_lft forever

$ cat /proc/sys/net/ipv4/ip_forward
0

$ sudo iptables -t nat -L -n -v
Chain PREROUTING (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    1    76 MASQUERADE  0    --  *      eth0    0.0.0.0/0            0.0.0.0/0

$ ping -c 4 8.8.8.8

PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=255 time=18.7 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=255 time=17.9 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=255 time=18.0 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=255 time=18.8 ms

--- 8.8.8.8 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3013ms
rtt min/avg/max/mdev = 17.887/18.336/18.760/0.388 ms
