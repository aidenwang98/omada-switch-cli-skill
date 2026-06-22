# Voice VLAN Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 64 Voice VLAN Commands

Location: extracted Word text lines 26288-26389

## Chapter Notes

Official documentation states: Voice VLANs are configured specially for voice data stream. By configuring Voice VLANs and adding the ports with voice devices attached to voice VLANs, you can perform QoS-related configuration for voice data, ensuring the transmission priority of voice data stream and voice quality.

- Use these commands only when the requested feature and target interface/VLAN/ring/session details are clear.

## voice vlan

### Purpose
The voice vlan command is used to enable Voice VLAN function. To disable Voice VLAN function, please use no voice vlan command.

### Command Mode
Global Configuration Mode

### Syntax
```text
voice vlan vlan-id
no voice vlan
```

### Parameters
```text
vlan-id
Specify IEEE 802.1Q VLAN ID, ranging from 2 to 4094.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the Voice VLAN function for VLAN 10:
Switch(config)# voice vlan 10
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## voice vlan (interface)

### Purpose
The voice vlan command is used to enable Voice VLAN function on the desired ports. To disable Voice VLAN function on ports, please use no voice vlan command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
voice vlan
no voice vlan
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the Voice VLAN function for port 1/0/1:
Switch(config)# interface gigabitEthernet 1/0/1
Switch(config-if)#voice vlan
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## voice vlan priority

### Purpose
The voice vlan priority command is used to configure the priority for the Voice VLAN. To restore to the default priority, please use no voice vlan priority command.

### Command Mode
Global Configuration Mode

### Syntax
```text
voice vlan priority pri
no voice vlan priority
```

### Parameters
```text
pri
Priority, ranging from 0 to 7, and the default value is 7.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the priority of the Voice VLAN as 5:
Switch(config)# voice vlan priority 5
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## voice vlan oui

### Purpose
The voice vlan oui command is used to create voice vlan OUI. To delete the specified voice vlan OUI, please use no voice vlan oui command.

### Command Mode
Global Configuration Mode

### Syntax
```text
voice vlan oui oui-prefix oui-desc string
no voice vlan mac-address oui-prefix
```

### Parameters
```text
oui-prefix
The OUI address of the voice device, in the format of XX:XX:XX.
string
Give a description to the OUI for identification which contains 16 characters at most.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Create a Voice VLAN OUI described as TP-Phone with the OUI address 00:11:11:11:11:11 and the mask address FF:FF:FF:00:00:00:
Switch(config)#voice vlan oui 00:11:11 oui-desc TP-Phone
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## show voice vlan

### Purpose
The show voice vlan command is used to display the global configuration information of Voice VLAN.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show voice vlan
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the configuration information of Voice VLAN globally:
Switch(config)# show voice vlan
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## show voice vlan oui-table

### Purpose
The show voice vlan oui command is used to display the configuration information of Voice VLAN OUI.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show voice vlan oui
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the configuration information of Voice VLAN OUI:
Switch(config)# show voice vlan oui-table
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## show voice vlan interface

### Purpose
The show voice vlan interface command is used to display the Voice VLAN configuration information of all ports.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show voice vlan interface
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the Voice VLAN configuration information of all ports and port channels:
Switch(config)# show voice vlan interface
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
