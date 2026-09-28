# Troubleshooting Log

Interviewers love these. Log every problem, even small ones.

| Date | Project | Symptom | Cause | Fix |
|------|---------|---------|-------|-----|
| | | Domain join fails | Client DNS not pointing to DC | Set DNS to 192.168.10.10 |
| | | | | |

## Common issues to watch for
- Client DNS not pointing to the DC: domain join fails
- DC without a static IP: AD/DNS becomes flaky
- Large time difference between client and DC: login/auth issues
- DHCP handing out the wrong DNS server: clients can't find the domain
- Trunk not configured: inter-VLAN routing fails
- Missing `ip helper-address` when DHCP is on another subnet
