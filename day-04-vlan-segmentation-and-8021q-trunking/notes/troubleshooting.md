# Day 04 Troubleshooting Record

## Incident 1 - GUEST-PC2 Connected to the Wrong Switch Port

### Expected Behaviour

`GUEST-PC1` (`192.168.20.11`) and `GUEST-PC2` (`192.168.20.12`) were intended to communicate across the inter-switch trunk in VLAN 20.

### Observed Behaviour

Pings between the guest PCs returned four timeouts and 100% packet loss.

Because the devices were in the same IP subnet, a default gateway was not required. The failure therefore pointed to a Layer 1 or Layer 2 problem.

### Investigation Sequence

1. Verified both guest IP addresses and subnet masks.
2. Used `show vlan brief` to confirm VLAN 20 existed on both switches.
3. Used `show interfaces trunk` to confirm VLAN 20 was allowed and active across `Gi0/1`.
4. Used `show mac address-table dynamic` on SW2 to determine where GUEST-PC2 was being learned.

The MAC table showed:

```text
Vlan    Mac Address       Type       Ports
10      00e0.8f2e.99e3    DYNAMIC    Fa0/1
```

The MAC address belonged to GUEST-PC2, but VLAN 10 and `Fa0/1` were reserved for STAFF-PC2.

### Root Cause

GUEST-PC2 had been connected to SW2 `Fa0/1`, a static access port in VLAN 10, instead of SW2 `Fa0/2`, the intended VLAN 20 guest port.

An access switch classifies an incoming untagged Ethernet frame according to the VLAN assigned to the ingress port. The guest PC's `192.168.20.12` address did not place it in VLAN 20; the `Fa0/1` switchport placed its frames in VLAN 10.

### Corrective Action

- Connected STAFF-PC2 to SW2 `Fa0/1` in VLAN 10.
- Connected GUEST-PC2 to SW2 `Fa0/2` in VLAN 20.
- Allowed the interfaces to return to an up/up state.
- Repeated the guest VLAN ping test.

### Verification

GUEST-PC1 and GUEST-PC2 then received four replies with 0% packet loss.

Evidence:

- `screenshots/12-wrong-port-mac-address-diagnosis.png`
- `screenshots/13-guest-pc2-connectivity-restored.png`
- `screenshots/14-guest-pc1-connectivity-restored.png`
- `screenshots/17-guest-pc2-ping-failure-and-recovery.png`

## Incident 2 - Deliberately Incorrect Staff Access VLAN

### Change Introduced

SW2 `Fa0/1`, normally assigned to VLAN 10, was deliberately moved to VLAN 20.

### Effect

STAFF-PC1 and STAFF-PC2 retained addresses in `192.168.10.0/24`, but their ports were no longer in the same Layer 2 broadcast domain. The ping failed with 100% packet loss.

### Diagnosis

```text
show interfaces fastEthernet0/1 switchport
```

The output identified `Access Mode VLAN: 20 (GUEST)` on the staff port.

### Fix

```text
configure terminal
interface fastEthernet0/1
switchport access vlan 10
end
```

The staff ping succeeded again after the port was restored to VLAN 10.

Evidence:

- `screenshots/18-staff-ping-failure-after-wrong-access-vlan.png`
- `screenshots/19-wrong-access-vlan-identified.png`
- `screenshots/20-access-vlan-restored-and-ping-verified.png`

## Incident 3 - VLAN 20 Removed From the Trunk Allow-List

### Change Introduced

VLAN 20 was deliberately removed from the SW1 trunk allow-list:

```text
interface gigabitEthernet0/1
switchport trunk allowed vlan 10,99,999
```

### Effect

- Guest VLAN 20 traffic could no longer cross between the switches.
- Staff VLAN 10 traffic continued to work.
- The physical trunk remained operational.

This showed that an up/up trunk can still have a VLAN-specific forwarding problem.

### Fix

```text
configure terminal
interface gigabitEthernet0/1
switchport trunk allowed vlan 10,20,99,999
end
```

Evidence:

- `screenshots/21-guest-vlan-failure-after-vlan20-removed-from-trunk.png`
- `screenshots/22-staff-vlan-remains-operational-during-trunk-fault.png`

## Troubleshooting Lessons

- Verify the physical connection before assuming the configuration is wrong.
- IP addressing alone does not determine VLAN membership.
- Use the MAC address table to connect an endpoint identity to a physical port and VLAN.
- Compare a failing VLAN with a working VLAN to narrow the fault domain.
- Verify the final state after every correction.
