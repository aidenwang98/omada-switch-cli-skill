# DHCPV6 L2 Relay Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 60 DHCPV6 L2 Relay Commands

Location: extracted Word text lines 25506-25627

## Chapter Notes

- Use these commands only when the requested feature and target interface/VLAN/ring/session details are clear.

## ipv6 dhcp l2relay

### Purpose
The ipv6 dhcp l2relay command is used to enable DHCPV6 L2 Relay function globally. To disable DHCPV6 L2 Relay function, please use no ipv6 dhcp l2relay command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ipv6 dhcp l2relay
no ipv6 dhcp l2relay
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable DHCPV6 L2 Relay function globally:
Switch(config)# ipv6 dhcp l2relay
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ipv6 dhcp l2relay vlan

### Purpose
The ipv6 dhcp l2relay vlan command is used to enable DHCPV6 L2 relay in the specified VLAN. To disable DHCPV6 L2 Relay in the specific vlan, please use no ipv6 dhcp l2relay vlan command.

### Command Mode
Global Configuration Mode

### Syntax
```text
Ipv6 dhcp l2relay vlan vlan-id
no ipv6 dhcp l2relay vlan vlan-id
```

### Parameters
```text
vlan-id
Specify the vlan to be enabled with DHCPV6 L2 relay.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable DHCP L2 Relay for VLAN 1:
Switch(config)# ipv6 dhcp l2relay vlan 1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ipv6 dhcp l2relay forwarding-mode

### Purpose
The ipv6 dhcp l2relay forwarding-mode command is used to enable the relay mode of DHCPv6 L2Relay. By default, it is not enabled. After enabling, the device will encapsulate the original DHCPv6 packet within the Relay Message option (option 9) of a Relay-Forward type packet in the RFC 6221 LDRA format, and then insert other relay agent options (such as interface-id, remote-id). It will also receive Relay-Reply type packets from the server, decapsulate them, and forward them to the client. To disable this function, please use no ipv6 dhcp l2relay forwarding-mode command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ipv6 dhcp l2relay forwarding-mode
no ipv6 dhcp l2relay forwarding-mode
```

### Parameters
```text
None
```

### Default
By default, it is not enabled.

### Example
```text
Enable DHCPv6 L2Relay to perform relay forwarding in LDRA format.:
Switch(config)# ipv6 dhcp l2relay forwarding-mode
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ipv6 dhcp l2relay information interface-id

### Purpose
The ipv6 dhcp l2relay information interface-id command is used to configure a custom interface-id (option 18) field. After enabling option 18, DHCPv6 L2Relay relay packets will carry the user-defined interface-id field. To remove this configuration, please use no ipv6 dhcp l2relay information interface-id command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
ipv6 dhcp l2relay information interface-id interfaceId
no ipv6 dhcp l2relay information interface-id
```

### Parameters
```text
interfaceId
Custom interface-id, with a length not exceeding 64 bytes. Printable characters except double quotes and question marks are allowed. The default value is the unprefixed port number of the local port.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure a custom interface-id as "tplink.1" under port 1/0/1:
Switch(config)# )# interface gigabitEthernet 1/0/1
Switch(config-if)# ipv6 dhcp l2relay information interface-id
tplink.1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ipv6 dhcp l2relay information option18

### Purpose
The ipv6 dhcp l2relay information command is used to enable option18 support of a specified port in DHCPV6 L2Relay. To disable this function, please use no ipv6 dhcp l2relay information command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
ipv6 dhcp l2relay information option18
no ipv6 dhcp l2relay information option18
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable option18 support in DHCPV6 L2Relay for port 2:
Switch(config)#interface gigabitEthernet 1/0/2
Switch(config-if)# ipv6 dhcp l2relay information option18
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ipv6 dhcp l2relay information option37

### Purpose
The ipv6 dhcp l2relay information option37 command is used to enable option37 support of a specified port in DHCPV6 L2Relay. To disable this function, please use no ipv6 dhcp l2relay information option37 command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
ipv6 dhcp l2relay information option37
no ipv6 dhcp l2relay information option37
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable option37 support in DHCPV6 L2Relay for port 2:
Switch(config)#interface gigabitEthernet 1/0/2
Switch(config-if)# ipv6 dhcp l2relay information option37
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ipv6 dhcp l2relay information remote-id

### Purpose
The ipv6 dhcp l2relay information remote-id command is used to specify the custom remote ID when option 37 customization is enabled. To clear the remote ID, please use no ipv6 dhcp l2relay information remote-id command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
Ipv6 dhcp l2relay information remote-id remoteID
no ipv6 dhcp l2relay information remote-id
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
tplink192.168.0.3
for port 2:
Switch(config)#interface gigabitEthernet 1/0/2
Switch(config-if)# ipv6 dhcp l2relay information remote-id tplink 192.168.0.3
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## show ipv6 dhcp l2relay interface

### Purpose
The show ipv6 dhcp l2relay command is used to display the global status and Option 18\37 configuration of DHCPV6 L2Relay.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ipv6 dhcp l2relay interface
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the configuration of DHCPV6 L2Relay:
Switch(config)# show ipv6 dhcp l2relay interface
```

### Notes
- Permission requirement: None.
