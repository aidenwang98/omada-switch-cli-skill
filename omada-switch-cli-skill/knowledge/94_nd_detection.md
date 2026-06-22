# ND Detection Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 94 ND Detection Commands

Location: extracted Word text lines 32412-32512

## Chapter Notes

Official documentation states: The ND Detection feature allows the switch to detect the ND packets based on the binding entries in the IPv6-MAC Binding Table and filter out the illegal ND packets. Before configuring ND Detection, complete IPv6-MAC Binding configuration. For details, refer to IPv6-MAC Binding Configurations.

- Use these commands only when the requested feature and target interface/VLAN/ring/session details are clear.

## ipv6 nd detection

### Purpose
The ipv6 nd detection command is used to enable the ND Detection function globally. To disable the ND Detection function, please use no ipv6 nd detection command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ipv6 nd detection
no ipv6 nd detection
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the ND Detection function globally:
Switch(config)#ipv6 nd detection
```

## ipv6 nd detection vlan

### Purpose
The ipv6 nd detection vlan command is used to enable ND Detection function on a specified VLAN. To disable ND Detection function on this VLAN, please use no ipv6 nd detection vlan command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ipv6 nd detection vlan vlan-range
no ipv6 nd detection vlan vlan-range
```

### Parameters
```text
vlan-range
Enter the vlan range in the format of 1-3, 5.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the ND Detection function on VLAN 1,4,6-7:
Switch(config)#ipv6 nd detection vlan 1,4,6-7
```

## ipv6 nd detection vlan logging

### Purpose
The ipv6 nd detection vlan logging command is used to enable Log function on a specified VLAN. To disable Log function on this VLAN, please use no ipv6 nd detection vlan logging command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ipv6 nd detection vlan vlan-range logging
no ipv6 nd detection vlan vlan-range logging
```

### Parameters
```text
vlan-range
Enter the vlan range in the format of 1-3, 5.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the Log function on VLAN 1,4,6-7:
Switch(config)#ipv6 nd detection vlan 1,4,6-7 logging
```

## ipv6 nd detection trust

### Purpose
The ipv6 nd detection trust command is used to configure the port for which the ND Detection function is unnecessary as the Trusted Port. To clear the Trusted Port list, please use no ipv6 nd detection trust command .The specific port, such as up-linked port, routing port and LAG port, should be set as Trusted Port. To ensure the normal communication of the switch, please configure the ND Detection Trusted Port before enabling the ND Detection function.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet/ interface port-channel / interface range port-channel)

### Syntax
```text
Ipv6 nd detection trust
no ipv6 nd detection trust
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the Gigabit Ethernet ports 1/0/2-5 as the Trusted Port:
Switch(config)#interface range gigabitEthernet 1/0/2-5
Switch(config-if-range)#ipv6 nd detection trust
```

## show ipv6 nd detection

### Purpose
The show ipv6 nd detection command is used to display the ND detection global configuration including the enable/disable status.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ipv6 nd detection
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the ND Detection configuration globally:
Switch(config)#show ipv6 nd detection
```

## show ipv6 nd detection interface

### Purpose
The show ipv6 nd detection interface command is used to display the interface configuration of ND Detection.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ipv6 nd detection interface[ fastEthernet port | gigabitEthernet port | ten-gigabitEthernet port | port-channel port-channel-id ]
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
Display the configuration of Gigabit Ethernet port 1/0/1:
Switch(config)#show ipv6 nd detection interface gigabitEthernet 1/0/1
Display the configuration of all Ethernet ports:
Switch(config)#show ipv6 nd detection interface
```

## show ipv6 nd detection statistics

### Purpose
The show ipv6 nd detection statistics command is used to display the ND statistics of each VLAN, including the number of forwarded and dropped ND packets.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ipv6 nd detection statistics
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the ipv6 ND Detection statistics of each VLAN.
Switch(config)#show ipv6 nd detection statistics
```

### Notes
- Official note: This command is only available on certain devices.

## show ipv6 nd detection vlan

### Purpose
The show ipv6 nd detection vlan command is used to display the VLAN configuration of ND Detection.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ipv6 nd detection vlan
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the ipv6 ND Detection configuration of VLAN.
Switch(config)#show ipv6 nd detection vlan
```
