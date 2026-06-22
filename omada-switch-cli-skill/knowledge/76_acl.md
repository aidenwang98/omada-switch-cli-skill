# ACL Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 76 ACL Commands

Location: extracted Word text lines 28567-29075

## Chapter Notes

Official documentation states: ACL (Access Control List) is used to filter data packets by configuring a series of match conditions, operations and time ranges. It provides a flexible and secured access control policy and facilitates you to control the network security.

- Use these commands only when the requested feature and target interface/VLAN/ring/session details are clear.

## access-list create

### Purpose
The access-list create command is used to create an ACL.

### Command Mode
Global Configuration Mode

### Syntax
```text
access-list create acl-id [ name acl-name ]
no access-list create { acl-id }
```

### Parameters
```text
acl-id
Enter an ACL ID. The IDs for MAC ACL are from 0 to 499. The IDs for IP ACL are from 500 to 999. The IDs for Combined ACL are from 1000 to 1499. The IDs for IPv6 ACL are from 1500 to 1999. The IDs for Packet Content ACL are from 2000 to 2499.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Create an IP ACL whose ID is 523:
Switch(config)# access-list create 523
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Official note: Packet Content ACL is only available on certain devices. acl-name Enter a name to identify the ACL.

## access-list packet-content profile

### Purpose
The access-list packet-content profile command is used to specify the offset of each chunk. There are four chunks to be configured. They must be configured before you configure the chunk value&mask.

### Command Mode
Global Configuration Mode

### Syntax
```text
access-list packet-content profile chunk-offset0 offset0 chunk-offset1 offset1 chunk-offset2 offset2 chunk-offset3 offset3
```

### Parameters
```text
offset0 -offset3: Specify the offset of each chunk. The value ranges from 0 to 31. When the offset is set as 31, it matches the first 127,128, 1, 2 bytes of the packet; when the offset is set as 0, it matches the 3, 4, 5, 6 bytes, and so on, for the rest of the offset value.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure a packet content profile with offset 0,1,2,3:
Switch(config)# access-list packet-content profile chunk-offset0 0 chunk-offset1 1 chunk-offset2 2 chunk-offset3 3
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Official note: This command is only available on certain devices.

## access-list resequence

### Purpose
The access-list resequence command is used to resequence the rules by providing a Start Rule ID and Step value.

### Command Mode
Global Configuration Mode

### Syntax
```text
access-list resequence acl-id-or-name start start-rule-id step rule-id-step-value
```

### Parameters
```text
acl-id-or-name
The ACL ID or name.
start-rule-id
The start rule ID.
rule-id-step-value
The step value.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Resequence the rules of ACL 12 with the start ID as 1 and step value as 5:
Switch(config)# access-list resequence 12 start 1 step 5
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## access-list mac

### Purpose
The access-list mac command is used to create MAC ACL. To delete the MAC ACL, please use no access-list mac.

### Command Mode
Global Configuration Mode

### Syntax
```text
access-list mac acl-id-or-name rule { auto | rule-id } { deny | permit } logging {enable | disable} [smac source-mac smask source-mac-mask ] [dmac destination-mac dmask destination-mac-mask ] [type ether-type] [pri dot1p-priority] [vid vlan-id] [tseg time-range-name]
no access-list mac acl-id-or-name rule rule-id
```

### Parameters
```text
acl-id-or-name
Enter the ID or name of the ACL that you want to add a rule for.
auto
The rule ID will be assigned automatically and the interval between rule IDs is 5.
rule-id
Assign an ID to the rule.
deny | permit
Specify the action to be taken with the packets that match the rule. By default, it is set to permit. The packets will be discarded if
deny
is selected and forwarded if
permit
is selected.
enable | disable
Enable or disable Logging function for the ACL rule. If "enable " is selected, the times that the rule is matched will be logged every 5 minutes. With ACL Counter trap enabled, a related trap will be generated if the matching times changes.
source-mac
Enter the source MAC address. The format is FF:FF:FF:FF:FF:FF.
source-mac-mask
Enter the mask of the source MAC address. This is required if a source MAC address is entered. The format is FF:FF:FF:FF:FF:FF.
destination-mac
Enter the destination MAC address. The format is FF:FF:FF:FF:FF:FF.
destination-mac-mask
Enter the mask of the destination MAC address. This is required if a destination MAC address is entered. The format is FF:FF:FF:FF:FF:FF.
ether-type
Specify an Ethernet-type with 4 hexadecimal numbers.
dot1p-priority: The user priority ranges from 0 to 7. The default is No Limit.
vlan-id
The VLAN ID ranges from 1 to 4094.
time-range-name
The name of the time-range. The default is No Limit.
```

### Default
By default, it is set to permit.

### Example
```text
Create MAC ACL 50 and configure Rule 5 to permit packets with source MAC address 00:34:a2:d4:34:b5:
Switch (config)#access-list create 50
Switch (config-mac-acl)#access-list mac 50 rule 5 permit logging disable smac 00:34:a2:d4:34:b5 smask ff:ff:ff:ff:ff:ff
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## access-list ip

### Purpose
The access-list ip command is used to add IP ACL rule. To delete the corresponding rule, please use no access-list ip command. IP ACLs analyze and process data packets based on a series of match conditions, which can be the source IP addresses and destination IP addresses carried in the packets.

### Command Mode
Global Configuration Mode

### Syntax
```text
access-list ip acl-id-or-name rule {auto | rule-id } {deny | permit} logging {enable | disable} [ sip sip-address sip-mask sip-address-mask ] [ dip dip-address dip-mask dip-address-mask ] [dscp dscp-value] [tos tos-value] [pre pre-value] [frag enable | disable] [protocol protocol [s-port s-port-number] [s-port-mask s-port-mask] [d-port d-port-number] [d-port-mask d-port-mask] [tcpflag tcpflag]] [tseg time-range-name] [vrf vrf-name]
no access-list ip acl-id-or-name rule rule-id
```

### Parameters
```text
acl-id-or-name
Enter the ID or name of the ACL that you want to add a rule for.
auto
The rule ID will be assigned automatically and the interval between rule IDs is 5.
rule-id
Assign an ID to the rule.
deny | permit
Specify the action to be taken with the packets that match the rule. By default, it is set to permit. The packets will be discarded if
deny
is selected and forwarded if
permit
is selected.
logging {enable | disable}
Enable or disable Logging function for the ACL rule. If "enable " is selected, the times that the rule is matched will be logged every 5 minutes. With ACL Counter trap enabled, a related trap will be generated if the matching times changes.
sip-address
Enter the source IP address.
sip-address-mask
Enter the mask of the source IP address. This is required if a source IP address is entered.
dip-address
Enter the destination IP address.
dip-address-mask
Enter the mask of the destination IP address. This is required if a destination IP address is entered.
dscp-value
Specify the DSCP value between 0 and 63.
tos-value
Specify an IP ToS value to be matched between 0 and 15.
pre-value
Specify an IP Precedence value to be matched between 0 and 7.
frag {enable | disable}
Enable or disable matching of fragmented packets. The default is disable. When enabled, the rule will apply to all fragmented packets and always permit to forward the last fragment of a packet.
```

### Default
By default, it is set to permit.

### Example
```text
Create IP ACL 600, and configure Rule 1 to permit packets with source IP address 192.168.1.100 and VRF v1:
Switch (config)#access-list create 600
Switch (config)#access-list ip 600 rule 1 permit logging disable vrf v1 sip 192.168.1.100 sip-mask 255.255.255.255
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Official note: frag {enable | disable} is only available on certain devices. protocol Specify a protocol type. s-port-number Specify the source port number. s-port-mask Specify the source port mask with 4 hexadecimal numbers. d-port-number Specify the destination port number. d-port-mask Specify the destination port mask with 4 hexadacimal numbers. tcpflag For TCP protocol, specify the flag value using either binary numbers or * (for example, 01*010*). The default is *, which indicates that the flag will not be matched. The flags are URG (Urgent flag), ACK (acknowledge flag), PSH(push flag), RST(reset flag),SYN(synchronize flag), and FIN(finish flag). time-range-name The name of the time-range. The default is No Limit. vrf-name VRF instance name.

## access-list combined

### Purpose
The access-list combined command is used to add Combined ACL rule. To delete the corresponding rule, please use no access-list extended command.

### Command Mode
Global Configuration Mode

### Syntax
```text
access-list combined acl-id-or-name rule {auto | rule-id } {deny | permit} logging {enable | disable} [smac source-mac-address smask source-mac-mask] [dmac dest-mac-address dmask dest-mac-mask] [vid vlan-id] [type ether-type] [pri priority] [sip source-ip-address sip-mask source-ip-mask]] [dip destination-ip-address dip-mask destination-ip-mask] [dscp dscp-value] [tos tos-value] [pre pre-value] [protocol protocol [s-port s-port-number s-port-mask s-port-mask] [d-port d-port-number d-port-mask d-port-mask] [tcpflag tcpflag]] [tseg time-range-name] [vrf vrf-name]
no access-list combined acl-id-or-name rule rule-id
```

### Parameters
```text
acl-id-or-name
Enter the ID or name of the ACL that you want to add a rule for.
auto
The rule ID will be assigned automatically and the interval between rule IDs is 5.
rule-id
Assign an ID to the rule.
deny | permit
Specify the action to be taken with the packets that match the rule. By default, it is set to permit. The packets will be discarded if
deny
is selected and forwarded if
permit
is selected.
logging {enable | disable}
Enable or disable Logging function for the ACL rule. If "enable " is selected, the times that the rule is matched will be logged every 5 minutes. With ACL Counter trap enabled, a related trap will be generated if the matching times changes.
source-mac-address
Enter the source MAC address.
source-mac-mask
Enter the source MAC address mask.
dest-mac-address
Enter the destination MAC address.
dest-mac-mask
Enter the destination MAC address mask. This is required if a destination MAC address is entered.
vlan-id: The VLAN ID ranges from 1 to 4094.
ether-type
Specify the Ethernet-type with 4 hexadecimal numbers.
priority
The user priority ranges from 0 to 7. The default is No Limit.
source-ip: Enter the source IP address.
source-ip-mask
Enter the mask of the source IP address. It is required if source IP address is entered.
destination-ip
This is required if a source IP address is entered.
destination-ip-mask
Enter the destination IP address mask. This is required if a destination IP address is entered.
dscp-value
Specify the DSCP value between 0 and 63.
tos-value
Specify an IP ToS value to be matched between 0 and 15.
pre-value
Specify an IP Precedence value to be matched between 0 and 7.
protocol
Specify a protocol type.
s-port-number
Specify the source port number.
s-port-mask
Specify the source port mask with 4 hexadecimal numbers.
d-port-number
Specify the destination port number.
d-port-mask
Specify the destination port mask with 4 hexadecimal numbers.
tcpflag
For TCP protocol, specify the flag value using either binary numbers or * (for example, 01*010*). The default is *, which indicates that the flag will not be matched. The flags are URG (Urgent flag), ACK (acknowledge flag), PSH(push flag), RST(reset flag),SYN(synchronize flag), and FIN(finish flag).
time-range-name
The name of the time-range. The default is No Limit.
vrf-name
VRF instance name.
```

### Default
By default, it is set to permit.

### Example
```text
Create Combined ACL 1100 and configure Rule 1 to deny packets with source IP address 192.168.3.100 and VRF v1 in VLAN 2:
Switch(config)# access-list create 1100
Switch(config)# access-list combined 1100 rule 1 deny logging disable vid 2 vrf v1 sip 192.168.3.100 sip
mask 255.255.255.255
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## access-list ipv6

### Purpose
The access-list ipv6 command is used to add IPv6 ACL rule. To delete the corresponding rule, please use no access-list ipv6 command. IPv6 ACLs analyze and process data packets based on a series of match conditions, which can be the source IP addresses and destination IP addresses carried in the packets, the DSCP and flow-label value, etc.

### Command Mode
Global Configuration Mode

### Syntax
```text
access-list ipv6 acl-id-or-name rule {auto | rule-id } {deny | permit} logging {enable | disable} [class class-value] [flow-label flow-label-value] [sip source-ip-address sip-mask source-ip-mask] [dip destination-ip-address dip-mask destination-ip-mask] [s-port source-port-number] [d-port destination-port-number] [tseg time-range-name] [vrf vrf-name]
no access-list ipv6 acl-id-or-name rule rule-id
```

### Parameters
```text
acl-id-or-name
Enter the ID or name of the ACL that you want to add a rule for.
auto
The rule ID will be assigned automatically and the interval between rule IDs is 5.
rule-id
Assign an ID to the rule.
deny | permit
Specify the action to be taken with the packets that match the rule. By default, it is set to permit. The packets will be discarded if
deny
is selected and forwarded if
permit
is selected.
logging {enable | disable}
Enable or disable Logging function for the ACL rule. If "enable " is selected, the times that the rule is matched will be logged every 5 minutes. With ACL Counter trap enabled, a related trap will be generated if the matching times changes.
class-value
Specify a class value to be matched. It ranges from 0 to 63.
flow-label-value
Specify a Flow Label value to be matched.
source-ip-address
Enter the source IP address. Enter the destination IPv6 address to be matched. All types of IPv6 address will be checked. You may enter a complete 128-bit IPv6 address but only the first 64 bits will be valid.
source-ip-mask
Enter the source IP address mask. The mask is required if the source IPv6 address is entered. Enter the mask in complete format (for example, ffff:ffff:0000:ffff). The mask specifies which bits in the source IPv6 address to match the rule.
destination-ip-address
Enter the destination IPv6 address to be matched. All types of IPv6 address will be checked. You may enter a complete 128-bit IPv6 addresses but only the first 64 bits will be valid.
destination-ip-mask: Enter the source IP address mask. The mask is required if the source IPv6 address is entered. Enter the mask in complete format (for example, ffff:ffff:0000:ffff). The mask specifies which bits in the source IPv6 address to match the rule.
source-port-number
Enter the TCP/UDP source port if TCP/UDP protocol is selected.
destination-port-number
Enter the TCP/UDP destination port if TCP/UDP protocol is selected.
time-range-name
The name of the time-range. The default is No Limit.
vrf-name
VRF instance name.
```

### Default
By default, it is set to permit.

### Example
```text
Create IPv6 ACL 1600 and configure Rule 1 to deny packets with source IPv6 address CDCD:910A:2222:5498:8475:1111:3900:2020 and VRF v1:
Switch(config)# access-list create 1600
Switch(config)# access-list ipv6 1600 rule 1 deny logging disable vrf v1 sip CDCD:910A:2222:5498:8475:1111:3900:2020 sip-mask ffff:ffff:ffff:ffff
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- User guidelines: Before binding an IPv6 ACL to a VLAN or interface, you should configure the SDM template as enterpriseV6 and save your configurations.

## access-list packet-content config

### Purpose
The access-list packet-content config command is used to add Packet Content ACL rule. To delete the corresponding rule, please use no access-list packet-content config command. Packet content ACLs analyze and process data packets based on 4 chunk match conditions, each chunk can specify a user-defined 4-byte segment carried in the packet's first 128 bytes.

### Command Mode
Global Configuration Mode

### Syntax
```text
access-list packet-content config acl-id-or-name rule {auto | rule-id } {deny | permit} logging {enable | disable} [chunk0 value mask0 mask] [chunk1 value mask1 mask] [chunk2 value mask2 mask] [chunk3 value mask3 mask] [tseg time-segment]
no access-list packet-content config acl-id-or-name rule rule-id
```

### Parameters
```text
acl-id-or-name
Enter the ID or name of the ACL that you want to add a rule for.
auto
The rule ID will be assigned automatically and the interval between rule IDs is 5.
rule-id
Assign an ID to the rule.
deny | permit
Specify the action to be taken with the packets that match the rule. Deny means to discard; permit means to forward. By default, it is set to permit.
logging {enable | disable}
Enable or disable Logging function for the ACL rule. If "enable" is selected, the times that the rule is matched will be logged every 5 minutes. With ACL Counter trap enabled, a related trap will be generated if the matching times changes.
value
Specify the chunk value, ranging from 0-ffffffff.
mask
Specify the chunk mask, ranging from 0-ffffffff. Chunk mask here must be written completely in 4-byte hex mode, like '0000ffff'.
time-segment
The name of the time-range. The default is No Limit.
```

### Default
By default, it is set to permit.

### Example
```text
Create a packet-content ACL rule with all 4 chunks configured, the rule id is 1 and the default action is permit:
SwitchSwitch(config)# access-list packet-content config rule 1 permit logging disable chunk0 45ea mask0 0000ffff chunk1 1111ffff mask1 ffffffff chunk2 ee34 mask2 ffff0000 chunk3 7878 mask3 000ffae3
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Official note: This command is only available on certain devices.

## access-list action

### Purpose
The access-list action command is used to specify a rule to be configured with policies and enter Action Configuration mode. To delete the corresponding policies, please use no access-list action command.

### Command Mode
Global Configuration Mode

### Syntax
```text
access-list action acl-id-or-name rule rule-id
no access-list action acl-id-or-name rule rule-id
```

### Parameters
```text
acl-id-or-name
Enter the ID or name of the ACL.
rule-id
Enter the ID of the ACL rule.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Specify the rule 1 of ACL 200 to be configured with policies:
Switch(config)# access-list action 200 rule 1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## redirect

### Purpose
This command is used to configure the operation of the action for ACL. For packets matched by the ACL, they are rerouted to a specified next-hop exit according to the policy routing rules. If the next hop VRF of the redirect is not specified, the public network is used by default.

### Command Mode
Action Configuration Mode

### Syntax
```text
redirect { nexthop | ipv6nexthop} ip-address [vrf vrf-name]
```

### Parameters
```text
nexthop: Indicates that the next hop address for the matched packet in policy routing is an IPv4 address.
ipv6nexthop: Indicates that the next hop address for the matched packet in policy routing is an IPv6 address.
ip-address: IP address.
vrf-name: The VRF instance to which the next hop of redirect belongs.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the PBR rule and redirect the next hop to VRF instance v1:
Switch (config-action)#redirect ipv6nexthop 4200::99 vrf v1
Switch(config-action)#redirect nexthop 1.1.1.1 vrf v1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## s-condition

### Purpose
The s-condition command is used to limit the rate of the matched packets. To restore the settings to the defaults, please use no s-condition.

### Command Mode
Action Configuration Mode

### Syntax
```text
s-condition rate rate burst burst-size osd { none | discard | remark dscp dscp }
no s-condition
```

### Parameters
```text
rate
Specify a rate, ranging from 0 to 1000000kbps.
burst-size
Specify the number of bytes allowed in one second ranging from 1 to 128.
osd
Select either
none
or
discard
as the action to be taken for the packets whose rate is beyond the specified rate. The default is None. When
remark dscp
is selected, you also need to specify the DSCP value for the matched packets. The DSCP value ranges from 0 to 63.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure a policy for rule 1 of ACL 6: limit the transmission rate of the matched packets as 1000 Kbps and if the number of bytes per second is beyond 100, the packets will be discarded by the switch:
Switch(config)#access-list action 6 rule 1
Switch(config-action)# s-condition rate 1000 burst 100 osd discard
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Official note: Remark DSCP is only available on certain devices.

## s-mirror

### Purpose
The s-mirror command is used to define the policy to mirror the matched packets to the desired port. To disable this policy, please use no s-mirror command.

### Command Mode
Action Configuration Mode

### Syntax
```text
s-mirror interface { fastEthernet port | gigabitEthernet port | ten-gigabitEthernet port }
```

### Parameters
```text
port
The destination port to which the packets will be mirrored.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure a policy for rule 1 of ACL 6: specify the mirror port as Gigabit Ethernet port 1/0/2 for the data packets matching this rule:
Switch(config)#access-list action 6 rule 1
Switch(config-action)#s-mirror interface gigabitEthernet 1/0/2
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## qos-remark

### Purpose
The qos-remark command is used to configure QoS Remark function of policy action. To restore the settings to the default, please use no qos-remark.

### Command Mode
Action Configuration Mode

### Syntax
```text
qos-remark [ dscp dscp ] [ priority pri ] [dot1p dot1p-pri]
no qos-remark
```

### Parameters
```text
dscp
DSCP of QoS Remark. Specify the DSCP region for the data packets matching the corresponding ACL. DSCP ranges from 0 to 63. By default, it is not limited.
pri
Local Priority of QoS Remark. Specify the local priority for the data packets matching the corresponding ACL. Local Priority ranges from 0 to 7.
dot1p-pri
802.1P priority of QoS Remark. This remark configuration will change the data packet's 802.1P priority field to the dot1p-pri you set. 802.1P priority ranges from 0 to 7.
```

### Default
By default, it is not limited.

### Example
```text
Configure a policy for rule 1 of ACL 6: specify the DSCP region as 30 and local priority 2 for the packets matching this rule:
Switch(config)#access-list action 6 rule 1
Switch(config-action)# qos-remark dscp 30 priority 2
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Official note: The DSCP and dot1p cannot be configured at the same time.

## access bind

### Purpose
The access-list policy name command is used to add Policy. To delete the corresponding Policy, please use no access-list policy name command. A Policy is used to control the data packets those match the corresponding ACL rules.

### Command Mode
Global Configuration Mode

### Syntax
```text
access-list bind acl-id-or-name interface { [ vlan vlan-list ] | [ fastEthernet port-list ] | [gigabitEthernet port-list ] | [ ten-gigabitEthernet port-list ] }
no access-list bind acl-id-or-name interface { [ vlan vlan-list ] | [ fastEthernet port-list ] | [gigabitEthernet port-list ] | [ ten-gigabitEthernet port-list ] }
```

### Parameters
```text
acl-id-or-name
Enter the ID or name of the ACL that you want to add a rule for.
vlan-list
Specify the ID or the ID list of the VLAN(s) that you want to bind the ACL to. The valid values are from 1 to 4094, for example, 2-3,5.
port-list
Specify the number or the list of the Ethernet port that you want to bind the ACL to.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Bind ACL 1 to port 3 and VLAN 4:
Switch(config)#access-list bind 1 interface vlan 4 gigabitEthernet 1/0/3
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## show access-list

### Purpose
The show access-list command is used to display configuration of ACL.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show access-list acl-id-or-name
```

### Parameters
```text
acl-id-or-name
The ID or name of the ACL selected to display the configuration.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the configuration of the MAC ACL whose ID is 20:
Switch(config)# show access-list 20
```

### Notes
- Permission requirement: None.

## show access-list bind

### Purpose
The show access-list bind command is used to display the configuration of ACL binding.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show access-list bind
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the configuration of Policy bind:
Switch(config)# show access-list bind
```

### Notes
- Permission requirement: None.

## show access-list status

### Purpose
The show access-list status command is used to display usage status of ACL entry resource.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show access-list status
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the usage status of ACL entry resource:
Switch(config)# show access-list status
```

### Notes
- Permission requirement: None.

## show access-list counter

### Purpose
The show access-list counter command is used to display the packet counter of a specified ACL.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show access-list acl-id-or-name counter
```

### Parameters
```text
acl-id-or-name
The ID or name of the ACL to display.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the packet counter of ACL 100:
Switch(config)# show access-list 100 counter
```

### Notes
- Permission requirement: None.

## clear access-list

### Purpose
The clear access-list command is used to clear the counter of matched packets of a specified ACL or rule.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
clear access-list acl-id-or-name [rule rule-id]
```

### Parameters
```text
acl-id-or-name
The ID or name of the ACL.
rule-id
The ID of the rule.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Clear the packet counter of ACL 100:
Switch(config)# clear access-list 100
```

### Notes
- Permission requirement: None.
