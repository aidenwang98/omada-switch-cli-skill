# MAC Address Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 19 MAC Address Commands

Location: extracted Word text lines 11148-11535

## Chapter Notes

Official documentation states: MAC Address configuration can improve the network security by configuring the Port Security and maintaining the address information by managing the Address Table.

- Use these commands only when the requested feature and target interface/VLAN/ring/session details are clear.

## mac address-table static

### Purpose
The mac address-table static command is used to add the static MAC address entry. To remove the corresponding entry, please use no mac address-table static command. The static address can be added or removed manually, independent of the aging time. In the stable networks, the static MAC address entries can facilitate the switch to reduce broadcast packets and enhance the efficiency of packets forwarding remarkably.

### Command Mode
Global Configuration Mode

### Syntax
```text
mac address-table static mac-addr vid vid interface { fastEthernet port | gigabitEthernet port | two-gigabitEthernet port | ten-gigabitEthernet port | hundred-gigabitEthernet port }
no mac address-table static { mac-addr [vid vid] | vid vid | interface { fastEthernet port | gigabitEthernet port | hundred-gigabitEthernet port | ten-gigabitEthernet port | twentyFive-gigabitEthernet port | two-gigabitEthernet port } }
```

### Parameters
```text
mac-addr
The MAC address of the entry you desire to add.
vid
The VLAN ID number of your desired entry. It ranges from 1 to 4094.
port
The Ethernet port number of your desired entry.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Add a static Mac address entry to bind the MAC address 00:02:58:4f:6c:23, VLAN1 and port 1 together:
Switch(config)# mac address-table static 00:02:58:4f:6c:23 vid 1 interface gigabitEthernet 1/0/1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## no mac address-table dynamic

### Purpose
The no mac address-table dynamic command is used to delete the specified dynamic MAC address, or dynamic MAC addresses based on the VLAN or the port.

### Command Mode
Global Configuration Mode

### Syntax
```text
no mac address-table dynamic { mac-addr | vid vid | interface {fastEthernet port | gigabitEthernet port | two-gigabitEthernet port | ten-gigabitEthernet port } }
```

### Parameters
```text
mac-addr
The MAC address you desire to delete.
vid
The VLAN ID on which you desire to delete MAC addresses.
port
The Ethernet port on which you desire to delete MAC addresses.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Delete the MAC addresses on VLAN 1:
Switch(config)# no mac address-table dynamic vid 1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## mac address-table aging-time

### Purpose
The mac address-table aging-time command is used to configure aging time for the dynamic address. To return to the default configuration, please use no mac address-table aging-time command.

### Command Mode
Global Configuration Mode

### Syntax
```text
mac address-table aging-time aging-time
no mac address-table aging-time
```

### Parameters
```text
aging-time
The aging time for the dynamic address. The value of it can be 0 or ranges from 10 to 630 seconds. When 0 is entered, the Auto Aging function is disabled. It is 300 by default.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the aging time as 500 seconds:
Switch(config)# mac address-table aging-time 500
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## mac address-table filtering

### Purpose
The mac address-table filtering command is used to add the filtering address entry. To delete the corresponding entry, please use no mac address-table filtering command. The filtering address function is to forbid the undesired package to be forwarded. The filtering address can be added or removed manually, independent of the aging time.

### Command Mode
Global Configuration Mode

### Syntax
```text
mac address-table filtering mac-addr vid vid
no mac address-table filtering {[ mac-addr ] [ vid vid ]}
```

### Parameters
```text
mac-addr
The MAC address to be filtered.
vid
The corresponding VLAN ID of the MAC address. It ranges from 1 to 4094.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Add a filtering address entry of which VLAN ID is 1 and MAC address is 00:1e:4b:04:01:5d:
Switch(config)# mac address-table filtering 00:1e:4b:04:01:5d vid 1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## mac address-table notification

### Purpose
The mac address-table notification command is used to configure global settings of MAC address table notification.

### Command Mode
Global Configuration Mode

### Syntax
```text
mac address-table notification { [ global-status enable | disable ] [ table-full-status enable | disable ] [ interval time ] }
```

### Parameters
```text
global-status enable | disable
Enable/Disable the notification function globally.
table-full-status enable | disable
Enable/Disable the MAC threshold notification. With this feature enabled, a SNMP notification is generated and sent to the network management system (NMS) when the threshold of the switch
s MAC address table is reached or exceeded.
interval time
Specify the notification trap interval between each set of traps that are generated to the NMS. The interval ranges from 1 to 1000 seconds, and it
s 1 second by default.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the global MAC address notification and table full notification, specify the notification sending interval as 2 seconds:
Switch(config)# mac address-table notification global-status enable table-full-status enable interval 2
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Official note: This command is only available on certain devices.

## mac address-table max-mac-count

### Purpose
The mac address-table max-mac-count command is used to configure the Port Security. To return to the default configurations, please use no mac address-table max-mac-count command. Port Security is to protect the switch from the malicious MAC address attack by limiting the maximum number of the MAC addresses that can be learned on the port. The port with Port Security feature enabled will learned the MAC address dynamically. When the learned MAC address number reaches the maximum, the port will stop learning. Therefore, the other devices with the MAC address unlearned cannot access to the network via this port.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet)

### Syntax
```text
mac address-table max-mac-count { [ max-number num ] [ mode { dynamic | static | permanent } ] [ status { forward | drop | disable } ] [ exceed-max-learned enable | disable ] }
no mac address-table max-mac-count [ max-number | mode | status ]
```

### Parameters
```text
num
The maximum number of MAC addresses that can be learned on the port. It ranges from 0 to 64. By default, this value is 64.
dynamic | static | permanent
Learn mode for MAC addresses. There are three modes, including Dynamic mode, Static mode and Permanent mode. When Dynamic mode is selected, the learned MAC address will be deleted automatically after the aging time. When Static mode is selected, the learned MAC address will be out of the influence of the aging time and can only be deleted manually. The learned entries will be cleared after the switch is rebooted. When permanent mode is selected, the learned MAC address will be out of the influence of the aging time and can only be deleted manually too. However, the learned entries will be saved even the switch is rebooted.
status
Select the action to be taken when the number of the MAC addresses reaches the maximum learning number on the port. By default, this function is disabled.
forward: The packets will be forward but not be learned when learned MAC number exceeds the maximum MAC address number on this port.
drop: The packets will be dropped when learned MAC number exceeds the maximum MAC address number on this port.
disable: The MAC address threshold on this port is disabled.
exceed-max-learned enable | disable
Enable/Disable the new-mac-learned notification on this port. With this feature enabled, a SNMP notification is generated and sent to the network management system (NMS) when the port learns a new MAC address.
```

### Default
By default, this value is 64. By default, this function is disabled.

### Example
```text
Enable Port Security function for port 1/0/1, select Static mode as the learn mode, and specify the maximum number of MAC addresses that can be learned on this port as 30. When the number of MAC address entries reaches 30 on this port, new entry will be dropped:
Switch(config)# interface gigabitEthernet 1/0/1
Switch(config-if)# mac address-table max-mac-count max-number 30 mode static status drop
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## mac address-table notification (interface)

### Purpose
mac address-table notification command is used to configure the MAC change notification on port.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet)

### Syntax
```text
mac address-table notification { [ learn-mode-change enable | disable ] [ new-mac-learned enable | disable ] [ exceed-max-learned enable | disable ] }
```

### Parameters
```text
learn-mode-change enable | disable
Enable/Disable the learn-mode-change notification. With this feature enabled, a SNMP notification is generated and sent to the network management system (NMS) when the learning mode of this port changes. To configure the learning mode configuration, please refer to
mac address-table max-mac-count
new-mac-learned enable | disable
Enable/Disable the new-mac-learned notification on this port. With this feature enabled, a SNMP notification is generated and sent to the network management system (NMS) when the port learns a new MAC address.
exceed-max-learned enable | disable
Enable/Disable the new-mac-learned notification on this port. With this feature enabled, a SNMP notification is generated and sent to the network management system (NMS) when the port learns a new MAC address.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the learn-mode-change notification on port 1/0/2:
Switch(config)# mac address-table notification global-status enable
Switch(config)# interface gigabitEthernet 1/0/2
Switch(config-if)# mac address-table notification learn-mode-change enable
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Official note: This command is only available on certain devices.

## mac address-table security

### Purpose
The mac address-table security command is used to configure the maximum number of MAC address cane be learned in specified VLANs.

### Command Mode
Global Configuration Mode

### Syntax
```text
mac address-table security vid vid max-learn number { forward | drop }
```

### Parameters
```text
vid
Specify the VLAN ID to configure its MAC address table.
number
Configure the threshold of the MAC address table in this VLAN. It ranges from 0 to 16383.
forward | drop | disable
Choose the mode when learned MAC number exceeds the threshold of the MAC address table in this VLAN.
Drop: The packets will be dropped when learned MAC number exceeds the threshold of the MAC address table in this VLAN.
Forward: The packets will be forward but not be learned when learned MAC number exceeds the threshold of the MAC address table in this VLAN.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the max learned MAC address number is VLAN 2 as 1000, and drop the packets that have no match in the MAC address table:
Switch(config)# mac address-table security vid 2 max-learn 1000 drop
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Official note: This command is only available on certain devices.

## mac address-table vlan-security

### Purpose
The mac address-table security command is used to configure the maximum number of MAC address cane be learned in specified VLANs.

### Command Mode
Global Configuration Mode

### Syntax
```text
mac address-table vlan-security { vid vid max-learn number | mode { forward | drop } }
```

### Parameters
```text
vid
Specify the VLAN ID to configure its MAC address table.
number
Configure the threshold of the MAC address table in this VLAN. It ranges from 0 to 16383.
forward | drop | disable
Choose the mode when learned MAC number exceeds the threshold of the MAC address table in this VLAN.
Drop: The packets will be dropped when learned MAC number exceeds the threshold of the MAC address table in this VLAN.
Forward: The packets will be forward but not be learned when learned MAC number exceeds the threshold of the MAC address table in this VLAN.
Disable: The threshold of the MAC address table is disabled.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the max learned MAC address number is VLAN 2 as 1000:
Switch(config)# mac address-table vlan-security vid 2 max-learn 1000
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Official note: This command is only available on certain devices.

## show mac address-table

### Purpose
The show mac address-table command is used to display the information of all address entries.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show mac address-table [ { dynamic | static | filtering } ]
```

### Parameters
```text
dynamic | static | filtering
the type of your desired entry. By default, all the entries are displayed.
```

### Default
By default, all the entries are displayed.

### Example
```text
Display the information of all address entries:
Switch(config)# show mac address-table
```

### Notes
- Permission requirement: None.

## show mac address-table | exclude

### Purpose
The show mac address-table | exclude command is used to exclude lines containing specific information from the show mac address-table output, such as certain MAC addresses or ports.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show mac address-table | exclude
text
```

### Parameters
```text
text
The text to match for exclusion. Supports up to eighty matching conditions, separated by |.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Filter the show mac address-table output to exclude entries associated with ports 1/0/1 and 1/0/9:
Switch(config)# show mac address-table | exclude "1/0/1 |1/0/9"
```

### Notes
- Permission requirement: None.

## show mac address-table | include

### Purpose
The show mac address-table | include command is used to include only lines containing specific information in the show mac address-table output, such as certain MAC addresses or ports.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show mac address-table | include
text
```

### Parameters
```text
text
The text to match for inclusion. Supports up to eighty matching conditions, separated by |.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display only entries in the show mac address-table output associated with ports 1/0/1 and 1/0/9:
Switch(config)# show mac address-table | include "1/0/1 |1/0/9"
```

### Notes
- Permission requirement: None.

## clear mac address-table

### Purpose
The show mac address-table command is used to clear the specified address entries.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
clear mac address-table { dynamic | static | filtering }
```

### Parameters
```text
dynamic | static | filtering
the type of your desired entry.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Clear the information of all static address entries:
Switch(config)# clear mac address-table static
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## show mac address-table aging-time

### Purpose
The show mac address-table aging-time command is used to display the Aging Time of the MAC address.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show mac address-table aging-time
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the Aging Time of the MAC address:
Switch(config)# show mac address-table aging-time
```

### Notes
- Permission requirement: None.

## show mac address-table max-mac-count

### Purpose
The show mac address-table max-mac-count interface gigabitEthernet command is used to display the security configuration of all ports or the specified port.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show mac address-table max-mac-count { all | interface { fastEthernet port | gigabitEthernet port | hundred-gigabitEthernet port | port-channel port-channel-id | ten-gigabitEthernet port | twentyFive-gigabitEthernet port | two-gigabitEthernet port } }
```

### Parameters
```text
all
Displays the security information of all the Ethernet ports.
port
The Ethernet port number.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the security configuration of all ports:
Switch(config)# show mac address-table max-mac-count all
Display the security configuration of port 1/0/1:
Switch(config)# show mac address-table max-mac-count interface gigabitEthernet 1/0/1
```

### Notes
- Permission requirement: None.

## show mac address-table interface

### Purpose
The show mac address-table interface command is used to display the address configuration of the specified port/port channel.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show mac address-table interface { fastEthernet port | gigabitEthernet port | hundred-gigabitEthernet port | port-channel port-channel-id | ten-gigabitEthernet port | twentyFive-gigabitEthernet port | two-gigabitEthernet port }
```

### Parameters
```text
port
The Ethernet port number.
port-channel-id
The ID of the port channel.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the address configuration of port 1/0/1:
Switch(config)# show mac address-table interface gigabitEthernet 1/0/1
```

### Notes
- Permission requirement: None.

## show mac address-table count

### Purpose
The show mac address-table count command is used to display the total amount of MAC address table.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show mac address-table count [ vlan vlan-id ]
```

### Parameters
```text
vlan-id
Specify the VLAN which the MAC entries belong to.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the total MAC entry information in different VLANs:
Switch(config)# show mac address-table count
```

### Notes
- Permission requirement: None.

## show mac address-table address

### Purpose
The show mac address-table address command is used to display the information of the specified MAC address.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show mac address-table address mac-addr [ interface { fastEthernet port | gigabitEthernet port | port-channel port-channel-id } | vid vlan-id ]
```

### Parameters
```text
mac-addr
The specified MAC address.
port
The Ethernet port number.
port-channel-id
The ID of the port channel.
vlan-id
Specify the VLAN which the entry belongs to.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the information of the MAC address 00:00:00:00:23:00 in VLAN 1:
Switch(config)#show mac address-table address 00:00:00:00:23:00 vid 1
```

### Notes
- Permission requirement: None.

## show mac address-table vlan

### Purpose
The show mac address-table vlan command is used to display the MAC address configuration of the specified vlan.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show mac address-table vlan vid
```

### Parameters
```text
vid
The specified VLAN id.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the MAC address configuration of vlan 1:
Switch(config)# show mac address-table vlan 1
```

### Notes
- Permission requirement: None.

## show mac address-table notification

### Purpose
The show mac address-table notification command is used to display the MAC notification configuration globally or on the specified port.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show mac address-table notification all
```

### Parameters
```text
all
Displays the notification information globally and of all the Ethernet ports.
port
Displays the notification information on the specified port.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the notification configuration of all the ports:
Switch(config)# show mac address-table notification all
```

### Notes
- Permission requirement: None.
- Official note: This command is only available on certain devices.

## show mac address-table security

### Purpose
The show mac address-table security command is used to display the MAC address security configuration globally or of the specified VLAN.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show mac address-table security [ vid vid ]
```

### Parameters
```text
vid
The specified VLAN id.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the MAC address security configuration of VLAN 1:
Switch(config)# show mac address-table security vid 1
```

### Notes
- Permission requirement: None.
- Official note: This command is only available on certain devices.
