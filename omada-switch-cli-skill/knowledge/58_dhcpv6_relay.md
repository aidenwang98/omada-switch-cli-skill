# DHCPV6 Relay Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 58 DHCPV6 Relay Commands

Location: extracted Word text lines 25255-25360

## Chapter Notes

Official documentation states: A DHCPV6 Relay agent is a Layer 3 device that forwards DHCPV6 packets between clients and servers. DHCPV6 Relay forward requests and replies between clients and servers when they are not on the same physical subnet.

- Use these commands only when the requested feature and target interface/VLAN/ring/session details are clear.

## ipv6 dhcp relay

### Purpose
The ipv6 dhcp relay command is used to enable DHCPV6 Relay function globally. To disable DHCPV6 Relay function, please use no ipv6 dhcp relay command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ipv6 dhcp relay
no ipv6 dhcp relay
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable DHCPV6 Relay function globally:
Switch(config)# ipv6 dhcp relay
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ipv6 dhcp relay vlan 1 helper-address

### Purpose
The ipv6 dhcp relay vlan 1 helper-address command is used to add DHCPV6 Server address to the Layer 3 interface. To delete the server address, please use no ipv6 dhcp relay vlan 1 helper-address command. When the command includes a VRF name, it indicates that the server address belongs to that specific VRF instance.

### Command Mode
Interface Configuration Mode

### Syntax
```text
Ipv6 dhcp relay vlan {vlan-id} helper-adress {ip-address} [vrf-name]
no ipv6 dhcp relay vlan {vlan-id} helper-address [ ip-address ]
```

### Parameters
```text
vlan-id
VLAN ID.
ip-address
DHCPv6 Server address.
vrf-name
VRF instance name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Add DHCPV6 Server address 2019:2020::21D:FFF:FE61:2005 to interface VLAN 1:
Switch(config)# ipv6 dhcp relay vlan 1 helper-address 2019:2020::21D:FFF:FE61:2005 vrf1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ipv6 dhcp relay information option 18

### Purpose
The ipv6 dhcp relay information option18 command is used to enable option 18 support of a specified port in DHCPV6 Relay. To disable this function, please use no ipv6 dhcp relay information option18 command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
ipv6 dhcp relay information option18
no ipv6 dhcp relay information option18
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable option18 support in DHCPV6 Relay for port 2:
Switch(config)#interface gigabitEthernet 1/0/2
Switch(config-if)# ipv6 dhcp relay information option18
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ipv6 dhcp relay information option37

### Purpose
The ipv6 dhcp relay information option37 command is used to enable option37 support of a specified port in DHCPV6 Relay. To disable this function, please use no ipv6 dhcp relay information option37 command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
ipv6 dhcp relay information option37
no ipv6 dhcp relay information option37
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable option37 support in DHCPV6 Relay for port 2:
Switch(config)#interface gigabitEthernet 1/0/2
Switch(config-if)# ipv6 dhcp relay information option37
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ipv6 dhcp relay information remote-id

### Purpose
The ipv6 dhcp relay information remote-id command is used to specify the custom remote ID when option37 customization is enabled. To clear the remote ID, please use no ipv6 dhcp relay information remote-id command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
Ipv6 dhcp relay information remote-id remoteID
no ipv6 dhcp relay information remote-id
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
Switch(config-if)# ipv6 dhcp relay information remote-id tplink 192.168.0.
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## show ipv6 dhcp relay

### Purpose
The show ipv6 dhcp relay command is used to display the global status and Option 18\37 configuration of DHCPV6 Relay.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ipv6 dhcp relay
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the configuration of DHCPV6 Relay:
Switch(config)# show ipv6 dhcp relay
```

### Notes
- Permission requirement: None.

## show ipv6 dhcp relay counters

### Purpose
The show ipv6 dhcp relay counters command is used to display the packet counter of the DHCPV6 relay.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ipv6 dhcp relay counters
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the packet counter of the DHCPV6 relay:
Switch# show ipv6 dhcp relay counters
```

### Notes
- Permission requirement: None.
