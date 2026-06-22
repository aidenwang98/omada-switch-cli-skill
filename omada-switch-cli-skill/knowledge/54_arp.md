# ARP Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 54 ARP Commands

Location: extracted Word text lines 23969-24201

## Chapter Notes

Official documentation states: Address Resolution Protocol (ARP) is used to resolve an IP address into an Ethernet MAC address. The switch maintains an ARP mapping table to record the IP-to-MAC mapping relations, which is used for forwarding packets. An ARP mapping table contains two types of ARP entries: dynamic and static. An ARP dynamic entry is automatically created and maintained by ARP. A static ARP entry is manually configured and maintained. Description This arp command is used to add a static ARP entry. To delete the specified ARP entry, please use the no arp command. If the command contains vrf, the arp belongs to the vrf instance. Syntax arp ip mac type [vrf vrf-name] no arp ip type [vrf vrf-name] Parameter The IP address of the static ARP entry. mac The MAC address of the static ARP entry. type The ARP type. Configure it as arpa vrf-name Specify the vrf name. Command Mode Global Configuration Mode Privilege Requirement Only Admin, Operator and Power User level users have access to these commands. Example Create a static ARP entry with the IP as 192.168.0.1 and the MAC as 00:11:22:33:44:55: Switch(config)# arp 192.168.0.1 00:11:22:33:44:55 arpa vrf v1

- Use these commands only when the requested feature and target interface/VLAN/ring/session details are clear.

## clear arp-cache

### Purpose
This clear arp-cache command is used to clear all the dynamic ARP entries. If the command contains VRF, the ARP entries of the VRF instance are clear.

### Command Mode
Privileged EXEC Mode

### Syntax
```text
clear arp-cache [vrf vrf-name]
```

### Parameters
```text
vrf-name
Specify the vrf name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Clear ARP entries in VRF v1:
Switch(config)# clear arp-cache vrf v1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## arp dynamicrenew

### Purpose
This arp dynamicrenew command is used to automatically renew dynamic ARP entries. To disable the switch to automatically renew dynamic ARP entries, please use the no arp dynamicremew command. By default, it is enabled.

### Command Mode
Global Configuration Mode

### Syntax
```text
arp dynamicremew
no arp dynamicremew
```

### Parameters
No parameters.

### Default
By default, it is enabled.

### Example
```text
Enable the switch to automatically renew the dynamic ARP entries:
Switch(config)# arp dynamicrenew
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## arp timeout

### Purpose
This arp timeout command is used to configure the ARP aging time of the interface.

### Command Mode
Global Configuration Mode

### Syntax
```text
arp timeout timeout
no arp timeout
```

### Parameters
```text
timeout
Specify the aging time, ranging from 10 to 3000 seconds. The default value is 1200 seconds.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the ARP aging time as 60 seconds:
Switch(config)# arp timeout 60
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## gratuitous-arp intf-status-up enable

### Purpose
This gratuitous-arp intf-status-up enable command is used to enable the Layer 3 interface to send a gratuitous ARP packet when the interface s status becomes up.

### Command Mode
Global Configuration Mode

### Syntax
```text
gratuitous-arp intf-status-up enable
no gratuitous-arp intf-status-up enable
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the switch
s Layer 3 interfaces to send gratuitous ARP packets when their status becomes up:
Switch(config)# gratuitous-arp intf-status-up enable
```

### Notes
- Permission requirement: None.

## gratuitous-arp dup-ip-detected enable

### Purpose
This gratuitous-arp dup-ip-detected enable command is used to enable the Layer 3 interface to send a gratuitous ARP packet when receiving a gratuitous packets of which the IP address is the same as its own.

### Command Mode
Global Configuration Mode

### Syntax
```text
gratuitous-arp dup-ip-detected enable
no gratuitous-arp dup-ip-detected enable
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the switch
s Layer 3 interface to send gratuitous ARP packets when receiving a gratuitous packets of which the IP address is the same as its own:
Switch(config)# gratuitous-arp dup-ip-detected enable
```

### Notes
- Permission requirement: None.

## gratuitous-arp learning enable

### Purpose
This gratuitous-arp learning enable command is used to enable the Layer 3 interface to learn MAC addresses from the gratuitous ARP packets.

### Command Mode
Global Configuration Mode

### Syntax
```text
gratuitous-arp learning enable
no gratuitous-arp learning enable
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the Layer 3 interface to learn MAC addresses from the gratuitous ARP packets:
Switch(config)# gratuitous-arp learning enable
```

### Notes
- Permission requirement: None.

## gratuitous-arp send-interval

### Purpose
This gratuitous-arp send-interval command is used to configure the interval at which the interface periodically send the gratuitous ARP packets.

### Command Mode
Interface Configuration Mode (interface vlan / interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
gratuitous-arp send-interval interval
```

### Parameters
```text
Interval
Specify the interval at which the interface periodically send the gratuitous ARP packets. Value 0 means the interface will not send gratuitous ARP packets.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Specify the interface VLAN 1 to send gratuitous ARP packets every 1 second:
Switch(config)# interface vlan 1
Switch(config-if)# gratuitous-arp send-interval 1
```

### Notes
- Permission requirement: None.

## ip proxy-arp

### Purpose
The ip proxy-arp command is used to enable Proxy ARP function on the specified VLAN interface or routed port. To disable Proxy ARP on this interface, please use no ip proxy-arp command.

### Command Mode
Interface Configuration Mode (interface vlan / interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
ip proxy-arp
no ip proxy-arp
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the Proxy ARP function on VLAN Interface 2:
Switch(config)# interface vlan 2
Switch(config-if)# ip proxy-arp
Enable the Proxy ARP function on routed port 1/0/2:
Switch(config)# interface gigabitEthernet 2
Switch(config-if)# no switchport
Switch(config-if)# ip proxy-arp
```

### Notes
- Permission requirement: None

## ip local-proxy-arp

### Purpose
The ip local-proxy-arp command is used to enable Local Proxy ARP function on the specified VLAN interface or routed port. To disable Local Proxy ARP function on this interface, please use no ip local-proxy-arp command.

### Command Mode
Interface Configuration Mode (interface vlan / interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
ip local-proxy-arp
no ip local-proxy-arp
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the Proxy ARP function on VLAN Interface 2:
Switch(config)# interface vlan 2
Switch(config-if)# ip local-proxy-arp
Enable the Proxy ARP function on routed port 1/0/2:
Switch(config)# interface gigabitEthernet 2
Switch(config-if)# no switchport
Switch(config-if)# ip local-proxy-arp
```

### Notes
- Permission requirement: None

## show arp

### Purpose
This show arp command is used to display the active ARP entries. If no parameter is speicified, all the active ARP entries will be displayed. If the VRF is specified, the arp entries of the VRF instance are displayed.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show arp [ ip ] [ mac ] [vrf vrf-name]
```

### Parameters
```text
Specify the IP address of your desired ARP entry.
mac
Specify the MAC address of your desired ARP entry.
vrf-name
Specify the VRF name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the ARP entry with the IP as 192.168.0.2 in vrf v1:
Switch(config)# show arp 192.168.0.2 vrf v1
```

### Notes
- Permission requirement: None.

## show ip arp (interface)

### Purpose
This show ip arp (interface) command is used to display the active ARP entries associated with a specified Layer 3 interface.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip arp { gigabitEthernet port | port-channel port-channel-id | vlan id }
```

### Parameters
```text
port
Specify the number of the routed port.
port-channel-id
Specify the ID of the port channel.
Specify the VLAN interface ID.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the ARP entry associated with VLAN interface 2:
Switch(config)# show ip arp vlan 2
```

### Notes
- Permission requirement: None.

## show ip arp summary

### Purpose
This show ip arp summary command is used to display the number of the active ARP entries.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip arp summary
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the number of the ARP entries:
Switch(config)# show ip arp summary
```

### Notes
- Permission requirement: None.

## show gratuitous-arp

### Purpose
This show gratuitous arp command is used to display the configuration of gratuitous ARP.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show gratuitous-arp
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the configuration of gratuitous ARP:
Switch(config)# show gratuitous-arp
```

### Notes
- Permission requirement: None.

## show ip proxy-arp

### Purpose
The show ip proxy-arp command is used to display the Proxy ARP status.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip proxy-arp
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the Proxy ARP status:
Switch(config)# show ip proxy-arp
```

### Notes
- Permission requirement: None
