# Port Isolation Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 13 Port Isolation Commands

Location: extracted Word text lines 10024-10066

## Chapter Notes

Official documentation states: Port Isolation provides a method of restricting traffic flow to improve the network security by forbidding the port to forward packets to the ports that are not on its forwarding port list.

- Use these commands only when the requested feature and target interface/VLAN/ring/session details are clear.

## port isolation

### Purpose
The port isolation command is used to configure the forward port/port channel list of a port/port channel, so that this port/port channel can only communicate with the ports/port channels on its list. To delete the corresponding configuration, please use no port isolation command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
port isolation { [ fa-forward-list fa-forward-list ] [ gi-forward-list gi-forward-list ] [ tw-forward-list tw-forward-list ] [ te-forward-list te-forward-list ] } [ po-forward-list po-forward-list ]
no port isolation
```

### Parameters
```text
fa-forward-list / gi-forward-list / tw-forward-list / te-forward-list
The list of Ethernet ports.
po-forward-list
The list of port channels.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set port 1, 2, 4 and port channel 2 to the forward list of port 1/0/5:
Switch(config)# interface gigabitEthernet 1/0/5
Switch(config-if)# port isolation gi-forward-list 1/0/1-2,1/0/4 po-forward-list 2
Set all Ethernet ports and port channels to forward list of port 1/0/2, namely restore to the default setting:
Switch(config)# interface gigabitEthernet 1/0/2
Switch(config-if)# no port isolation
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## show port isolation interface

### Purpose
The show port isolation interface command is used to display the forward port list of a port/port channel.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show port isolation interface [fastEthernet port | gigabitEthernet port | two-gigabitEthernet port | ten-gigabitEthernet port | port-channel port-channel-id ]
```

### Parameters
```text
port
The number of Ethernet port you want to show its forward port list, in the format of 1/0/2.
port-channel-id
The ID of port channel you want to show its forward port list, ranging from 1 to 6.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the forward-list of port 1/0/2:
Switch# show port isolation interface gigabitEthernet 1/0/2
Display the forward-list of all Ethernet ports and port channels:
Switch# show port isolation interface
```

### Notes
- Permission requirement: None.
