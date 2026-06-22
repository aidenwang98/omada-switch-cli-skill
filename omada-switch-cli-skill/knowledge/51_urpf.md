# URPF Configuration Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 51 URPF Configuration Commands (Only for Certain Devices)

Location: extracted Word text lines 23591-23622

## Chapter Notes

Official documentation states: Unicast Reverse Path Forwarding (URPF) aims to prevent network attacks based on source IP address spoofing. To safeguard against forged IP packet attacks on the network, at the network ingress point, the origin of IP packets is verified. If the source is suspicious, the packet is dropped directly; if it passes the URPF check, the IP packet is allowed to enter.

- This chapter is marked `Only for Certain Devices`; treat all configuration commands as model-dependent.

## urpf

### Purpose
This command is used to enable or disable the URPF feature. When enabled, it retrieves the previously configured filtering mode for security checks. If no mode was previously configured, it performs security checks based on the default strict-vlan filtering mode. Disabling the URPF feature will not modify the set filtering mode for when URPF was disabled.

### Command Mode
Global Configuration Mode

### Syntax
```text
urpf { enable| disable }
```

### Parameters
```text
None
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the URPF feature on the switch:
Switch(config)# urpf enable
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## urpf mode

### Purpose
This command is used to configure the URPF filter mode.

### Command Mode
Global Configuration Mode

### Syntax
```text
urpf mode { strict-vlan | strict-port | loose }
```

### Parameters
```text
strict-vlan: Filter the packets whose IP or VLAN do not meet the requirements
strict-port: Filter the packets whose IP or port do not meet the requirements
loose: Filter the packets whose IP does not meet the requirements
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the URPF feature on the switch:
Switch(config)# urpf mode strict-vlan
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.
