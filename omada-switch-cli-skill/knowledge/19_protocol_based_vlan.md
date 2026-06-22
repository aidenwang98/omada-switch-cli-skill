# Protocol-based VLAN Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 22 Protocol-based VLAN Commands

Location: extracted Word text lines 11834-11962

## Chapter Notes

Official documentation states: Protocol VLAN (Virtual Local Area Network) is the way to classify VLANs based on Protocols. A Protocol is relative to a single VLAN ID. The untagged packets and the priority-tagged packets matching the protocol template will be tagged with this VLAN ID.

- Use these commands only when the requested feature and target interface/VLAN/ring/session details are clear.

## protocol-vlan template

### Purpose
The protocol-vlan template command is used to create Protocol-based VLAN template. To delete Protocol-based VLAN template, please use no protocol-vlan template command.

### Command Mode
Global Configuration Mode

### Syntax
```text
For L2/L2+ switches:
protocol-vlan template name protocol-name frame { ether_2 ether-type type | snap ether-type type | llc dsap dsap_type ssap ssap_type }
no protocol-vlan template template-idx
For L3 switches:
protocol-vlan template name protocol-name frame { ether_2 ether-type type | snap ether-type type | llc dsap dsap_type ssap ssap_type }
no protocol-vlan template template-name
```

### Parameters
```text
protocol-name
Give a name for the Protocol-based VLAN Template , which contains 8 characters at most.
ether_2 ether-type type
Specify the Ethernet type.
snap ether-type type
Specify the Ethernet type.
llc dsap dsap_type ssap ssap_type
Specify the DSAP type and the SSAP type.
template-idx
The number of the Protocol-based VLAN Template. You can get the template corresponding to the number by the
show protocol-vlan template
command.
template-name
The name of the Protocol-base VLAN Template. You can get the template corresponding to the number by the
show protocol-vlan template
command.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Create a Protocol-based VLAN template named
whose Ethernet protocol type is 0x2024:
Switch(config)#protocol-vlan template name TP frame ether_2 ether-type 2024
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## protocol-vlan vlan

### Purpose
The protocol-vlan vlan command is used to create a Protocol-based VLAN entry. To delete a Protocol-based VLAN entry, please use no protocol-vlan vlan command.

### Command Mode
Global Configuration Mode

### Syntax
```text
For L2/L2+ switches:
protocol-vlan vlan vlan-id priority priority template template-idx
no protocol-vlan vlan group-idx
For L3 switches:
protocol-vlan vlan vlan-id priority priority template template-name
no protocol-vlan vlan group-name
```

### Parameters
```text
vlan-id
Specify IEEE 802.1Q VLAN ID, ranging from 1-4094.
priority
Specify the 802.1p priority for the packets that belong to the protocol VLAN, ranging from 0
7. The switch will determine the forwarding sequence according this value. The packets with larger value of 802.1p priority have the higher priority.
template-idx
The number of the Protocol-based VLAN Template. You can get the template corresponding to the number by the
show protocol-vlan template
command.
group-idx
The number of the Protocol-based VLAN entry. You can get the Protocol-based VLAN entry corresponding to the number by the
show protocol-vlan vlan
command.
template-name
The name of the Protocol-based VLAN Template. You can get the template corresponding to the number by the
show protocol-vlan template
command.
group-name
The name of the Protocol-based VLAN entry. You can get the Protocol-based VLAN entry corresponding to the number by the
show protocol-vlan vlan
command.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Create Protocol-based VLAN 2 and bind it with Protocol-based VLAN Template 3:
Switch(config)#protocol-vlan vlan 2 template 3
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## protocol-vlan group

### Purpose
The protocol-vlan command is used to add the port to a specified protocol group. To remove the port from this protocol group, please use no protocol-vlan group command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
For L2/L2+_ switches:
protocol-vlan group index
no protocol-vlan group index
For L3_ switches:
protocol-vlan group name
no protocol-vlan group name
```

### Parameters
```text
index
Specify the protocol group ID.
name
Specify the protocol group name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Add Gigabit Ethernet port 20 to protocol group 1:
Switch(config)#interface gigabitEthernet 1/0/20
Switch(config-if)#protocol-vlan group 1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## show protocol-vlan template

### Purpose
The show protocol-vlan template command is used to display the information of the Protocol-based VLAN templates.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show protocol-vlan template
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the information of the Protocol-based VLAN templates:
Switch(config)#show protocol-vlan template
```

### Notes
- Permission requirement: None.

## show protocol-vlan vlan

### Purpose
The show protocol-vlan vlan command is used to display the information about Protocol-based VLAN entry.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show protocol-vlan vlan
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display information of the Protocol-based VLAN entry:
Switch(config)#show protocol-vlan vlan
```

### Notes
- Permission requirement: None.
