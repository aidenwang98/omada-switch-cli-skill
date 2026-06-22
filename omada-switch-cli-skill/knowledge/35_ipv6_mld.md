# IPv6 MLD Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 34 IPv6 MLD Commands (Only for Certain Devices)

Location: extracted Word text lines 15659-15929

## Chapter Notes

Official documentation states: MLD (Multicast Listener Discovery) is a multicast member management protocol for IPv6 environments. Its function is similar to IGMP in IPv4, used for endpoints to report multicast group listening states to routers and control the forwarding scope of IPv6 multicast traffic.

- This chapter is marked `Only for Certain Devices`; treat all configuration commands as model-dependent.

## ipv6 mld

### Purpose
This command is used to configure the global hardware switch for MLD, allowing MLD packets to be sent to the CPU. Disabled by default.

### Command Mode
Global Configuration Mode

### Syntax
```text
ipv6 mld
no ipv6 mld
```

### Parameters
```text
None.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config)# (config)# ipv6 mld
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ipv6 mld last-member-query-count

### Purpose
This command is used to configure the Last Member Query Count on an interface. Default is 2.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ipv6 mld last-member-query-count value
no ipv6 mld last-member-query-count
```

### Parameters
```text
value
Last Member Query Count, ranging from 1 to 20.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config-if)# ipv6 mld last-member-query-count 3
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ipv6 mld last-member-query-interval

### Purpose
This command is used to configure the Last Member Query Interval on an interface. Default is 1000 milliseconds.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ipv6 mld last-member-query-interval value
no ipv6 mld last-member-query-interval
```

### Parameters
```text
value
Last Member Query Interval, in milliseconds, ranging from 1000 to 25500.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config-if)# ipv6 mld last-member-query-interval 2000
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ipv6 mld mroute-proxy

### Purpose
Configure this command on the MLD proxy downstream interface to specify the proxy upstream interface for this interface.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ipv6 mld mroute-proxy intf_type intf_id
no ipv6 mld mroute-proxy
```

### Parameters
```text
intf_type
Interface type of the specified proxy upstream interface.
intf_id
Interface ID of the specified proxy upstream interface.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config-if)# ipv6 mld mroute-proxy vlan 1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ipv6 mld proxy-service

### Purpose
Configure an interface as the MLD proxy upstream interface.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ipv6 mld proxy-service
no ipv6 mld proxy-service
```

### Parameters
```text
None,
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config-if)# ipv6 mld proxy-service
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ipv6 mld querier-timeout

### Purpose
This command is used to configure the timeout period for other queriers when this interface is not the querier. Default is (robustness (default: 2) * query-interval (default: 125)) + (query-max-response-time (default: 10) / 2) = 255 seconds.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ipv6 mld querier-timeout value
no ipv6 mld querier-timeout
```

### Parameters
```text
value
Querier timeout value, in seconds, ranging from 60 to 300.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config-if)# ipv6 mld querier-timeout 100
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ipv6 mld query-interval

### Purpose
This command is used to configure the interval at which the querier sends query messages. Default is 125 seconds.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ipv6 mld query-interval value
no ipv6 mld query-interval
```

### Parameters
```text
value
Query interval value, in seconds, range 1 to 18000.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config-if)# ipv6 mld query-interval 100
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ipv6 mld query-max-response-time

### Purpose
This command is used to configure the maximum query response time. Default is 10 seconds.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ipv6 mld query-max-response-time value
no ipv6 mld query-max-response-time
```

### Parameters
```text
value
Maximum query response time value, in seconds, range 1 to 240.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config-if)# ipv6 mld query-max-response-time 5
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ipv6 mld robustness

### Purpose
This command is used to configure the robustness value. Default is 2.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ipv6 mld robustness value
no ipv6 mld robustness
```

### Parameters
```text
value
Robustness value, range 2 to 7.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config-if)# ipv6 mld robustness 3
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ipv6 mld startup-query-count

### Purpose
This command is used to configure the initial query count for the querier. Default is 2.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ipv6 mld startup-query-count value
no ipv6 mld startup-query-count
```

### Parameters
```text
value
Startup query count value, range 1 to 20.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config-if)# ipv6 mld startup-query-count 3
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ipv6 mld startup-query-interval

### Purpose
This command is used to configure the initial query interval for the querier. Default is 31 seconds.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ipv6 mld startup-query-interval value
no ipv6 mld startup-query-interval
```

### Parameters
```text
value
Startup query interval value, in seconds, range 1 to 18000.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config-if)# ipv6 mld startup-query-interval 100
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ipv6 mld static-group

### Purpose
This command is used to configure a static group join on the interface.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ipv6 igmp static-group group_addr [ source src_addr ]
no ipv6 mld static-group group_addr [ source src_addr ]
```

### Parameters
```text
group_addr
Multicast group address to join.
src_addr
Specified multicast source for the group join.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config-if)# ipv6 mld static-group ff1e::1 souce 2001:1::101
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ipv6 mld version

### Purpose
This command is used to configure the MLD version. Default is MLDv2.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ipv6 mld version value
no ipv6 mld version
```

### Parameters
```text
value
Version value, range 1 to 2.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config-if)# ipv6 mld version 1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## show ipv6 mld groups

### Purpose
This command is used to display the MLD member group information.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ipv6 mld groups [ interface intf_type intf_id ] [ group_addr ] [ detail ]
show ipv6 mld [ vrf vrfname ] groups [ group_addr ] [ detail ]
```

### Parameters
```text
intf_type
Specified interface type to display.
intf_id
Specified interface ID to display.
group_addr
Specified multicast group member to display.
vrfname
Virtual Routing and Forwarding instance name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch#show ipv6 mld groups detail
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## show ipv6 mld proxy groups

### Purpose
This command is used to display MLD proxy upstream interface member group information.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ipv6 mld proxy groups [ interface intf_type intf_id ] [ group_addr ] [ detail ]
show ipv6 mld [ vrf vrfname ] proxy groups [ group_addr ] [ detail ]
```

### Parameters
```text
intf_type
Specified interface type to display.
intf_id
Specified interface ID to display.
group_addr
Specified multicast group member to display.
vrfname
Virtual Routing and Forwarding instance name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch# show ipv6 mld proxy groups detail
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## show ipv6 mld interface

### Purpose
This command is used to display MLD interface status/packet statistics.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ipv6 mld interface intf_type intf_id [ statistic ]
```

### Parameters
```text
intf_type
Specified interface type to display.
intf_id
Specified interface ID to display.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch# show ipv6 mld interface vlan 1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## show ipv6 mld

### Purpose
This command is used to display MLD global configuration and interface status under a VRF.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ipv6 mld [ vrf vrfname ]
```

### Parameters
```text
vrfname
Virtual Routing and Forwarding instance name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch# show ipv6 mld vrf test
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.
