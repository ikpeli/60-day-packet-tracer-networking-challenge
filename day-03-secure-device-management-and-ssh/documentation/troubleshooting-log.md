# Troubleshooting Log

## Scenario 1 — Missing SW2 Default Gateway

### Change introduced

```text
SW2-REMOTE(config)# no ip default-gateway 192.168.20.1
```

### Symptoms

- ADMIN-PC could not ping `192.168.20.2`.
- ADMIN-PC could not establish SSH to `192.168.20.2`.
- R1 could still ping `192.168.20.2` successfully.

### Reasoning

SW2 and R1 share `192.168.20.0/24`, so they communicate without a gateway. ADMIN-PC is in `192.168.10.0/24`; without a default gateway, SW2 cannot return traffic to that remote subnet. The successful R1 ping isolated the problem to SW2's off-subnet return path rather than the local link or SVI.

### Correction

```text
SW2-REMOTE(config)# ip default-gateway 192.168.20.1
SW2-REMOTE# copy running-config startup-config
```

### Verification

- ADMIN-PC again received ping replies from `192.168.20.2`.
- Remote management reachability was restored.

## Scenario 2 — Incorrect VTY Transport

### Change introduced

The SW2 VTY lines were temporarily changed to accept Telnet rather than SSH.

```text
SW2-REMOTE(config-line)# transport input telnet
```

### Symptoms

- Ping to SW2 remained successful.
- SSH to SW2 failed even though the IP path was healthy.
- Telnet became available during the controlled fault.

### Reasoning

Because ICMP still succeeded, addressing, switching and routing were operational. The failure was limited to the remote-management service. Inspecting the VTY configuration identified the transport mismatch.

### Correction

```text
SW2-REMOTE(config-line)# transport input ssh
SW2-REMOTE# copy running-config startup-config
```

### Verification

- SSH access was restored.
- Telnet was rejected after the repair.

## Evidence Notes

- Some captures show `SW1_ADMIN` while the topology label uses `SW1-ADMIN`.
- One SW2 capture shows the default VLAN label instead of the intended descriptive VLAN name.
- One captured banner contains a spelling error.

These are cosmetic documentation issues. They do not change interface state, IP forwarding, default-gateway behaviour, SSH operation or the demonstrated troubleshooting results. They are recorded here rather than hidden so the portfolio evidence remains accurate.
