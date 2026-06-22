# IPv4 IMPB Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 77 IPv4 IMPB Commands

Location: extracted Word text lines 29076-29235

## Chapter Notes

Official documentation states: You can bind the IP address, MAC address, VLAN and the connected Port number of the Host together, which can be the condition for the ARP Inspection and ip verify source to filter the packets.

- Use these commands only when the requested feature and target interface/VLAN/ring/session details are clear.

## ip source binding

### Purpose
The ip source binding command is used to bind the IP address, MAC address, VLAN ID and the Port number together manually. You can manually bind the IP address, MAC address, VLAN ID and the Port number together in the condition that you have got the related information of the Hosts in the LAN. to delete the IP-MAC VID-PORT entry from the binding table, please use no ip source binding index command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip source binding hostname ip-addr mac-addr vlan vlan-id interface { fastEthernet port | gigabitEthernet port | ten-gigabitEthernet port | port-channel port-channel-id } { none | arp-detection | ip-verify-source | both }
no ip source binding index ip-addr
```

### Parameters
```text
hostname
The Host Name, which contains 20 characters at most.
ip-addr
The IP address of the Host.
mac-addr
The MAC address of the Host.
vlan-id
The VLAN ID needed to be bound, ranging from 1 to 4094.
port
The number of port connected to the Host.
none | arp-detection | ip-verify-source | both
The protect type for the entry.
arp-detection
indicates ARP detection;
ip-verify-source
indicates IP source filter;
none
indicates applying none;
both
indicates applying both.
ip-addr
The IP address of the entry to be deleted.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Bind an ACL entry with the IP 192.168.0.1, MAC 00:00:00:00:00:01, VLAN ID 2 and the Port number 5 manually. And then enable the entry for the ARP detection:
Switch(config)#ip source binding host1 192.168.0.1 00:00:00:00:00:01 vlan 2 interface gigabitEthernet 1/0/5 arp-detection
Delete the IP-MAC
VID-PORT entry with the index 5:
Switch(config)#no ip source binding index 5
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## no ip source binding interface

### Purpose
The ip source binding interface command is used to delete IMPB entries bound to a specified port in batches.

### Command Mode
Global Configuration Mode

### Syntax
```text
no ip source binding interface { fastEthernet port | gigabitEthernet port | ten-gigabitEthernet port }
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
Switch(config)# no ip source binding interface gigabitEthernet 1/0/1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip dhcp snooping

### Purpose
The ip dhcp snooping command is used to enable DHCP snooping function globally. To disable DHCP Snooping function globally, please use no ip dhcp snooping command. DHCP Snooping functions to monitor the process of the Host obtaining the IP address from DHCP server, and record the IP address, MAC address, VLAN and the connected Port number of the Host for automatic binding.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip dhcp snooping
no ip dhcp snooping
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the DHCP snooping function globally:
Switch(config)#ip dhcp snooping
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip dhcp snooping vlan

### Purpose
The ip dhcp snooping vlan command is used to enable DHCP snooping function on a specified VLAN. To disable DHCP Snooping function on this VLAN, please use no ip dhcp snooping vlan command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip dhcp snooping vlan vlan-range
no ip dhcp snooping vlan vlan-range
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
Enable the DHCP snooping function on VLAN 1,4,6-7:
Switch(config)#ip dhcp snooping vlan 1,4,6-7
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip dhcp snooping max-entries

### Purpose
The ip dhcp snooping max-entries command is used to configure the maximum number of entries that can be learned on a port via DHCP Snooping. To restore to the default setting, please use no ip dhcp snooping max-entries command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
ip dhcp snooping max-entries value
no ip dhcp snooping max-entries
value
Enter the value of maximum number of entries that can be learned on the port via DHCP Snooping.
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the maximum number of entries that can be learned on port 1 as 100:
Switch(config)#interface gigabitEthernet 1/0/1
Switch(config-if)#ip dhcp snooping max-entries 100
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip dhcp snooping trust

### Purpose
The ip dhcp snooping trust command is used to configure the trust status of a specified interface, and only DHCP Server connected to a trusted port can assign packets to clients. To delete the status, please use no ip dhcp snooping trust command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
ip dhcp snooping trust
no ip dhcp snooping trust
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable DHCP snooping trust function for port 1/0/3:
Switch(config)#interface gigabitEthernet 1/0/3
Switch(config-if)#ip dhcp snooping trust
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## show ip source binding

### Purpose
The show ip source binding command is used to display the IP-MAC-VID- PORT binding table.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip source binding
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the IP-MAC-VID-PORT binding table:
Switch(config)#show ip source binding
```

### Notes
- Permission requirement: None.

## show ip dhcp snooping

### Purpose
The show ip dhcp snooping command is used to display the running status of DHCP Snooping.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip dhcp snooping
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the running status of DHCP Snooping:
Switch#show ip dhcp snooping
```

### Notes
- Permission requirement: None.

## show ip dhcp snooping interface

### Purpose
The show ip dhcp snooping interface command is used to display the DHCP Snooping configuration of a desired Gigabit Ethernet port/port channel or of all Ethernet ports/port channels.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip dhcp snooping interface [ gigabitEthernet port | port-channel port-channel-id ]
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
Display the DHCP Snooping configuration of all Ethernet ports and port channels:
Switch#show ip dhcp snooping interface
Display the DHCP Snooping configuration of Gigabit Ethernet port 1/0/5:
Switch#show ip dhcp snooping interface gigabitEthernet 1/0/5
```

### Notes
- Permission requirement: None.
