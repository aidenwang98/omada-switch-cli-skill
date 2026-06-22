# BGP Configuration Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 48 BGP Configuration Commands (Only for Certain Devices)

Location: extracted Word text lines 20365-22588

## Chapter Notes

Official documentation states: Border Gateway Protocol (BGP) is a distance vector routing protocol that enables routing reachability between Autonomous Systems (AS) and selects the best route. BGP establishes a unique unicast-based connection for each BGP neighbor. To enhance the reliability of peer connections, BGP uses TCP (port 179) as the underlying transmission mechanism. Since tasks like acknowledgment, retransmission, and sequencing are handled by the TCP layer, the session maintenance and update mechanisms of BGP are greatly simplified. As BGP operates over TCP, a separate point-to-point session needs to be established for each peer. Each BGP node passes routes from the routing table via downstream neighbors. BGP nodes perform route calculations based on the routes they advertise and pass the calculated results to upstream neighbors, so it s the primary task for routing BGP routes to successfully establish BGP neighbors. The three earlier versions are BGP-1, BGP-2, and BGP-3, which are mainly used to exchange reachable routing information between ASs, build inter-AS propagation paths, prevent routing loops, and apply some routing policies at the AS level. The current version is BGP-4.

- This chapter is marked `Only for Certain Devices`; treat all configuration commands as model-dependent.

## router bgp

### Purpose
This command is used to enable the BGP function and enter the Router BGP configuration mode. To disable BGP and clear BGP instances, please use the no router bgp command.

### Command Mode
Global Configuration Mode

### Syntax
```text
router bgp as-number
no router bgp as-number
```

### Parameters
```text
as-number
BGP AS number.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the BGP function on the switch:
Switch(config)# router bgp 100
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## address-family {ipv4 | ipv6} unicast

### Purpose
This command is used to enable the BGP IP address family function, and create the address-family configuration view. To disable this function, please use the no address-family {ipv4 | ipv6} unicast command.

### Command Mode
Router Configuration Mode

### Syntax
```text
address-family {ipv4 | ipv6} unicast
no address-family {ipv4 | ipv6} unicast
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the public BGP IPv6 unicast address family functionality:
Switch(config)#router bgp 100
Switch(config-router)#address-family ipv6 unicast
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## address-family {ipv4 | ipv6} vrf

### Purpose
This command is used to create a private VRF BGP instance and enable the corresponding IP address family functionality. To disable this function, please use the no address-family {ipv4 | ipv6} vrf command.

### Command Mode
Router Configuration Mode

### Syntax
```text
address-family {ipv4 | ipv6} vrf name
no address-family {ipv4 | ipv6} vrf name
```

### Parameters
```text
name: VRF name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Create a private VRF a BGP and enable its IPv4 unicast function:
Switch(config)#router bgp 100
Switch(config-router)#address-family ipv4 vrf a
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## address-family targeted-peer evpn

### Purpose
This command is used to enable the BGP L2VPN EVPN address family function. To disable this function, please use the no address-family l2vpn evpn command.

### Command Mode
Router Configuration Mode

### Syntax
```text
address-family l2vpn evpn
no address-family l2vpn evpn
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the public network BGP L2VPN EVPN address family functionality:
Switch(config)#router bgp 100
Switch(config-router)#address-family l2vpn evpn
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## advertise l2vpn evpn

### Purpose
This command is used to redistribute routes from the current address family into the L2VPN EVPN address family.

### Command Mode
Router Configuration Mode

### Syntax
```text
advertise l2vpn evpn
no advertise l2vpn evpn
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Redistribute public network BGP IPv4 unicast address family routes into the L2VPN EVPN address family:
Switch(config)#router bgp 100
Switch(config-router)#address-family ipv4 unicast
Switch (config-router-af)# advertise l2vpn evpn
Redistribute private network VRF a BGP IPv4 address family routes into the L2VPN EVPN address family:
Switch(config)#router bgp 100
Switch(config-router)#address-family ipv4 vrf a
Switch (config-router-vrf-af)# advertise l2vpn evpn
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## aggregate-address

### Purpose
This command is used to create an aggregate route in the BGP routing table. To delete an aggregate route in the BGP routing table, please use the no aggregate-address command.

### Command Mode
Router Configuration Mode

### Syntax
```text
aggregate-address ipv4-address ipv4-mask [as-set | summary-only]
no aggregate-address ipv4-address ipv4-mask
```

### Parameters
```text
ipv4-address: Specifies the IPv4 address of the aggregated route.
ipv4-mask: The network mask of the aggregated route.
as-set: Specifies the generation of routes with AS-SET.
summary-only: Neighbors will not learn the aggregated source detailed routes.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Create an aggregate route. The path advertised by this route is an AS set segment that contains all aggregate path information:
Switch(config)#router bgp 100
Switch(config-router)#aggregate-address 1.1.1.0 255.255.255.0 as-set
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## distance bgp

### Purpose
This command is used to specify the management distance.

### Command Mode
Router Configuration Mode

### Syntax
```text
distance bgp external-distance internal-distance local-distance
```

### Parameters
```text
external-distance: Management distance of internal routes
internal-distance : Management distance of external routes
local-distance: Management distance of local routes
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the BGP management distance:
Switch(config)#router bgp 100
Switch(config-router)#distance bgp 120 100 100
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## maximum-paths

### Purpose
This command is used to configure the number of paths for BGP to perform load balancing.

### Command Mode
Router Configuration Mode

### Syntax
```text
maximum-paths path-number [ibgp]
```

### Parameters
```text
path-number: Specifies the number of paths
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the number of load-balanced paths to 12 when the next-hop neighbors of multiple paths are all iBGP:
Switch(config)#router bgp 100
Switch(config-router)# maximum-paths 12 ibgp
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## network

### Purpose
This command is used to advertises a specified route from the local routing table into the BGP routing table.

### Command Mode
Router Configuration Mode

### Syntax
```text
network ipv4-address [mask] [ipv4-mask] [backdoor]
no network ipv4-address [mask] [ipv4-mask]
```

### Parameters
```text
ipv4-address: IPv4 address to be announced
ipv4-mask: IPv4 mask to be announced
backdoor: Declare as backdoor link and change ebgp route to ibgp route (advanced BGP feature)
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Advertise the route 1.1.1.1/32 into the local public BGP IPv4 unicast address family routing table:
Switch(config)#router bgp 100
Switch(config-router)#network 1.1.1.1 mask 255.255.255.0 backdoor
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## redistribute

### Purpose
This command is used to enable the route redistribution feature to allow routing information of other routing protocols to be published to BGP. The no command without optional parameters can cancel external route redistribution, and the no command with optional parameters can restoresthe optional parameters to their default values.

### Command Mode
Router Configuration Mode

### Syntax
```text
redistribute { connected | static | rip | isis | ospf process-id | isis [ tag area-name] } [ metric cost ]
no redistribute { connected | static | rip | isis | ospf process-id | isis [ tag area-name] }
```

### Parameters
```text
connected | static | rip | ospf | isis: Select the source routing protocol. Differentiated metrics can be defined when the routing information learned by the routing protocol is published to BGP.
process-id: Configure the instance number for redistributing OSPF routes.
area-name: Configure the area name for redistributing IS-ISf routes.
cost: Configure the metric for redistributing routes. The valid value is from 0 to 4294967295. This parameter is optional and defaults to the value specified by the default-metric command.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Redistribute RIP routing information to BGP:
Switch(config)#router bgp 100
Switch(config-router)#redistribute rip
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## slow-peer detection

### Purpose
This command is used to configure the BGP slow-peer detection function. To disable this function, please use the no slow-peer detection command.

### Command Mode
Router Configuration Mode

### Syntax
```text
slow-peer detection {threshold time | disable}
no slow-peer detection {threshold | disable}
```

### Parameters
```text
time: The slow-peer detection threshold, in seconds. The value ranges from 12 to 360 seconds.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set the public network BGP slow-peer detection threshold to 60 seconds:
Switch(config)#router bgp 100
Switch(config)#slow-peer detection threshold 60
Set the private network VRF a BGP slow-peer detection threshold to 60 seconds:
Switch(config)#router bgp 100
Switch(config-router)#address-family ipv4 vrf a
Switch(config-router-vrf-af)# slow-peer detection threshold 60
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## timers bgp

### Purpose
This command is used to configure the interval for sending keepalive messages and the neighbor hold time. To restore the default value, please use the no timers bgp command.

### Command Mode
Router Configuration Mode

### Syntax
```text
timers bgp keepalive hold
no timers bgp
```

### Parameters
```text
keepalive: The interval between for sending keepalive messages between neighbors, ranging from 1-65535 seconds. The default value is 60.
hold: Neighbor hold time, ranging from 1-65535 seconds. The default value is 180.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the keepalive message sending interval to 10 seconds and the hold time to 30 seconds:
Switch(config)#router bgp 100
Switch(config-router)#timers bgp 10 30
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## bgp always-compare-med

### Purpose
This command is used to allow the comparison of MED attribute values of routing paths from different AS neighbors. To restore the default value, please use the no bgp always-compare-med command.

### Command Mode
Router Configuration Mode

### Syntax
```text
bgp always-compare-med
no bgp always-compare-med
```

### Parameters
```text
None
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Allow the comparison of MED attribute values of routing paths from different AS neighbors:
Switch(config)#router bgp 100
Switch(config-router)#bgp always-compare-med
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## bgp bestpath as-path confed

### Purpose
This command is used to configure BGP routing to use as-path information for routes obtained from confederation neighbors. To cancel this configuration, please use the no bgp bestpath as-path confed command.

### Command Mode
Router Configuration Mode

### Syntax
```text
bgp bestpath as-path confed
no bgp bestpath as-path confed
```

### Parameters
```text
None
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure BGP routing to use as-path information for routes obtained from confederation neighbors:
Switch(config)#router bgp 100
Switch(config-router)#bgp bestpath as-path confed
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## bgp bestpath as-path ignore

### Purpose
This command is used to configure BGP to ignore AS path information when selecting routes. To cancel this configuration, please use the no bgp bestpath as-path ignore command.

### Command Mode
Router Configuration Mode

### Syntax
```text
bgp bestpath as-path ignore
no bgp bestpath as-path ignore
```

### Parameters
```text
None
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure BGP to ignore AS path information when selecting routes:
Switch(config)#router bgp 100
Switch(config-router)# bgp bestpath as-path ignore
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## bgp bestpath as-path multipath-relax

### Purpose
This command is used to configure the BGP multipath decision process to consider paths with the same AS_ PATH length. If not configured, the entire AS_PATH must match the multipath calculation. To cancel this configuration, please use the no bgp bestpath as-path multipath-relax command.

### Command Mode
Router Configuration Mode

### Syntax
```text
bgp bestpath as-path multipath-relax
no bgp bestpath as-path multipath-relax
```

### Parameters
```text
None
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the BGP multipath decision process to consider paths with the same AS_PATH length:
Switch(config)#router bgp 100
Switch(config-router)#bgp bestpath as-path multipath-relax
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## bgp bestpath compare-routerid

### Purpose
This command is used to enable the router ID information comparison when selecting EBGP routes. To disable this configuration, please use the no bgp bestpath compare-routerid command.

### Command Mode
Router Configuration Mode

### Syntax
```text
bgp bestpath compare-routerid
no bgp bestpath compare-routerid
```

### Parameters
```text
None
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the router ID information comparison when selecting EBGP routes:
Switch(config)#router bgp 100
Switch(config-router)#bgp bestpath as-path compare-routerid
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## bgp bestpath med confed

### Purpose
This command is used to allow MED comparison between BGP confederation paths. To disable this configuration, please use the no bgp bestpath med confed command. Note that confed and missing-as-worst can be configured and effective simultaneously.

### Command Mode
Router Configuration Mode

### Syntax
```text
bgp bestpath med confed [ missing-as-worst ]
no bgp bestpath med [confed] [missing-as-worst]
```

### Parameters
```text
None
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the router ID information comparison when selecting EBGP routes:
Switch(config)#router bgp 100
Switch(config-router)#bgp bestpath med confed
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## bgp bestpath med missing-as-worst

### Purpose
This command is used to configure BGP to treat a route without a MED value as having a MED value of 4,294,967,295 during path selection. To disable this configuration, please use the no bgp bestpath med missing-as-worst command. Note that confed and missing-as-worst can be configured and effective simultaneously.

### Command Mode
Router Configuration Mode

### Syntax
```text
bgp bestpath med missing-as-worst [ confed ]
no bgp bestpath med [missing-as-worst] [confed]
```

### Parameters
```text
None
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure BGP to treat routes without a MED value as having a MED value of 4,294,967,295:
Switch(config)#router bgp 100
Switch(config-router)# bgp bestpath med missing-as-worst
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## bgp client-to-client reflection

### Purpose
This command is used to configure the client-to-client route reflection. To disable this configuration, please use the no bgp client-to-client reflection command.

### Command Mode
Router Configuration Mode

### Syntax
```text
bgp client-to-client reflection
no bgp client-to-client reflection
```

### Parameters
```text
None
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the client-to-client route reflection:
Switch(config)#router bgp 100
Switch(config-router)#bgp client-to-client reflection
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## bgp cluster-id

### Purpose
This command is used to configure the cluster ID of the route reflector. To disable this configuration, please use the no bgp cluster-id command.

### Command Mode
Router Configuration Mode

### Syntax
```text
bgp cluster-id ip-address
no bgp cluster-id
```

### Parameters
```text
ip-address: IP address
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the reflector
s cluster ID to be 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# bgp cluster-id 1.1.1.1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## bgp confederation identifier

### Purpose
This command is used to condigure the confederation ID. To disable this configuration, please use the no bgp confederation identifier command.

### Command Mode
Router Configuration Mode

### Syntax
```text
bgp confederation identifier as
no bgp confederation identifier
```

### Parameters
```text
as: The confederation ID of the route reflector, ranging from 1 to 4294967295.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the confederation ID to 1:
Switch(config)#router bgp 100
Switch(config-router)# bgp confederation identifier 1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## bgp confederation peers

### Purpose
This command is used to configure a sub-AS belonging to the confederation. To disable this configuration, please use the no bgp confederation peers command.

### Command Mode
Router Configuration Mode

### Syntax
```text
bgp confederation peers as
no bgp confederation peers
```

### Parameters
```text
as: The sub-AS number of the confederation, ranging from 1 to 4294967295.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the sub-AS belonging to the confederation to 1:
Switch(config)#router bgp 100
Switch(config-router)# bgp confederation peers 1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## bgp dampening

### Purpose
This command is used to configure route dampening. To disable this configuration, please use the no bgp dampening command.

### Command Mode
Router Configuration Mode

### Syntax
```text
bgp dampening half-life reuse suppress max-suppress-time
no bgp dampening
```

### Parameters
```text
half-life: half-life: The time it takes for the penalty value to be halved. The range is 1-45 minutes, and the default value is 15.
reuse: The value at which the oscillating route can be reused. The range is 1-20000, and the default value is 750.
suppress: The value at which the oscillating route is suppressed. The range is 1-20000, and the default value is 2000.
max-suppress-time: The maximum duration of route suppression. The range is 1-255, and the default value is 4.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the time required for the route attenuation penalty value to be halved to 30 minutes, the reuse value to 500, the suppression value to 500, and the maximum suppression duration to 10:
Switch(config)#router bgp 100
Switch(config-router)# bgp dampening 30 500 500 10
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## bgp default ipv4-unicast

### Purpose
This command is used to configure IPv4 unicast to be activated for neighbors by default. To disable this configuration, please use the no bgp default ipv4-unicast command.

### Command Mode
Router Configuration Mode

### Syntax
```text
bgp default ipv4-unicast
no bgp default ipv4-unicast
```

### Parameters
```text
None
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure IPv4 unicast to be activated for neighbors by default:
Switch(config)#router bgp 100
Switch(config-router)#bgp default ipv4-unicast
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## bgp default local-preference

### Purpose
This command is used to configure the local preference. To disable this configuration, please use the no bgp default local-preference command.

### Command Mode
Router Configuration Mode

### Syntax
```text
bgp bgp default local-preference preference
no bgp default local-preference
```

### Parameters
```text
preference: Local preference, ranging from 0 to 4294967295, and the default value is 100.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the local preference to 200:
Switch(config)#router bgp 100
Switch(config-router)# bgp default local-preference 200
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## bgp deterministic-med

### Purpose
This command is used to configure BGP to select the path with the best MED from the paths advertised from the adjacent AS. To disable this configuration, please use the no bgp deterministic-med command.

### Command Mode
Router Configuration Mode

### Syntax
```text
bgp deterministic-med
no bgp deterministic-med
```

### Parameters
```text
None
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure BGP to select the path with the best MED from the paths advertised from the adjacent AS:
Switch(config)#router bgp 100
Switch(config-router)# bgp deterministic-med
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## bgp disable-ebgp-connected-route-check

### Purpose
This command is used to disable the connected route check for EBGP peers. By default, EBGP requires a direct connection to establish a peer relationship. After enabling this feature, EBGP peers can be established even without a direct connection. To disable this function, please use the no bgp disable-ebgp-connected-route-check command.

### Command Mode
Router Configuration Mode

### Syntax
```text
bgp disable-ebgp-connected-route-check
no bgp disable-ebgp-connected-route-check
```

### Parameters
```text
None
```

### Default
By default, EBGP requires a direct connection to establish a peer relationship.

### Example
```text
Configure BGP to establish EBGP peers in a non-directly-connected scenario
Switch(config)#router bgp 100
Switch(config-router)# bgp disable-ebgp-connected-route-check
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## bgp fast-external-failover

### Purpose
This command is used to configure BGP to reset the session immediately after the directly connected external neighbor is disconnected. To disable this configuration, please use the no bgp fast-external-failover command.

### Command Mode
Router Configuration Mode

### Syntax
```text
bgp fast-external-failover
no bgp fast-external-failover
```

### Parameters
```text
None
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure BGP to reset the session immediately after the directly connected external neighbor is disconnected:
Switch(config)#router bgp 100
Switch(config-router)# bgp fast-external-failover
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## bgp graceful-restart

### Purpose
This command is used to configure graceful restart of BGP, which applies to both the global BGP instance and private VRF BGP instances. To cancel the configuration, use the no bgp graceful-restart command.

### Command Mode
Router Configuration Mode

### Syntax
```text
bgp graceful-restart
no bgp graceful-restart
```

### Parameters
```text
None
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the gracefule restart of the BGP:
Switch(config)#router bgp 100
Switch(config-router)# bgp graceful-restart
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## bgp graceful-restart restart-time

### Purpose
This command is used to configure the maximum wait time that neighbor devices will allow for the local device to restart and re-establish BGP sessions during a BGP Graceful Restart event. This configuration applies to both the global BGP instance and private VRF BGP instances. To cancel the configuration, use the no bgp graceful-restart restart-time command.

### Command Mode
Router Configuration Mode

### Syntax
```text
bgp graceful-restart restart-time time
no bgp graceful-restart restart-time
```

### Parameters
```text
time: The maximum wait time for the local BGP neighbor to establish successfully during a graceful restart, ranging from 1 to 4095 seconds, and the default value is 120 seconds.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the maximum wait time for neighbors to re-establish BGP sessions as 240 seconds during a Graceful Restart:
Switch(config)#router bgp 100
Switch(config-router)#bgp graceful-restart restart-time 240
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## bgp graceful-restart rib-stale-time

### Purpose
This command is used to configure the maximum time for which the local Routing Information Base (RIB) retains stale routes during a local BGP Graceful Restart event. This configuration applies to both the global BGP instance and private VRF BGP instances. To cancel the configuration, use the no bgp graceful-restart rib-stale-time command.

### Command Mode
Router Configuration Mode

### Syntax
```text
bgp graceful-restart rib-stale-time time
no bgp graceful-restart rib-stale-time
```

### Parameters
```text
time: The maximum duration to retain stale BGP routing information during a graceful restart, ranging from 1-3600 seconds, and the default value is 120 seconds.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the maximum time for the local RIB to retain stale routes as 240 seconds during a Graceful Restart:
Switch(config)#router bgp 100
Switch(config-router)# bgp graceful-restart rib-stale-time 240
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## bgp graceful-restart select-defer-time

### Purpose
This command is used to configure the delay time before executing the route selection algorithm to update the local routing table after the local BGP device has performed a Graceful Restart and re-established its connections. This configuration applies to both the global BGP instance and private VRF BGP instances. To cancel the configuration, use the no bgp graceful-restart select-defer-time command.

### Command Mode
Router Configuration Mode

### Syntax
```text
bgp graceful-restart select-defer-time time
no bgp graceful-restart select-defer-time
```

### Parameters
```text
time: The time neighbor routers wait after receiving updated routing information from the restarting router before performing route selection, ranging from 0-3600 seconds, and the default value is 90 seconds.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the delay time for executing the route selection algorithm as 240 seconds after a Graceful Restart:
Switch(config)#router bgp 100
Switch(config-router)# bgp graceful-restart select-defer-time 240
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## bgp graceful-restart stalepath-time

### Purpose
This command is used to configure the maximum time for which the local router will retain routes learned from a neighbor when that neighbor experiences a control-plane failure (e.g., a BGP process restart). This configuration applies to both the global BGP instance and private VRF BGP instances.To cancel the configuration, use the no bgp graceful-restart stalepath-time command.

### Command Mode
Router Configuration Mode

### Syntax
```text
bgp graceful-restart stalepath-time time
no bgp graceful-restart stalepath-time
```

### Parameters
```text
time: The maximum duration to retain stale BGP path information during a graceful restart, ranging from 1 to 4095 seconds, and the default value is 120 seconds.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the maximum time for the local router to retain routes learned from a neighbor as 240 seconds when the neighbor has a control-plane failure:
Switch(config)#router bgp 100
Switch(config-router)# bgp graceful-restart stalepath-time 240
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## bgp graceful-shutdown

### Purpose
This command is used to enable the BGP Graceful Shutdown function. To disable this function, use the no bgp graceful-shutdown command.

### Command Mode
Router Configuration Mode

### Syntax
```text
bgp graceful-shutdown
no bgp graceful-shutdown
```

### Parameters
```text
None
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the BGP Graceful Shutdown function:
Switch(config)#router bgp 100
Switch(config-router)# bgp graceful-shutdown
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## bgp listen limit

### Purpose
This command is used to configure the maximum number of dynamic BGP neighbor sessions that can be established. This configuration applies to both the global BGP instance and private VRF BGP instances. To cancel the configuration, use the no bgp listen limit command.

### Command Mode
Router Configuration Mode

### Syntax
```text
bgp listen limit num
no bgp listen limit
```

### Parameters
```text
num: The maximum number. The range is 1 to 256. The default value is 100.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the maximum number of dynamic BGP neighbor sessions as 10:
Switch(config)#router bgp 100
Switch(config-router)# bgp listen limit 10
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## bgp listen range

### Purpose
This command is used to configure a listening range for BGP dynamic neighbors and add the dynamically established neighbors to a specified peer group. This configuration applies to both the global BGP instance and private VRF BGP instances. To disable this configuration, please use the no bgp listen range command.

### Command Mode
Router Configuration Mode

### Syntax
```text
bgp listen range address Neighbor tag
no bgp listen range address Neighbor tag
```

### Parameters
```text
address: The network range to listen on.
name: Peer group name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure a listening range for dynamic BGP neighbors as the 1.1.1.0/24 subnet and add them to the peer group named "aaa":
Switch(config)#router bgp 100
Switch(config-router)# bgp listen range 1.1.1.0/24 peer-group aaa
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## bgp log-neighbor-changes

### Purpose
This command is used to enable logging for BGP neighbor state changes. This configuration applies to both the global BGP instance and private VRF BGP instances. To disable this function, please use the no bgp log-neighbor-changes command.

### Command Mode
Router Configuration Mode

### Syntax
```text
bgp log-neighbor-changes
no bgp log-neighbor-changes
```

### Parameters
```text
None.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable logging for BGP neighbor state changes:
Switch(config)#router bgp 100
Switch(config-router)# bgp log-neighbor-changes
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## bgp max-med administrative

### Purpose
This command is used to configure the MED value for BGP routes advertised by this device. To disable this function, please use the no bgp max-med administrative command.

### Command Mode
Router Configuration Mode

### Syntax
```text
bgp max-med administrative [med]
no bgp max-med administrative
```

### Parameters
```text
med: MED value.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the MED value for BGP routes advertised by this device as 200:
Switch(config)#router bgp 100
Switch(config-router)# bgp max-med administrative 200
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## bgp max-med on-startup

### Purpose
This command is used to configure the MED value for BGP routes advertised by this device for a specified period after BGP startup. The MED reverts to its default value after this timer expires.To disable this function, please use the no bgp max-med on-startup command.

### Command Mode
Router Configuration Mode

### Syntax
```text
bgp max-med on-startup time [med]
no bgp max-med on-startup
```

### Parameters
```text
Time: The duration, in seconds. The range is 5 to 86400.
med: MED value.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the MED value for BGP routes advertised by this device as 200 for the first 5 seconds after BGP startup::
Switch(config)#router bgp 100
Switch(config-router)# bgp max-med on-startup 5 200
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## bgp network import-check

### Purpose
This command is used to configure BGP to check the reachability of the routes configured by the network command. To disable this configuration, please use the no bgp network import-check command.

### Command Mode
Router Configuration Mode

### Syntax
```text
bgp network import-check
no bgp network import-check
```

### Parameters
```text
None
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure BGP to check the reachability of the routes configured by the network command:
Switch(config)#router bgp 100
Switch(config-router)# bgp network import-check
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## bgp reject-as-sets

### Purpose
This command is used to configure BGP to filter out routes that contain the AS_SET or AS_CONFED_SET attributes. To disable this function, use the no no bgp reject-as-sets command.

### Command Mode
Router Configuration Mode

### Syntax
```text
bgp reject-as-sets
no bgp reject-as-sets
```

### Parameters
```text
None
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure BGP to filter out routes containing the AS_SET or AS_CONFED_SET attributes:
Switch(config)#router bgp 100
Switch(config-router)# bgp reject-as-sets
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## bgp router-id

### Purpose
This command is used to set the router ID. If you do not manually configure the router ID, or cancel the configured router ID, BGP will automatically select an interface IP address as the router ID. To delete the router ID, please use the no bgp router-id command.

### Command Mode
Router Configuration Mode

### Syntax
```text
bgp router-id router-id
no bgp router-id
```

### Parameters
```text
router-id: Router ID, which is a 32-bit unsigned integer in dotted decimal format, excluding 0.0.0.0. To avoid multiple routers using the same router ID during automatic election, it is recommended to configure this manually.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the BGP route ID to 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# bgp router-id 1.1.1.1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## no neighbor

### Purpose
This command is used to delete a specified BGP neighbor and all its associated configurations.

### Command Mode
Router Configuration Mode BGP VRF Address Family Configuration Mode (config-router-vrf-af). Note that the configuration takes effect for all address families under the VRF.

### Syntax
```text
no neighbor ip-address
```

### Parameters
```text
ip-address: Neighbor IP address.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Delete the global BGP neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# no neighbor 1.1.1.1
Delete the BGP neighbor 1.1.1.1 for the private VRF named "a":
Switch(config)#router bgp 100
Switch(config-router)# address-family ipv4 vrf a
Switch (config-router-vrf-af)# no neighbor 1.1.1.1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## neighbor activate

### Purpose
This command is used to configure BGP to enable the address family for the neighbor. To disable this configuration, please use the no neighbor activate command.

### Command Mode
Router Configuration Mode. Note: Configuration in this mode takes effect in the IPv4 unicast address family context. BGP Address Family Configuration Mode (config-router-af) BGP VRF Address Family Configuration Mode (config-router-vrf-af) BGP L2VPN EVPN Address Family Configuration Mode (address-family l2vpn evpn)

### Syntax
```text
neighbor ip-address | tag activate
no neighbor ip-address | tag activate
```

### Parameters
```text
ip-address: Neighbor IP address.
tag: Neighbor tag.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the IPv4 unicast address family for global BGP neighbor 1.1.1.1 in router configuration mode:
Switch(config)#router bgp 100
Switch(config-router)# neighbor 1.1.1.1 activate
Enable the IPv4 unicast address family for global BGP neighbor 1.1.1.1 in address family configuration mode:
Switch(config)#router bgp 100
Switch(config-router)# address-family ipv4 unicast
Switch (config-router-af)# neighbor 1.1.1.1 activate
Enable the IPv4 unicast address family for BGP neighbor 1.1.1.1 in VRF "a":
Switch(config)#router bgp 100
Switch(config-router)# address-family ipv4 vrf a
Switch (config-router-af)# neighbor 1.1.1.1 activate
Enable the L2VPN EVPN address family for global BGP neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# address-family l2vpn evpn
Switch (config-router-af)# neighbor 1.1.1.1 activate
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## neighbor addpath-tx-all-paths

### Purpose
This command is used to allow the gateway to advertise all learned feasible paths to a specified neighbor.To disable this configuration, please use the no neighbor addpath-tx-all-paths command.

### Command Mode
BGP Address Family Configuration Mode (config-router-af) BGP VRF Address Family Configuration Mode (config-router-vrf-af)

### Syntax
```text
neighbor ip-address | tag addpath-tx-all-paths
no neighbor ip-address | tag addpath-tx-all-paths
```

### Parameters
```text
ip-address: Neighbor IP address.
tag: Neighbor tag.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Allow the global BGP IPv4 address family to send all learned feasible paths to neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# address-family ipv4 unicast
Switch (config-router-af)# neighbor 1.1.1.1 addpath-tx-all-paths
Allow the private VRF "a" BGP IPv4 address family to send all learned feasible paths to neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# address-family ipv4 vrf a
Switch (config-router-vrf-af)# neighbor 1.1.1.1 addpath-tx-all-paths
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## neighbor addpath-tx-bestpath-per-AS

### Purpose
This command is used to allow the gateway to advertise one best path per AS to a specified neighbor. To disable this configuration, please use the no neighbor addpath-tx-bestpath-per-AS command.

### Command Mode
BGP Address Family Configuration Mode (config-router-af) BGP VRF Address Family Configuration Mode (config-router-vrf-af)

### Syntax
```text
neighbor ip-address | tag addpath-tx-bestpath-per-AS
no neighbor ip-address | tag addpath-tx-bestpath-per-AS
```

### Parameters
```text
ip-address: Neighbor IP address.
tag: Neighbor tag.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Allow the global BGP IPv4 address family to advertise one best path per AS to neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# address-family ipv4 unicast
Switch (config-router-af)# neighbor 1.1.1.1 addpath-tx-bestpath-per-AS
Allow the private VRF "a" BGP IPv4 address family to advertise one best path per AS to neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# address-family ipv4 vrf a
Switch (config-router-vrf-af)# neighbor 1.1.1.1 addpath-tx-bestpath-per-AS
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## neighbor advertisement-interval

### Purpose
This command is used to configure the minimum interval for advertising BGP route updates. To disable this configuration, please use the no command.

### Command Mode
Router Configuration Mode

### Syntax
```text
neighbor ip-address | tag advertisement-interval interval
no neighbor ip-address | tag advertisement-interval
```

### Parameters
```text
ip-address: Neighbor IP address.
tag: Neighbor tag.
interval: The minimum interval for advertising BGP routing updates, ranging from 0-600 seconds.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure BGP to advertise BGP routing updates for neighbor 1.1.1.1 at a minimum interval of 10 seconds:
Switch(config)#router bgp 100
Switch(config-router)# neighbor 1.1.1.1 advertisement-interval 10
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## neighbor allowas-in

### Purpose
This command is used to configure the maximum number of ASs in the AS path sent by the neighbor, including its own AS. To disable this configuration, please use the no command.

### Command Mode
Router Configuration Mode. Note: Configuration in this mode takes effect in the IPv4 unicast address family context. BGP Address Family Configuration Mode (config-router-af) BGP VRF Address Family Configuration Mode (config-router-vrf-af) BGP L2VPN EVPN Address Family Configuration Mode (address-family l2vpn evpn)

### Syntax
```text
neighbor ip-address | tag allowas-in number
no neighbor ip-address | tag allowas-in
```

### Parameters
```text
ip-address: Neighbor IP address.
tag: Neighbor tag.
number: AS number, ranging from 1 to10.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the global BGP IPv4 address family to accept routes from neighbor 1.1.1.1 even if the AS_PATH contains the local AS, allowing the local AS to appear up to 10 times:
Switch(config)#router bgp 100
Switch(config-router)# neighbor 1.1.1.1 allowas-in 10
Configure the global BGP IPv4 address family to accept routes from neighbor 1.1.1.1 even if the AS_PATH contains the local AS, allowing the local AS to appear up to 10 times (in address family mode):
Switch(config)#router bgp 100
Switch(config-router)# address-family ipv4 unicast
Switch(config-router-af)# neighbor 1.1.1.1 allowas-in 10
Configure the private VRF "a" BGP IPv4 address family to accept routes from neighbor 1.1.1.1 even if the AS_PATH contains the local AS, allowing the local AS to appear up to 10 times:
Switch(config)#router bgp 100
Switch(config-router)# address-family ipv4 vrf a
Switch(config-router-vrf-af)# neighbor 1.1.1.1 allowas-in 10
Configure the global BGP L2VPN EVPN address family to accept routes from neighbor 1.1.1.1 even if the AS_PATH contains the local AS, allowing the local AS to appear up to 10 times:
Switch(config)#router bgp 100
Switch(config-router)#address-family l2vpn evpn
Switch (config-router-af)# neighbor 1.1.1.1 allowas-in 10
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## neighbor as-override

### Purpose
This command is used to allow the local device to override the original AS number in received routes with its local AS number when advertising those routes. To disable this configuration, please use the no neighbor as-override command.

### Command Mode
BGP Address Family Configuration Mode (config-router-af) BGP VRF Address Family Configuration Mode (config-router-vrf-af)

### Syntax
```text
neighbor ip-address | tag as-override
no neighbor ip-address | tag as-override
```

### Parameters
```text
ip-address: Neighbor IP address.
tag: Neighbor tag.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Allow the global BGP instance to override the original AS number with the local AS number when advertising IPv4 address family routes to neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# address-family ipv4 unicast
Switch (config-router-af)# neighbor 1.1.1.1 as-override
Allow the private VRF "a" BGP instance to override the original AS number with the local AS number when advertising IPv4 address family routes to neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# address-family ipv4 vrf a
Switch (config-router-vrf-af)# neighbor 1.1.1.1 as-override
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## neighbor attribute-unchanged

### Purpose
This command is used to configure BGP attributes to be sent to neighbors without change. To disable this configuration, please use the no command.

### Command Mode
Router Configuration Mode (router bgp): Note: Configuration in this mode takes effect in the IPv4 unicast address family context. BGP Address Family Configuration Mode (config-router-af) BGP VRF Address Family Configuration Mode (config-router-vrf-af) BGP L2VPN EVPN Address Family Configuration Mode (address-family l2vpn evpn)

### Syntax
```text
neighbor ip-address | tag attribute-unchanged [as-path] [med] [next-hop]
no neighbor ip-address | tag attribute-unchanged
```

### Parameters
```text
ip-address: Neighbor IP address.
tag: Neighbor tag.
as-path: AS path attribute.
med: MED attribute.
next-hop: Next hop attribute.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the global BGP IPv4 address family to send routes with the AS_PATH attribute unchanged to neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# neighbor 1.1.1.1 attribute-unchanged as-path
Configure the global BGP IPv4 address family to send routes with the AS_PATH attribute unchanged to neighbor 1.1.1.1 (in address family mode):
Switch(config)#router bgp 100
Switch(config-router)# address-family ipv4 unicast
Switch (config-router-af)# neighbor 1.1.1.1 attribute-unchanged as-path
Configure the private VRF "a" BGP IPv4 address family to send routes with the AS_PATH attribute unchanged to neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# address-family ipv4 vrf a
Switch (config-router-vrf-af)# neighbor 1.1.1.1 attribute-unchanged as-path
Configure the global BGP L2VPN EVPN address family to send routes with the AS_PATH attribute unchanged to neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# address-family l2vpn evpn
Switch(config-router-af)# neighbor 1.1.1.1 attribute-unchanged as-path
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## neighbor bfd

### Purpose
This command is used to BGP to use BFD for detecting link status with a neighbor. To disable this configuration, please use the no neighbor bfd command.

### Command Mode
Router Configuration Mode

### Syntax
```text
neighbor ip-address | tag bfd [profile]
no neighbor ip-address | tag bfd
```

### Parameters
```text
ip-address: Neighbor IP address.
tag: Neighbor tag.
as-path: AS path attribute.
med: MED attribute.
profile: BFD profile name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure BGP to use BFD to detect link status with neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# neighbor 1.1.1.1 bfd
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## neighbor capability dynamic

### Purpose
This command is used to announce dynamic capabilities to neighbors. To disable this configuration, please use the no command.

### Command Mode
Router Configuration Mode BGP VRF address family configuration mode (config-router-vrf-af). Note that the configuration applies to all address families in the VRF.

### Syntax
```text
neighbor ip-address | tag capability dynamic
no neighbor ip-address | tag capability dynamic
```

### Parameters
```text
ip-address: Neighbor IP address.
tag: Neighbor tag.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure public BGP to dynamically advertise capabilities to neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# neighbor 1.1.1.1 capability dynamic
Configure private VRF 'a' BGP to dynamically advertise capabilities to neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# address-family ipv4 vrf a
Switch(config-router-vrf-af)# neighbor 1.1.1.1 capability dynamic
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## neighbor dampening

### Purpose
This command is used to configure route flap dampening for a neighbor. To disable this configuration, please use the no neighbor dampening command.

### Command Mode
BGP address family configuration mode (config-router-af) BGP VRF address family configuration mode (config-router-vrf-af)

### Syntax
```text
neighbor ip-address | tag dampening half-life reuse suppress max-suppress-time
no neighbor ip-address | tag dampening
```

### Parameters
```text
ip-address: Neighbor IP address.
tag: Neighbor tag.
half-life: Time required for the penalty value to halve, in the range of 1 to 45 minutes. Default is 15 minutes.
reuse: Threshold at which a flapping route can be reused, in the range of 1 to 20000. Default is 750.
suppress: Threshold at which a flapping route is suppressed, in the range of 1 to 20000. Default is 2000.
max-suppress-time: Maximum duration a route can be suppressed, in the range of 1 to 255. Default is 4 times the half-life.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure public BGP neighbor 1.1.1.1 route dampening for the IPv4 address family with a half-life of 30 minutes, reuse limit of 500, suppress limit of 500, and maximum suppress time of 10 times the half-life:
Switch(config)# address-family ipv4 unicast
Switch(config-router-af)# neighbor 1.1.1.1 dampening 30 500 500 10
Configure private VRF 'a' BGP neighbor 1.1.1.1 route dampening for the IPv4 address family with a half-life of 30 minutes, reuse limit of 500, suppress limit of 500, and maximum suppress time of 10 times the half-life:
Switch(config)#router bgp 100
Switch(config-router)# address-family ipv4 vrf a
Switch(config-router-vrf-af)# neighbor 1.1.1.1 dampening 30 500 500 10
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## neighbor default-originate

### Purpose
This command is used to advertise a default route to a neighbor. To disable this configuration, please use the no command.

### Command Mode
Router Configuration Mode (router bgp): Note: Configuration in this mode actually takes effect in the IPv4 unicast address family. BGP Address Family Configuration Mode (config-router-af) BGP VRF Address Family Configuration Mode (config-router-vrf-af)

### Syntax
```text
neighbor ip-address | tag default-originate
no neighbor ip-address | tag default-originate
```

### Parameters
```text
ip-address: Neighbor IP address.
tag: Neighbor tag.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure public BGP to advertise an IPv4 address family default route to neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# neighbor 1.1.1.1 default-originate
Configure public BGP to advertise an IPv4 address family default route to neighbor 1.1.1.1 (within the address family):
Switch(config)#router bgp 100
Switch(config-router)#address-family ipv4 unicast
Switch (config-router-af)# neighbor 1.1.1.1 default-originate
Configure private VRF a BGP to advertise an IPv4 address family default route to neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# address-family ipv4 vrf a
Switch(config-router-vrf-af)# neighbor 1.1.1.1 default-originate
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## neighbor description

### Purpose
This command is used to configure the neighbor description. To delete the neighbor description, please use the no command.

### Command Mode
Router Configuration Mode BGP VRF address family configuration mode (config-router-vrf-af). Note that the configuration applies to all address families in the VRF.

### Syntax
```text
neighbor ip-address | tag description description
no neighbor ip-address | tag description
```

### Parameters
```text
ip-address: Neighbor IP address.
tag: Neighbor tag.
description: Neighbor description.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the description for public BGP neighbor 1.1.1.1 as internet:
Switch(config)#router bgp 100
Switch(config-router)# neighbor 1.1.1.1 description internet
Configure the description for private VRF a BGP neighbor 1.1.1.1 as internet:
Switch(config)#router bgp 100
Switch(config-router)# address-family ipv4 vrf a
Switch(config-router-vrf-af)#neighbor 1.1.1.1 description internet
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## neighbor disable-connected-check

### Purpose
This command is used to configure the use of loopback address for one-hop EBGP neighbors. To cancel this configuration, please use the no command.

### Command Mode
Router Configuration Mode BGP VRF address family configuration mode (config-router-vrf-af). Note that the configuration applies to all address families in the VRF.

### Syntax
```text
neighbor ip-address | tag disable-connected-check
no neighbor ip-address | tag disable-connected-check
```

### Parameters
```text
ip-address: Neighbor IP address.
tag: Neighbor tag.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure public BGP to disable the directly-connected check for the connection with neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# neighbor 1.1.1.1 disable-connected-check
Configure private VRF a BGP to disable the directly-connected check for the connection with neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# address-family ipv4 vrf a
Switch(config-router-vrf-af)# neighbor 1.1.1.1 disable-connected-check
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## neighbor dont-capability-negotiate

### Purpose
This command is used to disable the negotiation on capabilities with neighbors. To cancel this configuration, please use the no command.

### Command Mode
Router Configuration Mode BGP VRF address family configuration mode (config-router-vrf-af). Note that the configuration applies to all address families in the VRF.

### Syntax
```text
neighbor ip-address | tag dont-capability-negotiate
no neighbor ip-address | tag dont-capability-negotiate
```

### Parameters
```text
ip-address: Neighbor IP address.
tag: Neighbor tag.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure public BGP not to perform capability negotiation with neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# neighbor 1.1.1.1 dont-capability-negotiate
Configure private VRF a BGP not to perform capability negotiation with neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# address-family ipv4 vrf a
Switch(config-router-vrf-af)# neighbor 1.1.1.1 dont-capability-negotiate
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## neighbor ebgp-multihop

### Purpose
This command is used to allow establishing connections with EBGP neighbors that are not on a directly connected network. To cancel this configuration, please use the no neighbor ebgp-multihop command.

### Command Mode
Router Configuration Mode BGP VRF address family configuration mode (config-router-vrf-af). Note that the configuration applies to all address families in the VRF.

### Syntax
```text
neighbor ip-address | tag ebgp-multihop hops
no neighbor ip-address | tag ebgp-multihop
```

### Parameters
```text
ip-address: Neighbor IP address.
tag: Neighbor tag.
hops: The maximum number of hops to reach an EBGP neighbor. The default value is 1, which means only directly connected neighbors are allowed.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure public BGP to set the maximum hop count to neighbor 1.1.1.1 as 10:
Switch(config)#router bgp 100
Switch(config-router)# neighbor 1.1.1.1 ebgp-multihop 10
Configure private VRF a BGP to set the maximum hop count to neighbor 1.1.1.1 as 10:
Switch(config)#router bgp 100
Switch(config-router)# address-family ipv4 vrf a
Switch(config-router-vrf-af)# neighbor 1.1.1.1 ebgp-multihop 10
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## neighbor enforce-first-as

### Purpose
This command is used to configure configure strict validation that the first AS number in the AS_PATH attribute of route updates received from an EBGP neighbor must exactly match the locally configured neighbor AS number. To cancel this configuration, please use the no command.

### Command Mode
Router Configuration Mode

### Syntax
```text
neighbor ip-address | tag enforce-first-as
no neighbor ip-address | tag enforce-first-as
```

### Parameters
```text
ip-address: Neighbor IP address.
tag: Neighbor tag.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure neighbor 1.1.1.1 to enforce first AS validation:
Switch(config)#router bgp 100
Switch(config-router)# neighbor 1.1.1.1 enforce-first-as
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## neighbor graceful-restart

### Purpose
This command is used to configure the graceful restart of BGP neighbors. To cancel this configuration, please use the no command.

### Command Mode
Router Configuration Mode BGP VRF address family configuration mode (config-router-vrf-af). Note that the configuration applies to all address families in the VRF.

### Syntax
```text
neighbor ip-address | tag graceful-restart
no neighbor ip-address | tag graceful-restart
```

### Parameters
```text
ip-address: Neighbor IP address.
tag: Neighbor tag.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure public BGP Graceful Restart capability for neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# neighbor 1.1.1.1 graceful-restart
Configure private VRF a BGP Graceful Restart capability for neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# address-family ipv4 vrf a
Switch(config-router-vrf-af)# neighbor 1.1.1.1 graceful-restart
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## neighbor graceful-restart-helper

### Purpose
This command is used to configure BGP to gracefully restart neighbor routers. To cancel this configuration, please use the no command.

### Command Mode
Router Configuration Mode BGP VRF address family configuration mode (config-router-vrf-af). Note that the configuration applies to all address families in the VRF.

### Syntax
```text
neighbor ip-address | tag graceful-restart-helper
no neighbor ip-address | tag graceful-restart-helper
```

### Parameters
```text
ip-address: Neighbor IP address.
tag: Neighbor tag.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure public BGP Graceful Restart helper capability for neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# neighbor 1.1.1.1 graceful-restart-helper
Configure private VRF a BGP Graceful Restart helper capability for neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# address-family ipv4 vrf a
Switch(config-router-vrf-af)# neighbor 1.1.1.1 graceful-restart-helper
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## neighbor local-as

### Purpose
This command is used to prepend the specified local AS to the AS path when BGP sends or receives the AS path from the specified neighbor. This configuration applies to EBGP neighbors. To cancel this configuration, please use the no command.

### Command Mode
Router Configuration Mode BGP VRF address family configuration mode (config-router-vrf-af). Note that the configuration applies to all address families in the VRF.

### Syntax
```text
neighbor ip-address | tag local-as as
no neighbor ip-address | tag local-as
```

### Parameters
```text
ip-address: Neighbor IP address.
tag: Neighbor tag.
as: The AS number to advertise externally.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the AS number that public BGP advertises itself as to neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# neighbor 1.1.1.1 local-as 5
Configure the AS number that private VRF a BGP advertises itself as to neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# address-family ipv4 vrf a
Switch(config-router-vrf-af)# neighbor 1.1.1.1 local-as 5
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## neighbor maximum-prefix

### Purpose
This command is used to specify the maximum number of routes received from a specific neighbor. To cancel this configuration, please use the no command.

### Command Mode
Router Configuration Mode. Note that configuration in this mode actually takes effect in the IPv4 unicast address family. BGP address family configuration mode (config-router-af) BGP VRF address family configuration mode (config-router-vrf-af)

### Syntax
```text
neighbor ip-address | tag maximum-prefix number
no neighbor ip-address | tag maximum-prefix
```

### Parameters
```text
ip-address: Neighbor IP address.
tag: Neighbor tag.
number: The maximum number of routes that can be received from this neighbor.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure public BGP to receive a maximum of 100 IPv4 address family routes from neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# neighbor 1.1.1.1 maximum-prefix 100
Configure public BGP to receive a maximum of 100 IPv4 address family routes from neighbor 1.1.1.1 (within the address family context):
Switch(config)#router bgp 100
Switch(config-router)# address-family ipv4 unicast
(config-router-af)# neighbor 1.1.1.1 maximum-prefix 100
Configure private VRF a BGP to receive a maximum of 100 IPv4 address family routes from neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# address-family ipv4 vrf a
Switch(config-router-vrf-af)# neighbor 1.1.1.1 maximum-prefix 100
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## neighbor maximum-prefix-out

### Purpose
This command is used to configure the maximum number of routes to be advertised to a neighbor. To cancel this configuration, please use the no command.

### Command Mode
BGP address family configuration mode (config-router-af) BGP VRF address family configuration mode (config-router-vrf-af)

### Syntax
```text
neighbor ip-address | tag maximum-prefix-out limit
no neighbor ip-address | tag maximum-prefix-out
```

### Parameters
```text
ip-address: Neighbor IP address.
tag: Neighbor tag.
Limit: Maximum number of route prefixes.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure public BGP IPv4 address family to advertise a maximum of 1000 route prefixes to neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)#address-family ipv4 unicast
Switch(config-router-af)# neighbor 1.1.1.1 maximum-prefix-out 1000
Configure private VRF a BGP IPv4 address family to advertise a maximum of 1000 route prefixes to neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)#address-family ipv4 vrf a
(config-router-vrf-af)# neighbor 1.1.1.1 maximum-prefix-out 1000
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## neighbor next-hop-self

### Purpose
This command is used to modify the next-hop attribute of BGP routes advertised to a specified neighbor, replacing it with the local router's interface IP address. To cancel this configuration, please use the no command.

### Command Mode
Router Configuration Mode. Configuration in this mode actually takes effect in the IPv4 unicast address family. BGP address family configuration mode (config-router-af) BGP VRF address family configuration mode (config-router-vrf-af) BGP L2VPN EVPN address family configuration mode (address-family l2vpn evpn)

### Syntax
```text
neighbor ip-address | tag next-hop-self [all]
no neighbor ip-address | tag next-hop-self [all]
```

### Parameters
```text
ip-address: Neighbor IP address.
tag: Neighbor tag.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure public BGP to use its own address as the next-hop for IPv4 address family routes sent to neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# neighbor 1.1.1.1 next-hop-self
Configure public BGP to use its own address as the next-hop for IPv4 address family routes sent to neighbor 1.1.1.1 (within the address family):
Switch(config)#router bgp 100
Switch(config-router)#address-family ipv4 unicast
Switch (config-router-af)# neighbor 1.1.1.1 next-hop-self
Configure private VRF a BGP to use its own address as the next-hop for IPv4 address family routes sent to neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)#address-family ipv4 vrf a
(config-router-vrf-af)# neighbor 1.1.1.1 next-hop-self
Configure public BGP to use its own address as the next-hop for L2VPN EVPN address family routes sent to neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# address-family l2vpn evpn
Switch(config-router-af)# neighbor 1.1.1.1 next-hop-self
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## neighbor nexthop-local unchanged

### Purpose
This command is used to specify that the next-hop link-local address of BGP IPv6 routes advertised by a neighbor should not be changed. To cancel this configuration, please use the no command.

### Command Mode
BGP IPv6 address family configuration mode (address-family ipv6 unicast

### Syntax
```text
neighbor ip-address | tag nexthop-local unchanged
no neighbor ip-address | tag nexthop-local unchanged
```

### Parameters
```text
ip-address: Neighbor IP address.
tag: Neighbor tag.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure public BGP to not change the next-hop link-local address for IPv6 address family routes sent to neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)#address-family ipv6 unicast
Switch(config-router-af)# neighbor 1.1.1.1 nexthop-local unchanged
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## neighbor override-capability

### Purpose
This command is used to ignore neighbor capability negotiation information and use the default capability information. To cancel this configuration, please use the no command.

### Command Mode
Router Configuration Mode BGP VRF address family configuration mode (config-router-vrf-af). Note that the configuration applies to all address families in the VRF.

### Syntax
```text
neighbor ip-address | tag override-capability
no neighbor ip-address | tag override-capability
```

### Parameters
```text
ip-address: Neighbor IP address.
tag: Neighbor tag.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure public BGP to ignore the capability negotiation result with neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# neighbor 1.1.1.1 override-capability
Configure private VRF a BGP to ignore the capability negotiation result with neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# ddress-family ipv4 vrf a
Switch(config-router-vrf-af)# neighbor 1.1.1.1 override-capability
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## neighbor passive

### Purpose
This command is used to disable the OPEN message sent to the neighbor. To cancel this configuration, please use the no command.

### Command Mode
Router Configuration Mode BGP VRF address family configuration mode (config-router-vrf-af). Note that the configuration applies to all address families in the VRF.

### Syntax
```text
neighbor ip-address | tag passive
no neighbor ip-address | tag passive
```

### Parameters
```text
ip-address: Neighbor IP address.
tag: Neighbor tag.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure public BGP not to actively send OPEN messages to neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# neighbor 1.1.1.1 passive
Configure private VRF a BGP not to actively send OPEN messages to neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# ddress-family ipv4 vrf a
Switch(config-router-vrf-af)# neighbor 1.1.1.1 passive
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## neighbor password

### Purpose
This command is used to configure the neighbor password. To cancel this configuration, please use the no command.

### Command Mode
Router Configuration Mode

### Syntax
```text
neighbor ip-address | tag password password
no neighbor ip-address | tag password
```

### Parameters
```text
ip-address: Neighbor IP address.
tag: Neighbor tag.
password: Neighbor password.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the password for public BGP neighbor 1.1.1.1 as abc:
Switch(config)#router bgp 100
Switch(config-router)# neighbor 1.1.1.1 password abc
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## neighbor peer-group

### Purpose
This command is used to configure neighbors to join the specified neighbor group. To cancel this configuration, please use the no command.

### Command Mode
Router Configuration Mode BGP VRF address family configuration mode (config-router-vrf-af): Note that the configuration applies to all address families in the VRF.

### Syntax
```text
neighbor ip-address | tag Neighbor tag
no neighbor ip-address | tag peer-group
```

### Parameters
```text
ip-address: Neighbor IP address.
tag: Neighbor tag.
name: Neighbor group name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure public BGP neighbor 1.1.1.1 to join peer group abc:
Switch(config)#router bgp 100
Switch(config-router)# neighbor 1.1.1.1 peer-group abc
Configure private VRF a BGP neighbor 1.1.1.1 to join peer group abc:
Switch(config)#router bgp 100
Switch(config-router)# address-family ipv4 vrf a
(config-router-vrf-af)# neighbor 1.1.1.1 peer-group abc
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## neighbor port

### Purpose
This command is used to configure the BGP port number of the neighbor. To cancel this configuration, please use the no command.

### Command Mode
Router Configuration Mode

### Syntax
```text
neighbor ip-address | tag port port
no neighbor ip-address | tag port
```

### Parameters
```text
ip-address: Neighbor IP address.
tag: Neighbor tag.
port: TCP port number, ranging from 0-65535.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the BGP port number for neighbor 1.1.1.1 as 200:
Switch(config)#router bgp 100
Switch(config-router)# neighbor 1.1.1.1 port 200
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## neighbor remote-as

### Purpose
This command is used to configure BGP neighbors. To cancel this configuration, please use the no command.

### Command Mode
Router Configuration Mode BGP VRF address family configuration mode (config-router-vrf-af): Note that the configuration applies to all address families in the VRF.

### Syntax
```text
neighbor ip-address | tag remote-as as
no neighbor ip-address | tag remote-as
```

### Parameters
```text
ip-address: Neighbor IP address.
tag: Neighbor tag.
as: AS number of the neighbor.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure a public BGP neighbor 1.1.1.1 located in AS 2:
Switch(config)#router bgp 100
Switch(config-router)# neighbor 1.1.1.1 remote-as 2
Configure a private VRF a BGP neighbor 1.1.1.1 located in AS 2:
Switch(config)#router bgp 100
Switch(config-router)#address-family ipv4 vrf a
Switch(config-router-vrf-af)# neighbor 1.1.1.1 remote-as 2
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## neighbor remove-private-AS

### Purpose
This command is used to remove the private AS number from outbound updates. To cancel this configuration, please use the no command.

### Command Mode
Router Configuration Mode. Configuration in this mode actually takes effect in the IPv4 unicast address family. BGP address family configuration mode (config-router-af) BGP VRF address family configuration mode (config-router-vrf-af)

### Syntax
```text
neighbor ip-address | tag remove-private-AS
no neighbor ip-address | tag remove-private-AS
```

### Parameters
```text
ip-address: Neighbor IP address.
tag: Neighbor tag.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure public BGP to remove private AS numbers from IPv4 updates sent to neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# neighbor 1.1.1.1 remove-private-AS
Configure public BGP to remove private AS numbers from IPv4 updates sent to neighbor 1.1.1.1 (within the address family):
Switch(config)#router bgp 100
Switch(config-router)# address-family ipv4 unicast
Switch(config-router-af)# neighbor 1.1.1.1 remove-private-AS
Configure private VRF a BGP to remove private AS numbers from IPv4 updates sent to neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# address-family ipv4 vrf a
Switch(config-router-vrf-af)# neighbor 1.1.1.1 remove-private-AS
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## neighbor route-reflector-client

### Purpose
This command is used to configure a neighbor as a client of a route reflector. To cancel this configuration, please use the no command.

### Command Mode
Router Configuration Mode. Configuration in this mode actually takes effect in the IPv4 unicast address family. BGP address family configuration mode (config-router-af) BGP VRF address family configuration mode (config-router-vrf-af) BGP L2VPN EVPN address family configuration mode (address-family l2vpn evpn)

### Syntax
```text
neighbor ip-address | tag route-reflector-client
no neighbor ip-address | tag route-reflector-client
```

### Parameters
```text
ip-address: Neighbor IP address.
tag: Neighbor tag.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure public BGP neighbor 1.1.1.1 as an IPv4 address family route reflector client:
Switch(config)#router bgp 100
Switch(config-router)# neighbor 1.1.1.1 route-reflector-client
Configure public BGP neighbor 1.1.1.1 as an IPv4 address family route reflector client (within the address family):
Switch(config)#router bgp 100
Switch(config-router)# address-family ipv4 unicast
Switch(config-router-af)# neighbor 1.1.1.1 route-reflector-client
Configure private VRF a BGP neighbor 1.1.1.1 as an IPv4 address family route reflector client:
Switch(config)#router bgp 100
Switch(config-router)# address-family ipv4 vrf a
Switch(config-router-vrf-af)#neighbor 1.1.1.1 route-reflector-client
Configure public BGP neighbor 1.1.1.1 as an L2VPN EVPN address family route reflector client:
Switch(config)#router bgp 100
Switch(config-router)# address-family l2vpn evpn
Switch(config-router-af)# neighbor 1.1.1.1 route-reflector-client
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## neighbor route-server-client

### Purpose
This command is used to configure a neighbor as a route server client. To cancel this configuration, please use the no command.

### Command Mode
BGP address family configuration mode (config-router-af) BGP L2VPN EVPN address family configuration mode (address-family l2vpn evpn)

### Syntax
```text
neighbor ip-address | tag route-server-client
no neighbor ip-address | tag route-server-client
```

### Parameters
```text
ip-address: Neighbor IP address.
tag: Neighbor tag.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure public BGP neighbor 1.1.1.1 as an IPv4 address family route server client:
Switch(config)#router bgp 100
Switch(config-router)# address-family ipv4 unicast
Switch(config-router-af)# neighbor 1.1.1.1 route-server-client
Configure public BGP neighbor 1.1.1.1 as an L2VPN EVPN address family route server client:
Switch(config)#router bgp 100
Switch(config-router)# address-family l2vpn evpn
Switch(config-router-af)# neighbor 1.1.1.1 route-server-client
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## neighbor sender-as-path-loop-detection

### Purpose
This command is used to configure the enabling of sender AS_PATH loop detection, preventing the router from advertising a route containing the neighbor's AS number to that same neighbor AS. To cancel this configuration, please use the no command.

### Command Mode
Router Configuration Mode.

### Syntax
```text
neighbor ip-address | tag sender-as-path-loop-detection
no neighbor ip-address | tag sender-as-path-loop-detection
```

### Parameters
```text
ip-address: Neighbor IP address.
tag: Neighbor tag.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure sender AS_PATH loop detection for neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# neighbor 1.1.1.1 sender-as-path-loop-detection
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## neighbor send-community

### Purpose
This command is used to configure the permission to send the community attribute to a neighbor. To cancel this configuration, please use the no command.

### Command Mode
BGP address family configuration mode (config-router-af) BGP VRF address family configuration mode (config-router-vrf-af)

### Syntax
```text
neighbor ip-address | tag send-community
no neighbor ip-address | tag send-community
```

### Parameters
```text
ip-address: Neighbor IP address.
tag: Neighbor tag.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure public BGP to allow sending the COMMUNITY attribute to neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# address-family ipv4 unicast
Switch(config-router-af)# neighbor 1.1.1.1 send-community
Configure private VRF a BGP to allow sending the COMMUNITY attribute to neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# address-family ipv4 vrf a
Switch(config-router-vrf-af)# neighbor 1.1.1.1 send-community
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## neighbor shutdown

### Purpose
This command is used to manually shut down a neighbor. To cancel this configuration, please use the no command.

### Command Mode
Router Configuration Mode BGP VRF address family configuration mode (config-router-vrf-af): Note that the configuration applies to all address families in the VRF.

### Syntax
```text
neighbor ip-address | tag shutdown
no neighbor ip-address | tag shutdown
```

### Parameters
```text
ip-address: Neighbor IP address.
tag: Neighbor tag.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Manually shut down public BGP neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# neighbor 1.1.1.1 shutdown
Manually shut down private VRF a BGP neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# address-family ipv4 vrf a
(config-router-vrf-af)# neighbor 1.1.1.1 shutdown
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## neighbor soft-reconfiguration inbound

### Purpose
This command is used to enable inbound soft reconfiguration on a BGP peer. Its main purpose is to allow the router to store all original updates received from the specified neighbor (including routes rejected by inbound route policies), so that inbound policies can be reapplied without requiring the neighbor to resend routing updates. To disable this feature, please use the no command.

### Command Mode
BGP address family configuration mode (config-router-af) BGP VRF address family configuration mode (config-router-vrf-af) BGP L2VPN EVPN address family configuration mode (address-family l2vpn evpn)

### Syntax
```text
neighbor ip-address | tag soft-reconfiguration inbound
no neighbor ip-address | tag soft-reconfiguration inbound
```

### Parameters
```text
ip-address: Neighbor IP address.
tag: Neighbor tag.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable inbound soft reconfiguration for the IPv4 address family for public BGP neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# address-family ipv4 unicast
Switch(config-router-af)# neighbor 1.1.1.1 soft-reconfiguration inbound
Enable inbound soft reconfiguration for the IPv4 address family for private VRF a BGP neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# address-family ipv4 vrf a
Switch(config-router-vrf-af)# neighbor 1.1.1.1 soft-reconfiguration inbound
Enable inbound soft reconfiguration for the L2VPN EVPN address family for public BGP neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# address-family l2vpn evpn
Switch(config-router-af)# neighbor 1.1.1.1 soft-reconfiguration inbound
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## neighbor strict-capability-match

### Purpose
This command is used to strictly match the capability negotiation between neighbors. To disable this feature, please use the no command.

### Command Mode
Router Configuration Mode BGP VRF address family configuration mode (config-router-vrf-af): Note that the configuration applies to all address families in the VRF.

### Syntax
```text
neighbor ip-address | tag strict-capability-match
no neighbor ip-address | tag strict-capability-match
```

### Parameters
```text
ip-address: Neighbor IP address.
tag: Neighbor tag.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enforce strict capability negotiation matching with public BGP neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# neighbor 1.1.1.1 strict-capability-match
Enforce strict capability negotiation matching with private VRF a BGP neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# address-family ipv4 vrf a
Switch(config-router-vrf-af)# neighbor 1.1.1.1 strict-capability-match
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## neighbor timers

### Purpose
This command is used to configure the interval for sending keepalive messages between neighbors and the neighbor hold time. To use to global configuration value, please use the no neighbor timers command.

### Command Mode
Router Configuration Mode BGP VRF address family configuration mode (config-router-vrf-af): Note that the configuration applies to all address families in the VRF.

### Syntax
```text
neighbor ip-address | tag timers keepalive hold
no neighbor ip-address | tag timers
```

### Parameters
```text
ip-address: Neighbor IP address.
tag: Neighbor tag.
keepalive: The interval between for sending keepalive messages between neighbors, ranging from 1-65535 seconds. The default value is 60.
hold: Neighbor hold time, ranging from 1-65535 seconds. The default value is 180.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set the keepalive interval to 10 seconds and hold time to 30 seconds for public BGP neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# neighbor 1.1.1.1 timers 10 30
Set the keepalive interval to 10 seconds and hold time to 30 seconds for private VRF a BGP neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# address-family ipv4 vrf a
Switch(config-router-vrf-af)# neighbor 1.1.1.1 timers 10 30
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## neighbor timers connect

### Purpose
This command is used to configure the interval of the neighbor reconnecting to the timer. To disable this feature, please use the no command.

### Command Mode
Router Configuration Mode BGP VRF address family configuration mode (config-router-vrf-af): Note that the configuration applies to all address families in the VRF.

### Syntax
```text
neighbor ip-address | tag timers connect connect
no neighbor ip-address | tag timers connect
```

### Parameters
```text
ip-address: Neighbor IP address.
tag: Neighbor tag.
connect: Interval of the neighbor reconnecting to the timer.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the reconnection timer to 100 seconds for public BGP neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# neighbor 1.1.1.1 timers connect 100
Configure the reconnection timer to 100 seconds for private VRF a BGP neighbor 1.1.1.1:
Switch(config)# address-family ipv4 vrf a
Switch(config-router-vrf-af)# neighbor 1.1.1.1 timers connect 100
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## neighbor tracking

### Purpose
This command is used to configure neighbor tracking functionality, specifying the delay time for route updates when real-time detection indicates a neighbor state change. To disable this feature, please use the no command.

### Command Mode
Router Configuration Mode

### Syntax
```text
neighbor ip-address | tag tracking [ delay time ]
no neighbor ip-address | tag tracking
```

### Parameters
```text
ip-address: Neighbor IP address.
tag: Neighbor tag.
time: Delay time for route updates, in seconds (range 0-65535, default is 10 seconds).
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure link state tracking for neighbor 1.1.1.1 and specify a route update delay time of 100 seconds:
Switch(config)#router bgp 100
Switch(config-router)# neighbor 1.1.1.1 tracking delay 100
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## neighbor ttl-security hops

### Purpose
This command is used to configure the interval of the neighbor reconnecting to the timer. To disable this feature, please use the no command.

### Command Mode
Router Configuration Mode BGP VRF address family configuration mode (config-router-vrf-af): Note that the configuration applies to all address families in the VRF.

### Syntax
```text
neighbor ip-address | tag ttl-security hops hops
no neighbor ip-address | tag ttl-security hops
```

### Parameters
```text
ip-address: Neighbor IP address.
tag: Neighbor tag.
hops: Maximum hop count.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure a maximum hop count of 10 for public BGP neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# neighbor 1.1.1.1 ttl-security hops 10
Configure a maximum hop count of 10 for private VRF a BGP neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# address-family ipv4 vrf a
Switch(config-router-vrf-af)# neighbor 1.1.1.1 ttl-security hops 10
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## neighbor update-group converge

### Purpose
This command is used to configure the synchronous convergence feature of a neighbor update group. After configuration, convergence is only considered complete after all neighbors within the group have finished their updates. To disable this feature, please use the no command.

### Command Mode
Router Configuration Mode BGP VRF address family configuration mode (config-router-vrf-af): Note that the configuration applies to all address families in the VRF.

### Syntax
```text
neighbor ip-address | tag update-group converge
no neighbor ip-address | tag update-group converge
```

### Parameters
```text
ip-address: Neighbor IP address.
tag: Neighbor tag.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the synchronous convergence feature for the update group of public BGP neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# neighbor 1.1.1.1 update-group converge
Configure the synchronous convergence feature for the update group of private VRF a BGP neighbor 1.1.1.1:
Switch(config)#router bgp 100
Switch(config-router)# address-family ipv4 vrf a
Switch(config-router-vrf-af)# neighbor 1.1.1.1 update-group converge
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## neighbor update-group independent

### Purpose
This command is used to forcibly designate a neighbor as a separate update group, causing its route updates to be processed completely independently. To disable this feature, please use the no command.

### Command Mode
Router Configuration Mode BGP VRF address family configuration mode (config-router-vrf-af): Note that the configuration applies to all address families in the VRF.

### Syntax
```text
neighbor ip-address | tag update-group independent
no neighbor ip-address | tag update-group independent
```

### Parameters
```text
ip-address: Neighbor IP address.
tag: Neighbor tag.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure public BGP neighbor 1.1.1.1 as a separate update group:
Switch(config)#router bgp 100
Switch(config-router)# neighbor 1.1.1.1 update-group independent
Configure private VRF a BGP neighbor 1.1.1.1 as a separate update group:
Switch(config)#router bgp 100
Switch(config-router)# address-family ipv4 vrf a
Switch(config-router-vrf-af)# neighbor 1.1.1.1 update-group independent
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## neighbor update-source

### Purpose
This command is used to specify the source IP address used when establishing a BGP session. To disable this feature, please use the no command.

### Command Mode
Router Configuration Mode BGP VRF address family configuration mode (config-router-vrf-af): Note that the configuration applies to all address families in the VRF.

### Syntax
```text
neighbor ip-address | tag update-source source
no neighbor ip-address | tag update-source
```

### Parameters
```text
ip-address: Neighbor IP address.
tag: Neighbor tag.
source: Specify the IP address used as the source interface for route updates.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the source IP for establishing a BGP session with public BGP neighbor 1.1.1.1 as 2.2.2.2:
Switch(config)#router bgp 100
Switch(config-router)# neighbor 1.1.1.1 update-source 2.2.2.2
Configure the source IP for establishing a BGP session with private VRF a BGP neighbor 1.1.1.1 as 2.2.2.2:
Switch(config)#router bgp 100
Switch(config-router)# address-family ipv4 vrf a
Switch(config-router-vrf-af)# neighbor 1.1.1. 1 update-source 2.2.2.2
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## neighbor weight

### Purpose
This command is used to set the default weight for routes from this neighbor. To delete the weight, please use the no command.

### Command Mode
Router Configuration Mode. Configuration in this mode actually takes effect in the IPv4 unicast address family. BGP address family configuration mode (config-router-af) BGP VRF address family configuration mode (config-router-vrf-af)

### Syntax
```text
neighbor ip-address | tag weight weight
no neighbor ip-address | tag weight
```

### Parameters
```text
ip-address: Neighbor IP address.
tag: Neighbor tag.
weight: Default weight, ranging from 0-65535.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the default weight for routes received from public BGP neighbor 1.1.1.1 as 10:
Switch(config)#router bgp 100
Switch(config-router)# neighbor 1.1.1.1 weight 10
Configure the default weight for routes received from public BGP neighbor 1.1.1.1 as 10 (within the address family):
Switch(config)#router bgp 100
Switch(config-router)# address-family ipv4 unicast
Switch(config-router-af)# neighbor 1.1.1.1 weight 10
Configure the default weight for routes received from private VRF a BGP neighbor 1.1.1.1 as 10:
Switch(config)#router bgp 100
Switch(config-router)# address-family ipv4 vrf a
(config-router-vrf-af)# neighbor 1.1.1.1 weight 10
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## show ip bgp

### Purpose
This command is used to view the BGP routing table.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip bgp [vrf vrfname] [ipv4 | ipv6] [ip-address| ip-address/mask-len]
```

### Parameters
```text
vrfname: VRF name.
ip-address: Network segment to display.
ip-address/mask-len: The network segment IP address and mask length to display.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the BGP routing table for the network segment 2.2.2.0:
Switch#show ip bgp 2.2.2.0
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## show ip bgp attribute-info

### Purpose
This command is used to view all BGP attribute information.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip bgp attribute-info
```

### Parameters
```text
None
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
View all BGP attribute information:
Switch# show ip bgp attribute-info
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## show ip bgp cidr-only

### Purpose
This command is used to view only routes with non-natural network masks.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip bgp [vrf vrfname] [ipv4 | ipv6] cidr-only
```

### Parameters
```text
vrfname: VRF name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
View only routes with non-natural network masks:
Switch# show ip bgp cidr-only
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## show ip bgp dampening flap-statistics

### Purpose
This command is used to view the statistics of route flap penalty.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip bgp [vrf vrfname] [ipv4 | ipv6] dampening flap-statistics
```

### Parameters
```text
vrfname: VRF name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the statistics of route flap penalty:
Switch# show ip bgp dampening flap-statistics
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## show ip bgp dampening dampened-paths

### Purpose
This command is used to view the information about dampened paths due to flapping.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip bgp [vrf vrfname] [ipv4 | ipv6] dampening dampened-paths
```

### Parameters
```text
vrfname: VRF name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the information about dampened paths due to flapping:
Switch# show ip bgp dampening dampened-paths
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## show ip bgp dampening parameters

### Purpose
This command is used to view the parameters related to route flapping.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip bgp [vrf vrfname] [ipv4 | ipv6] dampening parameters
```

### Parameters
```text
vrfname: VRF name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the parameters related to route flapping:
Switch# show ip bgp dampening parameters
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## show ip bgp {ipv4 | ipv6 | l2vpn evpn} all

### Purpose
This command is used to view the BGP routing table for the corresponding address family.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip bgp {ipv4 | ipv6 | l2vpn evpn} all
```

### Parameters
```text
None.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
View all BGP IPv4 address family routing tables:
Switch# show ip bgp ipv4 all
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## show ip bgp l2vpn evpn rd

### Purpose
This command is used to view the routing table for the corresponding BGP L2VPN EVPN RD.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip bgp l2vpn evpn rd [rd | all ]
```

### Parameters
```text
rd: ASN:NN or ipaddress:NN.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the routing tables for all BGP L2VPN EVPN RDs::
Switch# show ip bgp l2vpn evpn rd all
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## show ip bgp memory

### Purpose
This command is used to view the BGP memory information.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip bgp memory
```

### Parameters
```text
None,
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the BGP memory information.:
Switch# show ip bgp memory
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## show ip bgp neighbors

### Purpose
This command is used to view the BGP neighbor information.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip bgp [vrf vrfname] [ipv4 | ipv6] neighbors ip-address
```

### Parameters
```text
vrfname: VRF name.
ip-address: Neighbor IP address.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the BGP neighbor information:
Switch# show ip bgp neighbors
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## show ip bgp neighbors advertised-routes

### Purpose
This command is used to view the routing information advertised to neighbors.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip bgp [vrf vrfname] [ipv4 | ipv6] neighbors ip-address advertised-routes
show ip bgp [l2vpn evpn] neighbors ip-address advertised-routes
```

### Parameters
```text
vrfname: VRF name.
ip-address: Neighbor IP address.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the routing information advertised to neighbor 1.1.1.1:
Switch# show ip bgp neighbors 1.1.1.1 advertised-routes
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## show ip bgp neighbors bestpath-routes

### Purpose
This command is used to view the best-path route information learned from a specified neighbor

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip bgp [vrf vrfname] [ipv4 | ipv6] neighbors ip-address bestpath-routes
```

### Parameters
```text
vrfname: VRF name.
ip-address: Neighbor IP address.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the best-path route information learned from neighbor 1.1.1.1:
Switch# show ip bgp neighbors 1.1.1.1 bestpath-routes
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## show ip bgp neighbors dampened-routes

### Purpose
This command is used to view the dampened routes received from neighbors.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip bgp [vrf vrfname] [ipv4 | ipv6] neighbors ip-address dampened-routes
```

### Parameters
```text
vrfname: VRF name.
ip-address: Neighbor IP address.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the dampened routes received from neighbor 1.1.1.1:
Switch# show ip bgp neighbors 1.1.1.1 dampened-routes
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## show ip bgp neighbors flap-statistics

### Purpose
This command is used to view the flapping route information of a neighbor.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip bgp [vrf vrfname] [ipv4 | ipv6] neighbors ip-address flap-statistics
```

### Parameters
```text
vrfname: VRF name.
ip-address: Neighbor IP address.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
view the flapping route information of neighbor 1.1.1.1:
Switch# show ip bgp neighbors 1.1.1.1 flap-statistics
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## show ip bgp neighbors prefix-counts

### Purpose
This command is used to view he detailed prefix counts of a neighbor.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip bgp [vrf vrfname] [ipv4 | ipv6] neighbors ip-address prefix-counts
```

### Parameters
```text
vrfname: VRF name.
ip-address: Neighbor IP address.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the detailed prefix counts of neighbor 1.1.1.1:
Switch# show ip bgp neighbors 1.1.1.1 prefix-counts
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## show ip bgp neighbors received-routes

### Purpose
This command is used to view the routes received from neighbors.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip bgp [vrf vrfname] [ipv4 | ipv6] neighbors ip-address received-routes
```

### Parameters
```text
vrfname: VRF name.
ip-address: Neighbor IP address.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
View he routes received from neighbor 1.1.1.1:
Switch# show ip bgp neighbors 1.1.1.1 received-routes
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## show ip bgp neighbors routes

### Purpose
This command is used to view the routes learned from neighbors.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip bgp [vrf vrfname] [ipv4 | ipv6] neighbors ip-address routes
```

### Parameters
```text
vrfname: VRF name.
ip-address: Neighbor IP address.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the routes learned from neighbor 1.1.1.1:
Switch# show ip bgp neighbors 1.1.1.1 routes
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## show ip bgp nexthop

### Purpose
This command is used to view the next hop information.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip bgp nexthop ip-address
```

### Parameters
```text
ip-address: Network segment to display.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the BGP next hop information:
Switch# show ip bgp nexthop
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## show ip bgp peer-group

### Purpose
This command is used to view the peer group information.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip bgp [vrf vrfname] peer-group [name]
```

### Parameters
```text
vrfname: VRF name.
name: Peer group name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the BGP peer group information:
Switch# show ip bgp peer group
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## show ip bgp statistics

### Purpose
This command is used to view the route prefix statistical information for the corresponding BGP address family.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip bgp {[vrf vrfname] [ipv4 | ipv6]} statistics
show ip bgp l2vpn evpn statistics
```

### Parameters
```text
vrfname: VRF name.
name: Peer group name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the route prefix statistical information for all BGP IPv4 address families:
Switch# show ip bgp ipv4 statistics
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## show ip bgp statistics-all

### Purpose
This command is used to view the route prefix statistical count information for all address families.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip bgp statistics-all
```

### Parameters
```text
None.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the route prefix statistical count information for all address families::
Switch# show ip bgp statistics-all
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## show ip bgp summary

### Purpose
This command is used to view the summary of BGP neighbors.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip bgp [vrf vrfname] [ipv4 | ipv6] summary [established | falied] [neighbor ip-address | remote-as as]
```

### Parameters
```text
vrfname: VRF name.
as: as
AS number.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the summary of BGP neighbors:
Switch# show ip bgp summary
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## show ip bgp update-groups

### Purpose
This command is used to view the BGP update group information.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip bgp [vrf vrfname] [ipv4 | ipv6] update-groups [group-id]
show ip bgp l2vpn evpn update-groups [group-id]
```

### Parameters
```text
vrfname: VRF name.
group-id: as
Update group ID.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the BGP update group information:
Switch# show ip bgp update-groups
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## show ip bgp vrfs

### Purpose
This command is used to view the information for all BGP VRF instances.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip bgp vrfs
```

### Parameters
```text
None.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the information for all BGP VRF instances:
Switch# show ip bgp vrfs
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## clear ip bgp

### Purpose
This command is used to reset BGP neighbors.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
clear ip bgp [vrf vrfname] as
clear ip bgp [vrf vrfname] ip-address
```

### Parameters
```text
vrfname: VRF name.
as: AS number of the neighbor.
ip-address: Neighbor
s IP.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Reset BGP neighbor 1.1.1.1:
Switch# clear ip bgp 1.1.1.1
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## clear ip bgp all

### Purpose
This command is used to reset all BGP neighbors.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
clear ip bgp [vrf vrfname] all
```

### Parameters
```text
vrfname: VRF name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Reset all BGP neighbors:
Switch# clear ip bgp all
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## clear ip bgp dampening

### Purpose
This command is used to reset BGP route dampening.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
clear ip bgp dampening ip-address [mask]
```

### Parameters
```text
ip-address: Network segment IP address.
mask: Network segment mask.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Reset route dampening for network segment 1.1.1.0/24:
Switch# clear ip bgp dampening 1.1.1.0 255.255.255.0
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## clear ip bgp external

### Purpose
This command is used to reset reset all EBGP neighbors.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
clear ip bgp [vrf vrfname] external
```

### Parameters
```text
vrfname: VRF name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Reset all EBGP neighbors:
Switch# clear ip bgp external
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## clear ip bgp peer-group

### Purpose
This command is used to reset a specified BGP peer group.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
clear ip bgp [vrf vrfname] peer-group name
```

### Parameters
```text
vrfname: VRF name.
name: Peer group name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Reset all neighbors within BGP peer group a:
Switch# clear ip bgp peer-group a
Privileged EXEC Mode and Any Configuration Mode
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.
