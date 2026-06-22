# ARP Inspection Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 93 ARP Inspection Commands

Location: extracted Word text lines 32197-32411

## Chapter Notes

Official documentation states: ARP (Address Resolution Protocol) Detect function is to protect the switch from the ARP cheating, such as the Network Gateway Spoofing and Man-In-The-Middle Attack, etc.

- Use these commands only when the requested feature and target interface/VLAN/ring/session details are clear.

## ip arp inspection

### Purpose
The ip arp inspection command is used to enable the ARP Detection function globally. To disable the ARP Detection function, please use no ip arp detection command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip arp inspection
no ip arp inspection
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the ARP Detection function globally:
Switch(config)#ip arp inspection
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip arp inspection validate

### Purpose
The ip arp inspection validate command is used to enable the switch to check whether the reveided ARP packet is illegal. To disable,the feature please use no ip arp detection validate command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip arp inspection validate { src-mac | dst-mac | ip }
no ip arp inspection validate { src-mac | dst-mac | ip }
src-mac
Enable the switch to check whether the source MAC address and the sender MAC address are the same when receiving an ARP packet. If not, the ARP packet will be discarded.
dst-mac
Enable the switch to check whether the sender IP address of all ARP packets and the target IP address of ARP reply packets are legal. The illegal packets will be discarded.
Enable or disable the switch to check whether the sender IP address of all ARP packets and the target IP address of ARP reply packets are legal. The illegal packets will be discarded.
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the switch to check whether the source MAC address and the sender MAC address are the same when receiving an ARP packet
Switch(config)#ip arp inspection validate src-mac
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip arp inspection vlan

### Purpose
The ip arp inspection vlan command is used to enable the ARP Detection function on VLANs. To disable the ARP Detection function on VLANs, please use no ip arp detection vlan command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip arp inspection vlan vlan-list
no ip arp inspection vlan vlan-list
vlan-list
Enter the VLAN ID. The format is 1,5-9.
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the ARP Detection function on VLAN 2:
Switch(config)#ip arp inspection vlan 2
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip arp inspection vlan logging

### Purpose
The ip arp inspection vlan logging command is used to enable the Log function on the specific VLAN. To disable the Log function on the VLAN, please use no ip arp detection vlan logging command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip arp inspection vlan vlan-list logging
no ip arp inspection vlan vlan-list logging
vlan-list
Enter the VLAN ID. The format is 1,5-9.
logging
Enable the Log feature to make the switch generate a log when an ARP packet is discarded.
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the log feature on VLAN 2:
Switch(config)#ip arp inspection vlan 2 logging
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip arp inspection trust

### Purpose
The ip arp inspection trust command is used to configure the port for which the ARP Detect function is unnecessary as the Trusted Port. To clear the Trusted Port list, please use no ip arp detection trust command .The specific ports, such as up-linked port and routing port and LAG port, should be set as Trusted Port. To ensure the normal communication of the switch, please configure the ARP Trusted Port before enabling the ARP Detect function.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet)

### Syntax
```text
ip arp inspection trust
no ip arp inspection trust
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the Gigabit Ethernet ports 1/0/2-5 as the Trusted Port:
Switch(config)#interface range gigabitEthernet 1/0/2-5
Switch(config-if-range)#ip arp inspection trust
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip arp inspection limit-rate

### Purpose
The ip arp inspection limit-rate command is used to configure the ARP speed of a specified port. To restore to the default speed, please use no ip arp inspection limit-rate command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet)

### Syntax
```text
ip arp inspection limit-rate value
no ip arp inspection limit-rate
```

### Parameters
```text
value
The value to specify the maximum amount of the received ARP packets per second, ranging from 1 to 300 in pps(packet/second). By default, the value is 100.
```

### Default
By default, the value is 100.

### Example
```text
Configure the maximum amount of the received ARP packets per second as 50 pps for Gigabit Ethernet port 5:
Switch(config)#interface gigabitEthernet 1/0/5
Switch(config-if)#ip arp inspection limit-rate 50
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip arp inspection burst-interval

### Purpose
The ip arp inspection burst-interval command is used to configure the burst interval of a specified port. To restore to the default speed, please use no ip arp inspection burst-interval command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet)

### Syntax
```text
ip arp inspection burst-interval value
no ip arp inspection burst-interval
```

### Parameters
```text
value
Specify a time range. If the speed of received ARP packets in this time range reaches the limit for this time range, the port will be shut down. The valid values are from 1 to 15 seconds, and the default value is 1 second.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the burst interval as 2 seconds for Gigabit Ethernet port 5:
Switch(config)#interface gigabitEthernet 1/0/5
Switch(config-if)#ip arp inspection burst-interval 2
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip arp inspection recover

### Purpose
The ip arp inspection recover command is used to restore a port to the ARP transmit status from the ARP filter status.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet)

### Syntax
```text
ip arp inspection recover
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Restore Gigabit Ethernet port 1/0/5 to the ARP transmit status:
Switch(config)#interface gigabitEthernet 1/0/5
Switch(config-if)#ip arp inspection recover
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip arp inspection exceed

### Purpose
The ip arp inspection exceed command is used to configure the overspeed action. To delete this action, please use no ip arp inspection exceed command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet)

### Syntax
```text
ip arp inspection exceed [drop | shutdown] recover-time
no ip arp inspection exceed
```

### Parameters
```text
drop
Drop messages when speeding.
shutdown
Shut ports down when speeding.
recover-time
Configure self-recovery time.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the overspeed action as dropping messages when speeding and self-recovery time as 2 seconds for Gigabit Ethernet port 5:
Switch(config)#interface gigabitEthernet 1/0/5
Switch(config-if)#ip arp inspection exceed drop 2
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## show ip arp inspection

### Purpose
The show ip arp inspection command is used to display the ARP detection global configuration including the enable/disable status and the Trusted Port list.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip arp inspection
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the ARP detection configuration globally:
Switch(config)#show ip arp inspection
```

### Notes
- Permission requirement: None.

## show ip arp inspection interface

### Purpose
The show ip arp inspection interface command is used to display the interface configuration of ARP detection.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip arp inspection interface [ gigabitEthernet port ]
```

### Parameters
```text
port
The Ethernet port number.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the configuration of Gigabit Ethernet port 1/0/1:
Switch(config)#show ip arp inspection interface gigabitEthernet 1/0/1
Display the configuration of all Ethernet ports:
Switch(config)#show ip arp inspection interface
```

### Notes
- Permission requirement: None.

## show ip arp inspection vlan

### Purpose
The show ip arp inspection vlan command is used to display the VLAN configuration of ARP detection.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip arp inspection vlan
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the ARP Inspection configuration of VLAN:
Switch(config)#show ip arp inspection vlan
```

### Notes
- Permission requirement: None.

## show ip arp inspection statistics

### Purpose
The show ip arp inspection statistics command is used to display the number of the illegal ARP packets received.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip arp inspection statistics
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the number of the illegal ARP packets received:
Switch(config)#show ip arp inspection statistics
```

### Notes
- Permission requirement: None.

## clear ip arp inspection statistics

### Purpose
The clear ip arp inspection statistics command is used to clear the statistic of the illegal ARP packets received.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
clear ip arp inspection statistics
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Clear the statistic of the illegal ARP packets received:
Switch(config)#clear ip arp inspection statistics
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
