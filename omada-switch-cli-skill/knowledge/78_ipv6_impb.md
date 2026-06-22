# IPv6 IMPB Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 78 IPv6 IMPB Commands

Location: extracted Word text lines 29236-29455

## Chapter Notes

Official documentation states: You can bind the IPv6 address, MAC address, VLAN and the connected Port number of the Host together, which can be the condition for the ARP Inspection and ip verify source to filter the packets.

- Use these commands only when the requested feature and target interface/VLAN/ring/session details are clear.

## ipv6 source binding

### Purpose
The ipv6 source binding command is used to bind the IPv6 address, MAC address, VLAN ID and the Port number together manually. You can manually bind the IPv6 address, MAC address, VLAN ID and the Port number together in the condition that you have got the related information of the Hosts in the LAN. to delete the IPv6-MAC VID-PORT entry from the binding table, please use no ipv6 source binding index command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ipv6 source binding hostname ipv6-addr mac-addr vlan vlan-id interface { fastEthernet port | gigabitEthernet port | ten-gigabitEthernet port | port-channel port-channel-id } { none | nd-detection | ipv6-verify-source | both }
no ipv6 source binding index ipv6-addr
```

### Parameters
```text
hostname
The Host Name, which contains 20 characters at most.
Ipv6-addr
The IP address of the Host.
mac-addr
The MAC address of the Host.
vlan-id
The VLAN ID needed to be bound, ranging from 1 to 4094.
port
The number of port connected to the Host.
none | nd-detection | ipv6-verify-source | both
The protect type for the entry.
nd-detection
indicates ND detection;
ipv6-verify-source
indicates IPv6 source filter;
none
indicates applying none;
both
indicates applying both.
Ipv6-addr
The IPv6 address of the entry to be deleted.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
The following example shows how to bind an entry with the hostname host1, IPv6 address 2001:0:9d38:90d5::34, MAC address AA-BB-CC-DD-EE-FF, VLAN ID 10, port number 1/0/5, and enable this entry for ND Detection.
Switch(config)# ipv6 source binding host1 2001:0:9d38:90d5::34 aa:bb:cc:dd:ee:ff vlan 10 interface gigabitEthernet 1/0/5 nd-detection
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## no ipv6 source binding interface

### Purpose
The ipv6 source binding interface command is used to delete IMPB entries bound to a specified port in batches.

### Command Mode
Global Configuration Mode

### Syntax
```text
no ipv6 source binding interface { fastEthernet port | gigabitEthernet port | ten-gigabitEthernet port }
```

### Parameters
```text
port
The number of port.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Delete IMPB entries bound to port 1/0/1:
Switch(config)# no ipv6 source binding interface gigabitEthernet 1/0/1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ipv6 dhcp snooping

### Purpose
The ipv6 dhcp snooping command is used to enable DHCPv6 snooping function globally. To disable DHCPv6 Snooping function globally, please use no ipv6 dhcp snooping command. DHCPv6 Snooping functions to monitor the process of the Host obtaining the IP address from DHCPv6 server, and record the IPv6 address, MAC address, VLAN and the connected Port number of the Host for automatic binding.

### Command Mode
Global Configuration Mode

### Syntax
```text
ipv6 dhcp snooping
no ipv6 dhcp snooping
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the DHCPv6 snooping function globally:
Switch(config)#ipv6 dhcp snooping
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ipv6 dhcp snooping vlan

### Purpose
The ipv6 dhcp snooping vlan command is used to enable DHCP snooping function on a specified VLAN. To disable DHCP Snooping function on this VLAN, please use no ipv6 dhcp snooping vlan command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ipv6 dhcp snooping vlan vlan-range
no ipv6 dhcp snooping vlan vlan-range
```

### Parameters
```text
vlan-range
Specify the VLANs to enable the DHCP snooping function, in the format of 1-3, 5.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the DHCPv6 snooping function on VLAN 1,4,6-7:
Switch(config)#ipv6 dhcp snooping vlan 1,4,6-7
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ipv6 dhcp snooping max-entries

### Purpose
The ipv6 dhcp snooping max-entries command is used to configure the maximum number of entries that can be learned on a port via DHCPv6 Snooping. To restore to the default setting, please use no ipv6 dhcp snooping max-entries command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
Ipv6 dhcp snooping max-entries value
no ipv6 dhcp snooping max-entries
value: Enter the value of maximum number of entries that can be learned on the port via DHCPv6 Snooping.
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the maximum number of entries that can be learned on port 1 as 100:
Switch(config)#interface gigabitEthernet 1/0/1
Switch(config-if)#ipv6 dhcp snooping max-entries 100
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ipv6 nd snooping

### Purpose
The ipv6 nd snooping command is used to enable ND snooping function globally. To disable ND Snooping function globally, please use no ipv6 nd snooping command. ND Snooping functions to monitor the process of the duplication address detection, and record the IPv6 address, MAC address, VLAN and the connected Port number of the Host for automatic binding.

### Command Mode
Global Configuration Mode

### Syntax
```text
ipv6 nd snooping
no ipv6 nd snooping
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the ND snooping function globally:
T160G-28TS(config)#ipv6 nd snooping
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ipv6 nd snooping vlan

### Purpose
The ipv6 nd snooping vlan command is used to enable ND snooping function on a specified VLAN. To disable ND Snooping function on this VLAN, please use no ipv6 nd snooping vlan command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ipv6 nd snooping vlan vlan-range
no ipv6 nd snooping vlan vlan-range
```

### Parameters
```text
vlan-range
Specify the VLANs to enable the ND snooping function, in the format of 1-3, 5.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the ND snooping function on VLAN 1,4,6-7:
Switch(config)#ipv6 nd snooping vlan 1,4,6-7
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ipv6 nd snooping max-entries

### Purpose
The ipv6 nd snooping max-entries command is used to specify the maximum number of binding entries that are allow to be bound to a port. To return the default, please use no ipv6 nd snooping max-entries command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
ipv6 nd snooping max-entries value
no ipv6 nd snooping max-entries
```

### Parameters
```text
value
Specify the maximum number of ND snooping entries on this interface.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the maximum number of binding entries from ND Snooping of Gigabit Ethernet port 1/0/2 is 100:
Switch(config)#interface gigabitEthernet 1/0/2
Switch(config-if)#ipv6 nd snooping max-entries 100
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## show ipv6 source binding

### Purpose
The show ipv6 source binding command is used to display the IPv6-MAC-VID- PORT binding table.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ipv6 source binding
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the IPv6-MAC-VID-PORT binding table:
Switch(config)#show ipv6 source binding
```

### Notes
- Permission requirement: None.

## show ipv6 dhcp snooping

### Purpose
The show ipv6 dhcp snooping command is used to display the running status of DHCPv6 Snooping.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ipv6 dhcp snooping
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the running status of DHCPv6 Snooping:
Switch#show ipv6 dhcp snooping
```

### Notes
- Permission requirement: None.

## show ipv6 dhcp snooping interface

### Purpose
The show ipv6 dhcp snooping interface command is used to display the DHCPv6 Snooping configuration of a desired Gigabit Ethernet port/port channel or of all Ethernet ports/port channels.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ipv6 dhcp snooping interface [ gigabitEthernet port | port-channel port-channel-id ]
```

### Parameters
```text
port
The Ethernet port number.
port-channel-id
The ID of the port channel.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the DHCPv6 Snooping configuration of all Ethernet ports and port channels:
Switch#show ipv6 dhcp snooping interface
Display the DHCPv6 Snooping configuration of Gigabit Ethernet port 1/0/5:
Switch#show ipv6 dhcp snooping interface gigabitEthernet 1/0/5
```

### Notes
- Permission requirement: None.

## show ipv6 nd snooping

### Purpose
The show ipv6 nd snooping command is used to display the running status of ND Snooping.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ipv6 nd snooping
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the running status of ND Snooping:
Switch#show ipv6 nd snooping
```

### Notes
- Permission requirement: None.

## show ipv6 nd snooping interface

### Purpose
The show ipv6 nd snooping interface command is used to display the ND Snooping configuration of a desired Gigabit Ethernet port/port channel or of all Ethernet ports/port channels.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ipv6 nd snooping interface [ gigabitEthernet port | port-channel port-channel-id ]
```

### Parameters
```text
port
The Ethernet port number.
port-channel-id
The ID of the port channel.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the ND Snooping configuration of all Ethernet ports and port channels:
Switch#show ipv6 nd snooping interface
Display the ND Snooping configuration of Gigabit Ethernet port 1/0/5:
Switch#show ipv6 nd snooping interface gigabitEthernet 1/0/5
```

### Notes
- Permission requirement: None.
- Official note: This command is only available on certain devices.
