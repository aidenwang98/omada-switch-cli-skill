# VLAN-VPN Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 24 VLAN-VPN Commands (Only for Certain Devices)

Location: extracted Word text lines 12112-12312

## Chapter Notes

Official documentation states: Note: VLAN-VPN commands are only available on certain devices. VLAN-VPN (Virtual Private Network) function, the implement of a simple and flexible Layer 2 VPN technology, allows the packets with VLAN tags of private networks to be encapsulated with VLAN tags of public networks at the network access terminal of the Internet Service Provider. And these packets will be transmitted with double-tag across the public networks.

- This chapter is marked `Only for Certain Devices`; treat all configuration commands as model-dependent.
- When a command or note is device-specific in the official text, mention model and firmware dependency before recommending it.

## dot1q-tunnel

### Purpose
The dot1q-tunnel command is used to enable the VLAN-VPN function globally. To disable the VLAN-VPN function, please use the no dot1q-tunnel command.

### Command Mode
Global Configuration Mode

### Syntax
```text
dot1q-tunnel
no dot1q-tunnel
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the VLAN-VPN function globally:
Switch(config)#dot1q-tunnel
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## switchport dot1q-tunnel tpid

### Purpose
The switchport dot1q-tunnel tpid command is used to configure Global TPID for the ports. To restore to the default value, please use the no switchport dot1q-tunnel tpid command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
switchport dot1q-tunnel tpid tpid
no switchport dot1q-tunnel tpid
```

### Parameters
```text
tpid
The value of Global TPID. It must be 4 Hex integers. By default, it is 8100.
```

### Default
By default, it is 8100.

### Example
```text
Configure TPID of port 1/0/2 as 0x9100:
Switch(config)#interface gigabitEthernet 1/0/2
Switch(config-if)#switchport dot1q-tunnel tpid 9100
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## dot1q-tunnel mapping

### Purpose
The dot1q-tunnel mapping command is used to enable the VLAN Mapping feature globally. To disable this function, please use the no dot1q-tunnel mapping command. By default, the VLAN Mapping feature is disabled.

### Command Mode
Global Configuration Mode

### Syntax
```text
dot1q-tunnel mapping
no dot1q-tunnel mapping
```

### Parameters
No parameters.

### Default
By default, the VLAN Mapping feature is disabled.

### Example
```text
Enable the VLAN mapping feature globally:
Switch(config)#dot1q-tunnel mapping
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## switchport dot1q-tunnel mode

### Purpose
The switchport dot1q-tunnel mode command is used to configure the VPN port s mode. To close this VPN port, please use the no switchport dot1q-tunnel mode command. By default, no port has been configured as the VPN port. The VPN port mode uni and nni cannot switch to each other directly, so please close the VPN port and switch to the other mode if needed.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
switchport dot1q-tunnel mode { uni | nni }
no switchport dot1q-tunnel mode
```

### Parameters
```text
uni
The port connected to the clients.
nni
The port connected to the ISP.
```

### Default
By default, no port has been configured as the VPN port.

### Example
```text
Configure the Gigabit Ethernet port 1/0/3 as the VPN UNI ports:
Switch(config)#interface gigabitEthernet 1/0/3
Switch(config-if)#switchport dot1q-tunnel mode uni
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## switchport dot1q-tunnel missdrop (only for certain devices)

### Purpose
The switchport dot1q-tunnel missdrop command is used to enable the VLAN-VPN missdrop function for a specific port. To disable the VLAN-VPN missdrop function, please use the no switchport dot1q-tunnel missdrop command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
switchport dot1q-tunnel missdrop
no switchport dot1q-tunnel missdrop
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the VLAN-VPN missdrop function for Gigabit Ethernet port 1/0/3:
Switch(config)#interface gigabitEthernet 1/0/3
Switch(config-if)#switchport dot1q-tunnel missdrop
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Official note: For some devices, Missdrop can only be enabled on UNI ports. For other devices, Missdrop can only be enabled on NNI ports.
- Availability: Only for certain devices according to the official chapter title.

## switchport dot1q-tunnel use_inner_priority

### Purpose
The switchport dot1q-tunnel use_inner_priority command is used to use the inner 802.1p priority. To disable this function, please use the no switchport dot1q-tunnel use_inner_priority command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
switchport dot1q-tunnel use_inner_priority
no switchport dot1q-tunnel use_inner_priority
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the use inner priority function for Gigabit Ethernet port 1/0/3:
Switch(config)#interface gigabitEthernet 1/0/3
Switch(config-if)#switchport dot1q-tunnel use_inner_priority
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## switchport dot1q-tunnel mapping

### Purpose
The switchport dot1q-tunnel mapping command is used add the VLAN Mapping entry on a specified port. To delete the VLAN Mapping entry on this port, please use the no switchport dot1q-tunnel mapping command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
switchport dot1q-tunnel mapping c-vlan sp-vlan [ descript ]
no switchport dot1q-tunnel mapping [ c-vlan ]
```

### Parameters
```text
c-vlan
Customer VLAN ID, ranging from 1 to 4094.
sp-vlan
Service Provider VLAN ID, ranging from 1 to 4094.
descript
Give a Description to the VLAN Mapping entry, which contains 16 characters at most.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Add a VLAN Mapping entry on the Gigabit Ethernet port 1/0/3 with the Customer VLAN as VLAN 2 and the Service Provider VLAN as VLAN 3:
Switch(config)#interface gigabitEthernet 1/0/3
Switch(config-if)#switchport dot1q-tunnel mapping 2 3
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Official note: For some devices, choose a UNI port to enable VLAN mapping. For other devices, choose a NNI port to enable VLAN mapping.
- Availability: Only for certain devices according to the official chapter title.

## switchport dot1q-tunnel replace

### Purpose
The switchport dot1q-tunnel replace command is used to replace the customer VLAN ID with a VLAN ID of service provider on a specified port, rather than adds an outer tag. To delete the VLAN Replace entry on this port, please use the no switchport dot1q-tunnel replace command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
switchport dot1q-tunnel replace c-vlan sp-vlan [ descript ]
no switchport dot1q-tunnel replace c-vlan sp-vlan [ descript ]
```

### Parameters
```text
c-vlan
Customer VLAN ID, ranging from 1 to 4094.
sp-vlan
Service Provider VLAN ID, ranging from 1 to 4094.
descript
Give a Description to the VLAN Mapping entry, which contains 16 characters at most.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Add a VLAN Replace entry on the Gigabit Ethernet port 1/0/3 to replace the Customer VLAN (VLAN 2) with the Service Provider VLAN (VLAN 3):
Switch(config)# switchport dot1q-tunnel replace 2 3
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- User guidelines: Before configuring VLAN Replace, enable VLAN Mapping globally.
- Availability: Only for certain devices according to the official chapter title.

## switchport dot1q-tunnel replace-out

### Purpose
The switchport dot1q-tunnel replace-out command is used to replace the VLAN ID of service provider with a customer VLAN ID on a specified port. To delete the VLAN Replace entry on this port, please use the no switchport dot1q-tunnel replace-out command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
switchport dot1q-tunnel replace-out sp-vlan c-vlan [ descript ]
no switchport dot1q-tunnel replace-out sp-vlan c-vlan [ descript ]
```

### Parameters
```text
sp-vlan
Service Provider VLAN ID, ranging from 1 to 4094.
c-vlan
Customer VLAN ID, ranging from 1 to 4094.
descript
Give a Description to the VLAN Mapping entry, which contains 16 characters at most.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Add a VLAN Replace entry on the Gigabit Ethernet port 1/0/3 to replace the Service Provider VLAN (VLAN 2) with the Customer VLAN (VLAN 3):
Switch(config)# switchport dot1q-tunnel replace-out 2 3
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- User guidelines: Before configuring VLAN Replace-Out, enable VLAN Mapping globally.
- Availability: Only for certain devices according to the official chapter title.

## show dot1q-tunnel

### Purpose
The show dot1q-tunnel command is used to display the global configuration information of the VLAN VPN.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show dot1q-tunnel
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the global configuration information of the VLAN VPN:
Switch(config)#show dot1q-tunnel
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## show dot1q-tunnel mapping

### Purpose
The show dot1q-tunnel mapping command is used to display the information of VLAN Mapping entry.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show dot1q-tunnel mapping
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the information of VLAN Mapping entry:
Switch(config)#show dot1q-tunnel mapping
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## show dot1q-tunnel interface

### Purpose
The show dot1q-tunnel mapping interface command is used to display the VLAN VPN port type.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show dot1q-tunnel interface
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the port type of all VLAN VPN ports:
Switch(config)#show dot1q-tunnel interface
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.
