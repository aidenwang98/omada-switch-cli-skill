# SNMP Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 90 SNMP Commands

Location: extracted Word text lines 31162-31857

## Chapter Notes

Official documentation states: SNMP (Simple Network Management Protocol) functions are used to manage the network devices for a smooth communication, which can facilitate the network administrators to monitor the network nodes and implement the proper operation.

- Use these commands only when the requested feature and target interface/VLAN/ring/session details are clear.

## snmp-server

### Purpose
The snmp-server user command is used to add User. To delete the corresponding User, please use no snmp-server user command. The User in an SNMP Group can manage the switch via the management station software. The User and its Group have the same security level and access right.

### Command Mode
Global Configuration Mode

### Syntax
```text
snmp-server user name { local | remote } group-name [ smode v3 ] [ slev noAuthNoPriv ] [ cmode none ] [ cpwd confirm-pwd ] [ emode none ] [ epwd encrypt-pwd ]
snmp-server user name { local | remote } group-name [ smode v3 ] slev authNoPriv cmode { MD5 | SHA } cpwd confirm-pwd [ emode none] [ epwd encrypt-pwd ]
snmp-server user name { local | remote } group-name [ smode v3 ] slev authPriv cmode { MD5 | SHA } cpwd confirm-pwd emode { DES | AES-128 } epwd encrypt-pwd
```

### Parameters
```text
name
User Name, ranging from 1 to 16 characters.
local | remote
User Type, with local and remote options. Local indicates that the user is connected to a local SNMP engine, while remote means that the user is connected to a remote SNMP engine. As the remote engine ID and user password are used to compute the authentication and privacy digests, before configuring a remote user, you need to set the remote engine ID first.
group-name
The Group Name of the User. The User is classified to the corresponding Group according to its Group Name, Security Model and Security Level.
The security mode for the user. v3 indicates SNMPv3, the most secure model.
slev
The Security Level of SNMP v3 User. There are three options, including noAuthNoPriv (No authentication algorithm but a user name match is applied to check packets, and no privacy algorithm is applied to encrypt them), authNoPriv (An authentication algorithm is applied to check packets, but no privacy algorithm is applied to encrypt them) and authPriv (An authentication algorithm and a privacy algorithm are applied to check and encrypt packets). The security level from lowest to highest is: noAuthNoPriv, authNoPriv, authPriv, and the default is noAuthNoPriv. The security level of the user should not be lower than the group it belongs to.
cmode
The Authentication Mode of the SNMP v3 User, with none, MD5 and SHA options. None indicates no authentication method is used, MD5 indicates the port authentication is performed via HMAC-MD5 algorithm and SHA indicates the port authentication is performed via SHA (Secure Hash Algorithm). SHA authentication mode has a higher security than MD5 mode. By default, the Authentication Mode is
none
confirm-pwd
Authentication Password, ranging from 1 to 32 characters. The question marks and spaces are not allowed. This password in the configuration file will be displayed in the symmetric encrypted form.
emode
The Privacy Mode of the SNMP v3 User, with none, DES and AES-128 options. None indicates no privacy method is used, and DES indicates DES encryption method is used, and AES-128 indicates AES-128 encryption method is used. By default, the Privacy Mode is
none
encrypt-pwd
Privacy Password, ranging from 1 to 32 characters. The question marks and spaces are not allowed. This password in the configuration file will be displayed in the symmetric encrypted form.
```

### Default
By default, the Authentication Mode is none confirm-pwd Authentication Password, ranging from 1 to 32 characters. By default, the Privacy Mode is none encrypt-pwd Privacy Password, ranging from 1 to 32 characters.

### Example
```text
Add Local User admin to Group group2, and configure the Security Model of the user as v3, the Security Level of the group as authPriv, the Authentication Mode of the user as MD5, the Authentication Password as 11111, the Privacy Mode as DES, and the Privacy Password as 22222:
Switch(config)# snmp-server user admin local group2 smode v3 slev authPriv cmode MD5 cpwd 11111 emode DES epwd 22222
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## snmp-server view

### Purpose
The snmp-server view command is used to add View. To delete the corresponding View, please use no snmp-server view command. The OID (Object Identifier) of the SNMP packets is used to describe the managed objects of the switch, and the MIB (Management Information Base) is the set of the OIDs. The SNMP View is created for the SNMP management station to manage MIB objects.

### Command Mode
Global Configuration Mode

### Syntax
```text
snmp-server view name mib-oid { include | exclude }
no snmp-server view name mib-oid
```

### Parameters
```text
name
The entry name of View, ranging from 1 to 16 characters. Each View includes several entries with the same name.
mib-oid
MIB Object ID. It is the Object Identifier (OID) for the entry of View, ranging from 1 to 61 characters.
include | exclude
View Type, with include and exclude options. They represent the view entry can/cannot be managed by the SNMP management station individually.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Add a View named view1, configuring the OID as 1.3.6.1.6.3.20, and this OID can be managed by the SNMP management station:
Switch(config)# snmp-server view view1 1.3.6.1.6.3.20 include
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## snmp-server group

### Purpose
The snmp-server group command is used to manage and configure the SNMP group. To delete the corresponding SNMP group, please use no snmp-server group command. SNMP v3 provides the VACM (View-based Access Control Model) and USM (User-Based Security Model) mechanisms for authentication. The users in the SNMP Group can manage the device via the Read View, Write View and Notify View. And the authentication mode and the privacy mode guarantee the high security for the communication between the management station and the managed device.

### Command Mode
Global Configuration Mode

### Syntax
```text
snmp-server group name [ smode v3 ] [ slev { noAuthNoPriv | authNoPriv | authPriv }] [ read read-view ] [ write write-view ] [ notify notify-view ]
no snmp-server group name smode v3 slev { noAuthNoPriv | authNoPriv | authPriv }
```

### Parameters
```text
name
The SNMP Group name, ranging from 1 to 16 characters. The Group Name, Security Model and Security Level compose the identifier of the SNMP Group. These three items of the Users in one group should be the same.
The security mode for the group, v3 indicates SNMPv3, the most secure level.
slev
The Security Level of SNMP v3 Group. There are three options, including noAuthNoPriv (No authentication algorithm but a user name match is applied to check packets, and no privacy algorithm is applied to encrypt them), authNoPriv (An authentication algorithm is applied to check packets, but no privacy algorithm is applied to encrypt them) and authPriv (An authentication algorithm and a privacy algorithm are applied to check and encrypt packets). By default, the Security Level is noAuthNoPriv. There is no need to configure this in SNMP v1 Mode and SNMP v2c Mode.
read-view
Select the View to be the Read View. The management access is restricted to read-only, and changes cannot be made to the assigned SNMP View.
write-view
Select the View to be the Write View. The management access is writing only and changes can be made to the assigned SNMP View. The View defined both as the Read View and the Write View can be read and modified.
notify-view
Select the View to be the Notify View. The management station can receive notification messages of the assigned SNMP view generated by the switch's SNMP agent.
```

### Default
By default, the Security Level is noAuthNoPriv.

### Example
```text
Add a group, and configure the name as group 1, the Security Model as SNMP v3, the security level as authNoPriv, the management access to the assigned View viewDefault as read-write, besides the notification messages sent by View viewDefault can be received by Management station:
Switch(config)# snmp-server group group1 smode v3 slev authNoPriv read viewDefault write viewDefault notify viewDefault
Delete group 1:
Switch(config)# no snmp-server group group1 smode v3 slev authNoPriv
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## snmp-server user

### Purpose
The snmp-server user command is used to add User. To delete the corresponding User, please use no snmp-server user command. The User in an SNMP Group can manage the switch via the management station software. The User and its Group have the same security level and access right.

### Command Mode
Global Configuration Mode

### Syntax
```text
For L2/L2+ switches:
snmp-server user name { local | remote } group-name [ smode v3 ] [ slev noAuthNoPriv ] [ cmode none ] [ cpwd confirm-pwd ] [ emode none ] [ epwd encrypt-pwd ]
snmp-server user name { local | remote } group-name [ smode v3 ] slev authNoPriv cmode { MD5 | SHA } cpwd confirm-pwd [ emode none] [ epwd encrypt-pwd ]
snmp-server user name { local | remote } group-name [ smode v3 ] slev authPriv cmode { MD5 | SHA } cpwd confirm-pwd emode { DES | AES-128 } epwd encrypt-pwd
no snmp-server user name
For L3 switches:
snmp-server user name { local | remote } group-name [ smode v3 ] [ slev noAuthNoPriv ]
snmp-server user name { local | remote } group-name [ smode v3 ] slev authNoPriv cmode { MD5 | SHA } cpwd confirm-pwd
snmp-server user name { local | remote } group-name [ smode v3 ] slev authPriv cmode { MD5 | SHA } cpwd confirm-pwd emode { DES | AES-128 } epwd encrypt-pwd
no snmp-server user name
```

### Parameters
```text
name
User Name, ranging from 1 to 16 characters.
local | remote
User Type, with local and remote options. Local indicates that the user is connected to a local SNMP engine, while remote means that the user is connected to a remote SNMP engine. As the remote engine ID and user password are used to compute the authentication and privacy digests, before configuring a remote user, you need to set the remote engine ID first.
group-name
The Group Name of the User. The User is classified to the corresponding Group according to its Group Name, Security Model and Security Level.
The security mode for the user. v3 indicates SNMPv3, the most secure model.
slev
The Security Level of SNMP v3 User. There are three options, including noAuthNoPriv (No authentication algorithm but a user name match is applied to check packets, and no privacy algorithm is applied to encrypt them), authNoPriv (An authentication algorithm is applied to check packets, but no privacy algorithm is applied to encrypt them) and authPriv (An authentication algorithm and a privacy algorithm are applied to check and encrypt packets). The security level from lowest to highest is: noAuthNoPriv, authNoPriv, authPriv, and the default is noAuthNoPriv. The security level of the user should not be lower than the group it belongs to.
cmode
The Authentication Mode of the SNMP v3 User, with none, MD5 and SHA options. None indicates no authentication method is used, MD5 indicates the port authentication is performed via HMAC-MD5 algorithm and SHA indicates the port authentication is performed via SHA (Secure Hash Algorithm). SHA authentication mode has a higher security than MD5 mode. By default, the Authentication Mode is
none
confirm-pwd
Authentication Password, ranging from 1 to 16 characters. The question marks and spaces are not allowed. This password in the configuration file will be displayed in the symmetric encrypted form.
emode
The Privacy Mode of the SNMP v3 User, with none DES and AES-128 options. None indicates no privacy method is used, and DES indicates DES encryption method is used, and AES-128 indicates AES-128 encryption method is used, AES-128 privacy mode has a higher security than DES mode.By default, the Privacy Mode is
none
encrypt-pwd
Privacy Password, ranging from 1 to 32 characters. The question marks and spaces are not allowed. This password in the configuration file will be displayed in the symmetric encrypted form.
```

### Default
By default, the Authentication Mode is none confirm-pwd Authentication Password, ranging from 1 to 16 characters. By default, the Privacy Mode is none encrypt-pwd Privacy Password, ranging from 1 to 32 characters.

### Example
```text
Add Local User admin to Group group2, and configure the Security Model of the user as v3, the Security Level of the group as authPriv, the Authentication Mode of the user as MD5, the Authentication Password as 11111, the Privacy Mode as DES, and the Privacy Password as 22222:
Switch(config)# snmp-server user admin local group2 smode v3 slev authPriv cmode MD5 cpwd 11111 emode AES-128 epwd 2222
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## snmp-server community

### Purpose
The snmp-server community command is used to add Community. To delete the corresponding Community, please use no snmp-server community command. SNMP v1 and SNMP v2c adopt community name authentication. The community name can limit access to the SNMP agent from SNMP network management station, functioning as a password.

### Command Mode
Global Configuration Mode

### Syntax
```text
snmp-server community name { read-only | read-write } mib-view
no snmp-server community name
```

### Parameters
```text
name
Community Name, ranging from 1 to 16 characters.
read-only | read-write
The access rights of the community, with read-only and read-write options.
mib-view
The MIB View for the community to access.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Add community public, and the community has read-write management right to View viewDefault:
Switch(config)# snmp-server community public read-write viewDefault
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## snmp-server host

### Purpose
The snmp-server host command is used to add Notification. To delete the corresponding Notification, please use no snmp-server host command.

### Command Mode
Global Configuration Mode

### Syntax
```text
snmp-server host ip udp-port user-name [vrf vrfName] [ smode { v1 | v2c | v3 }] [ slev { noAuthNoPriv | authNoPriv | authPriv }] [ type { trap | inform }] [ retries retries ] [ timeout timeout ]
no snmp-server host ip user-name
```

### Parameters
```text
The IP Address of the management Host. Both IPv4 and IPv6 addresses are supported, for example 192.168.0.100 or fe80::1234.
udp-port
UDP port, which is used to send notifications. The UDP port functions with the IP address for the notification sending. It ranges from 1 to 65535.
user-name
The User name of the management station.
vrfName
The name of the VRF instance where the administrator is located.
smode
The Security Model of the management station, with v1, v2c and v3 options. By default, the option is v1.
slev
The Security Level of SNMP v3 User. There are three options, including noAuthNoPriv (No authentication algorithm but a user name match is applied to check packets, and no privacy algorithm is applied to encrypt them), authNoPriv (An authentication algorithm is applied to check packets, but no privacy algorithm is applied to encrypt them) and authPriv (An authentication algorithm and a privacy algorithm are applied to check and encrypt packets). By default, the Security Level is noAuthNoPriv.
type
The type of the notifications, with trap and inform options. Trap indicates traps are sent, while inform indicates informs are sent. The inform type has a higher security than the trap type and resend and timeout need to be configured if you select this option. You can only select the trap type in Security Model v1. By default, the type of the notifications is
trap
retries
The amount of times the switch retries an inform request, ranging from 1 to 255. The switch will resend the inform request if it doesn
t get the response from the management station during the Timeout interval, and it will terminate resending the inform request if the resending times reach the specified Retry times.
timeout
The maximum time for the switch to wait for the response from the management station before resending a request, ranging from 1 to 3600 in seconds.
```

### Default
By default, the option is v1. By default, the Security Level is noAuthNoPriv. By default, the type of the notifications is trap retries The amount of times the switch retries an inform request, ranging from 1 to 255.

### Example
```text
Add a Notification entry, and configure the IP address of the management Host as 192.168.0.146, the UDP port as 162, the User name of the management station as admin, the Security Model of the management station as v2c, the type of the notifications as inform, the maximum time for the switch to wait as 1000 seconds, and the retries time as 100:
For L2/L2+ switches:
Switch(config)#snmp-server host 192.168.0.146 162 admin smode v2c type inform retries 100 timeout 1000
For L3 switches:
Switch(config)#snmp-server host 192.168.0.146 162 admin smode v2c slev noAuthNoPriv type inform retries 100 timeout 1000
Switch(config)#snmp-server host fe80::1234 162 admin smode v2c slev noAuthNoPriv type inform retries 100 timeout 1000
Add a Notification entry, and configure the IP Address of the management Host as fe80::1234, the UDP port as 162, the User name of the management station as admin, the Security Model of the management station as v2c, the type of the notifications as inform, the maximum time for the switch to wait as 1000 seconds, and the retries time as 100:
Switch(config)# snmp-server host fe80::1234 162 admin smode v2c type inform retries 100 timeout 1000
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## snmp-server source-interface

### Purpose
The snmp-server source-interface command is used to configure the source interface for sending SNMP trap messages. By default, no source interface is specified for sending traps. After specifying a source interface, the IP address of the source interface will be used as the source IP address of trap messages, helping network management systems identify the alarm source. The source interface for sending traps must be a Layer 3 interface with a configured IP address; otherwise, the command will not take effect. For device security, it is recommended to configure the loopback address as the source interface. To remove this configuration, please use the no snmp-server source-interface command.

### Command Mode
Global Configuration Mode

### Syntax
```text
snmp-server source-interface [ gigabitEthernet port | port-channel port-channel-id |loopback id | vlan vlan-id ]
no snmp-server source-interface
```

### Parameters
```text
port
The port number.
port-channel-id
The ID of the port channel. Member ports in this port channel should all be routed ports.
The loopback interface ID.
vlan-id
The VLAN interface ID.
```

### Default
By default, no source interface is specified for sending traps.

### Example
```text
Configure the source interface for SNMP traps as the IP address of loopback 1:
Switch(config)# snmp-server source-interface loopback 1
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## snmp-server engineID

### Purpose
The snmp-server engineID command is used to configure the local and remote engineID of the switch. To restore to the default setting, please use no snmp-server engineID command.

### Command Mode
Global Configuration Mode

### Syntax
```text
snmp-server engineID { [ local local-engineID ] [ remote remote-engineID ] }
no snmp-server engineID
```

### Parameters
```text
local-engineID
Local Engine ID for local clients. The Engine ID is a unique alphanumeric string used to identify the SNMP engine on the switch. Its length ranges from 10 to 64 hexadecimal characters, which must be even number meanwhile.
remote-engineID
Remote Engine ID for the switch. The Engine ID is a unique alphanumeric string used to identify the SNMP engine on the remote device which receives informs from the switch. Its length ranges from 10 to 64 hexadecimal characters, which must be even number meanwhile. The snmp-server engineID will be disabled if the local and remote are both not configured.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Specify the local engineID as 1234567890, and the remote engineID as abcdef123456:
Switch(config)# snmp-server engineID local 1234567890
Switch(config)# snmp-server engineID remote abcdef123456
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## snmp-server traps snmp

### Purpose
The snmp-server traps snmp command is used to enable SNMP standard traps which include four types: linkup, linkdown, warmstart and coldstart. The command without parameter enables all SNMP standard traps. All SNMP standard traps are enabled by default. To disable the sending of SNMP standard traps, please use no snmp-server traps snmp command.

### Command Mode
Global Configuration Mode

### Syntax
```text
snmp-server traps snmp [ linkup | linkdown | warmstart | coldstart | auth-failure ]
no snmp-server traps snmp [ linkup | linkdown | warmstart | coldstart | auth-failure ]
```

### Parameters
```text
linkup
Indicates a port status changes from linkdown to linkup, and can be triggered when you connect a device to a port.
linkdown
Indicates a port status changes from linkup to linkdown, and can be triggered when you disconnect a device to a port.
warmstart
Indicates the SNMP feature on the switch is reinitialized with the physical configuration unchanged. The trap can be triggered if you disable and then enable SNMP after the SNMP is completely configured and enabled.
coldstart
Indicates an SNMP initialization caused by the reinitialization of the switch system. The trap can be triggered when you reboot the switch.
auth-failure
Triggered when a received SNMP request fails the authentication.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable SNMP standard linkup trap for the switch:
Switch(config)# snmp-server traps snmp linkup
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## snmp-server traps

### Purpose
The snmp-server traps command is used to enable SNMP extended traps. To disable the sending of SNMP extended traps, please use no snmp-server traps command. All SNMP extended traps are disabled by default.

### Command Mode
Global Configuration Mode

### Syntax
```text
snmp-server traps { rate-limit | cpu | flash | lldp remtableschange | lldp topologychange | loopback-detection | storm-control | spanning-tree | memory }
no snmp-server traps { rate-limit | cpu | flash | lldp remtableschange | lldp topologychange | loopback-detection | storm-control | spanning-tree | memory }
```

### Parameters
```text
rate-limit
Monitors whether the bandwidth has reached the limit you have set. The trap can be triggered when the Rate Limit feature is enabled and packets are sent to the port with a rate higher than what you have set.
cpu
Monitors the load status of the switch CPU. The trap can be triggered when the utilization rate of the CPU has exceeded the limit that you have set. The limit of CPU utilization rate for the switch is 80% by default.
flash
Triggered when flash is modified during operations such as backup, reset, firmware upgrade, configuration import, and so on.
lldp remtableschange
An lldp RemTablesChange notification is sent when the value of lldp StatsRemTableLastChangeTime changes. It can be utilized by an NMS host to trigger LLDP remote systems table maintenance polls.
lldp topologychange
A notification generated by the local device to sense the change in the topology that indicates a new remote device attached to a local port, or a remote device disconnected or moved from one port to another.
loopback-detection
The feature is used to detect loopbacks. And the trap is disabled by default. The system will generate the trap when a loopback is detected or cleared.
storm-control
The feature is used to monitor network storms. And the trap is disabled by default. The system will generate the trap when the rate of broadcast or multicast reaches the limit of storm control.
spanning-tree
The feature is used to monitor the spanning tree status. And the trap is disabled by default. The system will generate the trap in the following situations: a port changes from non-forwarding state to forwarding state or the other way round; a port receives a packet with TC flag or a TCN packet.
memory
The feature is used to monitor the memory. And the trap is disabled by default. The system will generate the trap when the memory utilization exceeds 80%.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable SNMP extended rate-limit trap for the switch:
Switch(config)# snmp-server traps rate-limit
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## snmp-server traps ddm

### Purpose
The snmp-server traps ddm command is used to enable the corresponding DDM traps. DDM function is used to monitor the status of the SFP modules inserted into the SFP ports on the switch. The command without parameter enables all SNMP DDM traps. To disable the sending of SNMP DDM traps, use no snmp-server traps ddm command. All DDM traps are disabled by default.

### Command Mode
Global Configuration Mode

### Syntax
```text
snmp-server traps ddm [ temperature | voltage | bias_current | tx_power | rx_power ]
no snmp-server traps ddm [ temperature | voltage | bias_current | tx_power | rx_power ]
```

### Parameters
```text
temperature
Monitors the temperature of SFP modules inserted into the SFP ports on the switch. The trap can be triggered when the temperature of any SFP module has reached the warning or alarm threshold.
voltage
Monitors the voltage of SFP modules inserted into the SFP ports on the switch. The trap can be triggered when the voltage of any SFP module has reached the warning or alarm threshold.
bias_current
Monitors the bias current of SFP modules inserted into the SFP ports on the switch. The trap can be triggered when the bias current of any SFP module has reached the warning or alarm threshold.
tx_power
Monitors the TX Power of SFP modules inserted into the SFP ports on the switch. The trap can be triggered when the TX Power of any SFP module has reached the warning or alarm threshold.
rx_power
Monitors the RX Power of SFP modules inserted into the SFP ports on the switch. The trap can be triggered when the RX Power of any SFP module has reached the warning or alarm threshold.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable all the SNMP DDM traps for the switch:
Switch(config)# snmp-server traps ddm
```

### Notes
- User guidelines: The snmp-server traps ddm command without any parameter is used to enable all the types of DDM traps. And the no snmp-server traps ddm command without any parameter is used to disable all the types of DDM traps. For more instructions about the alarm threshold or warning threshold, refer to Chapter 11 DDM Commands
- Official note: This command is only available on certain devices.

## snmp-server traps vlan

### Purpose
The snmp-server traps vlan command is used to enable the corresponding VLAN traps. The command without parameter enables all SNMP VLAN traps. To disable this function, please use no snmp-server traps vlan command. All VLAN traps are disabled by default.

### Command Mode
Global Configuration Mode

### Syntax
```text
snmp-server traps vlan [ create | delete ]
no snmp-server traps vlan [create | delete ]
```

### Parameters
```text
create
Triggered when certain VLANs are created successfully.
delete
Triggered when certain VLANs are deleted successfully.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable all SNMP extended VLAN-related traps for the switch:
Switch(config)# snmp-server traps vlan
Enable VLAN-created trap only for the switch:
Switch(config)# snmp-server traps vlan create
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## snmp-server traps security

### Purpose
The snmp-server traps security command is used to enable the corresponding security traps. To disable this feature, please use no snmp-server traps security command. All security traps are disabled by default.

### Command Mode
Global Configuration Mode

### Syntax
```text
snmp-server traps security { dhcp-filter | ip-mac-binding }
no snmp-server traps security { dhcp-filter | ip-mac-binding }
```

### Parameters
```text
dhcp-filter
Triggered when the DHCPv4 Filter feature is enabled and the switch receives DHCP packets from an illegal DHCP server.
ip-mac-binding
Triggered when the ARP Inspection feature is enabled and the switch receives an illegal ARP packet, or the IPv4 Source Guard feature is enabled and the switch receives an illegal IP packet.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the DHCP filter trap for the switch:
Switch(config)# snmp-server traps security dhcp-filter
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## snmp-server traps security dhcp6-filter

### Purpose
The snmp-server traps security dhcp6-filter command is used to enable the IPv6 DHCP Filter illegal message snmp trap and log function. To disable this function, please use no snmp-server traps security dhcp6-filter command. All security traps are disabled by default.

### Command Mode
Global Configuration Mode

### Syntax
```text
snmp-server traps security dhcp6-filter
no snmp-server traps security dhcp6-filter
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the IPv6 DHCP Filter illegal message snmp trap and log function:
Switch(config)# snmp-server traps security dhcp6-filter
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## snmp-server traps acl

### Purpose
The snmp-server traps acl command is used to enable the ACL trap. To disable this feature, please use no snmp-server traps acl command. It is disabled by default. The trap monitors matched ACL information, including the matched ACL ID, rule ID and the number of the matched packets. With both this trap and the Logging feature in ACL rule settings enabled, the switch will check the matched ACL information every five minutes and send SNMP traps if there is any updated information.

### Command Mode
Global Configuration Mode

### Syntax
```text
snmp-server traps acl
no snmp-server traps acl
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the ACL trap for the switch:
Switch(config)# snmp-server traps acl
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## snmp-server traps ip

### Purpose
The snmp-server traps ip command is used to enable IP traps. To disable this feature, please use no snmp-server traps ip command. All IP traps are disabled by default.

### Command Mode
Global Configuration Mode

### Syntax
```text
snmp-server traps ip { change | duplicate }
no snmp-server traps ip { change | duplicate }
```

### Parameters
```text
change
Enable SNMP IP change traps. The trap monitors the IP changed of each interface. The trap can be triggered when the IP address of any interface is changed.
duplicate
Enable SNMP IP duplicate traps. The trap can be triggered when the switch detects an IP conflict event.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the IP-Change trap for the switch:
Switch(config)# snmp-server traps ip change
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## snmp-server traps power (Only for Certain Devices)

### Purpose
The snmp-server traps power command is used to enable PoE traps. The command without parameter enables all PoE traps. To disable this feature, please use no snmp-server traps power command. All PoE traps are disabled by default.

### Command Mode
Global Configuration Mode

### Syntax
```text
snmp-server traps power [over-max-pwr-budget | port-pwr-change | port-pwr-deny | port-pwr-over-30w | port-pwr-overload | port-short-circuit | thermal-shutdown ]
no snmp-server traps power [over-max-pwr-budget | port-pwr-change | port-pwr-deny | port-pwr-over-30w | port-pwr-overload | port-short-circuit | thermal-shutdown ]
```

### Parameters
```text
over-max-pwr-budget
Triggered when the total power required by the connected PDs exceeds the maximum power the PoE switch can supply.
port-pwr-change
Triggered when the total power required by the connected PDs exceeds the maximum power the PoE switch can supply.
port-pwr-deny
Triggered when the switch powers off PDs on low-priority PoE ports. When the total power required by the connected PDs exceeds the system power limit, the switch will power off PDs on low-priority PoE ports to ensure stable running of the other PDs.
port-pwr-over-30w
Triggered when the power required by the connected PD exceeds 30 watts.
port-pwr-overload
Triggered when the power required by the connected PD exceeds the maximum power the port can supply.
port-short-circuit
Triggered when a short circuit is detected on a port.
thermal-shutdown
Triggered when the PSE chip overheats. The switch will stop supplying power in this case.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable all PoE traps for the switch:
Switch(config)# snmp-server traps power
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- Official note: This command is only available on certain devices

## snmp-server traps link-status

### Purpose
The snmp-server traps link-status command is used to enable SNMP link status trap for the specified port. To disable the sending of SNMP link status trap, please use no snmp-server traps link-status command. By default, it is enabled.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet)

### Syntax
```text
snmp-server traps link-status
no snmp-server traps link-status
```

### Parameters
No parameters.

### Default
By default, it is enabled.

### Example
```text
Enable SNMP link status trap for port 3:
Switch(config)# interface gigabitEthernet 1/0/3
Switch(config-if)# snmp-server traps link-status
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## rmon history

### Purpose
The rmon history command is used to configure the history sample entry. To return to the default configuration, please use no rmon history command. RMON (Remote Monitoring), basing on SNMP architecture, functions to monitor the network. History Group is one of the commonly used RMON Groups. After a history group is configured, the switch collects network statistics information periodically, based on which the management station can monitor network effectively.

### Command Mode
Global Configuration Mode

### Syntax
```text
rmon history index interface gigabitEthernet port [ interval interval ] [ owner owner-name ] [ buckets number ]
no rmon history index
```

### Parameters
```text
index
The index number of the entry, ranging from 1 to 12, in the format of 1-3,5.
port
The Ethernet port number.
interval
The interval to take samplings from the port, ranging from 10 to 3600 in seconds. By default, it is 1800.
owner-name
The owner of the history sample entry, ranging from 1 to 16 characters. By default, it is
monitor
number
The maximum number of buckets desired for the RMON history group of statistics, ranging from 1 to 130. The default is 50 buckets.
```

### Default
By default, it is 1800. By default, it is monitor number The maximum number of buckets desired for the RMON history group of statistics, ranging from 1 to 130.

### Example
```text
Configure the sample port as Gi1/0/2 and the sample interval as 100 seconds for the entry 1-3:
Switch(config)# rmon history 1-3 interface gigabitEthernet 1/0/2 interval 100 owner owner1
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## rmon event

### Purpose
The rmon event command is used to configure the entries of SNMP-RMON Event. To return to the default configuration, please use no rmon event command. Event Group, as one of the commonly used RMON Groups, is used to define RMON events. Alarms occur when an event is detected.

### Command Mode
Global Configuration Mode

### Syntax
```text
rmon event index [ user user-name ] [ description descript ] [ type { none | log | notify | log-notify }] [ owner owner-name ]
no rmon event index
```

### Parameters
```text
index
The index number of the event entry, ranging from 1 to 12. You can only select one entry for each command.
user-name
The name of the User to which the event belongs, ranging from 1 to 16 characters. By default, it is
public
descript
The description of the event, ranging from 1 to 16 characters. By default, it is empty.
type
The event type, with none, log, notify and both options. None indicates no processing, log indicates logging the event, notify indicates sending trap messages to the management station, and both indicates logging the event and sending trap messages to the management station.
owner-name
The owner of the event entry, ranging from 1 to 16 characters. By default, it is
monitor
```

### Default
By default, it is public descript The description of the event, ranging from 1 to 16 characters. By default, it is empty.

### Example
```text
Configure the user name of entry 1, 2, 3 and 4 as user1, the description of the event as description1, the type of event as log and the owner of the event as owner1:
Switch(config)# rmon event 1-4 user user1 description description1 type log owner owner1
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## rmon alarm

### Purpose
The rmon alarm command is used to configure SNMP-RMON Alarm Management. To return to the default configuration, please use no rmon alarm command. Alarm Group is one of the commonly used RMON Groups. RMON alarm management allows monitoring the specific alarm variables. When the value of a monitored variable exceeds the threshold, an alarm event is generated, which triggers the switch to act in the set way.

### Command Mode
Global Configuration Mode

### Syntax
```text
rmon alarm index { stats-index sindex } [ alarm-variable { revbyte | revpkt | bpkt | mpkt | crc-lign | undersize | oversize | jabber | collision | 64 | 65-127 | 128-511 | 512-1023 | 1024-10240 }] [ s-type { absolute | delta} ] [ rising-threshold r-hold ] [ rising-event-index r-event] [ falling-threshold f-hold] [ falling-event-index f-event] [ a-type {rise | fall | all} ] [ owner owner-name ] [ interval interval]
no rmon alarm index
```

### Parameters
```text
index
The index number of the Alarm Management entry, ranging from 1 to 12, in the format of 1-3,5.
sindex
Specify the statistics index.
alarm-variable
The alarm variable. By default, the option is revbyte.
s-type
Sample Type, which is the sampling method for the selected variable and comparing the value against the thresholds. There are two options, absolute and delta. Absolute indicates comparing the values directly with the thresholds at the end of the sampling interval. Delta indicates subtracting the last sampled value from the current value, and then comparing the difference in the values with the threshold. By default, the Sample Type is absolute.
r-hold
The rising counter value that triggers the Rising Threshold alarm, ranging from 1 to 2147483647. By default, it is 100.
r-event
Rise Event, which is the index of the corresponding event which will be triggered if the sampled value is larger than the Rising Threshold. It ranges from 1 to 12.
f-hold
The falling counter value that triggers the Falling Threshold alarm, ranging from 1 to 2147483647. By default, it is 100.
f-event
Fall Event, which is the index of the corresponding event which will be triggered if the sampled value is lower than the Falling Threshold. It ranges from 1 to 12.
a-type
Alarm Type, with rise, fall and all options. Rise indicates that the alarm event will be triggered when the sampled value exceeds the Rising Threshold, fall indicates that the alarm event will be triggered when the sampled value is under the Falling Threshold, and all indicates that the alarm event will be triggered either the sampled value exceeds the Rising Threshold or is under the Falling Threshold. By default, the Alarm Type is all.
owner-name
The owner of the entry, ranging from 1 to 16 characters. By default, it is monitor.
interval
The alarm interval time, ranging from 10 to 3600 in seconds. By default, it is 1800.
```

### Default
By default, the option is revbyte. By default, the Sample Type is absolute. By default, it is 100. By default, it is 100. By default, the Alarm Type is all. By default, it is monitor. By default, it is 1800.

### Example
```text
Configure rmon alarm entries 1-3 binding with statistics entry 2, the owners as owner1 and the alarm intervals as 100 seconds:
Switch(config)#rmon alarm 1-3 stats-index 2 owner owner1 interval 100
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## rmon statistics

### Purpose
The rmon statistics command is used to configure the entries of SNMP-RMON statistics. To delete the corresponding entry, please use no rmon statistics command. The maximum supported entries are 1000.

### Command Mode
Global Configuration Mode

### Syntax
```text
rmon statistics index interface gigabitEthernet port [ owner owner-name] [ status { underCreation | valid }]
no rmon statistics index
```

### Parameters
```text
index
The index number of the statistics entry, ranging from 1 to 65535, in the format of 1-3,5.
port
The statistics port number, in the format of 1/0/1.
owner-name
The creator of the event entry, ranging from 1 to 16 characters. By default, it is
monitor
status
The status of the statistics entry, either
underCreation
or
valid
underCreation
means this entry won
t take effect until it is modified to
valid
valid
means this entry takes effect immediately after it is created.
```

### Default
By default, it is monitor status The status of the statistics entry, either underCreation or valid underCreation means this entry won t take effect until it is modified to valid valid means this entry takes effect immediately after it is created.

### Example
```text
Configure the statistics entries 1-3 with the statistics port as 1/0/1, owner as owner1 and status as valid:
Switch(config)#rmon statistics 1-3 interface gigabitEthernet 1/0/1 owner owner1 status valid
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## show snmp-server

### Purpose
The show snmp-server command is used to display SNMP configuration globally.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show snmp-server
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display SNMP configuration globally:
Switch# show snmp-server
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## show snmp-server view

### Purpose
The show snmp-server view command is used to display the View table.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show snmp-server view
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the View table:
Switch# show snmp-server view
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## show snmp-server group

### Purpose
The show snmp-server group command is used to display the Group table.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show snmp-server group
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the Group table:
Switch# show snmp-server group
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## show snmp-server user

### Purpose
The show snmp-server user command is used to display the User table.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show snmp-server user
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the User table:
Switch# show snmp-server user
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## show snmp-server community

### Purpose
The show snmp-server community command is used to display the Community table.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show snmp-server community
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the Community table:
Switch# show snmp-server community
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## show snmp-server host

### Purpose
The show snmp-server host command is used to display the Host table.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show snmp-server host
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the Host table:
Switch# show snmp-server host
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## show snmp-server engineID

### Purpose
The show snmp-server engineID command is used to display the engineID of the SNMP.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show snmp-server engineID
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the engineID:
Switch# show snmp-server engineID
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## show rmon history

### Purpose
The show rmon history command is used to display the configuration of the history sample entry.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show rmon history [ index ]
```

### Parameters
```text
index
The index number of the entry selected to display the configuration, ranging from 1 to 12, in the format of 1-3, 5. You can select more than one entry for each command. By default, the configuration of all history sample entries is displayed.
```

### Default
By default, the configuration of all history sample entries is displayed.

### Example
```text
Display the configuration of all history sample entries:
Switch# show rmon history
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## show rmon event

### Purpose
The show rmon event command is used to display the configuration of SNMP-RMON Event.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show rmon event [ index ]
```

### Parameters
```text
index
The index number of the entry selected to display the configuration, ranging from 1 to 12, in the format of 1-3, 5. You can select more than one entry for each command. By default, the configuration of all SNMP-RMON enabled entries is displayed.
```

### Default
By default, the configuration of all SNMP-RMON enabled entries is displayed.

### Example
```text
Display the Event configuration of entry1-4:
Switch# show rmon event 1-4
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## show rmon alarm

### Purpose
The show rmon alarm command is used to display the configuration of the Alarm Management entry.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show rmon alarm [ index ]
```

### Parameters
```text
index
The index number of the entry selected to display the configuration, ranging from 1 to 12, in the format of 1-3, 5. You can select more than one entry for each command. By default, the configuration of all Alarm Management entries is displayed.
```

### Default
By default, the configuration of all Alarm Management entries is displayed.

### Example
```text
Display the configuration of the Alarm Management entry 1-2:
Switch# show rmon alarm 1-2
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## show rmon statistics

### Purpose
The show rmon statistics command is used to display the configuration of the specified statistics entry.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show rmon statistics [ index ]
```

### Parameters
```text
index
The index number of the statistics entry selected to display the configuration, ranging from 1 to 65535. By default, the configuration of all statistics entries is displayed.
```

### Default
By default, the configuration of all statistics entries is displayed.

### Example
```text
Display the configuration of the statistics entry 1:
Switch#show rmon statistics 1
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
