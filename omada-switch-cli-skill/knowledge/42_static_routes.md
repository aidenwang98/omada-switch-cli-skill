# Static Routes Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 42 Static Routes Commands

Location: extracted Word text lines 18125-18441

## Chapter Notes

- Use these commands only when the requested feature and target interface/VLAN/ring/session details are clear.

## ip routing

### Purpose
This ip routing command is used to enable IPv4 routing globally. To disable IPv4 routing, please use the no ip routing command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip routing
no ip routing
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable IPv4 routing feature for the switch:
Switch(config)# ip routing
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## interface vlan

### Purpose
This interface vlan command is used to create the VLAN interface. To delete the specified VLAN interface, please use the no interface vlan command.

### Command Mode
Global Configuration Mode

### Syntax
```text
interface vlan { vid }
no interface vlan { vid }
```

### Parameters
```text
vid
The ID of the VLAN.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Create the VLAN interface 2:
Switch(config)# interface vlan 2
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## interface loopback

### Purpose
This interface loopback command is used to create the loopback interface. To delete the specified loopback interface, please use the no interface loopback command.

### Command Mode
Global Configuration Mode

### Syntax
```text
interface loopback { id }
no interface loopback { id }
```

### Parameters
```text
The ID of the loopback interface, ranging from 1 to 64.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Create the loopback interface 1:
Switch(config)# interface loopback 1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## switchport

### Purpose
This switchport command is used to switch the Layer 3 interface into the Layer 2 port. To switch the Layer 2 port into the Layer 3 routed port, please use the no switchport command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
switchport
no switchport
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch port 1/0/9 into the routed port:
Switch(config)# interface gigabitEthernet 1/0/9
Switch(config-if)# no switchport
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## interface range port-channel

### Purpose
This interface range port-channel command is used to create multiple port-channel interfaces.

### Command Mode
Global Configuration Mode

### Syntax
```text
interface range port-channel port-channel-list
```

### Parameters
```text
port-channel-list
The list of the port-channel interface, ranging from 1 to 14, in the format of 1-3, 5.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Create the port-channel interfaces 1, 3, 4 and 5:
Switch(config)# interface port-channel 1,3-5
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## description

### Purpose
This description command is used to add a description to the Layer 3 interface, including routed port, port-channel interface, loopback interface and VLAN interface. To clear the description of the corresponding interface, please use the no description command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
description string
no description
```

### Parameters
```text
string
Content of an interface description, ranging from 1 to 32 characters.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Add a description system-if to the routed port 1/0/9 :
Switch(config)# interface gigabitEthernet 1/0/9
Switch(config-if)# no switchport
Switch(config-if)# description system-if
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## shutdown

### Purpose
This shutdown command is used to shut down the specified interface. The interface type include: routed port, port-channel interface, loopback interface and VLAN interface. To enable the specified interface, please use the no shutdown command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
shutdown
no shutdown
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Shut down the routed port 1/0/9:
Switch(config)# interface gigabitEthernet 1/0/9
Switch(config-if)# no switchport
Switch(config-if)# shutdown
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## interface port-channel

### Purpose
This interface port-channel command is used to create the port-channel interface. To delete the specified port-channel interface, please use the no interface port-channel command.

### Command Mode
Global Configuration Mode

### Syntax
```text
interface port-channel { port-channel-id }
no interface port-channel { port-channel-id }
```

### Parameters
```text
port-channel-id
The ID of the port-channel interface, ranging from 1 to 14.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Create the port-channel interface 1:
Switch(config)# interface port-channel 1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip route

### Purpose
This ip route command is configure the static route. To clear the corresponding entry, please use the no ip route command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip route [vrf vrf-name] { dest-address } { mask } [nexthop-vrf vrf-name] { next-hop-address } [ distance ]
no ip route [vrf vrf-name] { dest-address } { mask } [nexthop-vrf vrf-name] { next-hop-address } [ distance ]
```

### Parameters
```text
vrf-name
VRF instance name.
dest-address
The destination IP address.
mask
The subnet mask.
next-hop-address
The address of the next-hop.
distance
The distance metric of this route, ranging from 1 to 255. The smaller the distance is, the higher the priority is.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Create a static route with the destination IP address as 192.168.2.0, the subnet mask as 255.255.255.0 and the next-hop address as 192.168.0.2:
Switch(config)# ip route 192.168.2.0 255.255.255.0 192.168.0.2
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ipv6 routing

### Purpose
This ipv6 routing command is enale the IPv6 routing feature globally. To diable IPv6 routing, please use the no ipv6 routing command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ipv6 routing
no ipv6 routing
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable IPv6 routing globally:
Switch(config)# ipv6 routing
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ipv6 route

### Purpose
This ipv6 route command is configure the IPv6 static route. To clear the corresponding entry, please use the no ipv6 route command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ipv6 route [vrf vrf-name] { ipv6-dest-address } [nexthop-vrf vrf-name] { next-hop-address } [ distance ]
no ipv6 route [vrf vrf-name] { ipv6-dest-address } [nexthop-vrf vrf-name] { next-hop-address } [ distance ]
```

### Parameters
```text
vrf-name
VRF instance name.
ipv6-dest-address
Destination IPv6 address and mask length.
next-hop-address
Next hop IPv6 address.
distance
Routing metric, value range 1~255.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure a static route with a destination IP of 3200::/64, a prefix vrf of vrf1, a next hop IP of 3100::1234, and a next hop vrf of vrf2:
Switch(config)# ipv6 route vrf vrf1 3200::/64 nexthop-vrf vrf2 3100::1234
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## show interface vlan

### Purpose
The show interface vlan command is used to display the information of the specified interface VLAN.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show interface vlan vid
```

### Parameters
```text
vid
The VLAN ID.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the information of VLAN 2:
Switch(config)#show interface vlan 2
```

### Notes
- Permission requirement: None.

## show ip interface

### Purpose
This show ip interface command is used to display the detailed information of the specified Layer 3 interface.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip interface [ gigabitEthernet port | port-channel port-channel-id | loopback id | vlan vlan-id ]
```

### Parameters
```text
port
The port number.
port-channel-id
The ID of the port channel. Member ports in this port channel should all be routed ports.
The loopback interface ID.
vlan-id
The VLAN interface ID.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the detailed information of the VLAN interface 2:
Switch(config)# show ip interface vlan 2
```

### Notes
- Permission requirement: None.

## show ip interface brief

### Purpose
This show ip interface brief command is used to display the summary information of the Layer 3 interfaces.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip interface brief
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the summary information of the Layer 3 interfaces:
Switch(config)# show ip interface brief
```

### Notes
- Permission requirement: None.

## show ip route

### Purpose
This show ip route command is used to display IPv4 routing table information, and can be expanded to display routing table information of a certain VRF.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip route [vrf vrf-name]
```

### Parameters
```text
vrf-name
VRF instance name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the IPv4 routing table information under VRF1:
Switch(config)# show ip route vrf vrf1
```

### Notes
- Permission requirement: None.

## show ip route specify

### Purpose
This show ip route specify command is used to display the valid routing information to the specified IP address or network segments.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip route specify { ip } [ mask ] [ longer-prefixes ]
```

### Parameters
```text
Specify the destination IP address.
mask
Specify the destination IP address together with the parameter ip.
longer-prefixes
Specify the destination subnets that match the network segment determined by the ip and mask parameters.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the shortest route to 192.168.0.100:
Switch(config)# show ip route specify 192.168.0.100
Look up the route entry with the destination as 192.168.0.0/24:
Switch(config)# show ip route specify 192.168.0.0 255.255.255.0
Display the routes to all the subnets that belongs to 192.168.0.0/16:
Switch(config)# show ip route specify 192.168.0.0 255.255.0.0 longer-prefixes
```

### Notes
- Permission requirement: None.

## show ip route summary

### Purpose
This show ip route summary command is used to display the summary information of the route entries classified by their sources.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip route summary
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the summary information of route entries:
Switch(config)# show ip route summary
```

### Notes
- Permission requirement: None.

## show ipv6 interface

### Purpose
This command is used to display the configured IPv6 information of the management interface, including ipv6 function status, link-local address and global address, IPv6 multicast groups etc.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ipv6 interface
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the IPv6 information of the management interface:
Switch(config)# show ipv6 interface
```

### Notes
- Permission requirement: None.

## show ipv6 route

### Purpose
This show ipv6 route command is used to display IPv6 routing table information, and can be expanded to display routing table information of a certain VRF.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ipv6 route [vrf vrf-name]
```

### Parameters
```text
vrf-name
VRF instance name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the IPv6 routing table information under VRF1:
Switch(config)# show ipv6 route vrf vrf1
```

### Notes
- Permission requirement: None.

## show ipv6 route summary

### Purpose
This show ipv6 route summary command is used to display the summary information of the IPv6 route entries classified by their sources.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ipv6 route summary
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the summary information of IPv6 route entries:
Switch(config)# show ipv6 route summary
```

### Notes
- Permission requirement: None.
