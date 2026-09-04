# Addressing Table

## Network Summary

| Network | Prefix | Mask | Usable range | Broadcast | Purpose |
|---|---:|---:|---:|---:|---|
| `192.168.10.0` | `/24` | `255.255.255.0` | `192.168.10.1`–`192.168.10.254` | `192.168.10.255` | Administration LAN and VLAN 10 |
| `192.168.20.0` | `/24` | `255.255.255.0` | `192.168.20.1`–`192.168.20.254` | `192.168.20.255` | Remote-management LAN and VLAN 20 |

## Device Assignments

| Device | Interface | Address/prefix | Default gateway | Connected to |
|---|---|---:|---:|---|
| ADMIN-PC | Fa0 | `192.168.10.10/24` | `192.168.10.1` | SW1-ADMIN Fa0/1 |
| SW1-ADMIN | VLAN 10 | `192.168.10.2/24` | `192.168.10.1` | Management SVI |
| R1 | G0/0 | `192.168.10.1/24` | N/A | SW1-ADMIN Gi0/1 |
| R1 | G0/1 | `192.168.20.1/24` | N/A | SW2-REMOTE Gi0/1 |
| SW2-REMOTE | VLAN 20 | `192.168.20.2/24` | `192.168.20.1` | Management SVI |

## Why the Switches Need Default Gateways

A Layer 2 switch can communicate directly with hosts in the same management subnet. To reply to a host in another subnet, it sends the management packet to its configured default gateway. SW2-REMOTE therefore needs `192.168.20.1` to reply to ADMIN-PC at `192.168.10.10`.

R1 does not need a static route in this lab because it owns an active interface in each subnet. IOS automatically installs connected (`C`) and local (`L`) routes for those interfaces.
