# IS-IS Configuration Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 50 IS-IS Configuration Commands (Only for Certain Devices)

Location: extracted Word text lines 22886-23590

## Chapter Notes

Official documentation states: Intermediate System to Intermediate System (IS-IS) is a dynamic routing protocol proposed by ISO. Currently, IS-IS is also supported in TCP/IP environments. It is a widely used protocol in Interior Gateway Protocols (IGP). IS-IS is a link-state protocol, and the core concept of its routing calculation is the Shortest Path First (SPF) algorithm.

- This chapter is marked `Only for Certain Devices`; treat all configuration commands as model-dependent.

## router isis

### Purpose
The router isis command is used to create an IS-IS instance and enter the Router configuration mode. When the command includes a VRF name, it means that the IS-IS instance belongs to the VRF instance. When the VRF parameter is not specified, the IS-IS instance belongs to the public network. To delete the IS-IS instance, please use the no router isis command. When the VRFparameter is not specified, the corresponding instance will be deleted according to the area-tag.

### Command Mode
Global Configuration Mode

### Syntax
```text
router isis area-tag [vrf vrf-name]
no router isis area-tag [vrf vrf-name]
```

### Parameters
```text
area-tag
IS-IS instance name, used to identify an IS-IS instance on this switch.
vrf-name
VRF instance name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Create an ISIS instance aaa and add it to vrf1.
Switch(config)# router isis aaa vrf vrf1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## area-password

### Purpose
This command is used to enable the IS-IS Level-1 area authentication function. After the function is enabled, IS-IS will carry authentication information in the message exchange in the area and verify the authentication information. To disable this function, please use the no area-password command.

### Command Mode
Router Configuration Mode

### Syntax
```text
area-password { clear | md5 } { 0 | 7 } text
no area-password
```

### Parameters
```text
clear: Encrypt in plain text.
md5: Encrypt using md5 algorithm.
0: Enter plain text.
7: Enter in cipher text.
text: Password text
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure MD5 encrypted authentication for the IS-IS Level-1 area:
Switch(config-router)#area-password md5 0 tp-link
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## domain-password

### Purpose
This command is used to enable the authentication function of the IS-IS Level-2 area. After enabling this function, IS-IS will carry authentication information in the message exchange in this area and verify the authentication information. To disable this function, please use the no domain-password command.

### Command Mode
Router Configuration Mode

### Syntax
```text
domain-password { clear | md5 } { 0 | 7 } text
no domain-password
```

### Parameters
```text
clear: Encrypt in plain text.
md5: Encrypt using md5 algorithm.
0: Enter plain text.
7: Enter in cipher text.
text: Password text
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure MD5 encrypted authentication for the IS-IS Level-2 area:
Switch(config-router)#domain-password md5 0 tp-link
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## graceful-restart

### Purpose
This command is used to enable the IS-IS Graceful Restart function. When enabled, IS-IS will send restart notification messages to neighboring routers before initiating a restart. During the restart process, IS-IS strives to preserve routing information to minimize impact on other devices in the network. To disable this function, please use the no graceful-restart command.

### Command Mode
Router Configuration Mode

### Syntax
```text
graceful-restart
no graceful-restart
graceful-restart suppress-sa
no graceful-restart suppress-sa
graceful-restart t2-interval t2-interval
no graceful-restart t2-interval
graceful-restart t3-interval t3-interval
no graceful-restart t3-interval
```

### Parameters
```text
suppress-sa: Suppress partial advertisement information during the IS-IS graceful restart process.
t2-interval: The duration in IS-IS graceful restart during which the restarting router waits for neighboring routers to send CSNP (Complete Sequence Number PDU) to facilitate rapid database synchronization. The range is 30 to 1800 seconds, and the default value is 60 seconds.
T3-interval: The duration in IS-IS graceful restart during which the restarting router waits for neighboring routers to acknowledge its graceful restart. The range is 30 to 1800 seconds, and the default value is 300 seconds.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure graceful restart for IS-IS routes:
Switch(config-router)#graceful-restart
Switch(config-router)#graceful-restart suppress-sa
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## hostname

### Purpose
This command is used to enable the dynamic host name function of IS-IS. After enabling this function, IS-IS will configure a dynamic host name for the IS-IS system on the local switch and notify the neighbor device through the LSP message. To disable this function, please use the no hostname command.

### Command Mode
Router Configuration Mode

### Syntax
```text
hostname { name | dynamic }
no hostname
```

### Parameters
```text
name: Specified host name, in text form.
dynamic: Use dynamic host name, in this mode, the system configured host name will be obtained.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the dynamic host name function of IS-IS:
Switch(config-router)# hostname dynamic
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## is-type

### Purpose
This command is used to set the IS area type, which is Level-1-2 by default. To restore the default configuration, please use the no is-type command.

### Command Mode
Router Configuration Mode

### Syntax
```text
is-type { level-1 | level-1-2 | level-2-only }
no is-type
```

### Parameters
```text
level-1: Set the IS-IS area type to Level-1
level-1-2: Set the IS-IS area types to Level-1 and Level-2 level-2-only: Set the IS-IS area type to Level-2
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set the IS-IS area type to Level-1:
Switch(config-router)# is-type level-1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## log-adjacency-changes

### Purpose
This command is used to enable S-IS to record events of adjacency state changes. To disable this function, please use the no log-adjacency-changes command.

### Command Mode
Router Configuration Mode

### Syntax
```text
log-adjacency-changes
no log-adjacency-changes
```

### Parameters
```text
None
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set the IS-IS area type to Level-1:
Switch(config-router)# log-adjacency-changes
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## lsp-gen-interval

### Purpose
This command is used to configure the interval for generating LSPs. When the local network flaps, the IS-IS local LSP may be frequently refreshed, causing frequent IS-IS flapping. To restore the default configuration, please use the no lsp-gen-interval command.

### Command Mode
Router Configuration Mode

### Syntax
```text
lsp-gen-interval interval
no lsp-gen-interval
```

### Parameters
```text
interval: The interval for generating LSPs, ranging from 1 to 120s. It is 30s by default.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set the LSP generating interval to 10s:
Switch(config-router)# lsp-gen-interval 10
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## lsp-mtu

### Purpose
This command is used to configure the maximum length of a self-generated LSP. To restore the default configuration, please use the no lsp-mtu command.

### Command Mode
Router Configuration Mode

### Syntax
```text
lsp-mtu size
no lsp-mtu
```

### Parameters
```text
size: The maximum length of LSP, ranging from 512 to 4352 bytes. It is 1497 bytes by default.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set the maximum length of LSP to 1024 bytes:
Switch(config-router)# lsp-mtu 1024
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## lsp-refresh-interval

### Purpose
This command is used to configure the interval for refreshing the IS-IS LSP. To restore the default configuration, please use the no lsp-refresh-interval command.

### Command Mode
Router Configuration Mode

### Syntax
```text
lsp-refresh-interval interval [ level-1 | level-2 ]
no lsp-refresh-interval
```

### Parameters
```text
interval: The interval for refreshing the IS-IS LSP, ranging from 1 to 65535s. It is 900s by default.
level-1: LSP level-1 refresh interval
level-2: LSP level-2 refresh interval
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set the LSP refresh interval to 100s:
Switch(config-router)# lsp-refresh-interval 100
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## max-lsp-lifetime

### Purpose
This command is used to configure the maximum lifetime of an IS-IS LSP packet. To restore the default configuration, please use the no max-lsp-lifetime command.

### Command Mode
Router Configuration Mode

### Syntax
```text
max-lsp-lifetime time [ level-1 | level-2 ]
no max-lsp-lifetime
```

### Parameters
```text
time: The max lifetime of LSP, ranging from 350 to 65535s. It is 1200s by default.
level-1: LSP level-1 refresh interval
level-2: LSP level-2 refresh interval
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set the maximum lifetime of an LSP to 1000s:
Switch(config-router)# max-lsp-lifetime 1000
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## metric-style

### Purpose
This command is used to configure IS-IS metric style. To restore the default configuration, please use the no metric-style command. This command is used to configure NET of IS-IS. To delete NET, please use the no net command.

### Command Mode
Router Configuration Mode Router Configuration Mode

### Syntax
```text
metric-style { narrow | transition | wide }
no metric-style
net net-name
no net net-name
```

### Parameters
```text
narrow: Narrow mode. It is the default mode.
transition: Compatible mode, supporting both narrow and wide modes.
wide: Wide mode, mainly used for TE scenarios.
net-name: Network Entity Title, in the format of X
X.XXXX.XXXX.XXXX.00. The first
is the IS-IS area address, the 12
s in the middle are the switch
s System ID, and the last
is the SEL.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set IS-IS metric style to wide:
Switch(config-router)# metric-style wide
Configure IS-IS NET as 10.0000.0000.0000.1111.00:
Switch(config-router)#net 10.0000.0000.0000.1111.00
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands. Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## purge-originator

### Purpose
This command is used to enable the purge originator of IS-IS. To disable this function, please use the no purge-originator command.

### Command Mode
Router Configuration Mode

### Syntax
```text
purge-originator
no purge-originator
```

### Parameters
```text
None
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the purge originator of IS-IS:
Switch(config-router)#purge-originator
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## set-attached-bit

### Purpose
This command is used to set the ATT bit of IS-IS LSP. By default, Level-1-2 devices will set the ATT bit according to the rules of IS-IS protocol. After this command is configured, the ATT bit will always be set in Level-1 LSP. To cancel the setting of ATT bit, please use the no set-attached-bit command.

### Command Mode
Router Configuration Mode

### Syntax
```text
set-attached-bit
no set-attached-bit
```

### Parameters
```text
None
```

### Default
By default, Level-1-2 devices will set the ATT bit according to the rules of IS-IS protocol.

### Example
```text
Set the ATT bit of IS-IS LSP:
Switch(config-router)#set-attached-bit
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## set-overload-bit

### Purpose
This command is used to set the overload bit in IS-IS LSP. To cancel the overload bit setting, please use the no set-overload-bit command.

### Command Mode
Router Configuration Mode

### Syntax
```text
set-overload-bit
no set-overload-bit
```

### Parameters
```text
None
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set the overload bit in IS-IS LSP:
Switch(config-router)#set-overload-bit
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## spf interval

### Purpose
This command is used to configure the frequency of SPF calculations in IS-IS to balance network convergence speed and CPU load. To restore the default settings, please use the no spf-interval command.

### Command Mode
Router Configuration Mode

### Syntax
```text
spf-interval time
no spf-interva
```

### Parameters
```text
time: The interval for SPF calculation. The range is 1 to 120 seconds, and the default value is 2 seconds
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the interval for SPF calculation to 5 seconds:
Switch(config-router)# spf-interval 5
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## topology

### Purpose
This command is used to enable global IS-IS network multi-topology, allowing independent logical topologies to be created for different protocols or services. To disable this configuration, please use the no topology command.

### Command Mode
Router Configuration Mode

### Syntax
```text
topology { ipv6-unicast } [ overload ]
no topology { ipv6-unicast }
```

### Parameters
```text
ipv6-unicast: IS-IS enables IPv6 unicast topology.
overload: IS-IS enables topology to set overload bit.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure IS-IS multi-topology:
Switch(config-router)#topology ipv6-unicast overload
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## clear isis neighbor

### Purpose
This command is used to clear the neighbor relationship established by IS-IS and re-establish the relationship with neighbor device.

### Command Mode
Router Configuration Mode

### Syntax
```text
clear isis neighbor [ system-id ]
```

### Parameters
```text
system-id: System ID of the specified neighbor.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Clear all IS-IS neighbors:
Switch(config-router)#clear isis neighbor
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## redistribute

### Purpose
This command is used to redistribute routes. In a multi-protocol deployment scenario, routes of other protocols or other IS-IS instances can be redistributed to IS-IS, which will then flood the routes throughout the entire area.

### Command Mode
Router Configuration Mode

### Syntax
```text
redistribute { ipv4 { bgp | connected | rip | static | ospf process-id | isis area-name } | ipv6 { bgp | connected | ospf6 | ripng | static } } { level-1 | level-2 }
```

### Parameters
```text
ipv4: Redistribute IPv4 routing.
ipv6: Redistribute IPv6 routing.
bgp: Redistribute BGP routing.
connected: Redistribute direct routing.
ospf: redirect OSPF routing.
process-id: redirect OSPF routing instance number
isis: redirect IS-IS routing
area-name: redirect IS-IS routing area name
rip: redirect RIP routing
static: Redistribute static routes.
ospf6: Redistribute OSPFv3 routes.
ripng: Redistribute RIPng routes.
level-1: Redirect to level-1 area.
level-2: Redirect to level-2 area.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Redistribute IPv4 BGP routes to the level-1 area of IS-IS:
Switch(config-router)# redistribute ipv4 bgp level-1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## distance

### Purpose
This command is used to configure the distance of IS-IS protocol routes, that is, the route priority of IS-IS protocol. This function can change the priority strategy of different protocol routes in multi-protocol scenarios.

### Command Mode
Router Configuration Mode

### Syntax
```text
distance value
```

### Parameters
```text
value: Distance value, ranging from 1 to 255, and the default value is 110.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the distance of the IS-IS protocol to 100:
Switch(config-router)#distance 100
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip router isis

### Purpose
This command is used to enable IPv4 IS-IS on an interface, while its no form disables the IPv4 IS-IS functionality under the interface. Configuration of IS-IS settings under an interface is only permitted when either IPv4 or IPv6 IS-IS has been enabled. If both IPv4 and IPv6 IS-IS are disabled simultaneously, all IS-IS configurations under the interface will be cleared.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip router isis area-name
no ip router isis
```

### Parameters
```text
area-name: Specify the area name of the IS-IS instance.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable interface VLAN 1 on IS-IS instance 1:
Switch(config)#interface vlan 1
Switch(config-if)#ip router isis 1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ipv6 router isis

### Purpose
This command is used to enable IPv6 IS-IS on an interface. Its "no" form disables IPv6 IS-IS functionality on the interface. Interface-specific IS-IS configurations can only be performed when either IPv4 or IPv6 IS-IS is enabled. When both IPv4 and IPv6 IS-IS functionalities are disabled, all IS-IS configurations under the interface will be cleared.

### Command Mode
Interface Configuration Mode

### Syntax
```text
Ipv6 router isis area-name
no ipv6 router isis
```

### Parameters
```text
area-name: Specify the area name of the IS-IS instance.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable interface VLAN 1 on IS-IS IPV6 instance 1:
Switch(config)#interface vlan 1
Switch(config-if)#ipv6 router isis 1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## isis bfd

### Purpose
This command is used to enable BFD on an interface and notify IS-IS. IS-IS can quickly detect changes in interface status. To disable this function, please use the no isis bfd command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
isis bfd [ bfd-template ]
no isis bfd
```

### Parameters
```text
bfd-template: BFD template name, depending on the global BFD template configuration
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable BFD on interface VLAN 1 and notify IS-IS:
Switch(config)#interface vlan 1
Switch(config-if)#isis bfd
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## isis circuit-type

### Purpose
This command is used to configure the IS-IS area type of the interface. By default, the area type of the IS-IS interface is the area type configured globally for IS-IS. To restore the default configuration, please use the no isis circuit-type command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
isis circuit-type { level-1 | level-1-2 | level-2-only }
no isis circuit-type
```

### Parameters
```text
level-1: Set the IS-IS area type to Level-1
level-1-2: Set the IS-IS area types to Level-1 and Level-2
level-2-only: Set the IS-IS area type to Level-2
```

### Default
By default, the area type of the IS-IS interface is the area type configured globally for IS-IS.

### Example
```text
Set the IS-IS area type of interface VLAN 1 to Level-1:
Switch(config)#interface vlan 1
Switch(config-if)#isis circuit-type level-1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## isis csnp-interval

### Purpose
This command is used to configure the interval for sending CSNP packets of IS-IS on the interface. To restore the default configuration, please use the no isis csnp-interval command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
isis csnp-interval interval
no isis csnp-interval
```

### Parameters
```text
interval: The interval for sending CSNP packets, ranging from 1 to 600s, and the default value is 10.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set the CSNP message sending interval of IS-IS on interface VLAN 1 to 20s:
Switch(config)#interface vlan 1
Switch(config-if)#isis csnp-interval 20
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## isis hello-interval

### Purpose
This command is used to configure the interval for sending Hello packets of IS-IS on the interface. To restore the default configuration, please use the no isis csnp-interval command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
isis hello-interval interval
no isis hello-interval
```

### Parameters
```text
interval: The interval for sending Hello packets, ranging from 1 to 600s, and the default value is 3.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set the Hello message sending interval of IS-IS on interface VLAN 1 to 10s:
Switch(config)#interface vlan 1
Switch(config-if)#isis hello-interval 10
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## isis hello-multiplier

### Purpose
This command is used to configure the multiplier of the IS-IS Hello message on the interface. Hello-interval * Hello-multiplier is the neighbor s Hold timer. To restore the default configuration, please use the no isis hello-multiplier command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
isis hello-multiplier value
no isis hello-multiplier
```

### Parameters
```text
value: Hello multiplier, ranging from 2 to 100. It is 10 by default.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set the IS-IS Hello multiplier on interface VLAN 1 to 20:
Switch(config)#interface vlan 1
Switch(config-if)# isis hello-multiplier 20
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## isis metric

### Purpose
This command is used to configure the IS-IS metric on the interface. To restore the default configuration, please use the no isis metric command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
isis metric value
no isis metric
```

### Parameters
```text
value: IS-IS metric, ranging from 0 to16777215. It is 10 by default.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set the IS-IS metric on interface VLAN 1 to 20:
Switch(config)#interface vlan 1
Switch(config-if)#isis metric 20
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## isis network point-to-point

### Purpose
This command is used to configure the IS-IS network type of the interface. To restore the default configuration, please use the no isis network point-to-point command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
isis network point-to-point
no isis network point-to-point
```

### Parameters
```text
None.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set the IS-IS network type of interface VLAN 1 to P2P:
Switch(config)#interface vlan 1
Switch(config-if)# isis network point-to-point
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## isis passive

### Purpose
This command is used to configure the IS-IS silent function on the interface. After it is enabled, the interface will not be able to perform IS-IS message exchange and route calculation. To disable this dunction, please use the no isis passive command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
isis passive
no isis passive
```

### Parameters
```text
None.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Make the IS-IS on VALN 1 silent:
Switch(config)#interface vlan 1
Switch(config-if)#isis passive
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## isis password-key

### Purpose
This command is used to enable the IS-IS authentication function. After the function is enabled, IS-IS will carry authentication information in the message exchange in the area and verify the authentication information. To disable this function, please use the no area-password command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
isis password-key { clear | md5 } { 0 | 7 } text
no isis password-key
```

### Parameters
```text
clear: Encrypt in plain text.
md5: Encrypt using md5 algorithm.
0: Enter plain text.
7: Enter in cipher text.
text: Password text
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure MD5 encrypted authentication for the IS-IS on VLAN 1:
Switch(config)#interface vlan 1
Switch(config-if)#isis password-ket md5 0 tp-link
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## isis priority

### Purpose
This command is used to enable the IS-IS authentication function. After the function is enabled, IS-IS will carry authentication information in the message exchange in the area and verify the authentication information. To disable this function, please use the no area-password command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
isis priority value
no isis priority
```

### Parameters
```text
Value: The DIS election priority of the interface, ranging from 0 to 127, and the default value is 64.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set the IS-IS priority of interface VLAN 1 to 100:
Switch(config)#interface vlan 1
Switch(config-if)# isis priority 100
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## topology (2)

### Purpose
This command is used to enable IS-IS multi-topology under the interface, allowing the creation of independent logical topologies for different protocols or services. To disable this configuration, please use the no topology command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
topology { ipv6-unicast }
no topology { ipv6-unicast }
```

### Parameters
```text
ipv6-unicast: IS-IS enabled for IPv6 unicast topology.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure IS-IS multi-topology:
Switch(config)#interface vlan 1
Switch(config-if)#topology ipv6-unicast
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## isis three-way-handshake

### Purpose
This command is used to configure the three-way handshake mechanism of the IS-IS neighbor on the interface. By default, IS-IS neighbor establishment is a two-way handshake mechanism. Two-way handshakes have the problem of one-way neighbor establishment. It is recommended to use the three-way handshake mechanism. To restore the default configuration, please use the no isis three-way-handshake command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
isis three-way-handshake
no isis three-way-handshake
```

### Parameters
```text
None
```

### Default
By default, IS-IS neighbor establishment is a two-way handshake mechanism.

### Example
```text
Configure the IS-IS three-way handshake neighbor establishment mechanism on interface VLAN 1:
Switch(config)#interface vlan 1
Switch(config-if)#isis three-way-handshake
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## show isis database

### Purpose
This command is used to view the IS-IS database information.

### Command Mode
Not explicitly specified in the official documentation.

### Syntax
```text
show isis [ tag { area-name } ] database [ lsp-id | detail ]
```

### Parameters
```text
area-name: Specify the IS-IS area name for the query.
lsp-id: Specify the LSP ID for the query.
detail: View detailed informationCommand Mode
Privileged EXEC Mode and Any Configuration Mode
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the brief information of IS-IS database:
Switch#show isis database
```

### Notes
- Permission requirement: None
- Availability: Only for certain devices according to the official chapter title.

## show isis graceful-restart

### Purpose
This command is used to view the Graceful Restart information for IS-IS.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show isis [ tag { area-name } ] graceful-restart status
```

### Parameters
```text
area-name: Specify the IS-IS area name for the query.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the IS-IS Graceful Restart information:
Switch#show isis database
```

### Notes
- Permission requirement: None
- Availability: Only for certain devices according to the official chapter title.

## show isis hostname

### Purpose
This command is used to view the IS-IS host name mapping information.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show isis [ tag { area-name } ] hostnameParameter
area-name: Specify the IS-IS area name for the query.
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the IS-IS host name mapping information:
Switch# show isis hostname
```

### Notes
- Permission requirement: None
- Availability: Only for certain devices according to the official chapter title.

## show isis neighbor

### Purpose
This command is used to view the IS-IS neighbor information.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show isis [ tag { area-name } ] neighbor [ system-id | detail ]
```

### Parameters
```text
area-name: Specify the IS-IS area name for the query.
system-id: Specify the neighbor
s system ID for the query.
detail: View detailed information.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the brief information of IS-IS neighbor:
Switch# show isis neighbor
```

### Notes
- Permission requirement: None
- Availability: Only for certain devices according to the official chapter title.

## show isis route

### Purpose
This command is used to view the IS-IS routing information.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show isis [ tag { area-name } ] route
```

### Parameters
```text
None
```

### Default
Not explicitly specified in the official documentation.

### Example
Not explicitly specified in the official documentation.

### Notes
- Permission requirement: NoneExample View the IS-IS routing information: Switch# show isis route
- Availability: Only for certain devices according to the official chapter title.

## show isis summary

### Purpose
This command is used to view the IS-IS summary.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show isis [ tag { area-name } ] summary
```

### Parameters
```text
area-name: Specify the IS-IS area name for the query.
```

### Default
Not explicitly specified in the official documentation.

### Example
Not explicitly specified in the official documentation.

### Notes
- Permission requirement: NoneExample View the IS-IS summary: Switch# show isis summary
- Availability: Only for certain devices according to the official chapter title.

## show isis interface

### Purpose
This command is used to view the IS-IS interface information.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show isis [ tag { area-name } ] interface [ fastEthernet | gigabitEthernet | hundred-gigabitEthernet | loopback | port-channel | ten-gigabitEthernet | twentyFive-gigabitEthernet | two-gigabitEthernet | vlan ] [ detail ]
```

### Parameters
```text
area-name: Specify the IS-IS area name for the query.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the IS-IS interface information:
Switch# show isis interface
```

### Notes
- Permission requirement: None
- Availability: Only for certain devices according to the official chapter title.

## show isis topology

### Purpose
This command is used to view the IS-IS topology information.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show isis [ tag { area-name } ] topology [ level-1 | level-2 ]
```

### Parameters
```text
area-name: Specify the IS-IS area name for the query.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the IS-IS topology information:
Switch# show isis topology
```

### Notes
- Permission requirement: None
- Availability: Only for certain devices according to the official chapter title.
