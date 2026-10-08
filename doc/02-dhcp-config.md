\# 2. Configuración del Servicio DHCP



\## Verificación de Sintaxis

Comprobación de sintaxis en `/etc/dhcp/dhcpd.conf`:



```bash

$ sudo dhcpd -t



Internet Systems Consortium DHCP Server 4.4.3-P1

Copyright 2004-2022 Internet Systems Consortium.

All rights reserved.

For info, please visit \[https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Config file: /etc/dhcp/dhcpd.conf

Database file: /var/lib/dhcp/dhcpd.leases

PID file: /var/run/dhcpd.pid



isc-dhcp-server.service - LSB: DHCP server
isc-dhcp-server.service - LSB: DHCP server
     Loaded: loaded (/etc/init.d/isc-dhcp-server; generated)
     Active: active (running) since Thu 2026-10-08 19:33:07 UTC; 2min 40s ago
       Docs: man:systemd-sysv-generator(8)
    Process: 1868 ExecStart=/etc/init.d/isc-dhcp-server start (code=exited, status=0/SUCCESS)
      Tasks: 1 (limit: 496)
     Memory: 4.4M
        CPU: 19ms
     CGroup: /system.slice/isc-dhcp-server.service
             └─1880 /usr/sbin/dhcpd -4 -q -cf /etc/dhcp/dhcpd.conf eth2


Oct 08 19:33:05 bookworm dhcpd\[1880]: Wrote 0 deleted host decls to leases file.

Oct 08 19:33:05 bookworm dhcpd\[1880]: Wrote 0 new dynamic host decls to leases file.

Oct 08 19:33:05 bookworm dhcpd\[1880]: Wrote 0 leases to leases file.

Oct 08 19:33:05 bookworm dhcpd\[1880]: Server starting service.

Oct 08 19:33:07 bookworm isc-dhcp-server\[1868]: Starting ISC DHCPv4 server: dhcpd.

Oct 08 19:33:07 bookworm systemd\[1]: Started isc-dhcp-server.service - LSB: DHCP server.

Oct 08 19:33:10 bookworm dhcpd\[1880]: DHCPDISCOVER from 08:00:27:db:55:61 via eth2

Oct 08 19:33:11 bookworm dhcpd\[1880]: DHCPOFFER on 192.168.57.20 to 08:00:27:db:55:61 (bookworm) via eth2

Oct 08 19:33:11 bookworm dhcpd\[1880]: DHCPREQUEST for 192.168.57.20 (192.168.57.10) from 08:00:27:db:55:61 (bookworm) via eth2

Oct 08 19:33:11 bookworm dhcpd\[1880]: DHCPACK on 192.168.57.20 to 08:00:27:db:55:61 (bookworm) via eth2



\## Puerto de Escucha Activo

Verificación del socket escuchando en el puerto UDP 67:



```bash

$ sudo ss -lun



State       Recv-Q Send-Q Local Address:Port               Peer Address:Port            Process

UNCONN      0      0          0.0.0.0:67                      0.0.0.0:\*                  

UNCONN      0      0        127.0.0.1:323                     0.0.0.0:\*                  

UNCONN      0      0          0.0.0.0:68                      0.0.0.0:\*                  

UNCONN      0      0          0.0.0.0:68                      0.0.0.0:\*                  

UNCONN      0      0            \[::1]:323                        \[::]:\*

