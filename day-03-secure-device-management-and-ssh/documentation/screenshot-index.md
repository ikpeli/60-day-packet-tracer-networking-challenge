# Screenshot Index

The public evidence set contains 26 unique screenshots arranged in the technical order of the lab.

| No. | Path | Evidence shown |
|---:|---|---|
| 01 | `screenshots/01-topology/01-labelled-network-topology.png` | Complete labelled topology, ports, VLANs and IPv4 addresses |
| 02 | `screenshots/02-router-and-routing/02-r1-interface-configuration-and-status.png` | R1 interface addressing and `up/up` state |
| 03 | `screenshots/02-router-and-routing/03-r1-connected-routing-table.png` | Connected and local routes for both `/24` networks |
| 04 | `screenshots/03-connectivity-and-ssh/04-initial-connectivity-tests.png` | Initial gateway and remote reachability tests |
| 05 | `screenshots/03-connectivity-and-ssh/05-remote-switch-ping-success.png` | Successful routed ping to SW2 |
| 06 | `screenshots/03-connectivity-and-ssh/06-successful-ssh-to-r1.png` | Remote SSH session to R1 |
| 07 | `screenshots/03-connectivity-and-ssh/07-successful-ssh-to-sw1-vlan10.png` | Remote SSH session to SW1 |
| 08 | `screenshots/03-connectivity-and-ssh/08-successful-ssh-to-sw2-vlan20.png` | Routed SSH session to SW2 |
| 09 | `screenshots/03-connectivity-and-ssh/09-successful-local-connectivity-tests.png` | Successful local-subnet tests |
| 10 | `screenshots/03-connectivity-and-ssh/10-complete-end-to-end-ping-verification.png` | Final multi-destination ping verification |
| 11 | `screenshots/04-default-gateway-troubleshooting/11-remote-failure-after-gateway-removal.png` | Remote failure after removing SW2's gateway |
| 12 | `screenshots/04-default-gateway-troubleshooting/12-r1-local-reachability-during-gateway-fault.png` | R1 still reaches SW2 on the local subnet |
| 13 | `screenshots/04-default-gateway-troubleshooting/13-sw2-default-gateway-fault-and-restoration.png` | Gateway removal, restoration and configuration save |
| 14 | `screenshots/04-default-gateway-troubleshooting/14-remote-connectivity-restored.png` | Successful access after repairing the gateway |
| 15 | `screenshots/05-telnet-troubleshooting/15-vty-fault-telnet-access-enabled.png` | Controlled Telnet transport fault |
| 16 | `screenshots/05-telnet-troubleshooting/16-telnet-blocked-on-all-managed-devices.png` | Telnet attempts rejected by managed devices |
| 17 | `screenshots/05-telnet-troubleshooting/17-telnet-blocked-after-ssh-restoration.png` | Telnet rejected after restoring SSH-only VTY access |
| 18 | `screenshots/06-icmp-simulation/18-admin-pc-icmp-encapsulation.png` | ADMIN-PC constructs the ICMP Echo Request |
| 19 | `screenshots/06-icmp-simulation/19-sw1-layer2-forwarding.png` | SW1 forwards the Ethernet frame |
| 20 | `screenshots/06-icmp-simulation/20-r1-layer3-routing.png` | R1 routes the request between subnets |
| 21 | `screenshots/06-icmp-simulation/21-sw2-generates-icmp-reply.png` | SW2 changes ICMP Type 8 request to Type 0 reply |
| 22 | `screenshots/06-icmp-simulation/22-r1-routes-icmp-reply.png` | R1 routes the reply toward ADMIN-PC |
| 23 | `screenshots/06-icmp-simulation/23-sw1-forwards-return-frame.png` | SW1 forwards the return Ethernet frame |
| 24 | `screenshots/06-icmp-simulation/24-admin-pc-receives-icmp-reply.png` | ADMIN-PC receives the Echo Reply |
| 25 | `screenshots/07-ssh-simulation/25-admin-pc-sends-ssh-data.png` | SSH client sends application data |
| 26 | `screenshots/07-ssh-simulation/26-sw2-receives-ssh-on-port-22.png` | SW2 receives TCP traffic on destination port 22 |

## Excluded from the Public Set

Two original screenshots showed reversible Cisco Type 7 password strings. They were excluded deliberately and replaced by sanitized reference configurations in `configs/`. A duplicate topology screenshot and a duplicate configuration screenshot were also removed.
