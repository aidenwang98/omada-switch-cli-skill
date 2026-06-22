# IPv6 Verify Source Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 80 IPv6 Verify Source Commands

Location: extracted Word text lines 29523-29577

## Chapter Notes

Official documentation states: IPv6 Verify Source is to filter the IPv6 packets based on the IPv6-MAC Binding entries. Only the packets matched to the IPv6-MAC Binding rules can be processed, which can enhance the bandwidth utility. Before configuring IPv6 Verify Source feature, you should configure the SDM template as enterpriseV6 and save your configurations.

- Use these commands only when the requested feature and target interface/VLAN/ring/session details are clear.

## ipv6 verify source

### Purpose
The ipv6 verify source command is used to configure the IPv6 Verify Source mode for a specified port. To disable the IPv6 Verify Source function, please use no ipv6 verify source command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet )

### Syntax
```text
ipv6 verify source { sipv6+mac | sipv6 }
no ipv6 verify source
```

### Parameters
```text
sipv6+mac
Security type.
sipv6+mac
indicates that only the packets with its source IPv6 address, source MAC address and port number matched to the IPv6-MAC binding rules can be processed.
sipv6
Security type.
sipv6
indicates that only the packets with its source IPv6 address and port number matched to the IPv6-MAC binding rules can be processed.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the IPv6 Verify Source function for Gigabit Ethernet ports 5-10. Configure that only the packets with its source IPv6 address, source MAC address and port number matched to the IPv6-MAC binding rules can be processed:
Switch(config)#interface range gigabitEthernet 1/0/5-10
Switch(config-if-range)#ipv6 verify source sipv6+mac
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## show ipv6 verify source

### Purpose
The show ipv6 verify source command is used to display the IPv6 Verify Source configuration information.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ipv6 verify source
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the IPv6 Verify Source configuration information:
Switch(config)#show ipv6 verify source
```

### Notes
- Permission requirement: None.

## show ipv6 verify source interface

### Purpose
The show ipv6 verify source interface command is used to display the IPv6 verify source configuration of a desired Gigabit Ethernet port.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ipv6 verify source interface gigabitEthernet port
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
Display the IPv6 verify source configuration of Gigabit Ethernet port 1/0/5:
Switch#show ipv6 verify source interface gigabitEthernet 1/0/5
```

### Notes
- Permission requirement: None.
