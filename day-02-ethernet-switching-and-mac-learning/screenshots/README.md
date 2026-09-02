# Day 2 Screenshot Evidence

This folder contains the visual evidence collected during the Day 2 Ethernet switching and MAC address learning lab.

The screenshots document the completed topology, switch configuration, MAC address learning, ARP and ICMP simulation, connectivity tests, deliberate interface failure, troubleshooting process and network recovery.

## Evidence index

| No. | Filename | Evidence provided |
|---:|---|---|
| 1 | `01-completed-topology.png` | Completed Cisco 2960 and four-PC topology |
| 2 | `02-initial-mac-address-table.png` | Dynamic MAC address table before traffic |
| 3 | `03-arp-broadcast-simulation1.png` | First stage of the ARP broadcast simulation |
| 4 | `03-arp-broadcast-simulation2.png` | Second stage of the ARP broadcast simulation |
| 5 | `04-icmp-unicast-simulation1.png` | First stage of the ICMP unicast simulation |
| 6 | `04-icmp-unicast-simulation2.png` | Second stage of the ICMP unicast simulation |
| 7 | `04-icmp-unicast-simulation3.png` | Third stage of the ICMP unicast simulation |
| 8 | `05-successful-connectivity-test1.png` | First set of successful connectivity tests |
| 9 | `05-successful-connectivity-test2.png` | Second set of successful connectivity tests |
| 10 | `06-learned-mac-address-table.png` | Dynamically learned MAC-to-port mappings |
| 11 | `07-port-shutdown-failure.png` | Connectivity failure following the port shutdown |
| 12 | `08-port-restored-connectivity.png` | Successful connectivity after restoring the port |
| 13 | `09-interface-brief.png` | Management SVI and interface summary |
| 14 | `10-interface-status.png` | Switch access-port status |
| 15 | `11-show-running-config1.png` | First part of the SW1 running configuration |
| 16 | `11-show-running-config2.png` | Second part of the SW1 running configuration |
| 17 | `12-relearned-mac-address-table.png` | MAC address table after clearing and relearning |
| 18 | `13-disconnected-interface.png` | Disconnected or disabled interface evidence |
| 19 | `14-interface-Fa02.png` | Detailed FastEthernet0/2 interface information |

## Main observations

- The initial dynamic MAC address table contained no learned host entries.
- SW1 learned MAC addresses after receiving traffic from the PCs.
- The ARP request was broadcast through VLAN 1.
- ICMP traffic was forwarded as unicast after ARP resolution.
- Clearing the dynamic MAC address table caused SW1 to relearn the addresses.
- Disabling FastEthernet0/2 interrupted communication with PC-B.
- Restoring FastEthernet0/2 returned the network to normal operation.

Return to the [main Day 2 README](../README.md).

