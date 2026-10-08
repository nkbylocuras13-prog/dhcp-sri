# Práctica: Configuración de Servidor DHCP

Repositorio correspondiente a la Práctica de Servidor DHCP.

#Descripción del Proyecto
El objetivo de esta práctica es desplegar y configurar un servidor DHCP (`isc-dhcp-server`) conectado a una red privada interna y a una red pública, sirviendo direcciones IP dinámicas y estáticas a los clientes de la red, y configurando enrutamiento y NAT para proporcionarles acceso a Internet.

#Topología de Red
- **Servidor DHCP (`srv`)**:
  - Interfaz pública: Adaptador puente / Red pública.
  - Interfaz interna: IP `192.168.57.10/24` (Red `intnet`).
- **Cliente Dinámico (`c1`)**:
  - Obtiene IP dinámicamente en el rango `192.168.57.20 - 192.168.57.50`.
- **Cliente Estático (`printer`)**:
  - Obtiene IP fija `192.168.57.100` basada en su dirección MAC.

## 📁 Estructura del Repositorio
```text
.
├── conf/               # Archivos de configuración (dhcpd.conf, Vagrantfile, etc.)
├── doc/                # Documentación detallada y registros de la práctica
│   ├── 01-server-setup.md
│   ├── 02-dhcp-config.md
│   ├── 03-clients.md
│   └── leases.txt
├── .gitignore
└── README.md
├── Vagrantfile
