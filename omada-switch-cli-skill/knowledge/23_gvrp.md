# GVRP Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 26 GVRP Commands

Location: extracted Word text lines 12638-12737

## Chapter Notes

Official documentation states: GVRP (GARP VLAN registration protocol) is an implementation of GARP (generic attribute registration protocol). GVRP allows the switch to automatically add or remove the VLANs via the dynamic VLAN registration information and propagate the local VLAN registration information to other switches, without having to individually configure each VLAN.

- Use these commands only when the requested feature and target interface/VLAN/ring/session details are clear.

## gvrp

### Purpose
The gvrp command is used to enable the GVRP function globally. To disable the GVRP function, please use no gvrp command.

### Command Mode
Global Configuration Mode

### Syntax
```text
gvrp
no gvrp
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the GVRP function globally:
Switch(config)#gvrp
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## gvrp (interface)

### Purpose
The gvrp command is used to enable the GVRP function for the desired port. To disable it, please use no gvrp command. The GVRP feature can only be enabled for the trunk-type ports.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
gvrp
no gvrp
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the GVRP function for Gigabit Ethernet ports 1/0/2-6:
Switch(config)#interface range gigabitEthernet 1/0/2-6
Switch(config-if-range)#gvrp
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## gvrp registration

### Purpose
The gvrp registration command is used to configure the GVRP registration type for the desired port. To restore to the default value, please use no gvrp registration command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
gvrp registration { normal | fixed | forbidden }
no gvrp registration
```

### Parameters
```text
normal | fixed | forbidden
Registration mode. By default, the registration mode is
normal
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the GVRP registration mode as
fixed
for Gigabit Ethernet ports 1/0/2-6:
Switch(config)#interface range gigabitEthernet 1/0/2-6
Switch(config-if-range)#gvrp registration fixed
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## gvrp timer

### Purpose
The gvrp timer command is used to set a GVRP timer for the desired port. To restore to the default setting of a GARP timer, please use no gvrp timer command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
gvrp timer { leaveall | join | leave } value
no gvrp timer [leaveall | join | leave]
```

### Parameters
```text
leaveall | join | leave
They are the three timers: leave All, join and leave. Once the LeaveAll Timer is set, the port with GVRP enabled can send a LeaveAll message after the timer times out, so that other GARP ports can re-register all the attribute information. After that, the LeaveAll timer will start to begin a new cycle. To guarantee the transmission of the Join messages, a GARP port sends each Join message two times. The Join Timer is used to define the interval between the two sending operations of each Join message. Once the Leave Timer is set, the GARP port receiving a Leave message will start its Leave timer, and deregister the attribute information if it does not receive a Join message again before the timer times out.
value
The value of the timer. The LeaveAll Timer ranges from 1000 to 30000 centiseconds and the default value is 1000 centiseconds. The Join Timer ranges from 20 to 1000 centiseconds and the default value is 20 centiseconds. The Leave Timer ranges from 60 to 3000 centiseconds and the default value is 60 centiseconds.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set the GARP leaveall timer of Gigabit Ethernet port 1/0/6 as 2000 centiseconds and restore the join timer of it to the default value:
Switch(config)#interface gigabitEthernet 1/0/6
Switch(config-if)#gvrp timer leaveall 2000
Switch(config-if)#no gvrp timer join
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## show gvrp interface

### Purpose
The show gvrp interface command is used to display the GVRP configuration information of a specified Ethernet port or of all Ethernet ports.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show gvrp interface [fastEthernet port | gigabitEthernet port | ten-gigabitEthernet port | port-channel port-channel-id ]
```

### Parameters
```text
port
The port number.
port-channel-id
The ID of the port channel.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the GVRP configuration information of Gigabit Ethernet port 1:
Switch(config)#show gvrp interface gigabitEthernet 1/0/1
Display the GVRP configuration information of all Ethernet ports:
Switch(config)#show gvrp interface
```

### Notes
- Permission requirement: None.

## show gvrp global

### Purpose
The show gvrp global command is used to display the global GVRP status.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show gvrp global
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the global GVRP status:
Switch(config)#show gvrp global
```

### Notes
- Permission requirement: None.
