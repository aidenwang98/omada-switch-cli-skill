# IGMP Snooping Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 27 IGMP Snooping Commands

Location: extracted Word text lines 12738-13411

## Chapter Notes

Official documentation states: IGMP Snooping (Internet Group Management Protocol Snooping) is a multicast control mechanism running on Layer 2 switch. It can effectively prevent multicast groups being broadcasted in the network.

- Use these commands only when the requested feature and target interface/VLAN/ring/session details are clear.

## ip igmp snooping (global)

### Purpose
The ip igmp snooping command is used to configure IGMP Snooping globally. To disable the IGMP Snooping function, please use no ip igmp snooping command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip igmp snooping
no ip igmp snooping
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable IGMP Snooping function:
Switch(config)# ip igmp snooping
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip igmp snooping version

### Purpose
The ip igmp snooping version command is used to configure IGMP version globally. To return to the default configuration, please use no ip igmp snooping version command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip igmp snooping version {v1 | v2 | v3 }
no ip igmp snooping version
```

### Parameters
```text
v1 | v2 | v3
Specify the IGMP version. By default, it is IGMP v3.
v1: The switch works as an IGMPv1 Snooping switch. It can only process IGMPv1 messages from the host. Report messages of other versions are ignored.
v2: The switch works as an IGMPv2 Snooping switch. It can process both IGMPv1 and IGMPv2 messages from the host. IGMPv3 messages are ignored.
v3: The switch works as an IGMPv3 Snooping switch. It can process IGMPv1, IGMPv2 and IGMPv3 messages from the host.
```

### Default
By default, it is IGMP v3.

### Example
```text
Specify the IGMP version as v2:
Switch (config)# ip igmp snooping version v2
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip igmp snooping drop-unknown

### Purpose
The ip igmp snooping drop-unknown command is used to configure the way how the switch processes multicast streams that are sent to unknown multicast groups as Discard. By default, it is Forward. To return to the default configuration, please use no ip igmp snooping drop-unknown command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip igmp snooping drop-unknown
no ip igmp snooping drop-unknown
```

### Parameters
No parameters.

### Default
By default, it is Forward.

### Example
```text
Specify the operation to process unknown multicast as discard:
Switch(config)# ip igmp snooping drop-unknown
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip igmp snooping header-validation

### Purpose
The ip igmp snooping header-validation command is used to enable IGMP Header Validation globally. To disable the IGMP Header Validation function, please use no ip igmp snooping header-validation command. Generally, for IGMP packets, the TTL value should be 1, ToS field should be 0xC0, and Router Alert option should be 0x94040000. The fields to be validated depend on the IGMP version being used. IGMPv1 only checks the TTL field. IGMPv2 checks the TTL field and the Router Alert option. IGMPv3 checks TTL field, ToS field and Router Alert option. Packets that fail the validation process will be dropped.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip igmp snooping header-validation
no ip igmp snooping header-validation
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable IGMP Header Validation:
Switch(config)# ip igmp snooping header-validation
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip igmp snooping vlan-config

### Purpose
The ip igmp snooping vlan-config command is used to enable VLAN IGMP Snooping function or to modify IGMP Snooping parameters. To disable the VLAN IGMP Snooping function, please use no ip igmp snooping vlan-config command. To restore the default values, please use no ip igmp snooping vlan-config with specified parameters.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip igmp snooping vlan-config vlan-id-list [ rtime router-time | mtime member-time | ltime leave-time ]
no ip igmp snooping vlan-config vlan-id-list [ rtime | mtime | ltime ]
```

### Parameters
```text
vlan-id-list
The ID list of the VLAN desired to modify configuration, ranging from 1 to 4094, in the format of 1-3, 5.
router-time
The Router Port Aging Time. Within this time, if the switch does not receive IGMP query message from the router port, it will consider this port is not a router port any more. Valid values are from 60 to 600 in seconds, and the default value is 300 seconds.
member-time
The Member Port Aging Time. Within this time, if the switch does not receive IGMP report message from the member port, it will consider this port is not a member port any more. Valid values are from 60 to 600 in seconds, and the default value is 260 seconds.
leave-time
The Leave Time. Valid values are from 1 to 30 in seconds, and the default value is 1 second. When the switch receives a leave message from a port to leave a multicast group, it will wait for a Leave Time before removing the port from the multicast group. During the period, if the switch receives any report messages from the port, the port will not be removed from the multicast group. Exceptions are as follows:
If the member port ages out before the Leave Time ends and no report messages are received, the port will be removed from the multicast group once its Member Port Aging Time ends.
The Leave Time mechanism will not take effect when Fast Leave takes effect.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the IGMP Snooping function and modify Router Port Aging Time as 300 seconds, Member Port Aging Time as 200 seconds for VLAN 1-3:
Switch(config)# ip igmp snooping vlan-config 1-3 rtime 300
Switch(config)# ip igmp snooping vlan-config 1-3 mtime 200
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip igmp snooping vlan-config (immediate-leave)

### Purpose
This command is used to enable the Fast Leave feature for specific VLANs. To disable Fast Leave on the VLANs, please use no ip igmp snooping vlan-config vlan-id-list immediate-leave command. This function is disabled by default.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip igmp snooping vlan-config vlan-id-list immediate-leave
no ip igmp snooping vlan-config vlan-id-list immediate-leave
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
Switch(config)# ip igmp snooping vlan-config 1-3 immediate-leave
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip igmp snooping vlan-config (report-suppression)

### Purpose
This command is used to enable the IGMP Report Suppression function for specific VLANs. When enabled, the switch will only forward the first IGMP report message for each multicast group to the IGMP querier and suppress subsequent IGMP report messages for the same multicast group during one query interval. This feature prevents duplicate report messages from being sent to the IGMP querier. To disable the IGMP report suppression function and forward all the IGMP reports to the Layer 3 device in specific VLANs, please use no ip igmp snooping vlan-config vlan-id-list report-suppression command. This function is disabled by default.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip igmp snooping vlan-config vlan-id-list report-suppression
no ip igmp snooping vlan-config vlan-id-list report-suppression
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
Enable the IGMP Report Suppression for VLAN 1-3:
Switch(config)# ip igmp snooping vlan-config 1-3 report-suppression
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip igmp snooping vlan-config (router-ports-forbidden)

### Purpose
This command is used to forbid the specified ports as being router ports in the specified VLAN(s). To delete the forbidden router ports, please use no ip igmp snooping vlan-config vlan-id-list router-ports-forbidd command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip igmp snooping vlan-config vlan-id-list router-ports-forbidd interface { gigabitEthernet port-list | port-channel port-channel-list }
no ip igmp snooping vlan-config vlan-id-list router-ports-forbidd interface [ gigabitEthernet port-list | port-channel port-channel-list ]
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
Forbid the Ethernet ports 1/0/1-3 as being router ports in VLAN 1 :
Switch(config)# ip igmp snooping vlan-config 1 router-ports-forbidd interface gigabitEthernet 1/0/1-3
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip igmp snooping vlan-config (rport interface)

### Purpose
This command is used to specify the static router ports for specific VLANs. To delete the static router ports, please use no ip igmp snooping vlan-config vlan-id-list rport interface command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip igmp snooping vlan-config vlan-id-list rport interface { gigabitEthernet port-list | port-channel port-channel-list }
no ip igmp snooping vlan-config vlan-id-list rport interface { gigabitEthernet port-list | port-channel port-channel-list }
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
Switch(config)# ip igmp snooping vlan-config 1-2 rport interface gigabitEthernet 1/0/1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip igmp snooping vlan-config (static)

### Purpose
This command is used to configure interfaces to statically join a multicast group. To remove interfaces from a static multicast group, please use no ip igmp snooping vlan-config vlan-id-list staticcommand.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip igmp snooping vlan-config vlan-id-list static ip interface { gigabitEthernet port-list | port-channel port-channel-list }
no ip igmp snooping vlan-config vlan-id-list static ip interface { gigabitEthernet port-list | port-channel port-channel-list }
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
Configure port ports 1/0/1-3 in VLAN 2 to statically join multicast group 225.0.0.1:
Switch(config)# ip igmp snooping vlan-config 2 static 225.0.0.1 interface gigabitEthernet 1/0/1-3
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip igmp snooping vlan-config (querier)

### Purpose
This command is used to enable the IGMP Snooping Querier feature for specific VLANs. To disable the IGMP Snooping Querier feature on the VLANs, please use no ip igmp snooping vlan-config vlan-id-list querier command without any parameters. To restore the default values, please use no ip igmp snooping vlan-config vlan-id-list querier command with specified parameters.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip igmp snooping vlan-config vlan-id-list querier [ max-response-time response-time | query-interval interval | general-query source-ip ip-addr | last-member-query-count count | last-member-query-interval interval ]
no ip igmp snooping vlan-config vlan-id-list querier [ max-response-time | query-interval | general-query source-ip | last-member-query-count ]
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
The source IP address of the general query messages sent by the switch. It should be a unicast address. By default, it is 0.0.0.0.
count
The number of group-specific queries to be sent. With IGMP Snooping Querier enabled, when the switch receives an IGMP leave message, it obtains the address of the multicast group that the host wants to leave from the message. Then the switch sends out group-specific queries to this multicast group through the port receiving the leave message. If specified count of group-specific queries are sent and no report message is received, the switch will delete the multicast address from the multicast forwarding table. Valid values are from 1 to 5, and the default value is 2.
last-member-query-interval interval
The interval between group- specific queries.. Valid values are from 1 to 5 seconds, and the default value is 1 second.
```

### Default
By default, it is 0.

### Example
```text
Enable the IGMP Snooping Querier for VLAN 3, and configure the query interval as 100 seconds:
Switch(config)# ip igmp snooping vlan-config 3 querier
Switch(config)# ip igmp snooping vlan-config 3 querier query interval 100
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip igmp snooping vlan-config drop-unknown

### Purpose
The ip igmp snooping vlan-config drop-unknown command is used to enable the drop-unknown function for the specified VLAN. When enabled, unregistered IPv4 multicast traffic within this VLAN will be discarded. To disable this function, please use the no ip igmp snooping vlan-config drop-unknown command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip igmp snooping vlan-config vlan-id-list drop-unknown
no ip igmp snooping vlan-config vlan-id-list drop-unknown
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
Switch(config)# ip igmp snooping vlan-config 1 drop-unknown
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Official note: This command is only available on certain devices.

## ip igmp snooping vlan-config route-unknown

### Purpose
The ip igmp snooping vlan-config route-unknown command is used to enable the route-unknown function for the specified VLAN. When enabled, unregistered multicast traffic in this VLAN will be forwarded to IGMP snooping router ports. To disable this function, please use the no ip igmp snooping vlan-config route-unknown command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip igmp snooping vlan-config vlan-id-list route-unknown
no ip igmp snooping vlan-config vlan-id-list route-unknown
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
Switch(config)# ip igmp snooping vlan-config 1 route-unknown
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Official note: This command is only available on certain devices.

## ip igmp snooping vlan-config ssdp-flood

### Purpose
The ip igmp snooping vlan-config ssdp-flood command is used to enable the unconditional SSDP flooding on the specified port. Since the cause of SSDP packet loss in user scenarios is the enabling of multicast and drop unknown, this function can only take effect normally when both the current VLAN multicast and global multicast are enabled. After enabling, if IGMP snooping for the VLAN and globally is detected to be enabled, a dedicated multicast group is created and all ports within the VLAN are joined to this group. This created group cannot be manually modified or adjusted by the user, but the member information can be adjusted by adding or removing ports from the VLAN.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip igmp snooping vlan-configvlan list ssdp-flood
```

### Parameters
```text
vlan list
The VLAN on which this function needs to be enabled.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
After enabling IGMP snooping globally and on VLAN 1, enable unconditional SSDP flooding on VLAN 1:
Switch(config)# ip igmp snooping vlan-config 1 ssdp-flood
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip igmp snooping vlan-config querier-election

### Purpose
The ip igmp snooping vlan-config querier-election command is used to enable the querier-election function for the specified VLAN(s). To disable this function, please use no ip igmp snooping vlan-config querier-election command. The default value is 2. The default robustness value for a querier is 2. When the local device is not the elected querier, the robustness value is used to calculate the query interval of the current elected querier. The calculation formula is: Elected Querier Interval = (queryInterval * robustness) + maxResponseTime / 2.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip igmp snooping vlan-config vlan-id-list querier robustness robustness
no ip igmp snooping vlan-config vlan-id-list querier robustness
```

### Parameters
```text
vlan-id-list
A single VLAN ID or a VLAN ID range. Maximum length: 64 characters.
robustness
The robustness value of the querier. Value range: 1 to 255 (integer).
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the querier robustness value for VLAN 1 to 5:
Switch(config)# ip igmp snooping vlan-config 1 querier robustness 5
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip igmp snooping querier robustness

### Purpose
The ip igmp snooping querier robustness command is used to configure the robustness value for the querier. To disable this function, please use no ip igmp snooping querier robustness command without any parameters. By default, the querier-election function is disabled for VLANs.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip igmp snooping vlan-config vlan-id-list querier-election
no ip igmp snooping vlan-config vlan-id-list querier-election
```

### Parameters
```text
vlan-id-list
A single VLAN ID or a VLAN ID range. Maximum length: 64 characters.
```

### Default
By default, the querier-election function is disabled for VLANs.

### Example
```text
Enable the querier-election function for VLAN 1:
Switch(config)# ip igmp snooping vlan-config 1 querier-election
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip igmp snooping (interface)

### Purpose
The ip igmp snooping command is used to enable the IGMP Snooping function for the desired port. To disable the IGMP Snooping function, please use no ip igmp snooping command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
ip igmp snooping
no ip igmp snooping
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable IGMP Snooping function of port 1/0/3:
Switch(config)# interface gigabitEthernet 1/0/3
Switch(config-if)# ip igmp snooping
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip igmp snooping max-groups

### Purpose
The ip igmp snooping max-groups command is used to configure the maximum number of groups that a port can join in. The ip igmp snooping max-groups action is used to configure the action that the port takes when it receives an IGMP report message and the maximum number of entries is in the forwarding table. To remove the maximum group limitation and return to the default of no limitation on the specified port, please use the no ip igmp snooping max-groups command. To return to the default action of dropping the report, please use the no ip igmp snooping max-groups action command. These commands only apply to the dynamic multicast groups.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
ip igmp snooping max-groups maxgroup
ip igmp snooping max-groups action { drop | replace }
no ip igmp snooping max-groups
no ip igmp snooping max-groups action
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
Switch(config-if-range)#ip igmp snooping max-groups 10
Switch(config-if-range)#ip igmp snooping max-groups action replace
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip igmp snooping immediate-leave

### Purpose
The ip igmp snooping immediate-leave command is used to configure the Fast Leave function for port. To disable the Fast Leave function, please use no ip igmp snooping immediate-leave command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
ip igmp snooping immediate-leave
no ip igmp snooping immediate-leave
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the Fast Leave function for port 1/0/3:
Switch(config)# interface gigabitEthernet 1/0/3
Switch(config-if)# ip igmp snooping immediate-leave
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip igmp snooping authentication

### Purpose
The ip igmp snooping authenticaiton command is used to authenticate the users who want to join the limited multicast source. To disable the multicast authentication, please use no ip igmp snooping authentication command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
ip igmp snooping authentication
no ip igmp snooping authentication
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable IGMP authentication on port 1/0/3:
Switch(config)# interface gigabitEthernet 1/0/3
Switch(config-if)# ip igmp snooping authentication
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- User guidelines: The IGMP Authentication feature will take effect only when AAA function is enabled and the RADIUS server is configured. For how to enable AAA function and configure RADIUS server, please refer to aaa enable and radius-server host
- Official note: This command is only available on certain devices.

## ip igmp snooping accounting

### Purpose
The ip igmp snooping accounting command is used to enable IGMP accounting globally. To disable the IGMP accouting, please use no ip igmp snooping accounting command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip igmp snooping accounting
no ip igmp snooping accounting
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable IGMP accounting globally:
Switch(config)# ip igmp snooping accounting
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Official note: This command is only available on certain devices.

## ip igmp snooping tcn

### Purpose
The ip igmp snooping tcn command is used to globally enable the TCN flood for IGMP function. When enabled, IGMP snooping will respond to Topology Change Notifications (TCN). To disable this function, please use the no ip igmp snooping tcn command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip igmp snooping tcn
no ip igmp snooping tcn
```

### Parameters
```text
None.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the TCN flood for IGMP function:
Switch(config)# ip igmp snooping tcn
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip igmp snooping tcn flood-query-count

### Purpose
The ip igmp snooping tcn flood-query-count command is used to configure the number of General Query messages that need to be received before stopping multicast flooding in TCN receive mode. To restore the default value, please use the no ip igmp snooping tcn flood-query-count command. The default value is 2.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip igmp snooping tcn flood-query-count count
no ip igmp snooping tcn flood-query-count
```

### Parameters
```text
count
The number of General Query messages that need to be received in TCN receive mode before stopping flooding. Value range: 1 to 10 (integer).
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the number of General Query messages to be received before stopping flooding in TCN receive mode to 5:
Switch(config)# ip igmp snooping tcn flood-query-count 5
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip igmp snooping tcn query-solicit

### Purpose
The ip igmp snooping tcn query-solicit command is used to configure the sending of General Leave messages (gaddr=0.0.0.0), also known as Query Solicitation messages, towards router ports in TCN receive mode. To disable the sending of General Leave messages in TCN receive mode, please use the no ip igmp snooping tcn query-solicit command. By default, General Leave messages are not sent to router ports upon entering TCN receive mode.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip igmp snooping tcn query-solicit
no ip igmp snooping tcn query-solicit
```

### Parameters
```text
None.
```

### Default
By default, General Leave messages are not sent to router ports upon entering TCN receive mode.

### Example
```text
Configure the sending of General Leave messages towards router ports in TCN receive mode:
Switch(config)# ip igmp snooping tcn tcn query-solicit
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip igmp snooping vlan-config tcn-flood

### Purpose
The ip igmp snooping vlan-config tcn-flood command is used to configure unknown multicast traffic flooding within a VLAN after the VLAN enters the TCN state. To restore the default configuration, please use the no ip igmp snooping vlan-config tcn-flood command. By default, whether unknown multicast traffic floods after a VLAN enters the TCN state is determined by the drop-unknown configuration.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip igmp snooping vlan-config vlan-id-list tcn-flood
no ip igmp snooping vlan-config vlan-id-list tcn-flood
```

### Parameters
```text
vlan-id-list
A single VLAN ID or a VLAN ID range. Maximum length: 64 characters.
```

### Default
By default, whether unknown multicast traffic floods after a VLAN enters the TCN state is determined by the drop-unknown configuration.

### Example
```text
Configure unknown multicast traffic flooding within VLAN 1 after VLAN 1 enters the TCN state:
Switch(config)# ip igmp snooping vlan-config 1 tcn-flood
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip igmp snooping querier tcn-query-count

### Purpose
The ip igmp snooping querier tcn-query-count command is used to configure the number of General Query messages that need to be sent before stopping multicast flooding in TCN transmit mode. To restore the default value, please use the no ip igmp snooping querier tcn-query-count command. The default value is 2.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip igmp snooping tcn flood-query-count count
no ip igmp snooping tcn flood-query-count
ip igmp snooping vlan-config vlan-id-list querier tcn-query-count count
no ip igmp snooping vlan-config vlan-id-list querier tcn-query-count
```

### Parameters
```text
vlan-id-list
A single VLAN ID or a VLAN ID range. Maximum length: 64 characters.
count
The number of General Query messages that need to be received in TCN receive mode before stopping flooding. Value range: 1 to 10 (integer).
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the number of General Query messages to be sent before stopping flooding in TCN transmit mode for VLAN 1 to 5:
Switch(config)# ip igmp snooping vlan-config 1 querier tcn-query-count 5
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip igmp snooping querier tcn-query-interval

### Purpose
The ip igmp snooping querier tcn-query-interval command is used to configure the time interval for sending General Query messages in TCN transmit mode. To restore the default value, please use the no ip igmp snooping querier tcn-query-interval command. The default value is 10.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip igmp snooping vlan-config vlan-id-list querier tcn-query-interval interval
no ip igmp snooping vlan-config vlan-id-list querier tcn-query-interval
```

### Parameters
```text
vlan-id-list
A single VLAN ID or a VLAN ID range. Maximum length: 64 characters.
interval
The time interval for sending General Query messages in TCN transmit mode. Value range: 1 to 255 seconds (integer).
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the time interval for sending General Query messages in TCN transmit mode for VLAN 1 to 5 seconds:
Switch(config)# ip igmp snooping vlan-config 1 querier tcn-query-interval 5
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip igmp profile

### Purpose
The ip igmp profile command is used to create the configuration profile. To delete the corresponding profile, please use no ip igmp profile command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip igmp profile id
no ip igmp profile id
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
Switch(config)# ip igmp profile 1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

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
Switch(config)# ip igmp profile 1
Switch(config-igmp-profile)#deny
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

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
Switch(config)# ip igmp profile 1
Switch(config-igmp-profile)#permit
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

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
The start filtering multicast IP address.
end-ip
The end filtering multicast IP address.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure one of the filter multicast address entry as range 225.1.1.1 to 226.3.2.1 in profile 1:
Switch(config)# ip igmp profile 1
Switch(config-igmp-profile)#range 225.1.1.1 226.3.2.1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip igmp filter

### Purpose
The ip igmp filter command is used to bind the specified profile to the interface. To delete the binding, please use no ip igmp filter command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
ip igmp filter profile-id
no ip igmp filter
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
Switch(config-if)# ip igmp filter 1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## clear ip igmp snooping statistics

### Purpose
The clear ip igmp snooping statistics command is used to clear the statistics of the IGMP packets.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
clear ip igmp snooping statistics
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Clear the statistics of the IGMP packets:
Switch(config)# clear ip igmp snooping statistics
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## show ip igmp snooping

### Purpose
The show ip igmp snooping command is used to display the global configuration of IGMP snooping.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip igmp snooping
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the global configuration of IGMP:
Switch# show ip igmp snooping
```

### Notes
- Permission requirement: None.

## show ip igmp snooping interface

### Purpose
The show ip igmp snooping interface command is used to display the port configuration of IGMP snooping. If no interface is specified, it displays all interfaces IGMP snooping configurations.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip igmp snooping interface [ gigabitEthernet [port-list ] | port-channel [ port-channel-list ] ] { authentication | basic-config | max-groups | packet-stat }
```

### Parameters
```text
port-list
The list of Ethernet ports.
Port-channel-list
The list of port channels.
authentication | basic-config | max-groups | packet-stat
The related configuration information selected to display.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the IGMP baisic configuration configuration of all ports and port channels:
Switch# show ip igmp snooping interface basic-config
Display the IGMP basic configuration of port 1/0/2:
Switch# show ip igmp snooping interface gigabitEthernet 1/0/2 basic-config
Display the IGMP packet statistics of ports 1/0/1-4:
Switch# show ip igmp snooping interface gigabitEthernet 1/0/1-4 packet-stat
```

### Notes
- Permission requirement: None.
- Official note: Authentication is only available on certain devices.

## show ip igmp snooping vlan

### Purpose
The show ip igmp snooping vlan command is used to display the VLAN configuration of IGMP snooping.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip igmp snooping vlan [ vlan-id ]
```

### Parameters
```text
vlan-id
The VLAN ID selected to display.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the IGMP snooping configuration information of VLAN 2:
Switch# show ip igmp snooping vlan 2
```

### Notes
- Permission requirement: None.

## show ip igmp snooping groups

### Purpose
The show ip igmp snooping groups command is used to display the information of all IGMP snooping groups. It can be extended to some other commands to display the dynamic and static multicast information of a selected VLAN.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip igmp snooping groups [ vlan vlan-id ] [ multicast_addr | count | dynamic | dynamic count | static | static count ]
```

### Parameters
```text
vlan-id
The VLAN ID selected to display the information of all multicast items.
multicast_addr
IP address of the multicast group.
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
Display the information of all IGMP snooping groups:
Switch#show ip igmp snooping groups
Display all the multicast entries in VLAN 5:
Switch(config)#show ip igmp snooping groups vlan 5
Display the count of multicast entries in VLAN 5:
Switch(config)#show ip igmp snooping groups vlan 5 count
Display the dynamic multicast groups of VLAN 5
Switch(config)#show ip igmp snooping groups vlan 5 dynamic
Display the static multicast groups of VLAN 5
Switch(config)#show ip igmp snooping groups vlan 5 static
Display the count of dynamic multicast entries of VLAN 5
Switch(config)#show ip igmp snooping groups vlan 5 dynamic count
Display the count of static multicast entries of VLAN 5
Switch(config)#show ip igmp snooping groups vlan 5 static count
```

### Notes
- Permission requirement: None.

## show ip igmp profile

### Purpose
The show ip igmp profile command is used to display the configuration information of all the profiles or a specific profile.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip igmp profile [ id ]
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
Switch(config)# show ip igmp profile
```

### Notes
- Permission requirement: None.
