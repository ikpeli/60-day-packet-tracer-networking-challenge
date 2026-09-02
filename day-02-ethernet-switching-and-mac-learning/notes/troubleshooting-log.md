# Day 2 Troubleshooting Log

## Fault introduced

- **Device:** SW1
- **Interface:** FastEthernet0/2
- **Connected host:** PC-B
- **Action:** Applied the `shutdown` command.

## Symptoms observed

- PC-B's link indicator:
- PC-A-to-PC-B ping result:
- FastEthernet0/2 status in `show interfaces status`:
- FastEthernet0/2 state in `show interfaces fastEthernet 0/2`:
- PC-B entry in the MAC address table:

## Investigation

Commands used:

```text
show interfaces status
show interfaces fastEthernet 0/2
show mac address-table dynamic
```

Evidence and interpretation:

1. _Complete after testing._
2. _Complete after testing._
3. _Complete after testing._

## Corrective action

```text
configure terminal
interface fastEthernet 0/2
no shutdown
end
```

## Verification after recovery

- Port indicator after waiting for convergence:
- FastEthernet0/2 status:
- PC-A-to-PC-B ping result:
- MAC address relearned on FastEthernet0/2:

## Root cause statement

Complete after the lab:

> Connectivity to PC-B failed because _______________________________________. Service was restored by _______________________________________ and verified using _______________________________________.
