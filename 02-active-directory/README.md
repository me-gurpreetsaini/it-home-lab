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
- [ ] Created PC01 on the same network as DC01
- [ ] Set DNS to 192.168.10.10
- [ ] Tested `ping 192.168.10.10` and `nslookup lab.local`
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

## Problems and fixes
See [TROUBLESHOOTING.md](../TROUBLESHOOTING.md).

## What I learned
-
-
