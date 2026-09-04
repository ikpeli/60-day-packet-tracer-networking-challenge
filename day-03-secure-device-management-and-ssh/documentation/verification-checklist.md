# Verification Checklist

## Build and Addressing

- [x] ADMIN-PC, two switches and one router placed and cabled.
- [x] ADMIN-PC configured as `192.168.10.10/24` with gateway `192.168.10.1`.
- [x] R1 `G0/0` configured as `192.168.10.1/24` and shown `up/up`.
- [x] R1 `G0/1` configured as `192.168.20.1/24` and shown `up/up`.
- [x] SW1 management SVI configured as `192.168.10.2/24`.
- [x] SW2 management SVI configured as `192.168.20.2/24`.
- [x] Connected routes for both `/24` networks verified on R1.

## Security and Remote Management

- [x] Local administrator configured.
- [x] Domain name and RSA keys configured.
- [x] SSH version 2 enabled.
- [x] VTY lines configured with `login local`.
- [x] VTY lines restricted to SSH after testing.
- [x] Successful SSH session to R1 captured.
- [x] Successful SSH session to SW1 captured.
- [x] Successful SSH session to SW2 captured.
- [x] Telnet rejection captured after SSH-only restoration.

## Troubleshooting

- [x] SW2 default gateway deliberately removed.
- [x] Remote failure reproduced from ADMIN-PC.
- [x] Same-subnet R1-to-SW2 reachability verified during the fault.
- [x] SW2 default gateway restored.
- [x] Remote connectivity verified after repair.
- [x] VTY transport fault introduced.
- [x] Difference between ping reachability and SSH availability demonstrated.
- [x] SSH-only transport restored and verified.

## Simulation Mode

- [x] ICMP Echo Request created at ADMIN-PC.
- [x] Layer 2 forwarding inspected on SW1.
- [x] Layer 3 routing inspected on R1.
- [x] ICMP Echo Reply generation inspected on SW2.
- [x] Return forwarding inspected through R1 and SW1.
- [x] Echo Reply reception inspected at ADMIN-PC.
- [x] SSH application data inspected.
- [x] TCP destination port 22 verified at SW2.

## Portfolio Preparation

- [x] Packet Tracer file included.
- [x] Screenshots renamed and grouped by purpose.
- [x] Duplicate screenshots removed.
- [x] Screenshots exposing reversible password hashes excluded.
- [x] Public reference configurations sanitized.
- [x] A README included in every folder.
