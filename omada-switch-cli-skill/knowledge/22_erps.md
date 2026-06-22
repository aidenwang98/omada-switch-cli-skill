# ERPS Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 25 ERPS Commands

Location: extracted Word text lines 12313-12637

## Chapter Notes

Official documentation states: ERPS (Ethernet Ring Protection Switching) is an Ethernet ring link layer technology with high reliability and stability. It can prevent broadcast storms caused by the data loop if the Ethernet ring is complete. With a high convergence speed, it can quickly restore the communication paths among the nodes in the ring network when a link failure happens.

- Use these commands only when the requested feature and target interface/VLAN/ring/session details are clear.

## erps ring

### Purpose
The erps ring command is used to enable the ERPS ring function globally and create an ERPS ring. To disable the ERPS ring function, please use no erps ring command.

### Command Mode
Global Configuration Mode

### Syntax
```text
erps ring ring-id
no erps ring ring-id
```

### Parameters
```text
ring-id
The ID of the ERPS ring, ranging from 1 to 8.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the ERPS ring function globally:
Switch(config)#erps ring 1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## control-vlan

### Purpose
The control-vlan command is used to configure a control VLAN for an ERPS ring to forward RAPS PDUs .

### Command Mode
Global Configuration Mode

### Syntax
```text
control-vlan vlan-id
```

### Parameters
```text
vlan-id
Specify the ID of a control VLAN for ERPS ring, ranging from 1 to 4094.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure control VLAN 2 in ERPS ring 1:
Switch(config)#erps ring 1
Switch(ring-config)#control-vlan 2
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## description

### Purpose
The description command is used to add description information of an ERPS ring. To restore the default description, please use the no description command.

### Command Mode
Global Configuration Mode ERPS Ring Configuration Mode

### Syntax
```text
description description
no erps ring ringid description
```

### Parameters
```text
description
The description for the ERPS ring. It is the ring ID by default.
ringid
ERPS ring ID, e.g., 1, 5, 8
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Add description information
ring 1
Switch(ring-config)#description
ring 1
Restore ring 1's description to the default:
Switch(config)#no erps ring 1 description
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## guard-timer

### Purpose
The guard-timer command is used to configure the Guard timer in an ERPS ring. By default, the Guard timer is 200 centiseconds in an ERPS ring. To disable the guard-timer function, please use no guard-timer command.

### Command Mode
ERPS Ring Configuration Mode

### Syntax
```text
guard-timer time
no guard-timer
```

### Parameters
```text
time
The time setting for guard-timer, ranging from 1 to 200, In centiseconds.
```

### Default
By default, the Guard timer is 200 centiseconds in an ERPS ring.

### Example
```text
Configure the time for guard-timer as 100:
Switch(ring-config)#guard-timer 100
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## wtr-timer

### Purpose
The wtr-timer command is used to configure the Wait to Restore (WTR) timer in an ERPS ring. By default, the WTR timer is 5 minutes in an ERPS ring. To disable the wtr-timer function, please use no wtr-timer command.

### Command Mode
ERPS Ring Configuration Mode

### Syntax
```text
wtr-timer time
no wtr-timer
```

### Parameters
```text
time
The time setting for wtr-timer, ranging from 1 to 12.
```

### Default
By default, the WTR timer is 5 minutes in an ERPS ring.

### Example
```text
Configure the time for wtr-timer as 1:
Switch(ring-config)#wtr-timer 1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## holdoff-timer

### Purpose
The holdoff-timer command is used to configure the Holdoff timer in an ERPS ring. By default, the Holdoff timer is 0 deciseconds in an ERPS ring. When a fault occurs, the fault is not immediately reported to ERPS. Instead, the Holdoff timer starts. If the fault persists after the timer expires, the fault will be reported to ERPS. To disable the holdoff-timer function, please use no holdoff-timer command.

### Command Mode
ERPS Ring Configuration Mode

### Syntax
```text
holdoff-timer time
no holdoff-timer
```

### Parameters
```text
time
The time setting for holdoff-timer, ranging from 1 to 100.
```

### Default
By default, the Holdoff timer is 0 deciseconds in an ERPS ring.

### Example
```text
Configure the time for holdoff-timer as 10:
Switch(ring-config)#holdoff-timer 10
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## protected-instance

### Purpose
The protected-instance command is used to configure the Ethernet ring protection (ERP) instances in an ERPS ring. To disable the protected-instance function, please use no protected-instance command. By default, no ERP instance is configured in an ERPS ring.

### Command Mode
ERPS Ring Configuration Mode

### Syntax
```text
protected-instance instance
no protected-instance instance
```

### Parameters
```text
instance
The protected instance for the ERPS ring, ranging from 1 to 8.
```

### Default
By default, no ERP instance is configured in an ERPS ring.

### Example
```text
Configure the protected instance as 1, and map VLAN10-20 to instance 1:
Switch(ring)#spanning-tree mode mstp
Switch(ring)#spanning-tree mst configuration
Switch(ring)#instance 1 vlan 10-20
Switch(ring-config)#protected-instance 1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## raps-mel

### Purpose
The raps-mel command is used to configure the value of the MEL field in Ring Auto Protection Switching (RAPS) Protocol Data Units (PDUs) of the ERPS ring. To restore the default value of 7, please use the no raps-mel command.

### Command Mode
Global Configuration Mode ERPS Ring Configuration Mode

### Syntax
```text
raps-mel mel
no erps ring ringid raps-mel
```

### Parameters
```text
MEL value of the ERPS ring, ranging from 0 to 7. The default value is 7.
ringid
ERPS ring ID, e.g., 1, 5, 8
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the MEL value as 1:
Switch(ring-config)#raps-mel 1
Restore ring 1's RAPS-MEL to the default value:
Switch(config)#no erps ring 1 raps-mel
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## revertive

### Purpose
The revertive command is used to configure the revertive switching or non-revertive switching of the ERPS ring. To disable this function, please use the revertive disable command. By default, ERPS rings use revertive switching.

### Command Mode
ERPS Ring Configuration Mode

### Syntax
```text
revertive enable
revertive disable
```

### Parameters
No parameters.

### Default
By default, ERPS rings use revertive switching.

### Example
```text
Enable the revertive function:
Switch(ring-config)#revertive enable
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## sub-ring

### Purpose
The sub-ring command is used to configure the ERPS ring as an sub-ring. To disable this function, please use the no sub-ring command.

### Command Mode
ERPS Ring Configuration Mode

### Syntax
```text
sub-ring
no sub-ring
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the sub-ring function:
Switch(ring-config)#sub-ring
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## tc-notify erps

### Purpose
The tc-notify erps command is used to enable the network topology change notification function. To disable this function, please use the no tc-notify erps command. By default, this function is disabled.

### Command Mode
ERPS Ring Configuration Mode

### Syntax
```text
tc-notify erps ring ring-id
no tc-notify erps ring ring-id
```

### Parameters
```text
ring-id
the ring ID of the notification, ranging from 1 to 8.
```

### Default
By default, this function is disabled.

### Example
```text
Enable the network topology change notification function of ring 1:
Switch(ring-config)#tc-notify erps ring 1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## tc-protection interval

### Purpose
The tc-protection interval command is used to configure the network topology change protection interval for sending topology change notification messages. To disable this function, please use the no tc-protection interval command.

### Command Mode
ERPS Ring Configuration Mode

### Syntax
```text
tc-protection interval interval
no tc-protection interval interval
```

### Parameters
```text
interval
the time interval for tc-protection, ranging from 1 to 600.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the tc-protection interval of the ERPS ring as 1:
Switch(ring-config)#tc-protection interval 1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## tc-protection threshold

### Purpose
The tc-protection threshold command is used to configure the number of times ERPS parses topology change notifications and updates forwarding entries in the topology change protection interval. To disable this function, please use the no tc-protection threshold command.

### Command Mode
ERPS Ring Configuration Mode

### Syntax
```text
tc-protection threshold threshold
no tc-protection threshold
```

### Parameters
```text
threshold
the threshold for tc-protection, ranging from 1 to 255.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the tc-protection threshold of the ERPS ring as 1:
Switch(ring-config)#tc-protection threshold 1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## version

### Purpose
The version command is used to configure the ERPS version. To restore the ERPS ring's version to the default value of 1, please use the no version command,

### Command Mode
ERPS Ring Configuration Mode

### Syntax
```text
version version
no erps ring ringid version
```

### Parameters
```text
version
the version of the ERPS function, ranging from 1 to 2. The default value is 1.
ringid
ERPS ring ID, e.g., 1, 5, 8
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the ERPS version as 2:
Switch(ring-config)#version 2
Restore the ERPS ring 1's version to the default value of 1:
Switch(config)# no erps ring 1 version
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## virtual-channel

### Purpose
The virtual-channel command is used to configure the virtual channel (VC) mode for RAPS PDU transmission in a sub-ring. To disable this function, please use the no virtual-channel command.

### Command Mode
ERPS Ring Configuration Mode

### Syntax
```text
virtual-channel
no virtual-channel
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the virtual-channel function:
Switch(ring-config)#virtual-channel
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## erps ring rpl

### Purpose
The erps ring rpl command is used to add a port to the ERPS ring and specify the role of the port. To remove the role of the port, please use the no erps ring rpl command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet | interface range gigabitEthernet | interface port-channel | interface range port-channel )

### Syntax
```text
erps ring ring id [rpl owner |neighbour ]
```

### Parameters
```text
ring id
the ID of the ring that the port joins.
owner
configure the role of the port as owner.
neighbour
configure the role of the port as neighbour.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the role of port 1/0/2 in ring 1 as owner:
Switch(config)# interface gigabitEthernet 1/0/2
Switch(config-if)#erps ring 1 rpl owner
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## erps ring protect-switch

### Purpose
The erps ring protect-switch command is used to configure a port blocking mode for the ERPS port.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet | interface range gigabitEthernet | interface port-channel | interface range port-channel )

### Syntax
```text
erps ring ring id [protect-switch force |manual ]
```

### Parameters
```text
ring id
the ID of the ERPS ring, ranging from 1-255.
force
block a port forcibly.
manual
indicate the MS mode for blocking an ERPS port.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the switch mode of port 1/0/2 in ring 1 as force:
Switch(config)# interface gigabitEthernet 1/0/2
Switch(config-if)#erps ring 1 protect-switch force
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## show erps ring

### Purpose
The show erps ring command is used to display the ERPS ring information.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show erps ring {ring-id | all}
```

### Parameters
```text
ring id
show the information of a specified ring, ranging from 1 to 8.
show the information of all rings.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Show the information of all rings:
Switch(config)#show erps ring all
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## show erps statistics

### Purpose
The show erps statistics command is used to display the ERPS packet statistics.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show erps statistics
show erps statistics ring ringId
```

### Parameters
```text
ringId
ERPS ring ID.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display packet statistics for all ERPS rings:
Switch(config)# show erps statistics
Display packet statistics for ERPS ring 1:
Switch(config)# show erps statistics ring 1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
