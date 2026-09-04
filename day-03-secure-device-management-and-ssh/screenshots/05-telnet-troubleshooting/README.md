# 05 — Telnet and VTY Troubleshooting

These images demonstrate that IP reachability and application availability are separate conditions.

| Image | Evidence |
|---|---|
| `15-vty-fault-telnet-access-enabled.png` | Telnet is temporarily enabled as a controlled VTY fault |
| `16-telnet-blocked-on-all-managed-devices.png` | Telnet tests are rejected after hardening |
| `17-telnet-blocked-after-ssh-restoration.png` | SSH-only VTY transport is restored and verified |

The intended final state is `transport input ssh`; Telnet is not part of the secured solution.
