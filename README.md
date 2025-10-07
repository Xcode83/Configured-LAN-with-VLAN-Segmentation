🖧 Configured LAN with VLAN Segmentation & Inter-VLAN Routing
📘 Project Overview

This project demonstrates the design and configuration of a small-scale Local Area Network (LAN) with multiple VLANs (Virtual Local Area Networks) to separate departments within an organization.
Inter-VLAN communication is enabled using a Router-on-a-Stick configuration on a Cisco router.

The setup ensures network segmentation, improved security, and efficient traffic management within an enterprise environment.

🧩 Network Topology
![Uploading Screenshot 2025-10-07 221334.png…]()

Devices Used:

1 × Cisco 1941 Router

1 × Cisco 2960 Switch

6 × End Devices (PCs)

VLAN Distribution:

Department	VLAN ID	Subnet	Example IPs
HR	10	192.168.10.0/24	192.168.10.2–3
IT	20	192.168.20.0/24	192.168.20.2–3
Finance	30	192.168.30.0/24	192.168.30.2-3
⚙️ Configuration Summary
🖥️ Switch Configuration

Created and assigned VLANs (10, 20, 30)

Configured access ports for each VLAN

Configured trunk port for router connection
vlan 10
 name HR
vlan 20
 name IT
vlan 30
 name FINANCE
!
interface range fa0/1-2
 switchport mode access
 switchport access vlan 10
!
interface range fa0/3-4
 switchport mode access
 switchport access vlan 20
!
interface range fa0/5-6
 switchport mode access
 switchport access vlan 30
!
interface fa0/1
 switchport mode trunk



 🌐 Router Configuration

Configured sub-interfaces for Inter-VLAN Routing (Router-on-a-Stick):

interface g0/0.10
 encapsulation dot1Q 10
 ip address 192.168.10.1 255.255.255.0
!
interface g0/0.20
 encapsulation dot1Q 20
 ip address 192.168.20.1 255.255.255.0
!
interface g0/0.30
 encapsulation dot1Q 30
 ip address 192.168.30.1 255.255.255.0
!
interface g0/0
 no shutdown

💻 PC Configuration

Each PC assigned static IP based on VLAN:

Default Gateway: VLAN interface IP on router

Subnet Mask: 255.255.255.0

🔍 Verification

Ping tests performed within and across VLANs

VLAN segmentation verified using:

show vlan brief

show interfaces trunk

Used Packet Tracer Simulation Mode to capture ICMP packets for validation

🧰 Tools Used

🖥 Cisco Packet Tracer

🧾 Command-Line Interface (CLI)
