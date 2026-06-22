# MLD Snooping Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 33 MLD Snooping Commands

Location: extracted Word text lines 15217-15658

## Chapter Notes

Official documentation states: MLD Snooping (Multicast Listener Discovery Snooping) is a multicast control mechanism running on Layer 2 switch. It can effectively prevent multicast groups being broadcasted in the IPv6 network.

- Use these commands only when the requested feature and target interface/VLAN/ring/session details are clear.

## ipv6 mld snooping (global)

### Purpose
The ipv6 mld snooping command is used to enable MLD Snooping function globally. If this function is disabled, all related MLD Snooping function would not work. To disable this function, please use no ipv6 mld snooping command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ipv6 mld snooping
no ipv6 mld snooping
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable MLD Snooping:
Switch(config)# ipv6 mld snooping
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## ipv6 mld snooping drop-unknown

### Purpose
The ipv6 mld snooping drop-unknown command is used to enable the unknown multicast packets filter function. To disable this function, please use no ipv6 mld snooping drop-unknown command. By default, it is disabled.

### Command Mode
Global Configuration Mode

### Syntax
```text
ipv6 mld snooping drop-unknown
no ipv6 mld snooping drop-unknown
```

### Parameters
No parameters.

### Default
By default, it is disabled.

### Example
```text
Enable unknown multicast filter function:
Switch(config)# ipv6 mld snooping drop-unknown
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## ipv6 mld snooping vlan-config

### Purpose
The ipv6 mld snooping vlan-config command is used to enable VLAN MLD Snooping function or to modify MLD Snooping parameters. To disable the VLAN MLD Snooping function, please use no ipv6 mld snooping vlan-config command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ipv6 mld snooping vlan-config vlan-id-list [ rtime router-time | mtime member-time | ltime leave-time ]
no ipv6 mld snooping vlan-config vlan-id-list [ rtime | mtime | ltime ]
```

### Parameters
```text
vlan-id-list
The ID list of the VLAN desired to modify configuration, ranging from 1 to 4094, in the format of 1-3, 5.
router-time
The Router Port Aging Time. Within this time, if the switch does not receive any MLD query messages from the router port, it will consider this port is not a router port any more. Valid values are from 60 to 600 in seconds, and the default value is 300 seconds.
member-time
The Member Port Aging Time. Within this time, if the switch does not receive any MLD report messages from the member port, it will consider this port is not a member port any more. Valid values are from 60 to 600 in seconds, and the default value is 260 seconds.
leave-time
The Leave Time. Valid values are from 1 to 30 in seconds, and the default value is 1 second. When the switch receives a done message from a port to leave a multicast group, it will wait for a Leave Time before removing the port from the multicast group. During the period, if the switch receives any report messages from the port, the port will not be removed from the multicast group. Exceptions are as follows:
If the member port ages out before the Leave Time ends and no report messages are received, the port will be removed from the multicast group once its Member Port Aging Time ends.
The Leave Time mechanism will not take effect when Fast Leave takes effect.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the MLD Snooping function and modify Router Port Time as 300 seconds, Member Port Time as 200 seconds for VLAN 1-3:
Switch(config)# ipv6 mld snooping vlan-config 1-3 rtime 300
Switch(config)# ipv6 mld snooping vlan-config 1-3 mtime 200
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## ipv6 mld snooping vlan-config (immediate-leave)

### Purpose
This command is used to enable the Fast Leave feature for specific VLANs. To disable Fast Leave on the VLANs, please use no ipv6 mld snooping vlan-config vlan-id-list immediate-leave command. This function is disabled by default.

### Command Mode
Global Configuration Mode

### Syntax
```text
ipv6 mld snooping vlan-config vlan-id-list immediate-leave
no ipv6 mld snooping vlan-config vlan-id-list immediate-leave
```

### Parameters
```text
vlan-id-list
The ID list of the VLAN desired to modify configuration, ranging from 1 to 4094, in the format of 1-3, 5.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the Fast Leave for VLAN 1-3:
Switch(config)# ipv6 mld snooping vlan-config 1-3 immediate-leave
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ipv6 mld snooping vlan-config (report-suppression)

### Purpose
This command is used to enable the MLD Report Suppression function for specific VLANs. When enabled, the switch will only forward the first MLD report message for each multicast group to the MLD querier and suppress subsequent MLD report messages for the same multicast group during one query interval. This feature prevents duplicate report messages from being sent to the MLD querier. To disable the MLD report suppression function and forward all the MLD reports to the Layer 3 device in specific VLANs, please use no ipv6 mld snooping vlan-config vlan-id-list report-suppression command. This function is disabled by default.

### Command Mode
Global Configuration Mode

### Syntax
```text
ipv6 mld snooping vlan-config vlan-id-list report-suppression
no ipv6 mld snooping vlan-config vlan-id-list report-suppression
```

### Parameters
```text
vlan-id-list
The ID list of the VLAN desired to modify configuration, ranging from 1 to 4094, in the format of 1-3, 5.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the MLD Report Suppression for VLAN 1-3:
Switch(config)# ipv6 mld snooping vlan-config 1-3 report-suppression
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ipv6 mld snooping vlan-config (router-ports-forbidden)

### Purpose
This command is used to forbid the specified ports as being router ports in the specified VLAN(s). To delete the forbidden router ports, please use no ipv6 mld snooping vlan-config vlan-id-list router-ports-forbidd command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ipv6 mld snooping vlan-config vlan-id-list router-ports-forbidd interface { gigabitEthernet port-list | port-channel port-channel-list }
no ipv6 mld snooping vlan-config vlan-id-list router-ports-forbidd interface [ gigabitEthernet port-list | port-channel port-channel-list ]
```

### Parameters
```text
vlan-id-list
The ID list of the VLAN desired to modify configuration, ranging from 1 to 4094, in the format of 1-3, 5.
port-list
Forbid the specified ports as being router ports. Packets sent from multicast routers to these ports will be discarded.
port-channel-list
Forbid the specified port-channels as being router ports. Packets sent from multicast routers to these port-channels will be discarded.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Forbid the Ethernet ports 1/0/1-3 as being router ports in VLAN 1:
Switch(config)# ipv6 mld snooping vlan-config 1 router-ports-forbidd interface gigabitEthernet 1/0/1-3
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ipv6 mld snooping vlan-config (rport interface)

### Purpose
This command is used to specify the static router ports for specific VLANs. To delete the static router ports, please use no ipv6 mld snooping vlan-config vlan-id-list rport interface command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ipv6 mld snooping vlan-config vlan-id-list rport interface { gigabitEthernet port-list | port-channel port-channel-list }
no ipv6 mld snooping vlan-config vlan-id-list rport interface { gigabitEthernet port-list | port-channel port-channel-list }
```

### Parameters
```text
vlan-id-list
The ID list of the VLAN desired to modify configuration, ranging from 1 to 4094, in the format of 1-3, 5.
port-list
The list of Ethernet ports.
port-channel-list
The ID of the port channels.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set the router port as 1/0/1 for VLAN 1-2:
Switch(config)# ipv6 mld snooping vlan-config 1-2 rport interface gigabitEthernet 1/0/1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ipv6 mld snooping vlan-config (static)

### Purpose
This command is used to configure interfaces to statically join a multicast group. To remove interfaces from a static multicast group, please use no ipv6 mld snooping vlan-config vlan-id-list staticcommand.

### Command Mode
Global Configuration Mode

### Syntax
```text
ipv6 mld snooping vlan-config vlan-id-list static ip interface { gigabitEthernet port-list | port-channel port-channel-list }
no ipv6 mld snooping vlan-config vlan-id-list static ip interface { gigabitEthernet port-list | port-channel port-channel-list }
```

### Parameters
```text
vlan-id-list
The ID list of the VLAN desired to modify configuration, ranging from 1 to 4094, in the format of 1-3, 5.
Specify the IP address of the multicast group that the hosts want to join.
port-list
The list of Ethernet ports.
port-channel-list
The ID of the port channels.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure port ports 1/0/1-3 in VLAN 2 to statically join multicast group ff80::1234:1:
Switch(config)# ipv6 mld snooping vlan-config 2 static ff80::1234:1 interface gigabitEthernet 1/0/1-3
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ipv6 mld snooping vlan-config (querier)

### Purpose
This command is used to enable the MLD Snooping Querier feature for specific VLANs. To disable the MLD Snooping Querier feature on the VLANs, please use no ipv6 mld snooping vlan-config vlan-id-list querier command without any parameters. To restore the default values, please use no ipv6 mld snooping vlan-config vlan-id-list querier command with specified parameters.

### Command Mode
Global Configuration Mode

### Syntax
```text
ipv6 mld snooping vlan-config vlan-id-list querier [ max-response-time response-time | query-interval interval | general-query source-ip ip-addr | last-listener-query-count count | last-listener-query-interval interval ]
no ipv6 mld snooping vlan-config vlan-id-list querier [ max-response-time | query-interval | general-query source-ip | last-listener-query-count | last-listener-query-interval ]
```

### Parameters
```text
vlan-id-list
The ID list of the VLAN desired to modify configuration, ranging from 1 to 4094, in the format of 1-3, 5.
response-time
The host
s maximum response time to general query messages. Valid values are from 1 to 25 seconds, and the default value is 10 seconds.
query-interval interval
The interval between general query messages sent by the switch. Valid values are from 10 to 300 seconds, and the default value is 60 seconds.
ip-addr
The source IP address of the general query messages sent by the switch. It should be a unicast address. By default, it is fe80::2ff:ffff:fe00:1.
count
The number of group-specific queries to be sent. With MLD Snooping Querier enabled, when the switch receives an MLD done message, it obtains the address of the multicast group that the host wants to leave from the message. Then the switch sends out group-specific queries to this multicast group through the port receiving the done message. If specified count of group-specific queries are sent and no report message is received, the switch will delete the multicast address from the multicast forwarding table. Valid values are from 1 to 5, and the default value is 2.
last-member-query-interval interval
The interval between group- specific queries. Valid values are from 1 to 5 seconds, and the default value is 1 second.
```

### Default
By default, it is fe80::2ff:ffff:fe00:1.

### Example
```text
Enable the MLD Snooping Querier for VLAN 3, and configure the query interval as 100 seconds:
Switch(config)# ipv6 mld snooping vlan-config 3 querier
Switch(config)# ipv6 mld snooping vlan-config 3 querier query interval 100
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ipv6 mld snooping vlan-config drop-unknown

### Purpose
The ipv6 mld snooping vlan-config drop-unknown command is used to enable the drop-unknown function for the specified VLAN. When enabled, unregistered IPv6 multicast traffic within this VLAN will be discarded. To disable this function, please use the no ipv6 mld snooping vlan-config drop-unknown command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ipv6 mld snooping vlan-config vlan-id-list drop-unknown
no ipv6 mld snooping vlan-config vlan-id-list drop-unknown
```

### Parameters
```text
vlan-id-list
Single VLAN or VLAN range, maximum length 64 characters.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable drop-unknown for VLAN 1:
Switch(config)# ipv6 mld snooping vlan-config 1 drop-unknown
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Official note: This command is only available on certain devices.

## ipv6 mld snooping vlan-config route-unknown

### Purpose
The ipv6 mld snooping vlan-config route-unknown command is used to enable the route-unknown function for the specified VLAN. When enabled, unregistered multicast traffic in this VLAN will be forwarded to MLD snooping router ports. To disable this function, please use the no ipv6 mld snooping vlan-config route-unknown command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ipv6 mld snooping vlan-config vlan-id-list route-unknown
no ipv6 mld snooping vlan-config vlan-id-list route-unknown
```

### Parameters
```text
vlan-id-list
Single VLAN or VLAN range, maximum length 64 characters.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable route-unknown for VLAN 1:
Switch(config)# ipv6 mld snooping vlan-config 1 route-unknown
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Official note: This command is only available on certain devices.

## ipv6 mld snooping (interface)

### Purpose
The ipv6 mld snooping command is used to enable MLD Snooping function on the desired port. To disable this function, please use no ipv6 mld snooping command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
ipv6 mld snooping
no ipv6 mld snooping
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable MLD Snooping on port 1/0/3:
Switch(config)# interface gigabitEthernet 1/0/3
Switch(config-if)# ipv6 mld snooping
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## ipv6 mld snooping max-groups

### Purpose
The ipv6 mld snooping max-groups command is used to configure the maximum number of groups that a port can join in. The ipv6 mld snooping max-groups action is used to configure the action that the port takes when it receives an MLD report message and the maximum number of entries is in the forwarding table. To remove the maximum group limitation and return to the default of no limitation on the specified port, please use the no ipv6 mld snooping max-groups command. To return to the default action of dropping the report, please use the no ipv6 mld snooping max-groups action command. These commands only apply to the dynamic multicast groups.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
ipv6 mld snooping max-groups maxgroup
ipv6 mld snooping max-groups action { drop | replace }
no ipv6 mld snooping max-groups
no ipv6 mld snooping max-groups action
```

### Parameters
```text
maxgroup
Specify the maximum numbers of groups that the port can join. It ranges from 0 to 1000 and the default value is 1000.
drop
When the number of the dynamic multicast groups that a port joins has exceeded the max-group, the port will not join any new multicast group.
replace
When the number of the dynamic multicast groups that a port joins has exceeded the max-group, the newly joined multicast group will replace an existing multicast group with the lowest multicast group address.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Specify the maximum numbers of groups that ports 1/0/2-5 can join as 10, and configure the throttling action as replace:
Switch(config)#interface range gigabitEthernet 1/0/2-5
Switch(config-if-range)#ipv6 mld snooping max-groups 10
Switch(config-if-range)#ipv6 mld snooping max-groups action replace
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## ipv6 mld snooping immediate-leave

### Purpose
The ipv6 mld snooping immediate-leave command is used to configure the Fast Leave function for port. To disable the Fast Leave function, please use no ipv6 mld snooping immediate-leave command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
ipv6 mld snooping immediate-leave
no ipv6 mld snooping immediate-leave
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the Fast Leave function for port 1/0/3:
Switch(config)# interface gigabitEthernet 1/0/3
Switch(config-if)# ipv6 mld snooping immediate-leave
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## ipv6 mld profile

### Purpose
The ipv6 mld profile command is used to create the configuration profile. To delete the corresponding profile, please use no ipv6 mld profile command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ipv6 mld profile id
no ipv6 mld profile id
```

### Parameters
```text
Specify the id of the configuration profile, ranging from 1 to 999.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Create the profile 1:
Switch(config)# ipv6 mld profile 1
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## deny

### Purpose
The deny command is used to configure the filtering mode of profile as deny.

### Command Mode
Profile Configuration Mode

### Syntax
```text
deny
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the filtering mode of profile 1 as deny:
Switch(config)# ipv6 mld profile 1
Switch(config-MLD-profile)#deny
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## permit

### Purpose
The permit command is used to configure the filtering mode of profile as permit.

### Command Mode
Profile Configuration Mode

### Syntax
```text
permit
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the filtering mode of profile 1 as permit:
Switch(config)# ipv6 mld profile 1
Switch(config-igmp-profile)#permit
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## range

### Purpose
The range command is used to configure the range of the profile s filtering multicast address. To delete the corresponding filtering multicast address, please use no range command. A profile contains 16 filtering IP-range entries at most.

### Command Mode
Profile Configuration Mode

### Syntax
```text
range start-ip end-ip
no range start-ip end-ip
```

### Parameters
```text
start-ip
Start IPv6 multicast address of the filter entry..
end-ip
End IPv6 multicast address of the filter entry.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure one of the filter multicast address entry as range ff80::1234 to ff80::1235 in profile 1:
Switch(config)# ipv6 mld profile 1
Switch(config-igmp-profile)#range ff80::1234 ff80::1235
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## ipv6 mld filter

### Purpose
The ipv6 mld filter command is used to bind the specified profile to the interface. To delete the binding, please use no ipv6 mld filter command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
ipv6 mld filter profile-id
no ipv6 mld filter
```

### Parameters
```text
profile-id
Specify the profile ID, ranging from 1 to 999.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Bind profile 1 to interface gigabitEthernet 1/0/2:
Switch(config)# interface gigabitEthernet 1/0/2
Switch(config-if)# ipv6 mld filter 1
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## clear ipv6 mld snooping statistics

### Purpose
The clear ipv6 mld snooping statistics command is used to clear the statistics of the MLD packets.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
clear ipv6 mld snooping statistics
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Clear the statistics of the MLD packets:
Switch(config)# clear ipv6 mld snooping statistics
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## show ipv6 mld snooping

### Purpose
The show ipv6 mld snooping command is used to display the global configuration of MLD Snooping.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ipv6 mld snooping
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the global configuration of MLD Snooping:
Switch(config)# show ipv6 mld snooping
```

### Notes
- Permission requirement: None.

## show ipv6 mld snooping interface

### Purpose
The show ipv6 mld snooping interface command is used to display the port configuration of MLD snooping.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ipv6 mld snooping interface [ gigabitEthernet [ port | port-list ] ] { basic-config | max-groups | packet-stat }
show ipv6 mld snooping interface [ port-channel [ port-channel-list ] ] { basic-config | max-groups }
```

### Parameters
```text
port
The Ethernet port number.
port-list
The list of Ethernet ports.
basic-config | max-groups | packet-stat
The related configuration information selected to display.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the MLD baisic configuration configuration of all ports and port channels:
Switch# show ipv6 mld snooping interface basic-config
Display the MLD basic configuration of port 1/0/2:
Switch# show ipv6 mld snooping interface gigabitEthernet 1/0/2 basic-config
Display the MLD packet statistics of ports 1/0/1-4:
Switch# show ipv6 mld snooping interface gigabitEthernet 1/0/1-4 packet-stat
```

### Notes
- Permission requirement: None.

## show ipv6 mld snooping vlan

### Purpose
The show ipv6 mld snooping vlan command is used to display VLAN information of MLD Snooping.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ipv6 mld snooping vlan [ vlan-id ]
```

### Parameters
```text
vlan-id
The VLAN ID selected to display, ranging from 1 to 4094.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display all of the VLAN information:
Switch(config)# show ipv6 mld snooping vlan
```

### Notes
- Permission requirement: None.

## show ipv6 mld snooping groups

### Purpose
The show ipv6 mld snooping groups command is used to display multicast groups.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ipv6 mld snooping groups [ vlan { vlan-id } ] [ ipv6_multicast_addr | count | dynamic | dynamic count | static | static count ]
```

### Parameters
```text
vlan-id
The VLAN ID selected to display the information of all multicast items.
ipv6_multicast_addr
IPv6 address of the multicast group.
count
The numbers of all multicast groups.
dynamic
Display dynamic multicast groups.
dynamic count
The numbers of all dynamic multicast groups.
static
Display static multicast groups.
static count
The numbers of all static multicast groups.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display all of the multicast groups:
Switch(config)# show ipv6 mld snooping groups
```

### Notes
- Permission requirement: None.

## show ipv6 mld profile

### Purpose
The show ipv6 mld profile command is used to display the configuration information of all the profiles or a specific profile.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ipv6 mld profile [ id ]
```

### Parameters
```text
Specify the ID of the profile, ranging from 1 to 999.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the configuration information of all profiles:
Switch(config)# show ipv6 mld profile
```

### Notes
- Permission requirement: None.
