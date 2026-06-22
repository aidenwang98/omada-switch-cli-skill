# Private VLAN Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 23 Private VLAN Commands (Only for Certain Devices)

Location: extracted Word text lines 11963-12111

## Chapter Notes

Official documentation states: Note: Private VLAN commands are only available on certain devices. Private VLANs are configured specially for saving VLAN resource of uplink devices and decreasing broadcast.

- This chapter is marked `Only for Certain Devices`; treat all configuration commands as model-dependent.
- When a command or note is device-specific in the official text, mention model and firmware dependency before recommending it.

## private-vlan primary

### Purpose
The private-vlan primary command is used to configure the designated VLAN as the primary VLAN of the Private VLAN. To remove the primary VLAN property pf the current VLAN, please use no private-vlan primary command.

### Command Mode
VLAN Configuration Mode (VLAN)

### Syntax
```text
private-vlan primary
no private-vlan primary
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the VLAN 3 as the primary VLAN of the private VLAN:
Switch(config)#vlan 3
Switch(config-vlan)#private-vlan primary
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## private-vlan community

### Purpose
The private-vlan community command is used to configure the designated VLAN as the community VLAN of the Private VLAN. To remove the community VLAN property pf the current VLAN, please use no private-vlan community command.

### Command Mode
VLAN Configuration Mode (VLAN)

### Syntax
```text
private-vlan community
no private-vlan community
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the VLAN 4 as the community VLAN of the private VLAN:
Switch(config)#vlan 4
Switch(config-vlan)#private-vlan community
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## private-vlan isolated

### Purpose
The private-vlan isolated command is used to configure the designated VLAN as the isolated VLAN of the Private VLAN. To remove the isolated VLAN property pf the current VLAN, please use no private-vlan isolated command.

### Command Mode
VLAN Configuration Mode (VLAN)

### Syntax
```text
private-vlan isolated
no private-vlan isolated
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the VLAN 3 as the isolated VLAN of the private VLAN:
Switch(config)#vlan 3
Switch(config-vlan)#private-vlan isolated
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## private-vlan association

### Purpose
The private-vlan association command is used to associate primary VLAN with secondary VLAN. To exterminate the currently association, please use no private-vlan association command.

### Command Mode
VLAN Configuration Mode (VLAN)

### Syntax
```text
private-vlan association vlan_list
no private-vlan association vlan_list
```

### Parameters
```text
vlan_list
Secondary VLAN ID, ranging from 2 to 4094.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Associate primary VLAN 3 with community VLAN 4 as a private VLAN:
Switch(config)#vlan 3
Switch(config-vlan)#private-vlan association 4
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## switchport private-vlan

### Purpose
The switchport private-vlan command is used to configure the private VLAN mode for the switchport. To invalid the configuration, please use no switchport private-vlan command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
switchport private-vlan { promiscuous | host }
no switchport private-vlan
```

### Parameters
```text
promiscuous | host
configure the private VLAN mode for the switchport.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure Gigabit Ethernet port 3 as
host
Switch(config)#interface gigabitEthernet 1/0/3
Switch(config-if)#switchport private-vlan host
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## switchport private-vlan host-association

### Purpose
The switchport private-vlan host-association command is used to add host type port to private VLAN. To remove the port from Private VLAN, please use no switchport private-vlan host-association command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
switchport private-vlan host-association primary_vlan_id secondary_vlan_id vlantype
no switchport private-vlan host-association
```

### Parameters
```text
primary-vlan-id
Primary VLAN ID, ranging from 2 to 4094.
secondary-vlan-id
Secondary VLAN ID, ranging from 2 to 4094.
vlantype
Specify the type of the secondary VLAN, either community or isolated.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure host type Gigabit Ethernet port 1/0/3 as a member of primary VLAN 3 and secondary VLAN 4, with the type of VLAN 4 as community:
Switch(config)#interface gigabitEthernet 1/0/3
Switch(config-if)#switchport private-vlan host-association 3 4 community
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## switchport private-vlan mapping

### Purpose
The switchport private-vlan mapping command is used to add promiscuous type port to private VLAN. To remove the port from Private VLAN, please use no switchport private-vlan mapping command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
switchport private-vlan mapping primary_vlan_id secondary_vlan_id
no switchport private-vlan mapping
```

### Parameters
```text
primary-vlan-id
Primary VLAN ID, ranging from 2 to 4094.
secondary-vlan-id
Secondary VLAN ID, ranging from 2 to 4094.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure promiscuous type Gigabit Ethernet port 1/0/3 as a member of primary VLAN 3 and secondary VLAN 4:
Switch(config)#interface gigabitEthernet 1/0/3
Switch(config-if)#switchport private-vlan mapping 3 4
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## show vlan private-vlan

### Purpose
The show vlan private-vlan command is used to display the Private VLAN configuration information of the switch.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show vlan private-vlan
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the configuration information of all Private VLAN:
Switch(config)#show vlan private-vlan
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## show vlan private-vlan interface

### Purpose
The show vlan private-vlan interface command is used to display the Private VLAN configuration information of the specified port(s).

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show vlan private-vlan interface [fastEthernet port | gigabitEthernet port | ten-gigabitEthernet port | port-channel port-channel-id ]
```

### Parameters
```text
port
The port number.
port-channel-id
The ID of the port channel.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the configuration information of all the Ethernet ports:
Switch(config)#show vlan private-vlan interface
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.
