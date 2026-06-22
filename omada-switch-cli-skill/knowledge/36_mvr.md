# MVR Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 36 MVR Commands

Location: extracted Word text lines 16191-16422

## Chapter Notes

Official documentation states: MVR (Multicast VLAN Registration) allows a single multicast VLAN to be shared for multicast member ports in different VLANs in IPv4 network. In IGMP Snooping, if member ports are in different VLANs, a copy of the multicast streams is sent to each VLAN that has member ports. While MVR provides a dedicated multicast VLAN to forward multicast traffic over the Layer 2 network, to avoid duplication of multicast streams for clients in different VLANs. Clients can dynamically join or leave the multicast VLAN without interfering with their relationships in other VLANs.

- Use these commands only when the requested feature and target interface/VLAN/ring/session details are clear.
- Read the CLI prompt to determine the active view. `Switch(config)#` is Global Configuration Mode, while `Switch(config-if)#` is Interface Configuration Mode. The same command token, such as `mvr` or `no mvr`, can have different scope in different views.

## mvr (global)

### Purpose
The mvr command is used to enable MVR globally. To disable MVR, please use no mvr command.

### Command Mode
Global Configuration Mode

### Syntax
```text
mvr
no mvr
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable MVR globally:
Switch(config)# mvr
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## mvr group

### Purpose
The mvr group command is used to add multicast groups to MVR. To delete multicast groups from MVR, please use no mvr group command. You can configure up to 511 multicast groups.

### Command Mode
Global Configuration Mode

### Syntax
```text
mvr group ip-addr [count ]
no mvr group ip-addr [count ]
```

### Parameters
```text
ip-addr
The start IP address of the contiguous series of multicast groups.
count
The number of the multicast groups to be added to the MVR. Valid values are from 1 to 256, and the default value is 1.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Add multicast groups 225.1.2.3 -239.1.2.5 to MVR:
Switch (config)# mvr group 225.1.2.3 3
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## mvr mode

### Purpose
The mvr mode command is used to configure the MVR mode as compatible or dynamic. By default, it is compatible. To return to the default configuration, please use no mvr mode command.

### Command Mode
Global Configuration Mode

### Syntax
```text
mvr mode { compatible | dynamic }
no mvr mode
```

### Parameters
```text
compatible
In this mode, the switch does not forward report or leave messages from the hosts to the IGMP querier. So the IGMP querier cannot learn the multicast groups membership information from the switch. You have to statically configure the IGMP querier to transmit all the required multicast streams to the switch via the multicast VLAN.
dynamic
In this mode, after receiving report or leave messages from the hosts, the switch will forward them to the IGMP querier via the multicast VLAN (with appropriate translation of the VLAN ID). So the IGMP querier can learn the multicast groups membership information through the report and leave messages, and transmit the multicast streams to the switch via the multicast VLAN according to the multicast forwarding table.
```

### Default
By default, it is compatible.

### Example
```text
Configure the MVR mode as dynamic:
Switch(config)# mvr mode dynamic
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## mvr querytime

### Purpose
The mvr querytime command is used to configure the maximum time to wait for IGMP report on a receiver port before removing the port from multicast group membership. To return to the default configuration, please use no mvr querytime command.

### Command Mode
Global Configuration Mode

### Syntax
```text
mvr querytime time
no mvr querytime
```

### Parameters
```text
time
The query response time. Valid values are from 1 to100 tenths of a second, and the default value is 5 tenths of a second.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the query response time of MVR as 1 second, that is 10 tenths of a second:
Switch(config)# mvr querytime 10
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## mvr vlan

### Purpose
The mvr vlan command is used to specify the multicast VLAN. By default, it is VLAN 1. To return to the default configuration, please use no mvr vlan command.

### Command Mode
Global Configuration Mode

### Syntax
```text
mvr vlan vlan-id
no mvr vlan
```

### Parameters
```text
vlan-id
The ID of the multicast VLAN. Valid values are from 1 to 4094.
```

### Default
By default, it is VLAN 1.

### Example
```text
Configure the multicast VLAN as VLAN 10:
Switch(config)# mvr vlan 10
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## mvr (interface)

### Purpose
This command is used to enable MVR for specific interfaces. To disable MVR for the interfaces, please use no mvr command. By default, it is disabled.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet)

### Syntax
```text
mvr
no mvr
```

### Parameters
No parameters.

### Default
By default, it is disabled.

### Example
```text
Enable MVR for port 1/0/1:
Switch(config)# interface gigabitEthernet 1/0/1
Switch(config-if)#mvr
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## mvr type

### Purpose
The mvr type command is used to configure the MVR port type as receiver or source. By default, the port is a non-MVR port. If you attempt to configure a non-MVR port with MVR characteristics, the operation fails. To return to the default configuration, please use no mvr type command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet)

### Syntax
```text
mvr type { source | receiver }
no mvr type
```

### Parameters
```text
source
Configure the uplink ports that receive and send multicast data on the multicast VLAN as source ports. Source ports should belong to the multicast VLAN.
receiver
Configure the ports that are connecting to the hosts as receiver ports. A receiver port can only belong to one VLAN, and cannot belong to the multicast VLAN.
```

### Default
By default, the port is a non-MVR port.

### Example
```text
Configure the port 1/0/3 as a receiver port:
Switch(config)# interface gigabitEthernet 1/0/3
Switch(config-if)#mvr type receiver
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## mvr immediate

### Purpose
The mvr immediate command is used to enable the Fast Leave feature of MVR for specified port. To disable the Fast Leave feature of MVR for specific ports, please use no mvr immediate command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet)

### Syntax
```text
mvr immediate
no mvr immediate
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the Fast Leave feature of MVR for port 1/0/3:
Switch(config)# interface gigabitEthernet 1/0/3
Switch(config-if)#mvr immediate
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- User guidelines: Only receiver ports support Fast Leave. Before enabling Fast Leave for a port, make sure there is only a single receiver device connecting to the port.

## mvr vlan (group)

### Purpose
This command is used to statically add ports to an MVR group. Then the ports can receive multicast traffic sent to the IP multicast address via the multicast VLAN.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet)

### Syntax
```text
mvr vlan vlan-id group ip-addr
```

### Parameters
```text
vlan-id
The ID of the multicast VLAN. Valid values are from 1 to 4094.
ip-addr
The IP address of the multicast group.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Add port 1/0/3 to MVR group 225.1.2.3 statically. The multicast VLAN is VLAN 10:
Switch(config)# interface gigabitEthernet 1/0/3
Switch(config-if)#mvr vlan 10 group 225.1.2.3
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- User guidelines: This command applies to only receiver ports. The switch adds or removes the receiver ports to the corresponding multicast groups by snooping the report and leave messages from the hosts. You can also statically add a receiver port to an MVR group.

## mvr vlan (rule)

### Purpose
This command is used to change the VLAN of the receiver port, which will remove the receiver port from the original VLAN..

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet)

### Syntax
```text
mvr vlan vlan-id rule [untagged |tagged ]
```

### Parameters
```text
vlan-id
New VLAN ID, ranging from 1 to 4094.
untagged
Add a new VLAN in the untagged way.
tagged
Add a new VLAN in the tagged way.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Change the VLAN of port 1/0/3 to 100 in the untagged way:
Switch(config)# interface gigabitEthernet 1/0/3
Switch(config-if)#mvr vlan 100 rule untagged
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## mvr mode dynamic auto-enable

### Purpose
The mvr mode dynamic auto-enable command is used to enable automatic addition of source ports to all multicast groups. To disable this function, please use no mvr mode dynamic auto-enable command.

### Command Mode
Global Configuration Mode

### Syntax
```text
mvr mode dynamic auto-enable
no mvr mode dynamic auto-enable
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable automatic addition of source ports to all multicast groups:
Switch(config)#mvr mode dynamic auto-enable
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## show mvr

### Purpose
The show mvr command is used to display the global configuration of MVR.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show mvr
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the global configuration of mvr:
Switch# show mvr
```

### Notes
- Permission requirement: None.

## show mvr interface

### Purpose
The show mvr interface command is used to display the MVR configurations of specific interfaces.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show mvr interface gigabitEthernet [port | port-list ]
```

### Parameters
```text
port
The Ethernet port number.
port-list
The list of Ethernet ports.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the MVR configuration of port 1/0/3:
Switch# show mvr interface gigabitEthernet 1/0/3
```

### Notes
- Permission requirement: None.

## show mvr members

### Purpose
The show mvr members command is used to display the membership information of all MVR groups or the specified MVR group.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show mvr members [ ip-addr ] [ status active | inactive ]
```

### Parameters
```text
ip-addr
The multicast IP address of the MVR group.
active
Display all active MVR groups.
inactive
Display all inactive MVR groups.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the membership information of all MVR groups:
Switch# show mvr members
```

### Notes
- Permission requirement: None.
