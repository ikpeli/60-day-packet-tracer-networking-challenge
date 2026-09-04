# 07 — SSH Simulation

These images identify the secure management session at the application and transport layers.

| Image | Evidence |
|---|---|
| `25-admin-pc-sends-ssh-data.png` | ADMIN-PC sends SSH application data toward SW2 |
| `26-sw2-receives-ssh-on-port-22.png` | SW2 receives TCP traffic with destination port 22 |

Together they confirm that remote management is using SSH rather than Telnet.
