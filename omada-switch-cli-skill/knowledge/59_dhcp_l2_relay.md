# DHCP L2 Relay Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 59 DHCP L2 Relay Commands

Location: extracted Word text lines 25361-25505

## Chapter Notes

- Use these commands only when the requested feature and target interface/VLAN/ring/session details are clear.

## ip dhcp l2relay

### Purpose
The ip dhcp l2relay command is used to enable DHCP L2 Relay function globally. To disable DHCP L2 Relay function, please use no ip dhcp l2relay command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip dhcp l2relay
no ip dhcp l2relay
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable DHCP L2 Relay function globally:
Switch(config)# ip dhcp l2relay
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip dhcp l2relay vlan

### Purpose
The ip dhcp l2relay vlan command is used to enable DHCP L2 relay in the specified VLAN. To disable DHCP L2 Relay in the specific vlan, please use no ip dhcp l2relay vlan command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip dhcp l2relay vlan vlan-range
no ip dhcp l2relay vlan vlan-range
```

### Parameters
```text
vlan-range
Specify the vlan to be enabled with DHCP L2 relay.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable DHCP L2 Relay for VLAN 2:
Switch(config)# ip dhcp l2relay vlan 2
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip dhcp l2relay information option

### Purpose
The ip dhcp l2relay information option command is used to enable option82 support in DHCP Relay. To disable this function, please use no ip dhcp l2relay information option command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
ip dhcp l2relay information option
no ip dhcp l2relay information option
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable option82 support in DHCP Relay for port 2:
Switch(config)#interface gigabitEthernet 1/0/2
Switch(config-if)# ip dhcp l2relay information option
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip dhcp l2relay information strategy

### Purpose
The ip dhcp l2relay information strategy command is used to specify the operation for the Option 82 field of the DHCP request packets from the Host. To restore to the default option, please use no ip dhcp l2relay information strategy command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
ip dhcp l2relay information strategy { drop | keep | replace }
no ip dhcp l2relay information strategy
```

### Parameters
```text
drop | keep | replace
The operations for Option 82 field of the DHCP request packets from the Host. The default operation is keep.
drop: Discard the packet with the Option 82 field.
keep: Keep the Option 82 field in the packet.
replace: Replace the option 82 field with the system option defined by the switch.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Specify the option 82 strategy as replace to replace the Option 82 field with the local parameter on receiving the DHCP request packet for port 2:
Switch(config)#interface gigabitEthernet 1/0/2
Switch(config-if)# ip dhcp l2relay information strategy replace
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip dhcp l2relay information format

### Purpose
The ip dhcp l2relay information format command is used to select the format of option 82 sub-option value field. To restore to the default option, please use no ip dhcp l2relay information format command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
ip dhcp l2relay information format { normal | private }
no ip dhcp l2relay information format
```

### Parameters
```text
normal | private
The format type of option 82 sub-option value field.
normal: Indicates that the format of sub-option value field is TLV (type-length-value).
private: Indicates that the format of sub-option value field is the value you configure for the related sub-option.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Select the format of option 82 sub-option value field as TLV (type-length-value) for port 2:
Switch(config)#interface gigabitEthernet 1/0/2
Switch(config-if)#ip dhcp l2relay information format normal
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip dhcp l2relay information circuit-id

### Purpose
The ip dhcp l2relay information circuit-id command is used to specify the custom circuit ID when option 82 customization is enabled. To clear the circuit ID, please use no ip dhcp l2relay information circuit-id command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
ip dhcp l2relay information circuit-id circuitID
no ip dhcp l2relay information circuit-id
```

### Parameters
```text
circuitID
Specify the circuit ID, ranging from 1 to 64 characters.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Specify the circuit ID as
TP-Link
for port 2:
Switch(config)#interface gigabitEthernet 1/0/2
Switch(config-if)# ip dhcp l2relay information circuit-id TP-Link
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip dhcp l2relay information remote-id

### Purpose
The ip dhcp l2relay information remote-id command is used to specify the custom remote ID when option 82 customization is enabled. To clear the remote ID, please use no ip dhcp l2relay information remote-id command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
ip dhcp l2relay information remote-id remoteID
no ip dhcp l2relay information remote-id
```

### Parameters
```text
remoteID
Specify the remote ID, ranging from 1 to 64 characters.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Specify the remote ID as
TP-Link
for port 2:
Switch(config)#interface gigabitEthernet 1/0/2
Switch(config-if)# ip dhcp l2relay information remote-id TP-Link
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## show ip dhcp l2relay

### Purpose
The show ip dhcp l2relay command is used to display the global status and Option 82 configuration of DHCP Relay.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip dhcp l2relay
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the configuration of DHCP Relay:
Switch(config)# show ip dhcp l2relay
```

### Notes
- Permission requirement: None.

## show ip dhcp l2relay interface

### Purpose
The show ip dhcp l2relay interface command is used to display the DHCP L2 Relay status for the ports.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip dhcp l2relay interface [ gigabitEthernet port | port-channel port-channel-id ]
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the DHCP L2 Relay configuration of port 1/0/2:
Switch(config)# show ip dhcp l2relay interface gigabitEthernet 1/0/2
```

### Notes
- Permission requirement: None.
