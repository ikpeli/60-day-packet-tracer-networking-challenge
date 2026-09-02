# Day 2 Commands Used

## Switch operating modes

| Command | Purpose |
|---|---|
| `enable` | Enters privileged EXEC mode. |
| `configure terminal` | Enters global configuration mode. |
| `end` | Returns directly to privileged EXEC mode. |
| `exit` | Returns to the previous command mode. |

## Basic configuration

| Command | Purpose |
|---|---|
| `hostname SW1` | Changes the switch hostname. |
| `no ip domain-lookup` | Prevents mistyped commands from triggering DNS lookups. |
| `enable secret class` | Protects privileged EXEC mode with a lab password. |
| `service password-encryption` | Obscures supported plain-text passwords in the configuration. |
| `banner motd #AUTHORISED ACCESS ONLY#` | Displays a login warning banner. |
| `logging synchronous` | Prevents console messages from disrupting typed commands. |

## Management SVI

| Command | Purpose |
|---|---|
| `interface vlan 1` | Enters the default VLAN's switched virtual interface. |
| `ip address 192.168.10.2 255.255.255.0` | Assigns the management IPv4 address. |
| `no shutdown` | Administratively enables the interface. |

## Verification and switching

| Command | Purpose |
|---|---|
| `show ip interface brief` | Summarises interface addresses and states. |
| `show interfaces status` | Summarises access-port status, VLAN and speed. |
| `show interfaces fa0/2` | Displays detailed status and counters for FastEthernet0/2. |
| `show mac address-table dynamic` | Lists dynamically learned MAC addresses. |
| `show mac address-table interface fa0/1` | Filters the MAC table for one interface. |
| `clear mac address-table dynamic` | Clears dynamic MAC entries. |
| `show running-config` | Displays the active configuration. |
| `copy running-config startup-config` | Saves the active configuration. |

## PC commands

| Command | Purpose |
|---|---|
| `ipconfig /all` | Displays the PC's IPv4 and physical-address information. |
| `ping 192.168.10.20` | Tests reachability to PC-B. |
| `arp -a` | Displays the PC's ARP cache. |
| `arp -d 192.168.10.20` | Removes PC-B's ARP entry before simulation. |

