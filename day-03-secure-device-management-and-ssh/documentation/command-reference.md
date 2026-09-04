# Command Reference and Explanations

## CLI Navigation

| Command | Mode | What it does |
|---|---|---|
| `enable` | User EXEC | Enters privileged EXEC mode so verification and configuration commands can be used. |
| `configure terminal` | Privileged EXEC | Enters global configuration mode. |
| `exit` | Any submode | Moves back one configuration level or closes a remote session. |
| `end` | Configuration mode | Returns directly to privileged EXEC mode. |
| `do show ...` | Configuration mode | Runs a privileged `show` command without leaving configuration mode. |

## Device Identity and Basic Security

| Command | What it does |
|---|---|
| `hostname NAME` | Assigns the device name used in prompts and as part of the RSA key identity. |
| `no ip domain-lookup` | Prevents IOS from trying DNS resolution when a command is mistyped. |
| `enable secret VALUE` | Protects privileged EXEC mode with a hashed secret and is preferred to `enable password`. |
| `service password-encryption` | Obscures supported plain-text passwords in the configuration using reversible Type 7 encoding. |
| `username netadmin privilege 15 secret VALUE` | Creates a local administrator whose secret is used by `login local`. |
| `banner motd ^CTEXT^C` | Displays an access-warning message; `^C` is the selected delimiter. |
| `description TEXT` | Documents an interface's purpose without changing forwarding behaviour. |
| `copy running-config startup-config` | Saves the active RAM configuration to NVRAM for the next reload. |

## Router Interfaces and Routing

| Command | What it does |
|---|---|
| `interface GigabitEthernet0/0` | Enters configuration mode for the selected physical interface. |
| `ip address ADDRESS MASK` | Assigns an IPv4 address and subnet mask to a Layer 3 interface. |
| `no shutdown` | Administratively enables an interface. |
| `shutdown` | Administratively disables an interface for maintenance or fault testing. |
| `show ip interface brief` | Summarizes interface addresses and the physical/status protocol state. |
| `show ip route` | Displays the routing table, including connected and local routes. |

`up/up` means the physical interface and its line protocol are operational. `administratively down/down` means the interface is disabled by configuration.

## VLANs and Switch Management

| Command | What it does |
|---|---|
| `vlan 10` | Creates VLAN 10 or opens its VLAN configuration context. |
| `name ADMIN-MGMT` | Assigns a readable name to the current VLAN. |
| `switchport mode access` | Forces the selected port to operate as a non-trunking access port. |
| `switchport access vlan 10` | Places untagged frames entering that access port into VLAN 10. |
| `interface Vlan10` | Selects the SVI that gives the Layer 2 switch a management IP in VLAN 10. |
| `ip default-gateway 192.168.10.1` | Sets the next hop for switch-originated management traffic destined outside the local subnet. |
| `show vlan brief` | Displays VLANs, status and access-port membership. |

The management IP belongs to an SVI, not to a Layer 2 physical switchport.

## Console and Session Controls

| Command | What it does |
|---|---|
| `line console 0` | Selects the local console line. |
| `password VALUE` | Sets the line password; `login` is required to enforce it. |
| `login` | Requires the configured line password. |
| `logging synchronous` | Reprints interrupted input after console messages so the command line stays readable. |
| `exec-timeout 5 0` | Closes an idle EXEC session after five minutes and zero seconds. |

## SSH and VTY Security

| Command | What it does |
|---|---|
| `ip domain-name portfolio.local` | Supplies the domain portion needed with the hostname before RSA key generation. |
| `crypto key generate rsa modulus 1024` | Creates the RSA key pair required by the IOS SSH server in this Packet Tracer lab. |
| `ip ssh version 2` | Restricts the device to SSH version 2. |
| `show ip ssh` | Shows whether SSH is enabled and which version and timers are active. |
| `line vty 0 15` | Selects the virtual terminal lines used by remote sessions. |
| `login local` | Authenticates remote users against the local username database. |
| `transport input ssh` | Accepts SSH and rejects Telnet on the selected VTY lines. |
| `transport input telnet` | Accepts insecure Telnet; used only as a controlled fault in this lab. |

SSH configuration depends on a hostname, domain name, local user, RSA key pair, SSH version and correct VTY settings.

## ADMIN-PC Tests

| Command | What it proves |
|---|---|
| `ipconfig` | Confirms the host IP address, mask and default gateway. |
| `ping ADDRESS` | Tests ICMP/IP reachability, but does not prove that SSH is available. |
| `ssh -l netadmin ADDRESS` | Attempts encrypted remote login using the specified local username. |
| `telnet ADDRESS` | Attempts unencrypted remote access; it should fail after SSH-only hardening. |

## Useful Verification Commands

| Command | Evidence to inspect |
|---|---|
| `show running-config` | Active device configuration in RAM |
| `show startup-config` | Saved configuration loaded at boot |
| `show interfaces description` | Interface state and documentation |
| `show arp` | IPv4-to-MAC address mappings |
| `show mac address-table` | Switch MAC learning and forwarding-port associations |
| `show users` | Active management sessions where supported |
| `show line` | Console and VTY line state and timeout information |
