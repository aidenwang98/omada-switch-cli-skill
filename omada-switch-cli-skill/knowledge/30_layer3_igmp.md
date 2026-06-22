# Layer 3 IGMP Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 28 Layer 3 IGMP Commands (Only for Certain Devices)

Location: extracted Word text lines 13412-13771

## Chapter Notes

- This chapter is marked `Only for Certain Devices`; treat all configuration commands as model-dependent.

## ip igmp (global)

### Purpose
The ip igmp command is used to enable IGMP globally. To disable the IGMP function, please use no ip igmp command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip igmp
no ip igmp
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable IGMP function globally:
Switch(config)# ip igmp
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip igmp (on specific ports)

### Purpose
The ip igmp command is used to enable IGMP on specific ports. To disable the IGMP function, please use no ip igmp command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip igmp
no ip igmp
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable IGMP function on VLAN 2:
Switch(config)#interface vlan 2
Switch(config-if)#ip igmp
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip igmp header-validation

### Purpose
The ip igmp header-validation command is used to enable IGMP message header validation functions: TTL (Time To Live), ToS (Type of Service), and Router Alert options. For IGMPv1, only the TTL field is validated. For IGMPv2, the TTL and Router Alert fields are validated. For IGMPv3, the TTL, ToS and Router Alert fields are validated. To disable the IGMP function, please use no ip igmp header-validation command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip igmp header-validation [ vrf vrfname ]
no ip igmp header-validation [ vrf vrfname ]
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
Enable IGMP message header validation:
Switch(config)# ip igmp header-validation
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Official note: For certain models, this command is used to configure the Router Alert options only. Actual running results may vary by model/versions/regions.
- Availability: Only for certain devices according to the official chapter title.

## ip igmp join-group

### Purpose
This command is used to configure a static group join on an interface and join the group in the kernel.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip igmp join-group group_addr [ source src_addr ]
no ip igmp join-group group_addr [ source src_addr ]
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
Switch(config-if)# ip igmp join-group 235.0.0.1 souce 192.168.0.1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Official note: Do not use the ip igmp join-group command unless it is used in a test environment.
- Availability: Only for certain devices according to the official chapter title.

## ip igmp mroute-proxy

### Purpose
Configure this command on the IGMP proxy downstream interface to specify the proxy upstream interface for this interface.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip igmp mroute-proxy intf_type intf_id
no ip igmp mroute-proxy
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
Switch(config-if)# ip igmp mroute-proxy vlan 1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip igmp offlink

### Purpose
This command is used to allow receiving IGMP Report messages with source IP addresses not from the local network segment.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip igmp offlink
no ip igmp offlink
```

### Parameters
```text
None.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config-if)# ip igmp offlink
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip igmp proxy unsolicited-report-interval

### Purpose
This command is used to configure the unsolicited report interval for the proxy upstream interface. Default is 1000 milliseconds.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip igmp proxy unsolicited-report-interval value
no ip igmp proxy unsolicited-report-interval
```

### Parameters
```text
value
Unsolicited report interval value, in milliseconds, range 1000 to 25500.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config-if)# ip igmp proxy unsolicited-report-interval 1500
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip igmp proxy-service

### Purpose
Configure this interface as the proxy upstream interface.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip igmp proxy-service
no ip igmp proxy-service
```

### Parameters
```text
None,
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config-if)# ip igmp proxy-service
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip igmp querier-timeout

### Purpose
This command is used to configure the timeout period for other queriers when this interface is not the querier. Default is (robustness (default: 2) * query-interval (default: 125)) + (query-max-response-time (default: 10) / 2) = 255 seconds.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip igmp querier-timeout value
no ip igmp querier-timeout
```

### Parameters
```text
value
Querier timeout value, in seconds, range 60 to 300,
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config-if)# ip igmp querier-timeout 100
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip igmp static-group

### Purpose
This command is used to configure a static group join on the interface.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip igmp static-group group_addr [ source src_addr ]
no ip igmp static-group group_addr [ source src_addr ]
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
Switch(config-if)# ip igmp static-group 235.0.0.1 souce 192.168.0.1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip igmp version

### Purpose
The ip igmp version command is used to configure IGMP version globally. To return to the default configuration IGMPv3, please use no ip igmp version command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip igmp version {v1 | v2 | v3 }
no ip igmp version
```

### Parameters
```text
v1 | v2 | v3
Specify the IGMP version. By default, it is IGMP v3.
v1: The switch works as an IGMPv1 switch. It can only process IGMPv1 messages from the host. Report messages of other versions are ignored.
v2: The switch works as an IGMPv2 switch. It can process both IGMPv1 and IGMPv2 messages from the host. IGMPv3 messages are ignored.
v3: The switch works as an IGMPv3 switch. It can process IGMPv1, IGMPv2 and IGMPv3 messages from the host.
```

### Default
By default, it is IGMP v3.

### Example
```text
Specify the IGMP version as v2:
Switch (config-if)#ip igmp version v2
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip igmp last-member-query-count

### Purpose
The ip igmp last-member-query-count command is used to configure the number of times special group query messages sent on the specified interface. To restore the default value, please use no ip igmp last-member-query-count command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip igmp last-member-query-count count
no ip igmp last-member-query-count
```

### Parameters
```text
count: The number of times IGMP group-specific query messages are sent, ranging from 1-20. The default value is 2.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the number of times special group query messages sent on VLAN 2 as 3:
Switch (config)#interface vlan 2
Switch (config-if)#ip igmp last-member-query-count 3
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip igmp last-member-query-interval

### Purpose
The ip igmp last-member-query-interval command is used to configure the time interval for sending special group query messages on the specified interface. To restore the default value, please use no ip igmp last-member-query-interval command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip igmp last-member-query-interval interval
no ip igmp last-member-query-interval
```

### Parameters
```text
inteval: The interval for sending IGMP group-specific query messages. The value range is 10-255 (1/10 second). The default value is 10 (1/10 second).
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the time interval for sending special group query messages sent on VLAN 2 to 2 seconds:
Switch (config)#interface vlan 2
Switch (config-if)#ip igmp last-member-query-interval 20
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip igmp query-interval

### Purpose
The ip igmp query-interval command is used to configure the IGMP general query interval on a specified interface. To restore the default value, please use no ip igmp query-interval command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip igmp query-interval interval
no ip igmp query-interval
```

### Parameters
```text
inteval: The time interval for sending IGMP general query messages on the specified interface. The value range is 1-3600 seconds. The default value is 125 seconds.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the interval for sending IGMP general query messages on VLAN 2 to 50 seconds:
Switch (config)#interface vlan 2
Switch (config-if)#ip igmp query-interval 50
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip igmp query-max-response-time

### Purpose
The ip igmp query-max-response-time command is used to configure the maximum response time to IGMP general query messages on the specified interface. To restore the default value, please use no ip igmp query-max-response-time command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip igmp query-max-response-time time
no ip igmp query-max-response-time
```

### Parameters
```text
time: The maximum response time for general group query messages on the specified interface, the value range is 10-255 (1/10 seconds), the default value is 100 (1/10 seconds).
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the maximum response time for general group query messages on VLAN 2 to 5 seconds:
Switch (config)#interface vlan 2
Switch (config-if)#ip igmp query-max-response-time 50
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip igmp robustness

### Purpose
The ip igmp robustness command is used to configure the robustness coefficient on the specified interface. To restore the default value, please use no ip igmp robustness command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip igmp robustness robustness
no ip igmp robustness
```

### Parameters
```text
robustness: Specify the IGMP robustness coefficient, the value range is 1-255, and the default value is 2.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the robustness coefficient on VLAN 2 to 3:
Switch (config)#interface vlan 2
Switch (config-if)#ip igmp robustness 3
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip igmp startup-query-interval

### Purpose
The ip igmp startup-query-interval command is used to configure the time interval for sending initial query packets on the specified interface. To restore the default value, please use no ip igmp startup-query-interval command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip igmp startup-query-interval interval
no ip igmp startup-query-interval
```

### Parameters
```text
interval: The interval for sending IGMP initial query messages. The value range is 1-300 seconds. The default value is 31 seconds.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the time interval for sending initial query packets on VLAN 2 to 10 seconds:
Switch (config)#interface vlan 2
Switch (config-if)#ip igmp query-interval 10
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## show ip igmp

### Purpose
The show ip igmp command is used to display basic IGMP information.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip igmp [ vrf vrfname ]
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display basic IGMP information:
Switch(config)#show ip igmp
```

### Notes
- Permission requirement: vrfname Virtual Routing and Forwarding instance name.
- Availability: Only for certain devices according to the official chapter title.

## show ip igmp groups

### Purpose
The show ip igmp groups command is used to display the information of all dynamic multicast groups or specified multicast groups.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip igmp groups [ interface intf_type intf_id ] [ group_addr ] [ detail ]
show ip igmp [ vrf vrfname ] groups [ group_addr ] [ detail ]
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
Display the information of dynamic multicast 224.0.2.40:
Switch(config)#show ip igmp groups 224.0.2.40 detail
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## show ip igmp proxy groups

### Purpose
The show ip igmp proxy groups command is used to display the IGMP proxy upstream interface member group information.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip igmp proxy groups [ interface intf_type intf_id ] [ group_addr ] [ detail ]
show ip igmp [ vrf vrfname ] proxy groups [ group_addr ] [ detail ]
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
Display the IGMP proxy upstream interface member group information.
Switch(config)# show ip igmp proxy groups detail
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## show ip igmp interface

### Purpose
The show ip igmp interface command is used to display IGMP interface status/packet statistics.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip igmp interface intf_type intf_id [ statistic ]
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
Display the IGMP status/packet statistics on port 1/0/1:
Switch# show ip igmp interface vlan 1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.
