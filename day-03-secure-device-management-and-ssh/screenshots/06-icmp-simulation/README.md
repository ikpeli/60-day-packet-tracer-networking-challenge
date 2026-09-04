# 06 — ICMP Simulation

These images trace an ICMP exchange from ADMIN-PC to SW2-REMOTE and back.

| Image | Packet-processing stage |
|---|---|
| `18-admin-pc-icmp-encapsulation.png` | ADMIN-PC creates an Echo Request and selects its default gateway |
| `19-sw1-layer2-forwarding.png` | SW1 forwards the frame toward R1 |
| `20-r1-layer3-routing.png` | R1 routes the packet from the administration network to the remote network |
| `21-sw2-generates-icmp-reply.png` | SW2 receives Type 8 and generates Type 0 |
| `22-r1-routes-icmp-reply.png` | R1 routes the return packet toward `192.168.10.10` |
| `23-sw1-forwards-return-frame.png` | SW1 forwards the reply to ADMIN-PC |
| `24-admin-pc-receives-icmp-reply.png` | ADMIN-PC receives the Echo Reply |

The Layer 3 source and destination remain end-to-end addresses, while the Ethernet header changes at the router for each link segment.
