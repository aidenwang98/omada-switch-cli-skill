# PIM Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 29 PIM Commands (Only for Certain Devices)

Location: extracted Word text lines 13772-14444

## Chapter Notes

Official documentation states: Protocol Independent Multicast, abbreviated as PIM, uses unicast routing information to provide multicast forwarding functions in a layer 3 network.

- This chapter is marked `Only for Certain Devices`; treat all configuration commands as model-dependent.

## ip multicast-routing

### Purpose
The ip multicast-routing command is used to enable the IP multicast-routing function globally. To disable this function, please use the no ip multicast-routing command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip multicast-routing [ vrf vrfname ]
no ip multicast-routing [ vrf vrfname ]
```

### Parameters
```text
vrfname: Virtual Routing and Forwarding instance name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the IP multicast-routing function globally:
Switch(config)#ip multicast-routing
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip pim (globally)

### Purpose
The ip pim command is used to enable IP PIM globally. To disable the IP PIM function, please use no ip pim command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip pim {dense-mode | sparse-mode }
no ip pim {dense-mode | sparse-mode }
```

### Parameters
```text
dense-mode: Enable PIM DM globally.
sparse-mode: Enable PIM SM globally
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable PIM DM globally:
Switch (config)#ip pim dense-mode
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Official note: This command applies to L2+ switches only.
- Availability: Only for certain devices according to the official chapter title.

## ip pim (on specific ports)

### Purpose
The ip pim command is used to configure IP PIM on a specified port. To disable the IP PIM function, please use no ip pim command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip pim
no ip pim
```

### Parameters
```text
None.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable PIM on port 2:
Switch (config)#interface vlan 2
Switch (config-if)#ip pim
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip pim dense-mode

### Purpose
This command is used to configure the PIM DM (Dense Mode).

### Command Mode
Global Configuration Mode

### Syntax
```text
ip pim dense-mode [ vrf vrfname ]
no ip pim dense-mode [ vrf vrfname ]
```

### Parameters
```text
vrfname: Virtual Routing and Forwarding instance name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch (config)# ip pim dense-mode vrf test
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Official note: This command applies to L3 switches only.
- Availability: Only for certain devices according to the official chapter title.

## ip pim sparse-mode

### Purpose
This command is used to configure PIM Sparse Mode (SM).

### Command Mode
Global Configuration Mode

### Syntax
```text
ip pim sparse-mode [ vrf vrfname ]
no ip pim sparse-mode [ vrf vrfname ]
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
Switch(config)# ip pim sparse-mode vrf test
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Official note: This command applies to L3 switches only.
- Availability: Only for certain devices according to the official chapter title.

## ip pim anycast-rp

### Purpose
Anycast RP is an extension mechanism of the PIM-SM protocol. By configuring the same anycast address for multiple physical RPs, it enables multicast sources to register nearby and receivers to join nearby, addressing issues in the traditional single-RP model such as traffic concentration, slow fault convergence, and non-optimal paths. During configuration, both the anycast-rp address and member rp addresses are recommended to be configured as loopback addresses. Each anycast-rp member device needs to be configured with all member rp addresses. When removing the configuration, you can delete the entire anycast-rp configuration or only a specific member rp configuration.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip pim anycast-rp anycast_rp_addr member_addr [ vrf vrfname ]
no ip pim anycast-rp anycast_rp_addr [ member_addr ] [ vrf vrfname ]
```

### Parameters
```text
anycast_rp_addr : The anycast-rp address, representing a set of RPs.
member_addr: A member rp address within the RP set.
vrfname: Virtual Routing and Forwarding instance name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Assume Switch A and Switch B are building an anycast-rp. The anycast-rp address for both Switch A and Switch B is 1.1.1.1. Switch A's member-rp is 2.2.2.2, and Switch B's member-rp is 3.3.3.3. Using Switch A configuration as an example, it needs to configure all local and remote member rps:
Switch (config)# ip pim anycast-rp 1.1.1.1 2.2.2.2
Switch (config)# ip pim anycast-rp 1.1.1.1 3.3.3.3
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip pim ignore-rp-set-priority

### Purpose
This command configures to ignore the priority field of the RP-set during RP election, which is disabled by default.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip pim ignore-rp-set-priority [ vrf vrfname ]
no ip pim ignore-rp-set-priority [ vrf vrfname ]
```

### Parameters
```text
vrfname: Virtual Routing and Forwarding instance name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Ignore the priority field of the RP-set during RP election:
Switch (config)# ip pim ignore-rp-set-priority
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip pim register-rate-limit

### Purpose
This command configures the number of register messages the Designated Router (DR) can send per second. Register messages exceeding this limit will be dropped. Default is 0, meaning unlimited.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip pim register-rate-limit value[ vrf vrfname ]
no ip pim register-rate-limit [ vrf vrfname ]
```

### Parameters
```text
Value: Range for the number of register messages sent per second, ranging from 1 - 65535.
vrfname: Virtual Routing and Forwarding instance name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Ignore the priority field of the RP-set during RP election:
Switch (config)# ip pim ignore-rp-set-priority
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip pim register-rp-reachability

### Purpose
This command configures the checking the RP reachability for register messages. Default is enabled. By default, it is not displayed in show running-config. It will appear after being disabled with the no command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip pim register-rp-reachability [ vrf vrfname ]
no ip pim register-rp-reachability [ vrf vrfname ]
```

### Parameters
```text
vrfname: Virtual Routing and Forwarding instance name.
```

### Default
By default, it is not displayed in show running-config.

### Example
```text
Switch (config)# ip pim register-rp-reachability
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip pim register-source

### Purpose
This command configures the IP header source address for register messages sent by the Designated Router (DR), which can be configured as an IP address or an interface (using the interface's IP address). The configured source address should be unicast reachable to the RP to ensure proper PIM-SM registration/register-stop flow. By default, the source address is the RPF interface address towards the multicast source.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip pim register-source {ip_addr | interface intf_type intf_id} [ vrf vrfname ]
no ip pim register-source [ vrf vrfname ]
```

### Parameters
```text
ip_addr: IP address to be used as the source address for register messages.
intf_type : Interface type to be used for the register message source address.
intf_id : Interface ID to be used for the register message source address.
vrfname: Virtual Routing and Forwarding instance name.
```

### Default
By default, the source address is the RPF interface address towards the multicast source.

### Example
```text
Switch(config)# ip pim register-source 192.168.10.1
Switch(config)# ip pim register-source interface loopback 1
Switch(config)# no ip pim register-source
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip pim register-suppression

### Purpose
This command configures the time (in seconds) for which the Designated Router (DR) stops sending data-encapsulated registers to the RP after receiving a register-stop message. Default is 60 seconds.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip pim register-suppression value [ vrf vrfname ]
no ip pim register-suppression [ vrf vrfname ]
```

### Parameters
```text
value: Registration suppression time, in seconds, range 1 - 65535.
vrfname: Virtual Routing and Forwarding instance name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config)# ip pim register-suppression 100
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip pim router-id

### Purpose
This command configures the PIM router-id, which uniquely identifies a PIM device.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip pim router-id router-id [ vrf vrfname ]
no ip pim router-id [ vrf vrfname ]
```

### Parameters
```text
router-id: Dotted-decimal parameter.
vrfname: Virtual Routing and Forwarding instance name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config)# ip pim router-id 1.2.3.4
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip pim bsr-candidate

### Purpose
This command is used to configure a candidate BSR on the interface.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip pim bsr-candidate interface intf_type intf_id [ hash-mask-length ] [ priority ] [ interval ] [ vrf vrfname ]
no ip pim bsr-candidate [ vrf vrfname ]
```

### Parameters
```text
intf_type: Interface type used for C-BSR.
intf_id: Interface ID used for C-BSR.
hash-mask-length: Hash mask length used to map multicast group addresses to RPs. Default is 30, range 0 - 32.
priority: C-BSR election priority, where a higher value wins. Default is 0, range 0-255.
interval: Interval for sending PIM BSR messages, in seconds. Default is 60 seconds, range 1 - 16383.
vrfname: Virtual Routing and Forwarding instance name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config)# ip pim bsr-candidate int loopback 1 vrf test
Switch(config)# no ip pim bsr-candidate vrf test
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip pim rp-candidate

### Purpose
This command is used to configure a candidate RP.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip pim rp-candidate interface intf_type intf_id group_addr group_mask [ interval ] [ priority ] [ vrf vrfname ]
no ip pim rp-candidate interface intf_type intf_id group_addr group_mask [ vrf vrfname ]
```

### Parameters
```text
intf_type
Interface type used for C-RP.
intf_id
Interface ID used for C-RP.
group_addr
Multicast group address.
group_mask
Multicast group mask.
interval
C-RP advertisement message sending interval. Default is 60 seconds, range 1 - 16383.
priority
C-RP election priority, where a lower value wins. Default is 192, range 0-255.
vrfname
Virtual Routing and Forwarding instance name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config)# ip pim rp-candidate interface loopback 1 235.0.0.1 255.0.0.0 vrf test
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip pim rp-register-kat

### Purpose
This command is used to configure the KeepAlive Timer (KAT) time used by the RP to monitor register messages and multicast routing state. Default value is 3*registerSuppression(default:60)+reg_probe(default:5) = 185 seconds.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip pim rp-register-kat value [ vrf vrfname ]
no ip pim rp-register-kat [ vrf vrfname ]
```

### Parameters
```text
value
KAT time, in seconds, range 1 - 65535.
vrfname
Virtual Routing and Forwarding instance name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config)# ip pim rp-register-kat 100
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip pim spt-threshold

### Purpose
This command is used to configure the device to automatically switch to the SPT forwarding tree. Default is enabled. By default, it is not displayed in show running-config. It will appear after being disabled with the no command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip pim spt-threshold [ vrf vrfname ]
no ip pim spt-threshold [ vrf vrfname ]
```

### Parameters
```text
vrfname
Virtual Routing and Forwarding instance name.
```

### Default
By default, it is not displayed in show running-config.

### Example
```text
Switch(config)# ip pim spt-threshold
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip pim rp-address

### Purpose
This command is used to configure a static RP.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip pim rp-address rp_addr group_addr group_mask [ override ] [ vrf vrfname ]
no ip pim rp-address rp_addr group_addr group_mask [ vrf vrfname ]
```

### Parameters
```text
rp_addr: IP address of the RP.
group_addr: Multicast group address.
group_mask: Multicast group mask.
vrfname: Virtual Routing and Forwarding instance name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config)# ip pim rp-address 1.1.1.1 235.0.0.1 255.255.255.0 vrf test
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip pim ssm

### Purpose
This command is used to configure the PIM-SSM

### Command Mode
Global Configuration Mode

### Syntax
```text
ip pim ssm { group_addr group_mask | default} [ vrf vrfname ]
no ip pim ssm { group_addr group_mask | default} [ vrf vrfname ]
```

### Parameters
```text
group_addr
Multicast group address.
group_mask
Multicast group mask.
vrfname
Virtual Routing and Forwarding instance name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config)# ip pim ssm 235.0.0.0 255.0.0.0 vrf test
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip pim bsr-border

### Purpose
This command is used to configure the management border of the BSR domain.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip pim bsr-border
no ip pim bsr-border
```

### Parameters
```text
None
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the BSR management border on VLAN interface 2:
Switch(config)# ip pim bsr-border
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip pim exclude-genid

### Purpose
This command is used to configure the interface to send PIM hello messages without the Generation ID field. Default is disabled.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip pim exclude-genid
no ip pim exclude-genid
```

### Parameters
```text
None.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config-if)# ip pim exclude-genid
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip pim dr-priority

### Purpose
This command is used to configure the priority of the designated router (DR).

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip pim dr-priority pri
no ip pim dr-priority
```

### Parameters
```text
pri: DR priority, ranging from 0 to 4294967295. Its default value is 1.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the DR priority on VLAN interface 2 to 100:
Switch(config)#interface vlan 2
Switch(config-if)# ip pim dr-priority 100
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip pim hello-holdtime

### Purpose
This command is used to configure the aging time for PIM neighbors on the interface. Default is 3.5 * hello-interval(default:30) = 105 seconds.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip pim hello-holdtime value
no ip pim hello-holdtime
```

### Parameters
```text
value: hello-holdtime value, in seconds, range 1 - 65535.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config-if)# ip pim hello-holdtime 100
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip pim hello-interval

### Purpose
The ip pim hello-interval command is used to configure the time interval for sending Hello messages on the interface. To restore the default value, please use no ip pim hello-interval command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip pim hello-interval interval
no ip pim hello-interval
```

### Parameters
```text
interval: The time interval for sending Hello messages, ranging from 1 to 18725 seconds. The default value is 30 seconds.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the interval for VLAN interface 2 to send Hello messages to 100 seconds:
Switch (config)#interface vlan 2
Switch (config-if)# ip pim hello-interval 100
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip pim passive

### Purpose
The ip pim hello-interval command is used to configure the interface to enter passive mode, where it stops actively sending PIM messages. Default is disabled.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip pim passive
no ip pim passive
```

### Parameters
```text
None.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch (config-if)# ip pim passive
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip pim propagation-delay

### Purpose
This command is used to configure the propagation-delay field in the LAN Prune Delay option of PIM hello messages sent on the interface. Default is 500 milliseconds.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip pim propagation-delay value
no ip pim propagation-delay
```

### Parameters
```text
value: propagation-delay value, in milliseconds, range 1 - 32767.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch (config-if)# ip pim propagation-delay 1000
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip pim state-refresh

### Purpose
This command is used to configure the interval at which State-Refresh messages are sent on the interface in PIM Dense Mode. Default is 60 seconds.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip pim state-refresh origination-interval value
no ip pim state-refresh origination-interval
```

### Parameters
```text
value
State-Refresh message sending interval, in seconds, range 1 - 100.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch (config-if)# ip pim state-refresh origination-interval 100
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip pim unicast-bsm

### Purpose
This command is used to configure the interface to reply with a unicast PIM bootstrap message upon receiving a PIM hello message from a new neighbor. Default is disabled.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip pim unicast-bsm
no ip pim unicast-bsm
```

### Parameters
```text
None.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch (config-if)# ip pim unicast-bsm
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip pim join-prune-interval

### Purpose
This command is used to configure the interval for sending join/prune messages on the interface. To restore the default configuration, please use the no ip pim join-prune-interval command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip pim join-prune-interval interval
no ip pim join-prune-interval
```

### Parameters
```text
interval: The interval for sending join/prune messages, ranging from 1 to 18724 seconds. The default value is 60 seconds.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the interval for sending join/prune messages to 100 seconds.
Switch (config)#interface vlan 2
Switch (config-if)# ip pim join-prune-interval 100
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## show ip multicast

### Purpose
The show ip multicast command is used to display the global configuration information of IP multicast.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip multicast [ vrf vrfname ]
```

### Parameters
```text
vrfname: Virtual Routing and Forwarding instance name
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the global configuration information of IP multicast:
Switch(config)#show ip multicast
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## show ip mroute

### Purpose
The show ip mroute command is used to display the multicast routing table.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip mroute [vrf vrfname] [ [ group ip-addr ] | [ source ip-addr ] | detail | static [ source source-ip ] | [ summary ] ]
```

### Parameters
```text
vrfname: Virtual Routing and Forwarding instance name
group ip-addr: Multicast group IP address
source ip-addr: Multicast source IP address
detail: Displays detailed multicast routing table
static [ source source-ip ]: Displays all static multicast routing entries or static multicast routing entries with a specified source IP address
summary: Displays summary information of multicast routing entries
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display all multicast routing entries:
Switch(config)#show ip mroute
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## show ip pim

### Purpose
The show ip pim command is used to display the IP PIM global configuration related information.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip pim [ vrf vrfname ]
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
Display the IP PIM global configuration related information:
Switch(config)# show ip pim
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## show ip pim interface

### Purpose
The show ip pim interface command is used to display brief/detailed PIM interface information of specified interfaces or all interfaces.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip pim interface { intf_type intf_id | all } [ detail ]
show ip pim vrf vrfname interface all [ detail ]
```

### Parameters
```text
intf_type
Specifies the interface type to display.
intf_id
Specifies the interface ID to display.
vrfname
Virtual Routing and Forwarding instance name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config)# show ip pim vrf test interface all detail
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## show ip pim local-MemberShip

### Purpose
The show ip pim interface command is used to display PIM group membership information.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip pim local-MemberShip [ interface intf_type intf_id ]
show ip pim vrf vrfname local-MemberShip
```

### Parameters
```text
intf_type
Specifies the interface type to display.
intf_id
Specifies the interface ID to display.
vrfname
Virtual Routing and Forwarding instance name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config)# show ip pim local-MemberShip interface vlan 1
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## show ip pim mroute

### Purpose
This command is used to PIM multicast route related information.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip pim [ vrf vrfname ] mroute [ group group_addr] [ source src_addr ] detail
```

### Parameters
```text
group_addr
Specifies the multicast group to query.
src_addr
Specifies the multicast source to query.
vrfname
Virtual Routing and Forwarding instance name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config)# show ip pim vrf test mroute group 235.0.0.1 source 192.168.101.1 detail
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## show ip pim neighbor

### Purpose
The show ip pim neighbor command is used to display the IP PIM neighbor information.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip pim neighbor [ interface intf_type intf_id ] [ detail ]
show ip pim vrf vrfname neighbor [ detail ]
```

### Parameters
```text
intf_type
Specifies the interface type to display.
intf_id
Specifies the interface ID to display.
vrfname
Virtual Routing and Forwarding instance name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config)# show ip pim neighbor interfave vlan 1
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## show ip pim nexthop

### Purpose
This command is used to PIM next-hop related information.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip pim [ vrf vrfname ] nexthop
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
Switch(config)# show ip pim nexthop
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## show ip pim statistic

### Purpose
The show ip pim statistic command is used to display the IP PIM statistic information.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip pim statistic [ interface intf_type intf_id ]
show ip pim [ vrf vrfname ] statistic
```

### Parameters
```text
intf_type
Specifies the interface type to display.
intf_id
Specifies the interface ID to display.
vrfname
Virtual Routing and Forwarding instance name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display packet count information of all PIM interfaces:
Switch(config)#show ip pim vrf test statistic
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## show ip pim bsr-router

### Purpose
This command is used to view the information of candidate BSRs and candidate RPs.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip pim [ vrf vrfname ] bsr-router
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
Switch(config)# show ip pim vrf test bsr-router
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## show ip pim rp mapping

### Purpose
This command is used to view the multicast group information mapped to RPs.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip pim [ vrf vrfname ] rp mapping [ rp_addr | candidate | static ]
```

### Parameters
```text
rp_addr
Specifies the RP address to query.
vrfname
Virtual Routing and Forwarding instance name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config)# show ip pim rp mapping
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## show ip pim rp-hash

### Purpose
This command is used to view the the hash result of the specified multicast group.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip pim [ vrf vrfname ] rp hash group_addr
```

### Parameters
```text
group_addr
Specifies the multicast group to query.
vrfname
Virtual Routing and Forwarding instance name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config)# show ip pim vrf test rp hash 235.0.0.1
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## show ip pim ssm

### Purpose
This command is used to display PIM SSM configuration information.

### Command Mode
Global Configuration Mode

### Syntax
```text
show ip pim [ vrf vrfname ] ssm
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
Switch(config)# show ip pim vrf test ssm
```

### Notes
- Permission requirement: Privileged EXEC Mode and Any Configuration Mode
- Availability: Only for certain devices according to the official chapter title.
