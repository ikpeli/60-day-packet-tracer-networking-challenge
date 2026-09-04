# Sanitized Reference Configurations

This folder contains portfolio-safe build references for R1, SW1-ADMIN and SW2-REMOTE.

## Files

| File | Device |
|---|---|
| `r1-reference-config.txt` | Cisco 2911 router |
| `sw1-admin-reference-config.txt` | Local Cisco 2960 switch |
| `sw2-remote-reference-config.txt` | Remote Cisco 2960 switch |

## How to Use Them

- Replace every value enclosed in angle brackets before entering a configuration.
- These are learning references, not byte-for-byte exports of the Packet Tracer running configurations.
- Passwords, secrets and reversible password hashes are intentionally excluded.
- `service password-encryption` is basic obfuscation and must not be described as strong encryption.
- RSA 1024 is included for Packet Tracer compatibility; production key length must follow current platform and organizational policy.
