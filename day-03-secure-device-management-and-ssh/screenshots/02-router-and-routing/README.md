# 02 — Router and Routing

These images verify that R1 provides Layer 3 connectivity between the two management networks.

| Image | What it proves |
|---|---|
| `02-r1-interface-configuration-and-status.png` | `G0/0` and `G0/1` have the correct addresses and are `up/up` |
| `03-r1-connected-routing-table.png` | IOS installed connected and local routes for both `/24` networks |

No static route is required because both destination networks are directly connected to R1.
