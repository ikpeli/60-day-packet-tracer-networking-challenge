# 04 — Default-Gateway Troubleshooting

This evidence follows the complete fault-isolation cycle for a missing Layer 2 switch default gateway.

| Image | Evidence |
|---|---|
| `11-remote-failure-after-gateway-removal.png` | ADMIN-PC loses ping and SSH access to SW2 |
| `12-r1-local-reachability-during-gateway-fault.png` | R1 still reaches SW2 on their shared subnet |
| `13-sw2-default-gateway-fault-and-restoration.png` | Default gateway removed, restored and saved |
| `14-remote-connectivity-restored.png` | ADMIN-PC again reaches and manages SW2 |

The contrast between local success and remote failure identifies a return-path problem rather than a failed interface or SVI.
