# MAC-based VLAN Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 21 MAC-based VLAN Commands

Location: extracted Word text lines 11733-11833

## Chapter Notes

Official documentation states: MAC VLAN (Virtual Local Area Network) is the way to classify the VLANs based on MAC Address. A MAC address is relative to a single VLAN ID. The untagged packets and the priority-tagged packets coming from the MAC address will be tagged with this VLAN ID.

- Use these commands only when the requested feature and target interface/VLAN/ring/session details are clear.

## mac-vlan mac-address

### Purpose
The mac-vlan mac-address command is used to create a MAC-based VLAN entry. To delete a MAC-based VLAN entry, please use the no mac-vlan mac-address command.

### Command Mode
Global Configuration Mode

### Syntax
```text
mac-vlan mac-address mac-addr vlan vlan-id [description descript]
no mac-vlan mac-address mac-addr
```

### Parameters
```text
mac-addr
MAC address, in the format of XX:XX:XX:XX:XX:XX.
vlan-id
Specify IEEE 802.1Q VLAN ID, ranging from 1 to 4094.
descript
Give a description to the MAC address for identification, which contains 8 characters at most.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Create VLAN 2 with the MAC address 00:11:11:01:01:12 and the name
Switch(config)#mac-vlan mac-address 00:11:11:01:01:12 vlan 2 description TP
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## mac-vlan

### Purpose
The mac-vlan command is used to enable a port for the MAC-based VLAN feature. Only the port is enabled can'the configured MAC-based VLAN take effect. To disable the MAC-based VLAN function, please use no mac-vlan command. All the ports are disabled by default.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
mac-vlan
no mac-vlan
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the Gigabit Ethernet port 1/0/3 for the MAC-based VLAN feature:
Switch(config)#interface gigabitEthernet 1/0/3
Switch(config-if)#mac-vlan
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## show mac-vlan

### Purpose
The show mac-vlan command is used to display the information of the MAC-based VLAN entry. MAC address and VLAN ID can be used to filter the displayed information.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show mac-vlan { all | mac-address mac-addr | vlan vlan-id }
```

### Parameters
```text
mac-addr
MAC address, in the format of XX:XX:XX:XX:XX:XX.
vlan-id
Specify IEEE 802.1Q VLAN ID, ranging from 1 to 4094.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the information of all the MAC-based VLAN entry:
Switch(config)#show mac-vlan all
```

### Notes
- Permission requirement: None.

## show mac-vlan interface

### Purpose
The show mac-vlan interface command is used to display the port state of MAC-based VLAN.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show mac-vlan interface
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the enable state of all the ports:
Switch(config)#show mac-vlan interface
```

### Notes
- Permission requirement: None.

## show mac-vlan dot1x

### Purpose
The show mac-vlan dot1x command is used to display MAC entries that have been added to guest VLANs or assignment VLANs under MAC-based authentication.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show mac-vlan dot1x
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the MAC entries that have been added to guest VLANs or assignment VLANs under MAC-based authentication:
Switch(config)# show mac-vlan dot1x
```

### Notes
- Permission requirement: None.

## show vlan dot1x

### Purpose
The show vlan dot1x command is used to display the VLAN information that has been modified by the authentication function.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show vlan dot1x
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the VLAN information that has been modified by the authentication function:
Switch(config)# show vlan dot1x
```

### Notes
- Permission requirement: None.

## show interface switchport dot1x

### Purpose
The show interface switchport dot1x command is used to display the interface switchport information that has been modified by the authentication function.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show interface switchport dot1x
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the interface switchport information that has been modified by the authentication function:
Switch(config)# show interface switchport dot1x
```

### Notes
- Permission requirement: None.
