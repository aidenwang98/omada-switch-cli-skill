# DHCP Relay Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 57 DHCP Relay Commands

Location: extracted Word text lines 25053-25254

## Chapter Notes

Official documentation states: A DHCP Relay agent is a Layer 3 device that forwards DHCP packets between clients and servers. DHCP Relay forward requests and replies between clients and servers when they are not on the same physical subnet.

- Use these commands only when the requested feature and target interface/VLAN/ring/session details are clear.

## service dhcp relay

### Purpose
The service dhcp relay command is used to enable DHCP Relay function globally. To disable DHCP Relay function, please use no service dhcp relay command.

### Command Mode
Global Configuration Mode

### Syntax
```text
service dhcp relay
no service dhcp relay
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable DHCP Relay function globally:
Switch(config)# service dhcp relay
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip dhcp relay hops

### Purpose
The ip dhcp relay hops command is used to specify the maximum hops (DHCP Relay agent) that the DHCP packets can be relayed. To restore the default value, please use no service dhcp relay hops command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip dhcp relay hops hops
no ip dhcp relay hops
```

### Parameters
```text
hops
Specify the maximum hops (DHCP Relay agent) that the DHCP packets can be relayed. If a packet
s hop count is more than the value you set here, the packet will be dropped. The valid value ranges from the 1 to 16, and the default value is 4.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the maximum number of relay hops as 6:
Switch(config)# ip dhcp relay hops 6
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip dhcp relay time

### Purpose
The ip dhcp relay time command is used to specify the DHCP relay time threshold. DHCP relay time is the time elapsed since client began address acquisition or renewal process. When the elapsed time of the DHCP packet is greater than the value set here, the DHCP packet will be dropped by the switch. To restore the default value, please use no service dhcp relay time command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip dhcp relay time time
no ip dhcp relay time
```

### Parameters
```text
time
Specify the DHCP relay time threshold. The valid value ranges from 1 to 65535. The default value is 0, which means the switch will not examine this field of the DHCP packets.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the DHCP Relay time as 30 seconds:
Switch(config)# ip dhcp relay time 30
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip helper-address

### Purpose
The ip helper-address command is used to add DHCP Server address to the Layer 3 interface. To delete the server address, please use no ip helper-address command. When the command includes a VRF name, it indicates that the server address belongs to that specific VRF instance.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip helper-adress {ip-address} [vrf-name]
no ip helper-address [ ip-address ] [vrf-name]
```

### Parameters
```text
vrf-name
vrf-name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Add DHCP Server address 192.168.2.1 to interface VLAN 1:
Switch(config)# interface vlan 1
Switch(config-if)# ip helper-address 192.168.2.1 vrf1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip dhcp relay information option

### Purpose
The ip dhcp relay information option command is used to enable option 82 support in DHCP Relay. To disable this function, please use no ip dhcp relay information option command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet/interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
ip dhcp relay information option
no ip dhcp relay information option
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable option 82 support in DHCP Relay for port 2:
Switch(config)#interface gigabitEthernet 1/0/2
Switch(config-if)#ip dhcp relay information option
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip dhcp relay information strategy

### Purpose
The ip dhcp relay information strategy command is used to specify the operation for the Option 82 field of the DHCP request packets from the Host. To restore to the default option, please use no ip dhcp relay information strategy command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
ip dhcp relay information strategy { drop | keep | replace }
no ip dhcp relay information strategy
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
Switch(config-if)# ip dhcp relay information strategy replace
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip dhcp relay information format

### Purpose
The ip dhcp relay information format command is used to select the format of option 82 sub-option value field. To restore to the default option, please use no ip dhcp relay information format command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
ip dhcp relay information format { normal | private }
no ip dhcp relay information format
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
Switch(config-if)#ip dhcp relay information format normal
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip dhcp relay information circuit-id

### Purpose
The ip dhcp relay information circuit-id command is used to specify the custom circuit ID when option 82 customization is enabled. To clear the circuit ID, please use no ip dhcp relay information circuit-id command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
ip dhcp relay information circuit-id circuitID
no ip dhcp relay information circuit-id
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
Switch(config-if)# ip dhcp relay information circuit-id TP-Link
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip dhcp relay information remote-id

### Purpose
The ip dhcp relay information remote-id command is used to specify the custom remote ID when option 82 customization is enabled. To clear the remote ID, please use no ip dhcp relay information remote-id command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
ip dhcp relay information remote-id remoteID
no ip dhcp relay information remote-id
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
Switch(config-if)# ip dhcp relay information remote-id TP-Link
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip dhcp relay default-interface

### Purpose
The ip dhcp relay default-interface command is used to configure default relay agent interface. When the switch works at DHCP VLAN Relay mode and there is no IP interface in the VLAN, the switch uses the IP of default relay agent interface to fill in the relay agent IP address field of DHCP packets. To delete the default relay agent interface use no ip dhcp relay default-interface.

### Command Mode
Not explicitly specified in the official documentation.

### Syntax
```text
ip dhcp relay default-interface
no ip dhcp relay default-interface
Command mode
Interface Configuration Mode
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure interface VLAN 1 as the default relay agent interface:
Switch(config)# interface vlan 1
Switch(config-if)# ip dhcp relay default-interface
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip dhcp relay vlan

### Purpose
The ip dhcp relay vlan command is used to add DHCP server address to specified VLAN. If there is an IP interface in the VLAN and it has configured a DHCP server address at the interface level, then the configuration at the interface level has higher priority. In this case, the DHCP server configured on the VLAN will not be used to forward the DHCP packets. To delete the DHCP server address use no ip dhcp relay vlan. When the command includes a VRF name, it indicates that the server address belongs to that specific VRF instance.

### Command Mode
Not explicitly specified in the official documentation.

### Syntax
```text
ip dhcp relay vlan {vid} helper-adress {ip-address} [vrf-name]
no ip dhcp relay vlan {vid} helper-address [ ip-address ] [vrf-name]
```

### Parameters
```text
vid
VLAN ID.
ip-address
DHCP Server address.
vrf-name
VRF instance name.
Command mode
Global Configuration Mode
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Add DHCP server address 192.168.2.1 to VLAN 1:
Switch(config)# ip dhcp relay vlan 1 helper-address 192.168.2.1 vrf1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## show ip dhcp relay

### Purpose
The show ip dhcp relay command is used to display the global status and Option 82 configuration of DHCP Relay.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip dhcp relay
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the configuration of DHCP Relay:
Switch(config)# show ip dhcp relay
```

### Notes
- Permission requirement: None.
