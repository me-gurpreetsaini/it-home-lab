# Project 3: Cisco Packet Tracer Network

## Goal
Design and validate the network that would support the AD environment: two VLANs, inter-VLAN routing, and DHCP with relay.

## Topology
- 1 router (2911) or L3 switch (3560)
- 1 switch (2960)
- VLAN 10 SERVERS: 192.168.10.0/24
- VLAN 20 CLIENTS: 192.168.20.0/24

Add a screenshot of the topology here.

## Steps completed
- [ ] Built topology
- [ ] Created VLAN 10 (SERVERS) and VLAN 20 (CLIENTS) on the switch
- [ ] Assigned access ports
- [ ] Configured trunk (allowed VLANs 10, 20)
- [ ] Configured router-on-a-stick (G0/0.10 and G0/0.20 with dot1q)
- [ ] Configured DHCP (router pools or a DHCP server device)
- [ ] Added `ip helper-address` on the VLAN 20 subinterface (if DHCP server is in VLAN 10)
- [ ] Configured DNS (PT server or reachability to 192.168.10.10)
- [ ] Ran connectivity tests

## Configs
Paste the important config here (remove nothing sensitive, it's a lab).

```
! router
! switch
```

## Tests
| Test | From | To | Result |
|------|------|----|--------|
| Ping gateway | Client PC | 192.168.20.1 | |
| Ping other subnet gateway | Client PC | 192.168.10.1 | |
| Ping server/DNS | Client PC | 192.168.10.10 | |
| DHCP lease received | Client PC | | |

## Files
- Save your `.pkt` file in this folder.

## Problems and fixes
See [TROUBLESHOOTING.md](../TROUBLESHOOTING.md).

## What I learned
-
-
