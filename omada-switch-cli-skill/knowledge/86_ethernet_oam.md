# Ethernet OAM Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 86 Ethernet OAM Commands (Only for Certain Devices)

Location: extracted Word text lines 30101-30376

## Chapter Notes

Official documentation states: Note: Ethernet OAM commands are only available on certain devices. Ethernet OAM (standing for Operation, Administration, and Maintenance) is Layer 2 protocol that is used for monitoring and troubleshooting Ethernet networks. It can report the network status to network administrators through the OAMPDUs exchanged between two OAM entities. The operation of OAM on an Ethernet interface does not adversely affect data traffic as OAM is a slow protocol with very limited bandwidth potential.

- This chapter is marked `Only for Certain Devices`; treat all configuration commands as model-dependent.

## ethernet-oam

### Purpose
The ethernet-oam command is used to enable the Ethernet OAM function for the desired port. To disable the Ethernet OAM function, please use no ethernet-oam command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet)

### Syntax
```text
ethernet-oam
no ethernet-oam
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the Ethernet OAM function for Gigabit Ethernet port 1/0/2:
Switch(config)# interface gigabitEthernet 1/0/2
Switch(config-if)#ethernet-oam
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ethernet-oam mode

### Purpose
The ethernet-oam mode command is used to configure the OAM mode for the desired port. To return to the default configurations, please use no ethernet-oam mode command. The default mode is active.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet)

### Syntax
```text
ethernet-oam mode { passive | active }
no ethernet-oam mode
```

### Parameters
```text
passive
Specify the OAM mode as passive.
active
Specify the OAM mode as active.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure Ethernet OAM client to operate in passive mode for Gigabit Ethernet port 2:
Switch(config)# interface gigabitEthernet 1/0/2
Switch(config-if)#ethernet-oam mode passive
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ethernet-oam link-monitor symbol-period

### Purpose
The ethernet-oam link-monitor symbol-period command is used to configure the parameters about one of the link events, error symbol period event. To return to the default configurations, please use no ethernet-oam link-monitor symbol-period command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet)

### Syntax
```text
ethernet-oam link-monitor symbol-period { threshold threshold | window window | notify { disable | enable }}
no ethernet-oam link-monitor symbol-period { threshold | window | notify }
```

### Parameters
```text
threshold
Configure the error threshold for generating error symbol-period event. The range is from 1 to 4294967295 and the default value is 1.
window
Configure the error symbol-period event detection interval. The range is from 10 to 600, in terms of 100 ms intervals. The default value is 10.
notify
Enable/Disable the event notification. By default, it is enabled.
threshold | window | notify
The parameter that you want to return to the default configuration.
```

### Default
By default, it is enabled.

### Example
```text
For error symbol-period event, configure the error threshold as 5 and the event detection interval as 3 seconds on Gigabit Ethernet port 1/0/2:
Switch(config)# interface gigabitEthernet 1/0/2
Switch(config-if)# ethernet-oam link-monitor symbol-period threshold 5 window 30
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ethernet-oam link-monitor frame

### Purpose
The ethernet-oam link-monitor frame command is used to configure the parameters about one of the link events, error frame event. To return to the default configurations, please use no ethernet-oam link-monitor frame command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet)

### Syntax
```text
ethernet-oam link-monitor frame { [threshold threshold ] [ window window ] [notify { disable | enable } ] }
no ethernet-oam link-monitor frame { threshold | window | notify }
```

### Parameters
```text
threshold
Configure the error threshold for generating error frame event. The range is from 1 to 4294967295 and the default value is 1.
window
Configure the error symbol-period event detection interval. The range is from 10 to 600, in terms of 100 ms intervals. The default value is 10.
notify
Enable/Disable the event notification. By default, it is enabled.
threshold | window | notify
The parameter that you want to return to the default configuration.
```

### Default
By default, it is enabled.

### Example
```text
For error frame event, configure the error threshold as 6 and the event detection interval as 9 seconds on Gigabit Ethernet port 1/0/3:
Switch(config)# interface gigabitEthernet 1/0/3
Switch(config-if)# ethernet-oam link-monitor frame threshold 6 window 90
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ethernet-oam link-monitor frame-period

### Purpose
The ethernet-oam link-monitor frame-period command is used to configure the parameters about one of the link events, error frame period event. To return to the default configurations, please use no ethernet-oam link-monitor frame-period command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet)

### Syntax
```text
ethernet-oam link-monitor frame-period { [threshold threshold ] [ window window ] [notify { disable | enable } ] }
no ethernet-oam link-monitor frame-period { threshold | window | notify }
```

### Parameters
```text
threshold
Configure the error threshold for generating error frame period event. The range is from 1 to 4294967295 and the default value is 1.
window
Configure the error frame period event detection interval. The range is from 148810 to 89286000. The default value is 148810 for Fast Ethernet port and 1488100 for Gigabit Ethernet port.
notify
Enable/Disable the event notification. By default, it is enabled.
threshold | window | notify
The parameter that you want to return to the default configuration.
```

### Default
By default, it is enabled.

### Example
```text
For error frame period event, configure the error threshold as 6 and the event detection interval as 150000 frames on Gigabit Ethernet port 1/0/4:
Switch(config)# interface gigabitEthernet 1/0/4
Switch(config-if)# ethernet-oam link-monitor frame-period threshold 6 window 150000
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ethernet-oam link-monitor frame-seconds

### Purpose
The ethernet-oam link-monitor frame-seconds command is used to configure the parameters about one of the link events, error frame seconds event. To return to the default configurations, please use no ethernet-oam link-monitor frame-seconds command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet)

### Syntax
```text
ethernet-oam link-monitor frame-seconds { [threshold threshold ] [ window window ] [notify { disable | enable } ] }
no ethernet-oam link-monitor frame-seconds { threshold | window | notify }
```

### Parameters
```text
threshold
Configure the error threshold for generating error frame seconds event. The range is from 1 to 900 and the default value is 1.
window
Configure the error frame seconds event detection interval. The range is from 100 to 9000, in terms of 100 ms intervals. The default value is 600.
notify
Enable/Disable the event notification. By default, it is enabled.
threshold | window | notify
The parameter that you want to return to the default configuration.
```

### Default
By default, it is enabled.

### Example
```text
For error frame seconds event, configure the error threshold as 8 and the event detection interval as 30 seconds on Gigabit Ethernet port 5:
Switch(config)# interface gigabitEthernet 1/0/5
Switch(config-if)# ethernet-oam link-monitor frame-seconds threshold 8 window 300
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ethernet-oam remote-failure

### Purpose
The ethernet-oam remote-failure command is used to configure whether to notify the link faults or not. The link faults include dying gasp and critical event. To return to the default configurations, please use no ethernet-oam remote-failure command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet)

### Syntax
```text
ethernet-oam remote-failure { dying-gasp | critical-event } notify { disable | enable }
no ethernet-oam remote-failure { dying-gasp | critical-event } notify
```

### Parameters
```text
dying-gasp
Dying Gasp link event. Dying gasp means an unrecoverable fault, such as power failure, occurs.
critical-event
Critical Event. Critical-event means unspecified critical event occurs.
notify
Enable/Disable the event notification. By default, it is enabled.
```

### Default
By default, it is enabled.

### Example
```text
Disable the Dying Gasp link event notification on Gigabit Ethernet port 1/0/7:
Switch(config)# interface gigabitEthernet 1/0/7
Switch(config-if)# ethernet-oam remote-failure dying-gasp notify disable
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ethernet-oam remote-loopback received-remote- loopback

### Purpose
The ethernet-oam remote-loopback received-remote-loopback command is used to configure the client to process or to ignore the received remote loopback request. To return to the default configurations, please use no ethernet-oam remote-loopback received-remote-loopback command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet)

### Syntax
```text
ethernet-oam remote-loopback received-remote-loopback { process | ignore }
no ethernet-oam remote-loopback received-remote-loopback
```

### Parameters
```text
process
Process the received remote loopback request.
ignore
Ignore the received remote loopback request.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the client to process the received remote loopback request on Gigabit Ethernet port 1:
Switch(config)# interface gigabitEthernet 1/0/1
Switch(config-if)# ethernet-oam remote-loopback received -remote-loopback process
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ethernet-oam remote-loopback

### Purpose
The ethernet-oam remote-loopback command is used to request the remote peer to start or stop the Ethernet OAM remote loopback mode.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet)

### Syntax
```text
ethernet-oam remote-loopback { start | stop }
```

### Parameters
```text
start
Request the remote peer to start the Ethernet OAM remote loopback mode.
stop
Request the remote peer to stop the Ethernet OAM remote loopback mode.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Request the remote peer to start the Ethernet OAM remote loopback mode on Gigabit Ethernet port 1/0/3:
Switch(config)# interface gigabitEthernet 1/0/3
Switch(config-if)# ethernet-oam remote-loopback start
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## clear ethernet-oam statistics

### Purpose
The clear ethernet-oam statistics command is used to clear Ethernet OAM statistics.

### Command Mode
Global Configuration Mode

### Syntax
```text
clear ethernet-oam statistics [ interface [ fastEthernet port ] [ gigabitEthernet port ] [ ten-gigabitEthernet port ] [ two-gigabitEthernet port ] ]
```

### Parameters
```text
port
The Gigabit Ethernet port number. By default, the Ethernet OAM statistics of all ports are cleared.
```

### Default
By default, the Ethernet OAM statistics of all ports are cleared.

### Example
```text
Clear Ethernet OAM statistics of Gigabit Ethernet port 1/0/3:
Switch(config)# clear ethernet-oam statistics interface gigabit Ethernet 1/0/3
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## clear ethernet-oam event-log

### Purpose
The clear ethernet-oam event-log command is used to clear the Ethernet OAM event log.

### Command Mode
Global Configuration Mode

### Syntax
```text
clear ethernet-oam event-log [ interface gigabitEthernet port ]
```

### Parameters
```text
port
The Gigabit Ethernet port number. By default, the Ethernet OAM event logs of all ports are cleared.
```

### Default
By default, the Ethernet OAM event logs of all ports are cleared.

### Example
```text
Clear Ethernet OAM event log of Gigabit Ethernet port 1/0/3:
Switch(config)# clear ethernet-oam event-log interface gigabitEthernet 1/0/3
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## show ethernet-oam configuration

### Purpose
The show ethernet-oam configuration command is used to display Ethernet OAM configuration information.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ethernet-oam configuration [ interface gigabitEthernet port ]
```

### Parameters
```text
port
The Gigabit Ethernet port number. By default, the Ethernet OAM configuration information of all ports is displayed.
```

### Default
By default, the Ethernet OAM configuration information of all ports is displayed.

### Example
```text
Display Ethernet OAM configuration information of Gigabit Ethernet port 1/0/2:
Switch(config)# show ethernet-oam configuration interface gigabitEthernet 1/0/2
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## show ethernet-oam event-log

### Purpose
The show ethernet-oam event-log command is used to display the Ethernet OAM event log.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ethernet-oam event-log [ interface gigabitEthernet port ]
```

### Parameters
```text
port
The Gigabit Ethernet port number. By default, the Ethernet OAM event logs of all ports are displayed.
```

### Default
By default, the Ethernet OAM event logs of all ports are displayed.

### Example
```text
Display Ethernet OAM event log of Gigabit Ethernet port 1/0/2:
Switch(config)# show ethernet-oam event-log interface gigabitEthernet 1/0/2
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## show ethernet-oam statistics

### Purpose
The show ethernet-oam statistics command is used to display the Ethernet OAM statistics.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ethernet-oam statistics [ interface gigabitEthernet port ]
```

### Parameters
```text
port
The Gigabit Ethernet port number. By default, the Ethernet OAM statistics of all ports are displayed.
```

### Default
By default, the Ethernet OAM statistics of all ports are displayed.

### Example
```text
Display Ethernet OAM statistics of Gigabit Ethernet port 1/0/2:
Switch(config)# show ethernet-oam statistics interface gigabitEthernet 1/0/2
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## show ethernet-oam status

### Purpose
The show ethernet-oam status command is used to display the Ethernet OAM status of both the local and the remote client.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ethernet-oam status [ interface gigabitEthernet port ]
```

### Parameters
```text
port
The Gigabit Ethernet port number. By default, the Ethernet OAM status of all ports is displayed.
```

### Default
By default, the Ethernet OAM status of all ports is displayed.

### Example
```text
Display Ethernet OAM status of Gigabit Ethernet port 1/0/2:
Switch(config)# show ethernet-oam status interface gigabitEthernet 1/0/2
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.
