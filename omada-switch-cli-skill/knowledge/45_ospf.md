# OSPF Configuration Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 45 OSPF Configuration Commands (Only for Certain Devices)

Location: extracted Word text lines 18964-19680

## Chapter Notes

Official documentation states: OSPF is an Interior Gateway Protocol (IGP) designed expressly for IP networks, supporting IP subnetting and tagging of externally derived routing information. OSPF also allows packet authentication and uses IP multicast when sending and receiving packets. Currently, OSPF Version 2 (RFC2328) is used for the IPv4 protocol; Use OSPF Version 3 (RFC2740) for IPv6 protocol. Unless otherwise specified, the OSPF referred to in this chapter is OSPF Version 2.

- This chapter is marked `Only for Certain Devices`; treat all configuration commands as model-dependent.

## router ospf

### Purpose
When the OSPFv2 instance specified by the process-id has not been created, this command is used to create an OSPFv2 instance and enter Router configuration mode. If a vrf name is specified when using the command, it indicates that this OSPFv2 instance belongs to the specified VRF instance. If the vrf parameter is not specified, the created OSPFv2 instance will belong to the public network. When the OSPFv2 instance specified by the process-id already exists, using this command with the correct vrf name (or without the vrf parameter) will allow entry into Router configuration mode. The no command is used to delete the OSPFv2 instance. When the vrf parameter is not specified, the corresponding instance will be deleted based on the process-id.

### Command Mode
Global Configuration Mode

### Syntax
```text
router ospf process-id [vrf vrf-name]
no router ospf process-id [vrf vrf-name]
```

### Parameters
```text
process-id: Process ID, ranging from 1 to 65535. Sixteen processes can be created at most.
vrf-name: VRF instance name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Create an OSPFv2 instance with process ID 1 and add it to vrf1:
Switch(config)#router ospf 1 vrf vrf1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## router-id

### Purpose
The router-id command is used to configure the router ID. To delete the configured router-id, please use the no router-id command.

### Command Mode
Router Configuration Mode

### Syntax
```text
Router-id router-id
no router-id
```

### Parameters
```text
router-id: The route ID in the format of dotted decimal notation. 0.0.0.0 is illegal.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the router ID of OSPF routing process 1 as 1.1.1.1:
Switch(config)#router ospf 1
Switch(config-router)#router-id 1.1.1.1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## network

### Purpose
This network command is used to configure the network of a specified area. All the interfaces fallen into the configured network will belong to this area. To delete the specified network and its corresponding interfaces from this area, please use the no network command.

### Command Mode
Router Configuration Mode

### Syntax
```text
network ip-address wildcard-mask area area-id
no network ip-address wildcard-mask area area-id
```

### Parameters
```text
ip-address: The IP address of the network.
wildcard-mask: The wildcard mask of the network (such as 0.0.0.255). The subnet mask is also compatible (such as 255.0.0.0).
area-id: The area ID, in the format of an IP address in dotted decimal notation or decimal value ranging from 0 to 4294967295.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the network 192.168.0.0/24 in the area 0.0.0.0:
Switch(config)#router ospf 1
Switch(config-router)# network 192.168.0.0 255.255.255.0 area 0.0.0.0
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
number: The maximum number of the equal-cost multipath routings, ranging from 1 to 32. The default value is 32.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the maximum number of the equal-cost multipath routings as 2:
Switch(config)#router ospf 1
Switch(config-router)#maximum-paths 2
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## redistribute

### Purpose
The redistribute command is used to configure the ASBR to redistribute the external routes from other routing protocols to the OSPF domain in type-5 LSAs. To restore the certain optional parameters to default values, please use the no redistribute command with corresponding parameters.

### Command Mode
Router Configuration Mode

### Syntax
```text
redistribute { connected | static | rip | ospf process-id } [ metric cost ] [ metric-type type ]
no redistribute { connected | static | rip | ospf process-id } [ metric cost ] [ metric-type type ]
```

### Parameters
```text
connected: Specify the external route type as connected.
static: Specify the external route type as static.
rip: Specify the external route type as RIP.
ospf: Specify the external route type as OSPF.
process-id: The OSPF routing process ID, ranging from 1 to 65535. It
s not allowed to
redirect to the own process, for example, OSPF process 1 cannot redirect itself.
cost: The cost of the external routes, ranging from 1 to 16777214. Its default value is
defined in the command default-metric.
type: The type of the external routes, either 1 or 2. The default value is 2.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Redistribute the RIP routes from the external and advertise them as type 1 external routes in the OSPF domain:
Switch(config)#router ospf 1
Switch(config-router)#redistribute rip metric-type 1
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## default-metric

### Purpose
The default-metric command is used to configure the default cost of the redistributing external route. To restore to the default value, please use the no default-metric command.

### Command Mode
Router Configuration Mode

### Syntax
```text
default-metric cost
no default-metric
```

### Parameters
```text
cost: The default cost of the redistributing external route, ranging form 1 to 16777214.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the default cost of the redistributing external route as 12:
Switch(config)#router ospf 1
Switch(config-router)#default-metric 12
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## default-metric (2)

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
always: OSPF will advertise the default route whether there is default route is the IP routing table or not. If the parameter is not configured, OSPF will advertise the default route only when there is default route in the IP routing table.
cost: The default cost of the default route, ranging form 1 to 16777214. Its default value is 1.
type: The type of the external routes, either 1 or 2. The default value is 2.
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
bandwidth: The reference bandwidth, ranging from 1 to 4294967 Mbps. Its default value is 100Mbps.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the auto computing function of the interface cost and configure the reference bandwidth as 10000 Mbps:
Switch(config)#router ospf 1
Switch(config-router)#auto-cost reference-bandwidth 10000
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## distance

### Purpose
The distance command is used to configure the OSPF administrative distance. To restore to the default distance, please use the no distance command. The administrative distance represents the priority of the routes. The smaller administrative distance corresponds to higher priority. When different routing protocols possess the same route to the same destination, the route with the highest priority will be selected to add to the IP routing table according to the administrative distance.

### Command Mode
Router Configuration Mode

### Syntax
```text
distance administrative-distance
no distance
```

### Parameters
```text
administrative-distance: Routing administrative distance, ranging from 1 to 255. Its default value is 110. When this value is set to 255, it indicates that the source of routing information is unreliable and all related routes are ignored.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the OSPF routing administrative distance as 100:
Switch(config)#router ospf 1
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
spf-delay: The delay time of the SPF computing, ranging from 1 to 600000 milliseconds. The default value is 0 milliseconds.
spf-holdtime: The minimum interval between two SPF computings, ranging from 1 to 600000 milliseconds. The default value is 50 milliseconds.
spf-max-holdtime: The Maximum interval between two SPF computings, ranging from 1 to 600000 milliseconds. The default value is 5000 milliseconds.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the computing delay and interval of the SPF as 10 seconds:
Switch(config)#router ospf 1
Switch(config-router)#timers throttle spf 10000 10000 50000
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## compatible rfc 1583

### Purpose
The compatible rfc 1583 command is used to configure the OSPF s compatibility for the routing rules in the RFC 1583. To cancel the compatibility, please use the no compatible rfc1583 command. It is compatible by default.

### Command Mode
Router Configuration Mode

### Syntax
```text
compatible rfc1583
no compatible rfc1583
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the OSPF
s compatibility for the routing rules in RFC 1583:
Switch(config)#router ospf 1
Switch(config-router)#compatible rfc1583
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
area-id: The area ID, in the format of an IP address in dotted decimal notation or decimal value ranging from 1 to 4294967295.
no-summary: Configure the stub are as a totally stub area, where the ABR advertises neither the destinations in other areas nor the external routes. The stub area is not a totally stub area by default
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the area 1 as a totally stub area:
Switch(config)#router ospf 1
Switch(config-router)# area 1 stub no-summary
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
area area-id nssa [no summary | default-information-originate [ metric cost ] [ metrictype type]]
no area-id nssa [no summary | default-information-originate [ metric cost ] [ metrictype type]]
```

### Parameters
```text
area-id: The area ID, in the format of an IP address in dotted decimal notation or decimal value ranging from 1 to 4294967295.
no-summary: Configure the NSSA area as a totally NSSA area, where the ABR advertises neither the destinations in other areas nor the external routes. The NSSA area is not a totally NSSA area by default.
default-information-originate: Enable or disable advertising default route into NSSA area by sending a NSSA-External LSA. OSPF will not advertise default route if this parameter is not specified
cost: The default cost of the default route, ranging form 1 to 16777214. Its default value is 1.
type: The type of the external routes, either 1 or 2. The default value is 2.
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

## area default-cost

### Purpose
The area default-cost command is used to configure the cost of default route sent from ABR to stub or NSSA area.

### Command Mode
Router Configuration Mode

### Syntax
```text
area area-id default-cost cost
no area area-id default-cost
```

### Parameters
```text
area-id: The area ID, in the format of an IP address in dotted decimal notation or decimal value ranging from 1 to 4294967295.
cost: The cost value. It ranges from 1 to 16777214 and the default value is 1.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the cost of default route sent to Area 1 as 10:
Switch(config)#router ospf 1
Switch(config-router)#area 1 nssa
Switch(config-router)#area 1 default-cost 10
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## area range

### Purpose
The area range command is used to configure a summary route. To delete this route, please use the no area range command. By default no route is summarized. This command is only used with the ABR to summarize the route information of a certain area. The ABR only sends one summarized route of the routes in the aggregated segment to the other areas. An area can be configured with multiple summary segments, which can be aggregated by OSPF. If the no area range command is configured, the formally summarized routes will be redistributed.

### Command Mode
Router Configuration Mode

### Syntax
```text
area area-id range ip-address mask [ advertise ] [ cost cost ] [ not-advertise ]
no area area-id range ip-address mask [ advertise ] [ cost cost ] [ not-advertise ]
```

### Parameters
```text
area-id: The area ID, in the format of an IP address in dotted decimal notation or decimal value ranging from 0 to 4294967295.
ip-address: The destination of the aggregated route.
mask: The network mask of the aggregated route, in the format of dotted decimal notation.
advertise: Allow route aggregation of ABR broadcast.
not-advertise: Suppress route aggregation of ABR broadcast.
cost: The cost of the aggregated route, ranging from 1 to 16777214. The default value is the maximum one of all the aggregated routes. The cost parameter can be configured only when the advtise parameter is enabled. When configured as not-advtise, the cost parameter will be restored to the default value.
```

### Default
By default no route is summarized.

### Example
```text
Configure one aggregated route 100.100.0.0/16 with the cost 10 in the Area 0:
Switch(config)#router ospf 1
Switch(config-router)#area 0 range 100.100.0.0 255.255.0.0 cost 10
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## area authentication

### Purpose
The area authentication command is used to configure the authentication type of the ospf process. The process is not authenticated by default. To restore to default value, please use the no area authentication command.

### Command Mode
Router Configuration Mode

### Syntax
```text
area area-id authentication [ message-digest ]
no area authentication
```

### Parameters
```text
area-id: The area ID, in the format of an IP address in dotted decimal notation or decimal value ranging from 0 to 4294967295.
message-digest: Configure the configuration type as MD5.
If no authentication mode is specified here, the default mode will be simple authentication.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the authentication method to MD5 in the Area 0:
Switch(config)#router ospf 1
Switch(config-router)#area 0 authentication message-digest
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## area virtual-link

### Purpose
The area virtual-link command is used to configure the virtual-link. To delete the configured virtual-link, please use the no area virtual-link without any optional parameters. To restore the certain parameters to default values, please use the no area virtual-link command with corresponding parameters.

### Command Mode
Router Configuration Mode

### Syntax
```text
area transit-area virtual-link router-id [ dead-interval dead-interval ] [ hello-interval hello-interval ] [ retransmit-interval rtx-interval ] [ transmit-delay trans-delay ]
no area transit-area virtual-link router-id
```

### Parameters
```text
transit-area: The area ID, in the format of an IP address in dotted decimal notation or decimal value ranging from 1 to 4294967295.
router-id: The ID of the neighboring router on the opposite end of the virtual link, in the format of dotted decimal notation.
hello-interval: The interval of the hello packets, ranging from 1 to 65535 seconds and the default value is 10 seconds.
dead-interval: The time after which the neighbor becomes invalid. It ranges from 1 to 65535 seconds and the default value is 4 times as the hello-interval.
rtx-interval: The retransmission interval of the LSA, DD and LSR packets. It ranges from 1 to 65535 seconds and the default value is 5 seconds.
trans-delay: The LSA transmission delay. It ranges from 1 to 65535 seconds and the default value is 1 seconds.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure a virtual-link with the transmission area as Area 1 and the ID of the neighboring router on the other endpoint as 1.1.1.1:
Switch(config)#router ospf 1
Switch(config-router)#area 1 virtual-link 1.1.1.1
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## area virtual-link authentication

### Purpose
The area virtual-link authentication command is used to configure the authentication type of the virtual link. The virtual link is not authenticated by default. To restore to default value, please use the no area virtual-link authentication command.

### Command Mode
Router Configuration Mode

### Syntax
```text
area transit-area virtual-link router-id authentication [ message-digest | null ]
no area transit-area virtual-link router-id authentication
```

### Parameters
```text
transit-area: The transition area ID in the format of an IP address in dotted decimal notation or decimal value ranging from 1 to 4294967295.
router-id: The ID of the neighboring router on the other endpoint of the virtual link, in the format of dotted decimal notation.
message-digest: Configure the configuration type as MD5.
null: No authentication. By default it is no authentication.
If no authentication mode is specified here, the default mode will be simple authentication.
```

### Default
By default it is no authentication.

### Example
```text
Configure simple authentication as the authentication mode of a virtual-link with the transmission area as Area 2 and the ID of the neighboring router on the other endpoint as 3.3.3.3:
Switch(config)#router ospf 1
Switch(config-router)#area 2 virtual-link 3.3.3.3 authentication
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## area virtual-link authentication-key

### Purpose
The area virtual-link authentication-key command is used to configure the simple authentication key. To delete the key, please use the no area virtual-link authentication-key command.

### Command Mode
Router Configuration Mode

### Syntax
```text
area transit-area virtual-link router-id authentication-key [0|7]password
no area transit-area virtual-link router-id authentication-key
```

### Parameters
```text
transit-area: The transition area ID in the format of an IP address in dotted decimal notation or decimal value ranging from 1 to 4294967295.
router-id: The ID of the neighboring router on the other endpoint of the virtual link, in the format of dotted decimal notation.
[0|7]: Key form, 0 represents plaintext, 7 represents ciphertext.
password: A string from 1 to 8 alphanumeric characters or symbols. The password is case-sensitive, and cannot contain question marks. By default, it is empty.
```

### Default
By default, it is empty.

### Example
```text
Configure the authentication mode of a virtual-link as simple authentication, with the transmission area as Area 2 and the ID of the neighboring router on the other endpoint as 3.3.3.3, and the authentication key as 123456:
Switch(config)#router ospf 1
Switch(config-router)#area 2 virtual-link 3.3.3.3 authentication-key 123456
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## area virtual-link message-digest-key

### Purpose
The area virtual-link message-digest-key is used to configure the MD5 authentication ID and key of the virtual-link. To delete the specified configuration, please use the no area virtual-link message-digest- key command.

### Command Mode
Router Configuration Mode

### Syntax
```text
area transit-area virtual-link router-id message-digest-key id md5 [0|7] password
no area transit-area virtual-link router-id message-digest-key id
```

### Parameters
```text
transit-area: The transition area ID in the format of an IP address in dotted decimal notation or decimal value ranging from 1 to 4294967295.
router-id: The ID of the neighboring router on the other endpoint of the virtual link, in the format of dotted decimal notation.
id: The key ID of the MD5, ranging from 1 to 255.
[0|7]: Key form, 0 represents plaintext, 7 represents ciphertext.
password: A string from 1 to 16 alphanumeric characters or symbols. The password is case-sensitive, and cannot contain question marks. By default, it is empty.
```

### Default
By default, it is empty.

### Example
```text
Configure the authentication mode of a virtual-link as md5 authentication, with the transmission area as Area 2 and the ID of the neighboring router on the other endpoint as 3.3.3.3, with the authentication ID as 2 and the authentication key as 123456:
Switch(config)#router ospf 1
Switch(config-router)#area 2 virtual-link 3.3.3.3 message-digest- key 2 md5 123456
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## capability opaque

### Purpose
The capability opaque is used to enable the Opaque LSA feature. To disable this feature, please use the no capability opaque command.

### Command Mode
Router Configuration Mode

### Syntax
```text
capability opaque
no capability opaque
```

### Parameters
```text
None
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the Opaque LSA feature:
Switch(config)#router ospf 1
Switch(config-router)#capability opaque
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## graceful-restart

### Purpose
The graceful-restart is used to enable the OSPF GR feature. Before performing a graceful restart, ensure that the GR Restarter is configured with this feature. To disable this feature, please use the no graceful-restart command.

### Command Mode
Router Configuration Mode

### Syntax
```text
graceful-restart
no graceful-restart
```

### Parameters
```text
None
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the OSPF GR feature:
Switch(config)#router ospf 1
Switch(config-router)#graceful-restart
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## graceful-restart grace-period

### Purpose
The graceful-restart grace-period is used to configure the graceful restart period, that is, the maximum time required for the graceful restart process. If the actual restart time exceeds this value, the graceful restart will fail. To restore the default configuration, please use the no graceful-restart grace-period command.

### Command Mode
Router Configuration Mode

### Syntax
```text
graceful-restart grace-period period
no graceful-restart grace-period period
```

### Parameters
```text
period: Graceful restart period, ranging from 1 to 1800 seconds, and the default value is 120.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the graceful restart period to 180 seconds:
Switch(config)#router ospf 1
Switch(config-router)#graceful-restart grace-period 180
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## graceful-restart helper

### Purpose
The graceful-restart helper is used to enable the GR Helper feature to assist the GR Restarter in its graceful restart process. To restore the default configuration, please use the no graceful-restart helper command.

### Command Mode
Router Configuration Mode

### Syntax
```text
graceful-restart helper [ rid ]
no graceful-restart helper [ rid ]
```

### Parameters
```text
rid: GR Helper is supported for the neighboring GR Restarter whose router-id is rid. If rid is not specified, GR Helper is supported for all neighboring GR Restarters by default.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure GR Helper to support graceful restart for all neighboring GR Restarters:
Switch(config)#router ospf 1
Switch(config-router)#graceful-restart helper
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## graceful-restart helper planned-only

### Purpose
The graceful-restart helper planned-only is used to configure the GR Helper to only support planned-only restart function, which is disabled by default. To restore the default configuration, please use the no graceful-restart helper planned-only command.

### Command Mode
Router Configuration Mode

### Syntax
```text
graceful-restart helper planned-only
no graceful-restart helper planned-only
```

### Parameters
```text
None.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the GR Helper to support planned-only restart function:
Switch(config)#router ospf 1
Switch(config-router)#graceful-restart helper planned-only
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## graceful-restart helper strict-lsa-checking

### Purpose
The graceful-restart helper strict-lsa-checking is used to configure the GR Helper to strictly check LSA, which is disabled by default. When this function is configured, once the LSAs of the GR Restarter and the GR Helper do not match, the graceful restart will be failed. To restore the default configuration, please use the no graceful-restart helper strict-lsa-checking command.

### Command Mode
Router Configuration Mode

### Syntax
```text
graceful-restart helper strict-lsa-checking
no graceful-restart helper strict-lsa-checking
```

### Parameters
```text
None.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the GR Helper to strictly check LSA:
Switch(config)#router ospf 1
Switch(config-router)#graceful-restart helper strict-lsa-checking
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## ip ospf cost

### Purpose
The ip ospf cost is used to configure the interface cost. To restore to the default value, please use the no ip ospf cost command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip ospf cost cost
no ip ospf cost
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
Switch(config-if)# ip ospf cost 10
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## ip ospf retransmit-interval

### Purpose
The ip ospf retransmit-interval command is used to configure the interval to retransmit the LSA, DD and LSR packets on the specified interface. To restore to default value, please use the no ip ospf retransmit-interval command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip ospf retransmit-interval interval
no ip ospf retransmit-interval
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
Switch(config-if)#ip ospf retransmit-interval 10
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## ip ospf transmit-delay

### Purpose
The ip ospf transmit-delay is used to configure the transmission delay of LSA on the specified interface. To restore to default value, please use the no ip ospf transmit-delay.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip ospf transmit-delay delay
no ip ospf transmit-delay
```

### Parameters
```text
delay
The LSA transmission delay, ranging from 1 to 65535 seconds. The default value is 1 second.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the LSA transmission delay of interface VLAN 2 as 2 seconds.
Switch(config)#interface vlan 2
Switch(config-if)#ip ospf retransmit-delay 2
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## ip ospf priority

### Purpose
The ip ospf priority is used to configure the priority of the specified interface. To restore to the default value, please use the no ip ospf priority command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip ospf priority pri
no ip ospf priority
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
Switch(config-if)#ip ospf priority 1
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## ip ospf hello-interval

### Purpose
The ip ospf hello-interval is used to configure the hello intervals on the specified interface. To restore to the default value, please use the no ip ospf hello-interval command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip ospf hello-interval interval
no ip ospf hello-interval
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
Switch(config-if)#ip ospf hello-interval 20
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## ip ospf dead-interval

### Purpose
The ip ospf dead-interval command is used to set the number of seconds after the last device hello packet was seen before its neighbors declare the OSPF router to be down. To restore to default value, please use the no ip ospf dead-interval command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip ospf dead-interval interval
no ip ospf dead-interval
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
Switch(config-if)#ip ospf dead-interval 50
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## ip ospf authentication

### Purpose
The ip ospf authentication command is used to configure the authentication mode of the specified interface. To restore to default value, please use the no ip ospf authentication command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip ospf authentication [ message-digest ] [ null ]
no ip ospf authentication
```

### Parameters
```text
message-digest
Specify the authentication type as MD5.
null
No authentication. By default it is no authentication.
If no authentication mode is specified here, the default mode will be simple authentication.
```

### Default
By default it is no authentication.

### Example
```text
Configure the authentication type of interface VLAN 2 as MD5:
Switch(config)#interface vlan 2
Switch(config-if)#ip ospf authentication message-digest
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## ip ospf authentication-key

### Purpose
The ip ospf authentication-key command is used to configure the key of the simple authentication. To cancel this configuration, please use the no ip ospf authentication-key command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip ospf authentication-key password
no ip ospf authentication-key
```

### Parameters
```text
password
Super password, a string from 1 to 8 alphanumeric characters or symbols. The password is case sensitive, allows spaces but ignores leading spaces, and cannot contain question marks. By default, it is empty.
```

### Default
By default, it is empty.

### Example
```text
Configure the authentication mode of interface VLAN 2 as simple authentication, and the password as 123:
Switch(config)#interface vlan 2
Switch(config-if)#ip ospf authentication-key 123
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## ip ospf message-digest-key

### Purpose
The ip ospf message-digest-key is used to configure the ID and password of the md5 authentication on the specified interface. To cancel the configuration, please use no ip ospf message-digest-key command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip ospf message-digest-key id md5 password
no ip ospf message-digest-key id
```

### Parameters
```text
The ID of the md5 authentication key, ranging from 1 to 255.
password
A string from 1 to 16 alphanumeric characters or symbols. The password is case sensitive, and cannot contain question marks. Key configuration is required to take effect.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure md5 authentication key ID as 1 and password as abc on interface VLAN 2:
Switch(config)#interface vlan 2
Switch(config-if)#ip ospf message-digest-key 1 md5 abc
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## ip ospf network

### Purpose
The ip ospf network command is used to configure the network type on the specified interface. To restore to default, please use the no ip ospf network command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip ospf network { broadcast | non-broadcast | point-to-multipoint | point-to-point }
no ip ospf network
```

### Parameters
```text
broadcast
The broadcast network type. It is the default value.
non-broadcast
The NBMA network type.
point-to-multipoint
The point-to-multipoint network type.
point-to-point
The point-to-point network type.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the network type on interface VLAN 2 as broadcast:
Switch(config)#interface vlan 2
Switch(config-if)#ip ospf network broadcast
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## ip ospf mtu-ignore

### Purpose
The ip ospf mtu-ignore command is used to ignore the MTU check in the DD exchanging process. This check is scheduled by default and the adjacency relationship will not establish if the MTUs are not matched. To restore to the default value, please use the no ip ospf mtu-ignore command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip ospf mtu-ignore
no ip ospf mtu-ignore
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure interface VLAN 2 to ignore the MTU field check in the DD exchange process:
Switch(config)#interface vlan 2
Switch(config-if)#ip ospf mtu-ignore
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## ip ospf passive

### Purpose
The ip ospf passive command is used to prevent an interface from sending OSPF packets. To restore to the default settings, please use no ip ospf passive command. The interface is allowed to send OSPF packets by default.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip ospf passive
no ip ospf passive
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Prevent interface VLAN 2 from sending OSPF packets:
Switch(config)#interface vlan 2
Switch(config-if)#ip ospf passive
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## clear ip ospf

### Purpose
The clear ip ospf command is used to reset the OSPF process, which will clear all the dynamic information. The clear ip ospf process command will reset all the OSPF processes.

### Command Mode
Privileged EXEC Mode

### Syntax
```text
clear ip ospf [ process-id ]
clear ip ospf process
```

### Parameters
```text
process-id
The process ID, ranging from 1 to 65535.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Reset all the OSPF processes:
Switch#clear ip ospf process
Reset selected OSPF processes? (Y/N):y
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## show ip ospf

### Purpose
The show ip ospf is used to display the global information of the OSPF process.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip ospf [ process-id ]
```

### Parameters
```text
process-id
The process ID, ranging from 1 to 65535. The global information of all the OSPF processes will be displayed if no process-id is specified.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the global information of all the OSPF processes:
Switch#show ip ospf
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## show ip ospf database

### Purpose
The show ip ospf database command is used to display the LSDB. The detailed LSA information will be displayed if the LSA type is specified. The LSDB summary information will be displayed if the LSA type is not specified.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip ospf [ process-id ] database [ asbr-summary | external | network | nssa-external | router | summary ]
```

### Parameters
```text
process-id
The process ID, ranging from 1 to 65535. The LSDBs of all processes will be displayed if no process ID is specified.
asbr-summary | external | network | nssa-external | router | summary
The LSA type.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the detailed information of router-LSA in process 1:
Switch#show ip ospf 1 database router
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## show ip ospf interface

### Purpose
The show ip ospf interface command is used to display the interface information.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip ospf [ process-id ] interface [ interface-name interface-number ]
```

### Parameters
```text
process-id
The process ID. The information of all the processes will be displayed if process ID is not specified.
interface-name interface-number
Specify the interface name and number to display the interface
s detailed information.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the information of the interfaces in all the OSPF processes:
Switch#show ip ospf interface
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## show ip ospf neighbor

### Purpose
The show ip ospf neighbor command is used to display information of the OSPF neighbor.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip ospf [ process-id ] neighbor [ detail | interface-name interface-number ]
```

### Parameters
```text
process-id
The process ID, ranging from 1 to 65535. The neighbors
information of all processes will be displayed if no process ID is specified.
detail
The detailed information of the neighbor.
interface-name interface-number
Specify the interface name and number to display the neighbor
s detailed information on this interface.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the neighbors
detailed information in process 1:
Switch#show ip ospf 1 neighbor detail
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## show ip ospf border-routers

### Purpose
The show ip ospf border-routers is used to display the routing tables of the ABR/ASBR.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip ospf [ process-id ] border-routers
```

### Parameters
```text
process-id
The process ID, ranging from 1 to 65535. The ABR/ASBR routing tables of all processes will be displayed if no process ID is specified.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the ABR/ASBR routing tables of all the OSPF processes:
Switch#show ip ospf border-routers
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## show ip ospf route

### Purpose
The show ip ospf route command is used to display the OSPF routing table.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip ospf route
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the routing tables of OSPF:
Switch#show ip ospf route
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## show ip ospf [process-id] graceful-restart helper

### Purpose
The show ip ospf [process-id] graceful-restart helper command is used to view the status and configuration information of the GR Helper and the reason of last exit.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip ospf [process-id] graceful-restart helper
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the status and configuration information of the GR Helper and the reason of last exit:
Switch# show ip ospf graceful-restart helper
```

### Notes
- Availability: Only for certain devices according to the official chapter title.
