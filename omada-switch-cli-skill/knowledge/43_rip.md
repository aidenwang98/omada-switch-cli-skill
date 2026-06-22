# RIP Configuration Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 43 RIP Configuration Commands (Only for Certain Devices)

Location: extracted Word text lines 18442-18784

## Chapter Notes

Official documentation states: RIP (Routing Information Protocol) is a routing protocol suitable for small networks and has lower requirements in terms of bandwidth, configuration, and management. As a routing protocol based on distance vector algorithm, RIP uses hop count as the measurement standard.

- This chapter is marked `Only for Certain Devices`; treat all configuration commands as model-dependent.

## router rip

### Purpose
This router rip command is used to enable the RIP function on the switch. To disable this function, please use the no router rip command. You can specify to create a RIP instance under a certain VRF.

### Command Mode
Global Configuration Mode

### Syntax
```text
router rip [vrf vrf-name]
no router rip [vrf vrf-name]
```

### Parameters
```text
vrf-name: VRF instance name
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the RIP function of the switch in VRF v1:
Switch(config)#router rip vrf v1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## network

### Purpose
The network command is used to enable the RIP function on the corresponding interface of the configured network segment. To disable the RIP function on the corresponding interface, please use no network command.

### Command Mode
Router Configuration Mode

### Syntax
```text
network network number
no network network number
```

### Parameters
```text
network number: Network number, the format is 192.168.0.0. If you enter an IP address, the network number will be automatically obtained based on the mask length of the natural network segment. Entering 0.0.0.0 means enabling the RIP function on all interfaces.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the rip function of network segment 192.168.0.0:
Switch(config-router)#network 192.168.0.0
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## version

### Purpose
The version command is used to configure the version of packets sent and received by RIP. By default, the switch sends RIPv2 packets and receives RIPv1 and RIPv2 packets. To restore the default message version settings, please use the no version command.

### Command Mode
Router Configuration Mode

### Syntax
```text
version {1|2}
no version
```

### Parameters
```text
1: Send and receive RIPv1 messages.
2: Send and receive RIPv2 messages.
```

### Default
By default, the switch sends RIPv2 packets and receives RIPv1 and RIPv2 packets.

### Example
```text
Configure the RIP message version as RIPv1:
Switch(config-router)#version 1
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## timer basic

### Purpose
The timer basic command is used to configure the RIP timer. To restore the timer configuration to its default, please use the no timer basic command.

### Command Mode
Router Configuration Mode

### Syntax
```text
timer basic update-value timeout-value garbage-collect-value
no timer basic
```

### Parameters
```text
update-value: Routing table update time, ranging from 5 to 86400 seconds. The default value is 30.
timeout-value: Routing table aging time, ranging from 5 to 86400 seconds. The default value is 180.
garbage-collect-value: The expiration time after the routing entry is unreachable. When the entry is unreachable, the routing entry is removed from the routing table after the expiration time. The range is 5~86400 seconds, and the default value is 120.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set the routing table update time to 50 seconds, the routing table aging time to 100 seconds, and the routing entry expiration time to 100 seconds:
Switch(config-router)#timer basic 50 100 100
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## distance

### Purpose
The distance command is used to configure the management distance of RIP routing. To restore the default configuration, please use the no distance command.

### Command Mode
Router Configuration Mode

### Syntax
```text
distance distance
no distance
```

### Parameters
```text
distance: Management distance of RIP routing, ranging from 1 to 255. The default value is 120.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the management distance of RIP routing to100:
Switch(config-router)#distance 100
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## auto-summary

### Purpose
The auto-summary command is used to enable the automatic summary function of RIP. After this function is enabled, routing entries will be automatically summarized into natural network segments, which can reduce the number of routing entries issued for each update. To disable this function, use the no auto-summary command.

### Command Mode
Router Configuration Mode

### Syntax
```text
auto-summary
no auto-summary
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the automatic summary function of RIP:
Switch(config-router)#auto-summary
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## default-metric

### Purpose
The default-metric command is used to set the default metric for redirection routes. To restore the default configuration, please use the no default-metric command.

### Command Mode
Router Configuration Mode

### Syntax
```text
default-metric metric
no default-metric
```

### Parameters
```text
metric: The default metric of the redirect route, ranging from 1 to 15, and the default value is 1.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set the default metric for redirection routes to 5:
Switch(config-router)#default-metric 5
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## redistribute

### Purpose
The redistribute command is used to set the metric for redirection routes. To restore the default configuration, please use the no redistribute command.

### Command Mode
Router Configuration Mode

### Syntax
```text
redistribute { ospf process-id | connected | static } [ metric metric-value ]
no redistribute { ospf process-id | connected | static } [ metric ]
```

### Parameters
```text
ospf: Enable RIP redirect OSPF routing function.
process-id: Redirected OSPF process number.
connected: Enable RIP redirect direct routing function.
static: Enable RIP redirect static routing function.
metric-value: The metric of the redirect route.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set RIP to redirect ospf process 1, and set metric to 3:
Switch(config-router)#redistribute ospf 1 metric 3
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## allow-ecmp

### Purpose
The allow-ecmp command is used to enable the ECMP function. To disable this function, please use the no allow-ecmp command.

### Command Mode
Router Configuration Mode

### Syntax
```text
allow-ecmp
no allow-ecmp
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the ECMP function of RIP:
Switch(config-router)#allow-ecmp
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## default-information originate

### Purpose
The default-information originate command is used to introduce a default route into RIP. To disable this function, please use the no default-information originate command.

### Command Mode
Router Configuration Mode

### Syntax
```text
default-information originate
no default-information originate
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Introduce a default route into RIP:
Switch(config-router)#default-information originate
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## neighbor

### Purpose
The neighbor command is used to configure the neighbor of RIP. After configuring the neighbor, RIP will send RIP packets to the neighbor through unicast packets. To clear the neighbor configuration, please use the no neighbor command.

### Command Mode
Router Configuration Mode

### Syntax
```text
neighbor ip-address
no neighbor ip-address
```

### Parameters
```text
ip-address: IP address of RIP
s neighbor.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Specify 192.168.0.100 as the RIP neighbor:
Switch(config-router)#neighbor 192.168.0.100
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## passive-interface

### Purpose
The passive-interface command is used to configure the interface not to send RIP packets but only to receive RIP packets. A unicast response will be sent out when a neighbor is configured at the same time.To disable this function, please use the no passive-interface command.

### Command Mode
Router Configuration Mode

### Syntax
```text
passive-interface interface { fastEthernet | gigabitEthernet | hundred-gigabitEthernet | loopback | port-channel | ten-gigabitEthernet | twentyFive-gigabitEthernet | two-gigabitEthernet | vlan } interface-value
no passive-interface interface { fastEthernet | gigabitEthernet | hundred-gigabitEthernet | loopback | port-channel | ten-gigabitEthernet | twentyFive-gigabitEthernet | two-gigabitEthernet | vlan } interface-value
```

### Parameters
```text
interface-value: Specify the interface to be configured as passive-interface.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure VLAN 2 as passive-interface:
Switch(config-router)# passive-interface interface vlan 2
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip rip authentication mode

### Purpose
The ip rip authentication mode command is used to configure the authentication mode of RIP messages, and its no command is used to clear the configuration of authentication mode. The authentication function only takes effect when the authentication mode and password are configured.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip rip authentication mode { md5 | simple }
no ip rip authentication mode
```

### Parameters
```text
md5: Configure the authentication mode of RIP to md5 authentication.
simple: Configure the authentication mode of RIP to plain text authentication.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set the RIP authentication mode of VLAN 2 to md5 authentication:
Switch(config)#interface vlan 2
Switch(config-if)#ip rip authentication mode md5
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip rip authentication string

### Purpose
The ip rip authentication string command is used to configure the password and key ID for RIP authentication. The key ID is only used for md5 authentication.This command cannot be configured at the same time as the ip rip authentication key-chain command. To clear the password and key ID of RIP authentication, please use the no ip rip authentication string command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip rip authentication string password [ key-id key-id-value ]
no ip rip authentication string
```

### Parameters
```text
password: RIP authentication password, 16 characters at most.
key-id-value: Key ID for RIP authentication, ranging from 1 to 255. The default value is 1.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the rip authentication password of interface VLAN 2 as tplink and the key ID as 2:
Switch(config)#interface vlan 2
Switch(config-if)#ip rip authentication string tplink key-id 2
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip rip authentication key-chain

### Purpose
The ip rip authentication key-chain command is used to configure the password and key ID for RIP authentication by binding key-chain. This command cannot be configured at the same time as the ip rip authentication string command. To clear key-chain binding, please use the no ip rip authentication key-chain command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip rip authentication key-chain key-chain-name
no ip rip authentication key-chain
```

### Parameters
```text
key-chain-name: The name of the key-chain to be bound.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure key chain as 1, set key as 0, the corresponding password as tplink, and bind the RIP authentication of VLAN 1 to key chain 1:
Switch(config)#key chain 1
Switch (config-keychain)#key 0 key-string tplink
Switch (config-keychain)#exit
Switch (config)#interface vlan 1
Switch (config-if)#ip rip authentication key-chain 1
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip rip receive version

### Purpose
The ip rip receive version command is used to configure the version of RIP packets received by the interface. If the receive version of an interface is not configured, it will be determined by the global configuration. To restore the default configuration, please use the no ip rip receive version command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip rip receive version { 1 | 2 }
no ip rip receive version
```

### Parameters
```text
1: Configure the receive version of the interface to RIPv1.
2: Configure the receive version of the interface to RIPv2.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set the receive version of VLAN 1 to RIPv1:
Switch (config)#interface vlan 1
Switch (config-if)#ip rip receive version 1
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip rip send version

### Purpose
The ip rip send version command is used to configure the version of RIP packets sent by the interface. If the send version of an interface is not configured, it will be determined by the global configuration. To restore the default configuration, please use the no ip rip receive version command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip rip send version { 1 | 2 }
no ip rip send version
```

### Parameters
```text
1: Configure the send version of the interface to RIPv1.
2: Configure the send version of the interface to RIPv2.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set the send version of VLAN 1 to RIPv1:
Switch (config)#interface vlan 1
Switch (config-if)#ip rip send version 1
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip rip split-horizon

### Purpose
The ip rip split-horizon command is used to configure the split horizon function of the interface. This function is enabled by default. When this function is enabled, RIP will not send routing entries learned from this interface out of this interface. When this function is disabled, RIP will only send routing entries according to the routing table. To disable this function, please use the no ip rip split-horizon command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip rip split-horizon [ poison-reverse ]
no ip rip split-horizon
```

### Parameters
```text
poison-reverse: Enable the poison-reverse function of the interface. After this function is enabled, the entries learned from the interface will have the metric set to 16 before being sent out. Disable the poison reversal function by configuring the ip rip split-horizon command.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the poison-reverse function of VLAN 1:
Switch (config)#interface vlan 1
Switch (config-if)#ip rip split-horizon poison-reverse
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip rip v2-broadcast

### Purpose
The ip rip v2-broadcast command is used to enable the RIPv2 packet broadcast function of the interface. By default, RIPv2 messages are sent through multicast. After this function is enabled on an interface, RIPv2 messages on the interface are sent through broadcast. To disable this function, please use the no ip rip v2-broadcast command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip rip v2-broadcast
no ip rip v2-broadcast
```

### Parameters
No parameters.

### Default
By default, RIPv2 messages are sent through multicast.

### Example
```text
Enable the RIPv2 packet broadcast function of VLAN 1:
Switch (config)#interface vlan 1
Switch (config-if)#ip rip v2-broadcast
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## show ip rip

### Purpose
The show ip rip command is used to display the RIP routing table.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip rip [vrf vrf-name]
```

### Parameters
```text
vrf-name: VRF instance name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the RIP routing table of VRF v1:
Switch#show ip rip vrf v1
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## show ip rip status

### Purpose
The show ip rip status command is used to display the RIP status.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip rip [vrf vrf-name] status
```

### Parameters
```text
vrf-name: VRF instance name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the RIP status of VRF v1:
Switch#show ip rip status vrf v1
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## clear ip rip

### Purpose
The clear ip rip command is used to clear the routing entries for RIP learning and re-request routing information from other devices.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
clear ip rip [vrf vrf-name]
```

### Parameters
```text
vrf-name: VRF instance name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Clear the routing entries for RIP learning and rerequest routing information from of VRF v1:
Switch#clear ip rip vrf v1
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.
