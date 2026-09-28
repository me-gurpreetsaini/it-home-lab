## 2026-09-28
- **Project:** Domain Controller
- **Goal today:** Build DC01 and promote it to a domain controller
- **What I did:** Created the DC01 VM in VMware Workstation Pro 17 (2 CPU, 4 GB RAM, 60 GB disk, host-only network). Installed Windows Server 2022 Standard (Desktop Experience). Set a static IP (192.168.10.10/255.255.255.0, DNS pointing to itself). Installed the AD DS and DNS Server roles. Promoted DC01 to a domain controller, creating a new forest and domain: lab.local. Confirmed success by logging in as LAB\Administrator.
- **Next:** Set up DHCP on DC01, then verify AD/DNS before starting Project 2 (joining a client to the domain)

---
