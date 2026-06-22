# DHCPv6 Filter Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 82 DHCPv6 Filter Commands

Location: extracted Word text lines 29714-29832

## Chapter Notes

Official documentation states: DHCPv6 Filter function allows the user to not only to restrict all DHCPv6 Server packets but also to receive any specified DHCPv6 server packet by any specified DHCPv6 client, it is useful when one or more DHCPv6 servers are present on the network and both provide DHCPv6 services to different distinct groups of clients.

- Use these commands only when the requested feature and target interface/VLAN/ring/session details are clear.

## ipv6 dhcp filter

### Purpose
The ipv6 dhcp filter command is used to enable DHCP Filter function globally. To disable DHCPv6 Filter function globally, please use no ipv6 dhcp filter command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ipv6 dhcp filter
no ipv6 dhcp filter
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the DHCPv6 Filter function globally:
Switch(config)#ipv6 dhcp filter
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ipv6 dhcp filter (interface)

### Purpose
The ipv6 dhcp filter (interface) command is used to enable DHCPv6 Filter function on a specified port. To disable DHCPv6v Filter function on this port, please use no ipv6 dhcp filter (interface) command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
ipv6 dhcp filter
no ipv6 dhcp filter
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the DHCPv6 filter on port 1/0/1
Switch(config)#interface gigabitEthernet 1/0/1
Switch(Config-if)#ipv6 dhcp filter
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ipv6 dhcp filter limit rate

### Purpose
The ipv6 dhcp filter limit rate command is used to enable the Flow Control feature for the DHCPv6 packets. The excessive DHCPv6 packets will be discarded. To restore to the default configuration, please use no ipv6 dhcp filter limit rate command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
ipv6 dhcp filter limit rate value
no ipv6 dhcp filter limit rate
```

### Parameters
```text
value
The value of Flow Control. The options are 5/10/15/20/25/30 (packet/second). The default value is 0, which stands for
disable
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set the Flow Control of GigabitEthernet port 2 as 20 pps:
Switch(config)#interface gigabitEthernet 1/0/2
Switch(config-if)#ipv6 dhcp filter limit rate 20
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ipv6 dhcp filter decline rate

### Purpose
The ipv6 dhcp filter decline rate command is used to enable the Decline Protect feature and configure the rate limit on DHCP Decine packets. The excessive DHCPv6 Decline packets will be discarded. To disable the Decline Protect feature, please use no ipv6 dhcp filter decline rate command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
ipv6 dhcp filter decline rate value
no ipv6 dhcp filter decline rate
```

### Parameters
```text
value
Specify the rate limit of DHCPv6 Decline packets, and the optional values are 0, 5, 10, 15, 20, 25 and 30 (units:packet/second). It default value is 0, which stands for
disable
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the rate limit of DHCPv6 Decline packets as 20 packets per second on Gigabit Ethernet port 1/0/2:
Switch(config)#interface gigabitEthernet 1/0/2
Switch(config-if)#ipv6 dhcp filter decline 20
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ipv6 dhcp filter server permit-entry

### Purpose
ipv6 dhcp filter server permit-entry command is used to add entry for the legal DHCPv6 server. To restore to the default option, please use no ipv6 dhcp snooping information strategy command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ipv6 dhcp filter server permit-entry server-ip ipAddr interface { fastEthernet port | gigabitEthernet port | ten-gigabitEthernet port | interface port-channel port-channel-id }
no ipv6 dhcp filter server permit-entry server-ip ipAddr interface { fastEthernet port | gigabitEthernet port | ten-gigabitEthernet port | interface port-channel port-channel-id }
```

### Parameters
```text
ipAddr
Specify the IPv6 address of the legal DHCPv6 server.
port-list | port-channel-id
Specify the port that the legal DHCPv6 server is connected to.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Create an entry for the legal DHCPv6 server whose IP address is 192.168.0.100 and connected port number is 1/0/1:
Switch(config)#ipv6 dhcp filter server permit-entry server-ip 2003::1 interface gigabitEthernet 1/0/1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## show ipv6 dhcp filter

### Purpose
The show ipv6 dhcp filter command is used to display the configuration of DHCPv6 Filter.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ipv6 dhcp filter
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the DHCPv6 Filter configuration:
Switch#show ipv6 dhcp filter
```

### Notes
- Permission requirement: None.

## show ipv6 dhcp filter interface

### Purpose
The show ipv6 dhcp filter interface command is used to display the configuration of DHCPv6 Filter on ports.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ipv6 dhcp filter interface [fastEthernet port | gigabitEthernet port | ten-gigabitEthernet port | port-channel port-channel-id ]
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the DHCPv6 Filter configuration on port 1/0/3:
Switch#show ipv6 dhcp filter interface gigabitEthernet 1/0/3
```

### Notes
- Permission requirement: None.

## show ip dhcp filter server permit-entry

### Purpose
The show ipv6 dhcp filter server permit-entry command is used to display the legal server configuration.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ipv6 dhcp filter server permit-entry
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the legal DHCPv6 server configuration:
Switch#show ipv6 dhcp filter server permit-entry
```

### Notes
- Permission requirement: None.
