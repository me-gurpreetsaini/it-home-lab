# Troubleshooting Log

Interviewers love these. Log every problem, even small ones.

| Date | Project | Symptom | Cause | Fix |
|------|---------|---------|-------|-----|
| 2026-09-29 | Active Directory | PC01 got IP 192.168.226.130 instead of 192.168.10.x | VMware's built-in DHCP on VMnet1 (host-only) conflicted with DC01's DHCP server, and VMnet1's subnet didn't match | Disabled VMware's local DHCP service on VMnet1, changed its subnet to 192.168.10.0/24 |
| 2026-09-29 | Active Directory | Couldn't create OU named "Users" | AD already has a built-in Users container with that exact name | Renamed custom OUs to Lab-Admins, Staff, Workstations to avoid collision |
| | | | | |

## Detailed writeup: PC01 got the wrong IP

**Symptom:** PC01 received IP 192.168.226.130, DNS 192.168.226.1, DHCP Server 192.168.226.254, nowhere near the 192.168.10.0/24 network DC01 lives on.

![PC01 with wrong IP](02-active-directory/screenshots/09-pc01-wrong-network.png)

**Root cause:** Both PC01 and DC01 were set to VMware's "Host-only" network (VMnet1), but VMware Workstation runs its own built-in DHCP service on host-only networks by default. Two DHCP servers existed on the same network at once, VMware's built-in one and the one configured on DC01. PC01 received an address from VMware's DHCP server first, landing it on the wrong subnet entirely.

**Fix:** Opened VMware's Virtual Network Editor, selected VMnet1, disabled "Use local DHCP service to distribute IP addresses to VMs", and changed the subnet from 192.168.226.0 to 192.168.10.0/24 to match the lab's network design.

![VMnet1 DHCP fix](02-active-directory/screenshots/10-vmnet-dhcp-fix.png)

**Result:** After running `ipconfig /release` and `ipconfig /renew` on PC01, it correctly received IP 192.168.10.100 from DHCP Server 192.168.10.10 (DC01), with DNS also set to 192.168.10.10. Ping to DC01 succeeded with 0% loss, and nslookup resolved lab.local correctly.

![PC01 with correct DHCP lease](02-active-directory/screenshots/11-pc01-correct-dhcp.png)
![Ping and nslookup results](02-active-directory/screenshots/12-ping-nslookup.png)

**What this taught me:** Two DHCP servers on one network is a real-world networking problem, not just a lab quirk. Checking for rogue or conflicting DHCP servers is a common troubleshooting step when a device gets an unexpected IP.

## Common issues to watch for
- Client DNS not pointing to the DC: domain join fails
- DC without a static IP: AD/DNS becomes flaky
- Large time difference between client and DC: login/auth issues
- DHCP handing out the wrong DNS server: clients can't find the domain
- Trunk not configured: inter-VLAN routing fails
- Missing `ip helper-address` when DHCP is on another subnet
