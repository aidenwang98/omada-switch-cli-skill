# OSPFv3 Configuration Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 46 OSPFv3 Configuration Commands (Only for Certain Devices)

Location: extracted Word text lines 19681-20127

## Chapter Notes

Official documentation states: OSPF is an Interior Gateway Protocol (IGP) designed expressly for IP networks, supporting IP subnetting and tagging of externally derived routing information. OSPF also allows packet authentication and uses IP multicast when sending and receiving packets. Currently, OSPF Version 2 (RFC2328) is used for the IPv4 protocol; Use OSPF Version 3 (RFC2740) for IPv6 protocol. OSPFv3 is short for OSPF Version 3 and is the OSPF routing protocol running on IPv6 (RFC5340, same as RFC2740).

- This chapter is marked `Only for Certain Devices`; treat all configuration commands as model-dependent.

## ipv6 router ospf

### Purpose
The ipv6 router ospf command is used to enable an OSPFv3 routing process and enter the router configuration mode. To delete the specified OSPFv3 routing process, please use the no ipv6 router ospf command. When the OSPFv3 instance has not been created, this command is used to create an OSPFv3 instance and enter the Router configuration mode. When the command has a VRF name, it means that the OSPFv3 instance belongs to the VRF instance; if the VRF parameter is not specified, the OSPFv3 instance belongs to the public network after it is created. When the OSPFv3 instance has been created, using this command with or without the correct VRF name can enter the Router configuration mode.

### Command Mode
Global Configuration Mode

### Syntax
```text
ipv6 router ospf [vrf vrf-name]
no ipv6 router ospf [vrf vrf-name]
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
Create an OSPFv3 instance and add it to vrf1:
Switch(config)#ipv6 router ospf vrf vrf1
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## router-id

### Purpose
The router-id command is used to configure the router ID. The no router-id command is used to delete the configured router ID. If no router ID is configured manually or the configured router ID is deleted, the highest IPV6 address among all loopback interfaces will be chosen as the router ID.

### Command Mode
Router Configuration Mode

### Syntax
```text
Router-id router-id
no router-id
```

### Parameters
```text
router-id
The route ID in the format of dotted decimal notation. 0.0.0.0 is illegal.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the router ID of OSPFv3 routing process 1 as 1.1.1.1:
Switch(config)#ipv6 router ospf 1
Switch(config-router)#router-id 1.1.1.1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## maximum-paths

### Purpose
The maximum-paths command is used to configure the maximum number of the equal-cost multipath routings. To restore to default value, please use the no maximum-paths command.

### Command Mode
Router Configuration Mode

### Syntax
```text
maximum-paths number
no maximum-paths
```

### Parameters
```text
number
The maximum number of the equal-cost multipath routings, ranging from 1 to 32. The default value is 32.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the maximum number of the equal-cost multipath routings as 2:
Switch(config)#ipv6 router ospf
Switch(config-router)#maximum-paths 2
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## redistribute

### Purpose
The redistribute command is used to configure the ASBR to redistribute the external routes from other routing protocols to the OSPFv3 domain in type-5 LSAs. To restore the certain optional parameters to default values, please use the no redistribute command with corresponding parameters.

### Command Mode
Router Configuration Mode

### Syntax
```text
redistribute { connected | static | rip }
no redistribute { connected | static | rip }
```

### Parameters
```text
connected
Specify the external route type as connected.
static
Specify the external route type as static.
rip
Specify the external route type as RIPNG.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Redistribute the RIPNG routes from the external in the OSPFv3 domain.
Switch(config)#ipv6 router ospf
Switch(config-router)#redistribute rip
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## default-information originate

### Purpose
The default-information originate command is used to advertise the default route as AS-External LSA. To cancel the advertisement of the default route, please use the no default-information originate command without any optional parameters. To restore the certain parameters to default values, please use the no default-information originate command with corresponding parameters.

### Command Mode
Router Configuration Mode

### Syntax
```text
default-information originate [ always ] [ metric cost ] [ metric-type type ]
no default-information originate [ always ] [ metric cost ] [ metric-type type ]
```

### Parameters
```text
always
OSPFv3 will advertise the default route whether there is default route is the IPV6 routing table or not. If the parameter is not configured, OSPFv3 will advertise the default route only when there is default route in the IPV6 routing table.
cost
The default cost of the default route, ranging form 1 to 16777214. Its default value is 1.
type
The type of the external routes, either 1 or 2. The default value is 2.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure OSPF to advertise the default route whether there is default route is the IP routing table or not:
Switch(config)#router ospf 1
Switch(config-router)#default-information originate always
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## auto-cost

### Purpose
The auto-cost command is used to enable the auto computing function of the interface cost and configure the reference bandwidth. The interface cost is the ratio of the reference bandwidth to the interface bandwidth. To restore the reference bandwidth to default value, please use the no auto-cost reference-bandwidth command.

### Command Mode
Router Configuration Mode

### Syntax
```text
auto-cost reference-bandwidth bandwidth
no auto-cost reference-bandwidth
```

### Parameters
```text
bandwidth
The reference bandwidth, ranging from 1 to 4294967 Mbps. Its default value is 100Mbps.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the auto computing function of the interface cost and configure the reference bandwidth as 10000 Mbps:
Switch(config)#ipv6 router ospf
Switch(config-router)#auto-cost reference-bandwidth 10000
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## distance

### Purpose
The distance command is used to configure the OSPFv3 administrative distance. To restore to the default distance, please use the no distance command. The administrative distance represents the priority of the routes. The smaller administrative distance corresponds to higher priority. When different routing protocols possess the same route to the same destination, the route with the highest priority will be selected to add to the IPv6 routing table according to the administrative distance.

### Command Mode
Router Configuration Mode

### Syntax
```text
distance administrative-distance
no distance
```

### Parameters
```text
administrative-distance
Routing administrative distance, ranging from 1 to 254. Its default value is 110.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the OSPFV3 routing administrative distance as 100:
Switch(config)#ipv6 router ospf
Switch(config-router)#distance 100
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## distance ospf

### Purpose
The distance ospf command is used to configure the OSPFv3 distance for different types of routes. To restore to the default distance, please use the no distance command.

### Command Mode
Router Configuration Mode

### Syntax
```text
distance ospf { external distance | inter-area distance | intra-area distance }
no distance
```

### Parameters
```text
external
External type 5 and type 7 routes.
inter-area
Inter-area routes.
intra-area
Intra-area routes.
distance
Distance for different types of routes, ranging from 1 to 254. Its default value is 110.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the OSPFV3 routing administrative distance as 100:
Switch(config)#ipv6 router ospf
Switch(config-router)#distance 100
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## timers throttle spf

### Purpose
The timers throttle spf command is used to configure the computing delay and interval of the SPF, thus preventing the consumption of the CPU and memory caused by frequent SPF computing. To restore to the default value, please use the no timers throttle spf command.

### Command Mode
Router Configuration Mode

### Syntax
```text
timers throttle spf spf-delay spf-holdtime spf-max-holdtime
no timers throttle spf
```

### Parameters
```text
spf-delay
The delay time of the SPF computing, ranging from 1 to 600000 milliseconds. The default value is 0 milliseconds.
spf-holdtime
The minimum interval between two SPF computings, ranging from 1 to 600000 milliseconds. The default value is 50 milliseconds
spf-max-holdtime
The Maximum interval between two SPF computings, ranging from 1 to 600000 milliseconds. The default value is 5000 milliseconds
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the computing delay and interval of the SPF as 10 seconds:
Switch(config)#ipv6 router ospf
Switch(config-router)#timers throttle spf 10000 10000 50000
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## timers lsa arrival

### Purpose
The timers lsa arrival command is used to configure the time interval for OSPFv3 LSA reception. To restore to the default value, please use the no timers lsa arrival command.

### Command Mode
Router Configuration Mode

### Syntax
```text
timers lsa arrival delay-time
no timers lsa arrival
```

### Parameters
```text
delay-time
The time interval for OSPFv3 LSA reception, ranging from 1 to 600000 milliseconds. The default value is 1000 milliseconds.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the time interval for OSPFv3 LSA reception as 10 seconds:
Switch(config)#ipv6 router ospf
Switch(config-router)#timers lsa arrival 10000
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## area stub

### Purpose
The area stub command is used to define an area as a stub area. To restore the stub area to a normal one, please use the no area stub command. To restore the certain parameters to default values, please use the no area stub command with corresponding parameters.

### Command Mode
Router Configuration Mode

### Syntax
```text
area area-id stub [ no-summary ]
no area area-id stub [ no-summary ]
```

### Parameters
```text
area-id: The area ID, in the format of an IP address in dotted decimal notation or decimal value ranging from 0 to 4294967295.
no-summary
Configure the stub are as a totally stub area, where the ABR advertises neither the destinations in other areas nor the external routes. The stub area is not a totally stub area by default.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the area 1 as a totally stub area:
Switch(config)#ipv6 router ospf
Switch(config-router)#area 1 stub no-summary
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## area nssa

### Purpose
The area nssa command is used to define an area as a NSSA area. To restore the NSSA area to a normal one, please use the no area nssa command without any optional parameters. To restore the certain parameters to default values, please use the no area nssa command with corresponding parameters.

### Command Mode
Router Configuration Mode

### Syntax
```text
area area-id nssa [ no-summary ]
no area area-id nssa [ no-summary ]
```

### Parameters
```text
area-id: The area ID, in the format of an IP address in dotted decimal notation or decimal value ranging from 0 to 4294967295.
no-summary
Select to not send summary LSAs into the NSSA.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the Area 1 as a totally NSSA area:
Switch(config)#router ospf 1
Switch(config-router)# area 1 nssa no-summary
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## area range

### Purpose
The area range is to configure a summary route. To delete this route, please use the no area range command. By default no route is summarized. This command is only used with the ABR to summarize the route information of a certain area. The ABR only sends one summarized route of the routes in the aggregated segment to the other areas. An area can be configured with multiple summary segments, which can be aggregated by OSPF. If the no area range command is configured, the formally summarized routes will be redistributed.

### Command Mode
Router Configuration Mode

### Syntax
```text
area area-id range ipv6-address/mask-num [ advertise ] [ cost cost ] [ not-advertise ]
no area area-id range ip-address mask [ advertise ] [ cost cost ] [ not-advertise ]
```

### Parameters
```text
area-id: The area ID, in the format of an IP address in dotted decimal notation or decimal value ranging from 0 to 4294967295.
ipv6-address
The destination of the aggregated route.
mask-num
The network mask for aggregated route, in the format of mask bits.
cost
The cost of the aggregated route, ranging from 1 to 16777214. The default value is the maximum one of all the aggregated routes.
```

### Default
By default no route is summarized.

### Example
```text
Configure one aggregated route 2001::1/64 with the cost 10 in the Area 0:
Switch(config)# ipv6 router ospf
Switch(config-router)# area 0 range 2001::1/64 cost 10
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## ipv6 ospf area

### Purpose
The ipv6 ospf area is used to assign the interface to different regions. By default, the interface does not belong to any area. Only the interface attached to a certain area can receive ospfv3 packets normally. To restore to the default value, please use the no ipv6 ospf area command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip ospf area area-id [ instance-id instance-id ]
no ip ospf area area-id [ instance-id instance-id ]
```

### Parameters
```text
area-id: The area ID, in the format of an IP address in dotted decimal notation or decimal value ranging from 0 to 4294967295.
instance-id
The instance ID, ranging from 0 to 255. OSPFv3 supports running multiple instances on a single link, using the optional parameter instance-id as the instance identifier. The instance number only affects the reception of OSPFv3 messages. By default, this parameter value is 0. To restore the default value, use the no ipv6 ospf area area-id instance-id command.
```

### Default
By default, the interface does not belong to any area. By default, this parameter value is 0.

### Example
```text
Assign interface VLAN 2 to area 10:
Switch(config)#interface vlan 2
Switch(config-if)#ipv6 ospf area 10
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## ipv6 ospf cost

### Purpose
The ipv6 ospf cost is used to configure the interface cost. To restore to the default value, please use the no ipv6 ospf cost command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ipv6 ospf cost cost
no ipv6 ospf cost
```

### Parameters
```text
cost
The interface cost, ranging from 1 to 65535. The default value is calculated according to the bandwidth.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the cost of interface VLAN 2 as 10:
Switch(config)#interface vlan 2
Switch(config-if)#ipv6 ospf cost 10
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## ipv6 ospf retransmit-interval

### Purpose
The ipv6 ospf retransmit-interval command is used to configure the interval to retransmit the LSA, DD and LSR packets on the specified interface. To restore to default value, please use the no ipv6 ospf retransmit-interval command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
Ipv6 ospf retransmit-interval interval
no ipv6 ospf retransmit-interval
```

### Parameters
```text
interval
The retransmit interval, ranging from 1 to 65535 seconds. The default value is 5 seconds.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the retransmission interval of interface VLAN 2 as 10 seconds:
Switch(config)#interface vlan 2
Switch(config-if)#ipv6 ospf retransmit-interval 10
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## ipv6 ospf transmit-delay

### Purpose
The ipv6 ospf transmit-delay is used to configure the transmission delay of LSA on the specified interface. To restore to default value, please use the no ipv6 ospf transmit-delay.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ipv6 ospf transmit-delay delay
no ipv6 ospf transmit-delay
```

### Parameters
```text
delay
The LSA transmission delay, ranging from 1 to 3600 seconds. The default value is 1 second.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the LSA transmission delay of interface VLAN 2 as 2 seconds.
Switch(config)#interface vlan 2
Switch(config-if)#ipv6 ospf retransmit-delay 2
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## ipv6 ospf priority

### Purpose
The ipv6 ospf priority is used to configure the priority of the specified interface. To restore to the default value, please use the no ipv6 ospf priority command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ipv6 ospf priority pri
no ipv6 ospf priority
```

### Parameters
```text
pri
The priority of the interface, ranging from 0 to 255 and the default value is 1. Interface with the priority 0 cannot be elected as DR or BDR.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the priority of the interface VLAN 2 as 1:
Switch(config)#interface vlan 2
Switch(config-if)#ipv6 ospf priority 1
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## ipv6 ospf hello-interval

### Purpose
The ipv6 ospf hello-interval is used to configure the hello intervals on the specified interface. To restore to the default value, please use the no ipv6 ospf hello-interval command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ipv6 ospf hello-interval interval
no ipv6 ospf hello-interval
```

### Parameters
```text
Interval
The interval of the hello packets, ranging from 1 to 65535 seconds and the default value is 10 seconds.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the interval of the hello packets sent on interface VLAN 2 as 20 seconds:
Switch(config)#interface vlan 2
Switch(config-if)#ipv6 ospf hello-interval 20
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## ipv6 ospf dead-interval

### Purpose
The ipv6 ospf dead-interval command is used to set the number of seconds after the last device hello packet was seen before its neighbors declare the OSPFv3 router to be down. To restore to default value, please use the no ipv6 ospf dead-interval command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ipv6 ospf dead-interval interval
no ipv6 ospf dead-interval
```

### Parameters
```text
Interval
The interval of the hello packets, ranging from 1 to 65535 seconds and the default value is 10 seconds.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the neighbor
s failure interval on interface VLAN 2 as 50 seconds:
Switch(config)#interface vlan 2
Switch(config-if)#ipv6 ospf dead-interval 50
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## ipv6 ospf network

### Purpose
The ipv6 ospf network command is used to configure the network type on the specified interface. To restore to default, please use the no ipv6 ospf network command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ipv6 ospf network { broadcast | point-to-point }
no ipv6 ospf network
```

### Parameters
```text
broadcast
The broadcast network type. It is the default value.
point-to-point
The point-to-point network type.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the network type on interface VLAN 2 as broadcast:
Switch(config)#interface vlan 2
Switch(config-if)#ipv6 ospf network broadcast
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## ipv6 ospf mtu-ignore

### Purpose
The ipv6 ospf mtu-ignore command is used to ignore the MTU check in the DD exchanging process. This check is scheduled by default and the adjacency relationship will not establish if the MTUs are not matched. To restore to the default value, please use the no ipv6 ospf mtu-ignore command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ipv6 ospf mtu-ignore
no ipv6 ospf mtu-ignore
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure interface VLAN 2 to ignore the MTU field check in the DD exchange process:
Switch(config)#interface vlan 2
Switch(config-if)#ipv6 ospf mtu-ignore
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## ipv6 ospf passive

### Purpose
The ipv6 ospf passive command is used to prevent an interface from sending OSPFv3 packets. To restore to the default settings, please use no ipv6 ospf passive command. The interface is allowed to send OSPFv3 packets by default.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ipv6 ospf passive
no ipv6 ospf passive
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Prevent interface VLAN 2 from sending OSPFv3 packets:
Switch(config)#interface vlan 2
Switch(config-if)#ipv6 ospf passive
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## clear ipv6 ospf

### Purpose
The clear ipv6 ospf command is used to reset the OSPFv3 process, which will clear all the dynamic information. The clear ipv6 ospf process command will reset the OSPFv3 process. The clear ipv6 ospf interface command will reset the configuration of the interface in the OSPFv3 process.

### Command Mode
Privileged EXEC Mode

### Syntax
```text
clear ipv6 ospf { process | interface }
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Reset the OSPFv3 process:
Switch#clear ipv6 ospf process
Reset selected OSPFv3 processes? (Y/N):y
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## show ipv6 ospf

### Purpose
The show ipv6 ospf is used to display the global information of the OSPFv3 process.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ipv6 ospf
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the global information of the OSPFv3 processes:
Switch#show ipv6 ospf
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## show ipv6 ospf database

### Purpose
The show ip ospf database command is used to display the LSDB.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ipv6 ospf database
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the LSDB in OSPFv3 process:
Switch#show ipv6 ospf database
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## show ipv6 ospf interface

### Purpose
The show ipv6 ospf interface command is used to display the interface information.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ipv6 ospf interface
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the information of the interfaces in the OSPFv3 process:
Switch#show ipv6 ospf interface
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## show ipv6 ospf neighbor

### Purpose
The show ipv6 ospf neighbor command is used to display information of the OSPFv3 neighbor.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ipv6 ospf neighbor
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the neighbors
detailed information in OSPFv3 process:
Switch#show ipv6 ospf neighbor
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## show ipv6 ospf border-routers

### Purpose
The show ipv6 ospf border-routers is used to display the routing tables of the ABR/ASBR.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ipv6 ospf border-routers
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the ABR/ASBR routing tables of the OSPFv3 proces:
Switch#show ipv6 ospf border-routers
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## show ipv6 ospf rib

### Purpose
The show ipv6 ospf rib command is used to display the OSPFv3 routing table.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ipv6 ospf route
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the routing tables of OSPFv3:
Switch#show ipv6 ospf rib
```

### Notes
- Availability: Only for certain devices according to the official chapter title.
