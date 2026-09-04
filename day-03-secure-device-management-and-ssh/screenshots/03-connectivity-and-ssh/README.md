# 03 — Connectivity and SSH

These images prove successful IP reachability and encrypted remote management.

| Image | Evidence |
|---|---|
| `04-initial-connectivity-tests.png` | Initial reachability tests and the expected early convergence behaviour |
| `05-remote-switch-ping-success.png` | Routed ICMP reachability to `192.168.20.2` |
| `06-successful-ssh-to-r1.png` | Authenticated SSH access to R1 |
| `07-successful-ssh-to-sw1-vlan10.png` | Authenticated SSH access to SW1 |
| `08-successful-ssh-to-sw2-vlan20.png` | Authenticated routed SSH access to SW2 |
| `09-successful-local-connectivity-tests.png` | Successful local management-network pings |
| `10-complete-end-to-end-ping-verification.png` | Final end-to-end connectivity verification |

An occasional first ping timeout can occur while ARP entries are being learned; repeated zero-loss results confirm steady-state connectivity.
