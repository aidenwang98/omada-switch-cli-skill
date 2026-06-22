# Etherchannel Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 17 Etherchannel Commands

Location: official printed page 177-184; actual PDF page 223-230

## Chapter Notes

Official documentation states: Etherchannel Commands are used to configure LAG and LACP function.

LAG (Link Aggregation Group) combines multiple ports into a high-bandwidth data path; the LAG bandwidth is the sum of its member-port bandwidth.

LACP (Link Aggregation Control Protocol), defined in IEEE802.3ad, implements dynamic link aggregation and disaggregation by exchanging LACP packets with the peer device.

In this knowledge base:
- `EtherChannel Group`, `channel-group`, and `port-channel` are all interpreted in the official chapter context as link-aggregation-related objects.
- In `channel-group num`, `num` is the EtherChannel Group number. In practical configuration, it can be understood as the LAG ID / aggregation group ID.
- `mode on` means static LAG.
- `mode active` / `mode passive` mean LACP modes.

## channel-group

### Purpose
Add a port to an EtherChannel Group and configure its mode; use `no channel-group` to remove the port from the EtherChannel Group.

### Command Mode
Interface Configuration Mode (interface fastEthernet | gigabitEthernet | two-gigabitEthernet | ten-gigabitEthernet / interface range fastEthernet | gigabitEthernet | two-gigabitEthernet | ten-gigabitEthernet)

### Syntax
```text
channel-group num mode { on | active | passive }
no channel-group
```

### Parameters
- `num`: EtherChannel Group number. L2/L2+ switches range: 1 to 8; L3 access switches range: 1 to 64; L3 aggregation switches range: 1 to 120. In practical configuration, it can be understood as the LAG ID / aggregation group ID.
- `on`: Enable the static LAG.
- `active`: Enable the active LACP mode.
- `passive`: Enable the passive LACP mode.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config)# interface range gigabitEthernet 1/0/2-4
Switch(config-if-range)# channel-group 1 mode on
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- `mode on` is static LAG; `mode active` and `mode passive` are LACP modes.

## port-channel load-balance

### Purpose
Configure the Aggregate Arithmetic of the LAG; use `no port-channel load-balance` to restore the default configuration.

### Command Mode
Global Configuration Mode

### Syntax
```text
port-channel load-balance { src-mac | dst-mac | src-dst-mac | src-ip | dst-ip | src-dst-ip }
no port-channel load-balance
```

### Parameters
- `src-mac`: based on packets' source MAC address.
- `dst-mac`: based on packets' destination MAC address.
- `src-dst-mac`: based on packets' source and destination MAC addresses.
- `src-ip`: based on packets' source IP address.
- `dst-ip`: based on packets' destination IP address.
- `src-dst-ip`: based on packets' source and destination IP addresses.

### Default
`src-dst-mac`.

### Example
```text
Switch(config)# port-channel load-balance src-dst-ip
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## lacp system-priority

### Purpose
Configure the global LACP system priority; use `no lacp system-priority` to restore the default configuration.

### Command Mode
Global Configuration Mode

### Syntax
```text
lacp system-priority pri
no lacp system-priority
```

### Parameters
- `pri`: system priority, range: 0 to 65535.

### Default
32768.

### Example
```text
Switch(config)# lacp system-priority 1024
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## lacp port-priority

### Purpose
Configure LACP port priority for specified ports; use `no lacp port-priority` to restore the default configuration.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet)

### Syntax
```text
lacp port-priority pri
no lacp port-priority
```

### Parameters
- `pri`: port priority, range: 0 to 65535.

### Default
32768.

### Example
```text
Switch(config)# interface range gigabitEthernet 1/0/1-3
Switch(config-if-range)# lacp port-priority 1024
Switch(config)# interface gigabitEthernet 1/0/4
Switch(config-if)# lacp port-priority 2048
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## lacp timeout

### Purpose
Modify the LACP keepalive packet timeout period for all ports or selected ports; use `no lacp timeout` to restore the default value.

### Command Mode
Interface Configuration Mode

### Syntax
```text
lacp timeout { long | short }
no lacp timeout
```

### Parameters
- `long | short`: LACP keepalive packet timeout control value for all or selected ports on this device.`long` means long timeout, and `short` means short timeout.

### Default
long.

### Example
```text
Switch(config)# interface gigabitEthernet 1/0/1
Switch(config-if)# lacp timeout short
Switch(config)# interface gigabitEthernet 1/0/1
Switch(config-if)# no lacp timeout
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Official documentation states: For this configuration to affect the keepalive packet transmission interval of the peer device, at least one of the two aggregation devices must run in LACP Active mode.
- This option can only be configured on ports with LACP enabled, and it appears in the corresponding interface section of `show running-config`.
- If a port is removed from an LACP group after the timeout type is configured, or is converted to a static LAG member port, its timeout type returns to the default value.
- If configured in batch through `interface range`, the setting only applies to ports with LACP enabled.
- This option cannot be configured in Port-channel view; attempting to do so causes an error.

## show etherchannel

### Purpose
Display EtherChannel information.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show etherchannel [ channel-group-num ] { detail | summary }
```

### Parameters
- `channel-group-num`: EtherChannel Group number. L2/L2+ switches range: 1 to 8; L3 access switches range: 1 to 64; L3 aggregation switches range: 1 to 120. Defaults to empty, display information for all EtherChannel Groups.
- `detail`: detailed EtherChannel information.
- `summary`: summary EtherChannel information.

### Default
`channel-group-num` defaults to empty, display information for all EtherChannel Groups.

### Example
```text
Switch(config)# show etherchannel 1 detail
```

### Notes
- Permission requirement: None.

## show etherchannel load-balance

### Purpose
Display the Aggregate Arithmetic of the LAG.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show etherchannel load-balance
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config)# show etherchannel load-balance
```

### Notes
- Permission requirement: None.

## show lacp

### Purpose
Display LACP information for the specified EtherChannel Group.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show lacp [ channel-group-num ] { internal | neighbor }
```

### Parameters
- `channel-group-num`: EtherChannel Group number. L2/L2+ switches range: 1 to 8; L3 access switches range: 1 to 64; L3 aggregation switches range: 1 to 120. Defaults to empty, display information for all LACP groups.
- `internal`: internal LACP information.
- `neighbor`: neighbor LACP information.

### Default
`channel-group-num` defaults to empty, display information for all LACP groups.

### Example
```text
Switch(config)# show lacp 1 internal
```

### Notes
- Permission requirement: None.

## show lacp sys-id

### Purpose
Display the global LACP system priority.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show lacp sys-id
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config)# show lacp sys-id
```

### Notes
- Permission requirement: None.
