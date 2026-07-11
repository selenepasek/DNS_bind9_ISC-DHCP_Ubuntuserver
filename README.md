# DNS_bind9_ISC-DHCP_Ubuntuserver
Lab project to practice networking fundamentals: setting up a DNS and DHCP server on an Ubuntu Server VM, running on VMware ESXi infrastructure.

Objective

Build a server that resolves local domain names (DNS) and automatically assigns IPs to network clients (DHCP), simulating the basic infrastructure of a corporate network.

Technologies used

Ubuntu Server (VM on VMware ESXi)
BIND9 — DNS server
ISC DHCP Server — DHCP server
VMware ESXi — Virtualization and isolated network (vSwitch / Port Group)


Architecture

Isolated network created in ESXi (LAN-DNS-DHCP, vSwitch0)
Server with static IP: 192.168.1.147/24
DNS zone: asirlab.local
DHCP range: 192.168.1.200 - 192.168.1.220


⚙️⚙️ Configuration ⚙️ ⚙️

1. Network and static IP
A dedicated Port Group was created in ESXi and a static IP was configured via Netplan.

2. DNS (BIND9)
Local zone asirlab.local with A records for ns and www.
Configuration in /etc/bind/named.conf.local and /etc/bind/db.asirlab.local.


3. DHCP (ISC-DHCP-Server)
Assignment range: 192.168.1.200-220
Gateway: 192.168.1.1
DNS handed to clients: 192.168.1.147 (the server itself)
Domain: asirlab.local
