# DHCPv4 Filter Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 81 DHCPv4 Filter Commands

Location: extracted Word text lines 29578-29713

## Chapter Notes

Official documentation states: DHCPv4 Filter function allows the user to not only to restrict all DHCP Server packets but also to receive any specified DHCP server packet by any specified DHCP client, it is useful when one or more DHCP servers are present on the network and both provide DHCP services to different distinct groups of clients.

- Use these commands only when the requested feature and target interface/VLAN/ring/session details are clear.

## ip dhcp filter

### Purpose
The ip dhcp filter command is used to enable DHCP Filter function globally. To disable DHCP Filter function globally, please use no ip dhcp filter command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip dhcp filter
no ip dhcp filter
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the DHCP Filter function globally:
Switch(config)#ip dhcp filter
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip dhcp filter (interface)

### Purpose
The ip dhcp filter (interface) command is used to enable DHCP Filter function on a specified port. To disable DHCP Filter function on this port, please use no ip dhcp filter (interface) command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
ip dhcp filter
no ip dhcp filter
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the DHCP filter on port 1/0/1
Switch(config)#interface gigabitEthernet 1/0/1
Switch(Config-if)#ip dhcp filter
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip dhcp filter mac-verify

### Purpose
The ip dhcp filter mac-verify command is used to enable the MAC Verify feature. To disable the MAC Verify feature, please use no ip dhcp filter mac-verify command. There are two fields of the DHCP packet containing the MAC address of the Host. The MAC Verify feature is to compare the two fields and discard the packet if the two fields are different.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
ip dhcp filter mac-verify
no ip dhcp filter mac-verify
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the MAC Verify feature for the Gigabit Ethernet port 10/2:
Switch(config)#interface gigabitEthernet 1/0/2
Switch(config-if)#ip dhcp filter mac-verify
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip dhcp filter limit rate

### Purpose
The ip dhcp filter limit rate command is used to enable the Flow Control feature for the DHCP packets. The excessive DHCP packets will be discarded. To restore to the default configuration, please use no ip dhcp filter limit rate command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
ip dhcp filter limit rate value
no ip dhcp filter limit rate
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
Switch(config-if)#ip dhcp filter limit rate 20
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip dhcp filter decline rate

### Purpose
The ip dhcp filter decline rate command is used to enable the Decline Protect feature and configure the rate limit on DHCP Decine packets. The excessive DHCP Decline packets will be discarded. To disable the Decline Protect feature, please use no ip dhcp filter decline rate command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
ip dhcp filter decline rate value
no ip dhcp filter decline rate
```

### Parameters
```text
value
Specify the rate limit of DHCP Decline packets, and the optional values are 0, 5, 10, 15, 20, 25 and 30 (units:packet/second). It default value is 0, which stands for
disable
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the rate limit of DHCP Decline packets as 20 packets per second on Gigabit Ethernet port 1/0/2:
Switch(config)#interface gigabitEthernet 1/0/2
Switch(config-if)#ip dhcp filter decline rate 20
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip dhcp filter server permit-entry

### Purpose
ip dhcp filter server permit-entry command is used to add entry for the legal DHCP server. To restore to the default option, please use no ip dhcp snooping information strategy command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip dhcp filter server permit-entry server-ip ipAddr client-mac macAddr interface { fastEthernet port | gigabitEthernet port | ten-gigabitEthernet port | interface port-channel port-channel-id }
no ip dhcp filter server permit-entry server-ip ipAddr client-mac macAddr interface { fastEthernet port | gigabitEthernet port | ten-gigabitEthernet port | interface port-channel port-channel-id }
```

### Parameters
```text
ipAddr
Specify the IP address of the legal DHCPv4 server.
macAddr
Specify the MAC address of the DHCP Client. The value
means all client mac addresses.
port-list | port-channel-id
Specify the port that the legal DHCPv4 server is connected to.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Create an entry for the legal DHCPv4 server whose IP address is 192.168.0.100 and connected port number is 1/0/1 without client MAC address restricted:
Switch(config)#ip dhcp filter server permit-entry server-ip 192.168.0.100 client-mac all interface gigabitEthernet 1/0/1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## show ip dhcp filter

### Purpose
The show ip dhcp filter command is used to display the configuration of DHCP Filter.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip dhcp filter
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the DHCP Filter configuration:
Switch#show ip dhcp filter
```

### Notes
- Permission requirement: None.

## show ip dhcp filter interface

### Purpose
The show ip dhcp filter interface command is used to display the configuration of DHCP Filter on ports.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip dhcp filter interface [fastEthernet port | gigabitEthernet port | ten-gigabitEthernet port | port-channel port-channel-id ]
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the DHCP Filter configuration on port 1/0/3:
Switch#show ip dhcp filter interface gigabitEthernet 1/0/3
```

### Notes
- Permission requirement: None.

## show ip dhcp filter server permit-entry

### Purpose
The show ip dhcp filter server permit-entry command is used to display the legal server configuration.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip dhcp filter server permit-entry
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the legal DHCP server configuration:
Switch#show ip dhcp filter server permit-entry
```

### Notes
- Permission requirement: None.
