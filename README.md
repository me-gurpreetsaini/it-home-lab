# IT Home Lab

Hands-on home lab built to learn the fundamentals behind help desk, desktop support, and junior sysadmin work.

## Projects

| # | Project | What I built | Status |
|---|---------|--------------|--------|
| 1 | [Domain Controller](01-domain-controller/) | Windows Server VM running AD DS + DNS (+ optional DHCP) | Not started |
| 2 | [Active Directory](02-active-directory/) | Domain-joined client, OUs, users, groups, Group Policy | Not started |
| 3 | [Cisco Packet Tracer](03-cisco-packet-tracer/) | VLANs, trunking, router-on-a-stick, DHCP relay | Not started |

## Lab environment

- Hypervisor: VirtualBox / VMware Workstation Player (pick one, delete the other)
- Servers: Windows Server 2019/2022 (Evaluation)
- Clients: Windows 10/11
- Network simulation: Cisco Packet Tracer (version: ___)

## Network design

| Network | Subnet | Gateway | Notes |
|---------|--------|---------|-------|
| Servers (VLAN 10) | 192.168.10.0/24 | 192.168.10.1 | DC01 = 192.168.10.10 |
| Clients (VLAN 20) | 192.168.20.0/24 | 192.168.20.1 | DHCP, DNS = 192.168.10.10 |

Domain: `lab.local`

> Note: Packet Tracer is a simulator and can't connect to the VMs. The VMs are the real Active Directory environment; Packet Tracer validates the network design using the same addressing.

## Skills demonstrated

- Windows Server installation and configuration
- Active Directory Domain Services, DNS, DHCP
- User, group, and OU management
- Group Policy (GPO)
- VLANs, trunking, inter-VLAN routing, DHCP relay
- Troubleshooting with ping, nslookup, ipconfig, gpupdate

## Logs

- [LAB-LOG.md](LAB-LOG.md): what I did each session
- [TROUBLESHOOTING.md](TROUBLESHOOTING.md): problems I hit and how I fixed them
