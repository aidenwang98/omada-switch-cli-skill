# IP Verify Source Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 79 IP Verify Source Commands

Location: extracted Word text lines 29456-29522

## Chapter Notes

Official documentation states: IP Verify Source is to filter the IP packets based on the IP-MAC Binding entries. Only the packets matched to the IP-MAC Binding rules can be processed, which can enhance the bandwidth utility.

- Use these commands only when the requested feature and target interface/VLAN/ring/session details are clear.

## ip verify source

### Purpose
The ip verify source command is used to configure the IP Verify Source mode for a specified port. To disable the IP Verify Source function, please use no ip verify source command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet)

### Syntax
```text
ip verify source { sip+mac | sip }
no ip verify source
```

### Parameters
```text
sip+mac
Security type.
sip+mac
indicates that only the packets with its source IP address, source MAC address and port number matched to the IP-MAC binding rules can be processed.
sip
Security type.
indicates that only the packets with its source IP address and port number matched to the IP-MAC binding rules can be processed.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the IP Verify Source function for Gigabit Ethernet ports 5-10. Configure that only the packets with its source IP address, source MAC address and port number matched to the IP-MAC binding rules can be processed:
Switch(config)#interface range gigabitEthernet 1/0/5-10
Switch(config-if-range)#ip verify source sip+mac
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Official note: sip is only available on certain devices.

## ip verify source logging

### Purpose
The ip verify source logging command is used to enable the log feature. With this feature enabled, the switch will generate a log when illegal packets are received. To disable the log feature, please use no ip verify source logging command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip verify source logging
no ip verify source logging
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the log feature to make the switch generate logs when receiving illegal packets:
Switch(config)#ip verify source logging
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## show ip verify source

### Purpose
The show ip verify source command is used to display the IP Verify Source configuration information.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip verify source
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the IP Verify Source configuration information:
Switch(config)#show ip verify source
```

### Notes
- Permission requirement: None.

## show ip verify source interface

### Purpose
The show ip verify source interface command is used to display the IP verify source configuration of a desired Gigabit Ethernet port.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip verify source interface [fastEthernet port | gigabitEthernet port | ten-gigabitEthernet port | port-channel port-channel-id ]
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
Display the IP verify source configuration of Gigabit Ethernet port 1/0/5:
Switch#show ip verify source interface gigabitEthernet 1/0/5
```

### Notes
- Permission requirement: None.
