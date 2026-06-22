# Loopback Detection Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 14 Loopback Detection Commands

Location: extracted Word text lines 10067-10196

## Chapter Notes

Official documentation states: With loopback detection feature enabled, the switch can detect loops using loopback detection packets. When a loop is detected, the switch will display an alert or further block the corresponding port according to the configuration.

- Use these commands only when the requested feature and target interface/VLAN/ring/session details are clear.

## loopback-detection (global)

### Purpose
The loopback-detection command is used to enable the loopback detection function globally. To disable it, please use no loopback detection command.

### Command Mode
Global Configuration Mode

### Syntax
```text
loopback-detection
no loopback-detection
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the loopback detection function globally:
Switch(config)# loopback-detection
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## loopback-detection interval

### Purpose
The loopback-detection interval command is used to define the interval of sending loopback detection packets from switch ports to network, aiming at detecting network loops periodically.

### Command Mode
Global Configuration Mode

### Syntax
```text
loopback-detection interval interval-time
```

### Parameters
```text
interval-time
The interval of sending loopback detection packets. It ranges from 1 to 1000 seconds. By default, this value is 30.
```

### Default
By default, this value is 30.

### Example
```text
Specify the interval-time as 50 seconds:
Switch(config)# loopback-detection interval 50
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## loopback-detection recovery-time

### Purpose
The loopback-detection recovery-time command is used to configure the time after which the blocked port would automatically recover to normal status.

### Command Mode
Global Configuration Mode

### Syntax
```text
loopback-detection recovery-time recovery-time
```

### Parameters
```text
recovery-time
The time after which the blocked port would automatically recover to normal status, and the loopback detection would restart. It ranges from 2 to 1000000 seconds. By default, this value is 90.
```

### Default
By default, this value is 90.

### Example
```text
Configure the recovery-time as 70 seconds:
Switch(config)# loopback-detection recovery-time 70
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## loopback-detection (interface)

### Purpose
The loopback-detection command is used to enable the loopback detection function of the specified port. To disable it, please use no loopback-detection command.

### Command Mode
Interface Configuration Mode (interface fastEthernet | gigabitEthernet | two-gigabitEthernet | ten-gigabitEthernet / interface range fastEthernet | gigabitEthernet | two-gigabitEthernet | ten-gigabitEthernet / interface port-channel / interface range port-channel )

### Syntax
```text
loopback-detection
no loopback-detection
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the loopback detection function of ports 1-3:
Switch(config)# interface range gigabitEthernet 1/0/1-3
Switch(Config-if-range)# loopback-detection
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## loopback-detection config process-mode

### Purpose
The loopback-detection config process-mode command is used to configure the process-mode for the ports by which the switch copes with the detected loops. You also need to configure the recovery mode to remove the block status of the port or VLAN when the process-mode is Port Based or VLAN Based.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet | interface range gigabitEthernet | interface port-channel | interface range port-channel )

### Syntax
```text
loopback-detection config process-mode { alert | port-based | vlan-based } recovery-mode { auto | manual }
```

### Parameters
```text
alert
When a loop is detected, the switch will send a trap message and generate an entry on the log file. It is the default setting.
port-based
When a loop is detected, the switch will send a trap message and generate an entry on the log file. In addition, the switch will block the port on which the loop is detected and no packets can pass through the port.
vlan-based
When a loop is detected, the switch will send a trap message and generate an entry on the log file. In addition, the switch will block the VLAN in which the loop is detected and only the packets of the blocked VLAN cannot pass through the port.
auto
Block status can be automatically removed after recovery time.
manual
Block status can only be removed manually.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the loopback detection process-mode as port-based, and configure the recovery mode as manual for port 2:
Switch(config)# interface gigabitEthernet 1/0/2
Switch(config-if)# loopback-detection config process-mode port-based recovery-mode manual
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## loopback-detection recover

### Purpose
The loopback-detection recover command is used to remove the block status of selected ports, recovering the blocked ports to normal status,

### Command Mode
Interface Configuration Mode (interface gigabitEthernet | interface range gigabitEthernet | interface port-channel | interface range port-channel )

### Syntax
```text
loopback-detection recover
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Recover the blocked port 1/0/2 to normal status:
Switch(config)# interface gigabitEthernet 1/0/2
Switch(config-if)# loopback-detection recover
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## show loopback-detection global

### Purpose
The show loopback-detection global command is used to display the global configuration of loopback detection function such as loopback detection global status, loopback detection interval and loopback detection recovery time.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show loopback-detection global
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the global configuration of loopback detection function:
Switch# show loopback-detection global
```

### Notes
- Permission requirement: None.

## show loopback-detection interface

### Purpose
The show loopback-detection interface command is used to display the configuration of loopback detection function and the status of the specified Ethernet port.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show loopback-detection interface [ fastEthernet port | gigabitEthernet port | two-gigabitEthernet port | ten-gigabitEthernet port | port-channel lagid ] [ detail ]
```

### Parameters
```text
port
The Ethernet port number.
lagid
The number of LAG, ranging from 1 to 14.
detail
Displays the loop status and block status of the VLAN which the specified port belongs to.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the configuration of loopback detection function and the status of all ports:
Switch# show loopback-detection interface
Display the configuration of loopback detection function and the status of port 5:
Switch# show loopback-detection interface gigabitEthernet 1/0/5
```

### Notes
- Permission requirement: None.
