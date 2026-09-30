# Project 2: Active Directory

## Goal
Join a Windows client to `lab.local` and perform core AD administration: OUs, users, groups, and Group Policy.

## Environment
- VM name: PC01
- Specs: 2 CPU cores, 4 GB RAM, 60 GB disk
- OS: Windows 10 / 11
- Same VM network as DC01
- IP: 192.168.10.20 (static) or DHCP; DNS = 192.168.10.10

## Steps completed
- [x] Created PC01 on the same network as DC01
- [x] Set DNS to 192.168.10.10
- [x] Tested `ping 192.168.10.10` and `nslookup lab.local`
- [ ] Joined the domain and rebooted
- [ ] Created OUs: Users, Computers, Admins
- [ ] Created user `jdoe`
- [ ] Created groups `GG-IT-Admins` and `GG-Staff` and added members
- [ ] Created a GPO on the Users OU (Prohibit access to Control Panel)
- [ ] Logged in as `jdoe`, ran `gpupdate /force`, confirmed Control Panel is blocked

## Screenshots to capture
1. Successful ping and nslookup from PC01
2. "Welcome to the lab.local domain" message
3. OU structure in ADUC
4. Users and groups
5. GPO in Group Policy Management
6. Control Panel blocked message on PC01 as jdoe

## Verification
```
whoami
gpupdate /force
gpresult /r
```
Paste results here.
## Networking setup and troubleshooting

Before joining the domain, I confirmed PC01 could reach DC01 over the network.

### Problem: PC01 got the wrong IP
PC01 received 192.168.226.130 from DHCP Server 192.168.226.254, not the 192.168.10.x network DC01 lives on.

![PC01 with wrong IP](screenshots/09-pc01-wrong-network.png)

### Fix: disabled VMware's competing DHCP service
VMware Workstation runs its own built-in DHCP on host-only networks (VMnet1) by default. This conflicted with the DHCP server on DC01. Disabled "Use local DHCP service to distribute IP addresses to VMs" on VMnet1 and set its subnet to 192.168.10.0/24 to match the lab design.

![VMnet1 DHCP fix](screenshots/10-vmnet-dhcp-fix.png)

### Result: PC01 got the correct lease from DC01
After releasing and renewing, PC01 received 192.168.10.100 from DHCP Server 192.168.10.10 (DC01), with DNS also set to 192.168.10.10.

![PC01 with correct DHCP lease](screenshots/11-pc01-correct-dhcp.png)

### Verified connectivity to DC01
Pinged DC01 successfully (0% loss) and resolved lab.local via nslookup.

![Ping and nslookup results](screenshots/12-ping-nslookup.png)

## Problems and fixes
See [TROUBLESHOOTING.md](../TROUBLESHOOTING.md).

## What I learned
-
-
