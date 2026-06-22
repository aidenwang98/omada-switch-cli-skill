# Interface Configuration Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 12 Interface Configuration Commands

Location: official printed page 139-148; actual PDF page 185-194

## interface

### Purpose
Enter Interface Configuration Mode to configure the corresponding port.

### Command Mode
Global Configuration Mode

### Syntax
```text
interface fastEthernet | gigabitEthernet | two-gigabitEthernet | ten-gigabitEthernet port
interface port-channel num
```

### Parameters
- `fastEthernet port`: 100M Ethernet port number.
- `gigabitEthernet port`: Gigabit Ethernet port number.
- `ten-gigabitEthernet port`: 10-Gigabit Ethernet port number.
- `two-gigabitEthernet port`: 2.5-Gigabit Ethernet port number.
- `port-channel num`: Ethernet channel number.In actual use, set `num` to the target LAG ID to enter the corresponding LAG / port-channel view, for example `interface port-channel 2`.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config)# interface gigabitEthernet 1/0/2
```

### Notes
- The Syntax line for this command has overlapping layout on the PDF page; official confirmation states that `interface port-channel num` is used to enter the LAG / port-channel view, where `num` is the target LAG ID.
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## interface range

### Purpose
Enter interface range Configuration Mode to configure multiple Ethernet ports at the same time.

### Command Mode
Global Configuration Mode

### Syntax
```text
interface range fastEthernet | gigabitEthernet | two-gigabitEthernet | ten-gigabitEthernet port-list
```

### Parameters
- `fastEthernet port`: 100M Ethernet port number.
- `gigabitEthernet port`: Gigabit Ethernet port number.
- `ten-gigabitEthernet port`: 10-Gigabit Ethernet port number.
- `two-gigabitEthernet port`: 2.5-Gigabit Ethernet port number.
- `port-list`: The list of Ethernet ports.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config)# interface range gigabitEthernet 1/0/1-3,1/0/6-7,1/0/9
```

### Notes
- Official documentation states: Commands in Interface Range gigabitEthernet Mode are applied independently to all ports in the range; if execution fails on one port, execution on other ports is not affected.
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## description

### Purpose
Add a description to an Ethernet port; use `no description` to clear the port description.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
description string
no description
```

### Parameters
- `string`: Port description content, length: 1 to 16 characters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config)# interface gigabitEthernet 1/0/5
Switch(config-if)# description Port_5
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## shutdown

### Purpose
Disable an Ethernet port; use `no shutdown` to re-enable the port.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
shutdown
no shutdown
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config)# interface gigabitEthernet 1/0/3
Switch(config-if)# shutdown
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## flow-control

### Purpose
Enable flow-control on a port; use `no flow-control` to disable it. Official documentation states that after flow-control is enabled, Ingress Rate and Egress Rate can be synchronized to avoid packet loss in the network.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
flow-control
no flow-control
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config)# interface gigabitEthernet 1/0/3
Switch(config-if)# flow-control
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## duplex

### Purpose
Configure the Duplex Mode of an Ethernet port; use `no duplex` to restore the default configuration.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
duplex { auto | full | half }
no duplex
```

### Parameters
- `auto | full | half`: Ethernet port duplex mode, including auto-negotiation mode, full-duplex mode, and half-duplex mode.

### Default
Official documentation states: Gigabit Ethernet ports default to auto-negotiation mode.

### Example
```text
Switch(config)# interface gigabitEthernet 1/0/3
Switch(config-if)# duplex full
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## jumbo-size

### Purpose
Specify the jumbo frame size.

### Command Mode
Global Configuration Mode

### Syntax
```text
jumbo-size size
```

### Parameters
- `size`: Jumbo frame value, range: 1518 to 9216 bytes.

### Default
1518 bytes.

### Example
```text
Switch(config)# jumbo-size 9216
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## speed

### Purpose
Configure the Speed Mode of an Ethernet port; use `no speed` to restore the default configuration.

### Command Mode
Interface Configuration Mode (interface fastEthernet | gigabitEthernet | two-gigabitEthernet | ten-gigabitEthernet / interface range fastEthernet | gigabitEthernet | two-gigabitEthernet | ten-gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
speed { 10 | 100 | 1000 | 2500 | 5000 | 10000 | auto }
no speed
```

### Parameters
- `10 | 100 | 1000 | 2500 | 5000 | 10000 | auto`: Ethernet port speed mode, corresponding to 10Mbps, 100Mbps, 1000Mbps, 2500Mbps, 5000Mbps, 10000Mbps, and Auto negotiation mode.

### Default
Auto negotiation mode.

### Example
```text
Switch(config)# interface gigabitEthernet 1/0/3
Switch(config-if)# speed 100
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## clear counters

### Purpose
Clear statistics for all Ethernet ports and port channels, or clear statistics for a specified interface.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
clear counters
clear counters interface [ fastEthernet | gigabitEthernet | two-gigabitEthernet | ten-gigabitEthernet port ] [ port-channel port-channel-id ]
```

### Parameters
- `port`: Ethernet port number.
- `port-channel-id`: The ID of the port channel.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config)# clear counters
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## show fiber-ports

### Purpose
Display information for all optical modules.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show fiber-ports
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config)# show fiber-ports
```

### Notes
- Official documentation notes: This command is only available on certain devices.
- Permission requirement: None.

## show interface status

### Purpose
Display the connection status of Ethernet ports / port channels.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show interface status [ fastEthernet port ] [ gigabitEthernet port ] [ two-gigabitEthernet port ] [ ten-gigabitEthernet port ] [ port-channel port-channel-id ]
```

### Parameters
- `port`: Ethernet port number.
- `port-channel-id`: The ID of the port channel.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config)# show interface status
Switch(config)# show interface status gigabitEthernet 1/0/1
```

### Notes
- Permission requirement: None.

## show interface counters

### Purpose
Display statistics for all ports / port channels, or for a specified interface.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show interface counters [ fastEthernet | gigabitEthernet | two-gigabitEthernet | ten-gigabitEthernet port ] [ port-channel port-channel-id ]
```

### Parameters
- `port`: Ethernet port number.
- `port-channel-id`: The ID of the port channel.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config)# show interface counters
Switch(config)# show interface counters gigabitEthernet 1/0/2
```

### Notes
- Permission requirement: None.

## show interface configuration

### Purpose
Display the configuration of all ports and port channels, including Port-status, Flow Control, Negotiation Mode, and Port-description; the configuration of a specified interface can also be displayed.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show interface configuration [ fastEthernet | gigabitEthernet | two-gigabitEthernet | ten-gigabitEthernet port ] [ port-channel port-channel-id ]
```

### Parameters
- `port`: Ethernet port number.
- `port-channel-id`: The ID of the port channel.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config)# show interface configuration
Switch(config)# show interface configuration gigabitEthernet 1/0/2
```

### Notes
- Permission requirement: None.

## show onvif ipc-classify

### Purpose
Display whether ports are in direct connection state, the current traffic identification status, and traffic identification results. Official documentation states that the identification result indicates whether the device connected to the port is an IPC, and may show IPC or Other.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show onvif ipc-classify
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config)# show onvif ipc-classify
```

### Notes
- This command belongs to Chapter 12 Interface Configuration Commands, but is not a core common port-configuration scenario in the first version; use it cautiously when generating CLI suggestions.
- Permission requirement: None.
