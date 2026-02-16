# Cisco Port Security (Packet Tracer Lab)

This repository contains a Cisco Packet Tracer lab demonstrating **Switch Port Security** to protect access-layer ports from unauthorized devices using MAC-based controls (Layer 2).

## What this lab demonstrates
- Enabling `port-security` on access ports
- Limiting the number of allowed MAC addresses (`maximum`)
- MAC learning options: **Sticky** and **Static**
- Violation actions: `shutdown` and `restrict`
- Verification and troubleshooting using show commands
- (Optional) Automatic recovery from `err-disabled` due to security violations

## Topology / Files
- `topology.pkt` — Packet Tracer topology file
- `README.md` — Documentation

## Baseline Configuration (Sticky + Shutdown)
Example for an access port allowing **only one device** (sticky MAC learning):

```bash
enable
configure terminal

interface fastEthernet0/1
 description PORT-SECURITY_STICKY_MAX1
 switchport mode access
 spanning-tree portfast
 switchport port-security
 switchport port-security maximum 1
 switchport port-security mac-address sticky
 switchport port-security violation shutdown
exit

end
write memory
