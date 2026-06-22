# IPv6 Address Configuration Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 53 IPv6 Address Configuration Commands

Location: extracted Word text lines 23847-23968

## Chapter Notes

Official documentation states: The IPv6 address configuration commands are provided in the Interface Configuration Mode, which includes the routed port, the port-channel interface and the VLAN interface. Enter the configuration mode of these Layer 3 interfaces and configure their IPv6 parameters.

- Use these commands only when the requested feature and target interface/VLAN/ring/session details are clear.

## ipv6 enable

### Purpose
This command is used to enable the IPv6 function on the specified Layer 3 interface. IPv6 function should be enabled before the IPv6 address configuration management. By default it is enabled on VLAN interface 1. IPv6 function can only be enabled on one Layer 3 interface at a time. If the IPv6 function is disabled, the corresponding IPv6-based modules will be invalid, for example SSHv6, SSLv6, TFTPv6 and more. To disable the IPv6 function, please use no ipv6 enable command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ipv6 enable
no ipv6 enable
```

### Parameters
No parameters.

### Default
By default it is enabled on VLAN interface 1.

### Example
```text
Enable the IPv6 function on the VLAN interface 1:
Switch(config)# interface vlan 1
Switch(config-if)# ipv6 enable
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ipv6 address autoconfig

### Purpose
This command is used to enable the automatic configuration of the ipv6 link-local address. The switch has only one ipv6 link-local address, which can be configured automatically or manually. The general ipv6 link-local address has the prefix as fe80::/10. IPv6 routers cannot forward packets that have link-local source or destination addresses to other links. The autu-configured ipv6 link-local address is in EUI-64 format. To verify the uniqueness of the link-local address, the manually configured ipv6 link-local address will be deleted when the auto-configured ipv6 link-local address takes effect.

### Command Mode
Not explicitly specified in the official documentation.

### Syntax
```text
ipv6 address autoconfig
Configuration Mode
Interface Configuration Mode
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the automatic configuration of the ipv6 link-local address on VLAN interface 1:
Switch(config)# interface vlan 1
Switch(config-if)# ipv6 address autoconfig
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ipv6 address link-local

### Purpose
The ipv6 address link-local command is used to configure the ipv6 link-local address manually on a specified interface. To delete the configured link-local address, please use no ipv6 address link-local command.

### Command Mode
Not explicitly specified in the official documentation.

### Syntax
```text
ipv6 address ipv6-addr link-local
no ipv6 address ipv6-addr link-local
```

### Parameters
```text
ipv6-addr
The link-local address of the interface. It should be a standardized IPv6 address with the prefix fe80::/10, otherwise this command will be invalid.
Configuration Mode
Interface Configuration Mode
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the link-local address as fe80::1234 on the VLAN interface 1:
Switch(config)# interface vlan 1
Switch(config-if)# ipv6 address fe80::1234 link-local
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ipv6 address dhcp

### Purpose
The ipv6 address dhcp command is used to enable the DHCPv6 Client function. When this function is enabled, the Layer 3 interface will try to obtain IP from DHCPv6 server. To delete the allocated IP from DHCPv6 server and disable the DHCPv6 Client function, please use no ipv6 address dhcp command.

### Command Mode
Not explicitly specified in the official documentation.

### Syntax
```text
ipv6 address dhcp
no ipv6 address dhcp
Configuration Mode
Interface Configuration Mode
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the DHCP Client function on VLAN interface 1:
Switch(config)# interface vlan 1
Switch(config-if)# ipv6 address dhcp
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ipv6 address ra

### Purpose
This command is used to configure the interface s global IPv6 address according to the address prefix and other configuration parameters from its received RA(Router Advertisement) message. To disable this function, please use no ipv6 address ra command.

### Command Mode
Not explicitly specified in the official documentation.

### Syntax
```text
ipv6 address ra
no ipv6 address ra
Configuration Mode
Interface Configuration Mode
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the automatic ipv6 address configuration function to obtain IPv6 address through the RA message on VLAN interface 1:
Switch(config)# interface vlan 1
Switch(config-if)# ipv6 address ra
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ipv6 address eui-64

### Purpose
This command is used to manually configure a global IPv6 address with an extended unique identifier (EUI) in the low-order 64 bits on the interface. Specify only the network prefix. The last 64 bits are automatically computed from the switch MAC address. To remove a EUI-64 IPv6 address from the interface, please use the no ipv6 address eui-64 command.

### Command Mode
Not explicitly specified in the official documentation.

### Syntax
```text
ipv6 address ipv6-addr eui-64
no ipv6 address ipv6-addr eui-64
```

### Parameters
```text
ipv6-addr
Global IPv6 address with 64 bits network prefix, for example 3ffe::/64.
Configuration Mode
Interface Configuration Mode
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure an EUI-64 global address on the interface with the network prefix 3ffe::/64:
Switch(config)# interface vlan 1
Switch(config-if)# ipv6 address 3ffe::/64 eui-64
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ipv6 address

### Purpose
This command is used to manually configure a global IPv6 address on the interface. To remove a global IPv6 address from the interface, please use no ipv6 address command.

### Command Mode
Not explicitly specified in the official documentation.

### Syntax
```text
ipv6 address ipv6-addr
no ipv6 address ipv6-addr
```

### Parameters
```text
ipv6-addr
Global IPv6 address with network prefix, for example 3ffe::1/64.
Configuration Mode
Interface Configuration Mode
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the global address 3001::1/64 on VLAN interface 1:
Switch(config)# interface vlan 1
Switch(config-if)# ipv6 address 3001::1/64
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## show ipv6 interface

### Purpose
This command is used to display the configured ipv6 information of the management interface, including ipv6 function status, link-local address and global address, ipv6 multicast groups etc.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ipv6 interface
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the ipv6 information of the management interface:
Switch(config)# show ipv6 interface
```

### Notes
- Permission requirement: None.
