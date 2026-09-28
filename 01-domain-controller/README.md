# Project 1: Domain Controller

## Goal
Build a Windows Server VM (DC01) that acts as a domain controller for a new forest, `lab.local`, running AD DS and DNS.

## Environment
- VM name: DC01
- Specs: 2 CPU cores, 4-8 GB RAM, 60 GB disk
- OS: Windows Server (version: ___)
- Network mode: Host-Only / Internal Network (pick one)
- Static IP: 192.168.10.10 / 255.255.255.0, DNS = 192.168.10.10 (itself)

## Steps completed
- [ ] Created DC01 VM
- [ ] Installed Windows Server (Standard, Desktop Experience)
- [ ] Set static IP
- [ ] Renamed server to DC01 and rebooted
- [ ] Installed AD DS and DNS Server roles
- [ ] Promoted to domain controller (new forest `lab.local`)
- [ ] Verified AD and DNS (ADUC opens, forward lookup zone `lab.local` exists)

### Optional: DHCP
- [ ] Installed DHCP Server role and completed configuration
- [ ] Created scope 192.168.10.100 - 192.168.10.200
- [ ] Set options: 003 gateway, 006 DNS (192.168.10.10), 015 domain (lab.local)
- [ ] Activated scope

## Screenshots to capture
Save into `screenshots/` and link them here.
1. VM settings (CPU, RAM, disk, network)
2. Static IP configuration
3. Roles installed in Server Manager
4. Promotion wizard summary (blank out any passwords)
5. ADUC showing the domain
6. DNS Manager showing the `lab.local` zone

## Verification
```
ipconfig /all
nslookup lab.local
```
Paste results here.

## Problems and fixes
See [TROUBLESHOOTING.md](../TROUBLESHOOTING.md). Summarize the big ones here.

## What I learned
-
-
