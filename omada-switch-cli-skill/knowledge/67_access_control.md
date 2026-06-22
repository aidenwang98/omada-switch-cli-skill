# Access Control Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 66 Access Control Commands

Location: extracted Word text lines 26508-26638

## Chapter Notes

- Use these commands only when the requested feature and target interface/VLAN/ring/session details are clear.

## user access-control ip-based enable

### Purpose
The user access-control ip-based enable command is used to configure the access control mode IP-based. To disable the access control feature, please use no user access-control command.

### Command Mode
Global Configuration Mode

### Syntax
```text
user access-control ip-based enable
no user access-control
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the access control mode as IP-based:
Switch(config)# user access-control ip-based enable
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## user access-control ip-based

### Purpose
The user access-control ip-based command is used to limit the IP-range of the users for login. Only the users within the IP-range you set here are allowed to login. You can add up to 30 IP-based entries. To cancel the user access limit, please use no user access-control ip-based command.

### Command Mode
Global Configuration Mode

### Syntax
```text
user access-control ip-based { ip-addr ip-mask } [ snmp ] [ telnet ] [ ssh ] [ http ] [ https ] [ ping ] [ all ]
no user access-control ip-based index id
```

### Parameters
```text
ip-addr
The source IP address. Only the users within the IP-range you set here are allowed for login. 5 IP-based entries can be configured at most.
ip-mask
The subnet mask of the IP address.
[ snmp ] [ telnet ] [ ssh ] [ http ] [ https ] [ ping ] [ all ]
Specify the access interface. These interfaces are enabled by default.
Delete the specified IP-based entry.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the access-control of the user whose IP address is 192.168.0.148:
Switch(config)# user access-control ip-based 192.168.0.148 255.255.255.255
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## user access-control mac-based enable

### Purpose
The user access-control mac-based enable command is used to configure the access control mode MAC-based. To disable the access control feature, please use no user access-control command.

### Command Mode
Global Configuration Mode

### Syntax
```text
user access-control mac-based enable
no user access-control
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the access control mode as MAC-based:
Switch(config)# user access-control mac-based enable
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## user access-control mac-based

### Purpose
The user access-control mac-based command is used to limit the MAC address of the users for login. Only the user with this MAC address you set here is allowed to login. You can add up to 30 mac-based control entries. To delete the mac-based access control entry, please use no user access-control mac-based command.

### Command Mode
Global Configuration Mode

### Syntax
```text
user access-control mac-based { mac-addr } [ snmp ] [ telnet ] [ ssh ] [ http ] [ https ] [ ping ] [ all ]
no user access-control mac-based index id
```

### Parameters
```text
mac-addr
The source MAC address. Only the user with this MAC address is allowed to login.
[ snmp ] [ telnet ] [ ssh ] [ http ] [ https ] [ ping ] [ all ]
Specify the access interface. These interfaces are enabled by default.
Specify the ID of the mac-based entry to be deleted.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure that only the user whose MAC address is 00:00:13:0A:00:01 is allowed to login:
Switch(config)# user access-control mac-based 00:00:13:0A:00:01
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## user access-control port-based enable

### Purpose
The user access-control port-based enable command is used to configure the access control mode Port-based. To disable the access control feature, please use no user access-control command.

### Command Mode
Global Configuration Mode

### Syntax
```text
user access-control port-based enable
no user access-control
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the access control mode as Port-based:
Switch(config)# user access-control port-based enable
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## user access-control port-based

### Purpose
The user access-control port-based command is used to limit the ports for login. Only the users connected to these ports you set here are allowed to login. You can add up to 30 port-based control entries. To delete the port-based access control entry, please use no user access-control port-based command.

### Command Mode
Global Configuration Mode

### Syntax
```text
user access-control port-based interface { gigabitEthernet port-list } [ snmp ] [ telnet ] [ ssh ] [ http ] [ https ] [ ping ] [ all ]
no user access-control port-based index id
```

### Parameters
```text
port-list
The list group of Ethernet ports, in the format of 1/0/1-4. You can appoint 5 ports at most.
[ snmp ] [ telnet ] [ ssh ] [ http ] [ https ] [ ping ] [ all ]
Specify the access interface. These interfaces are enabled by default.
Specify the ID of the port-based entry to be deleted.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure that only the users connected to ports 2-6 are allowed to login:
Switch(config)# user access-control port-based interface gigabitEthernet 1/0/2-6
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## user access-control ipv6-based enable

### Purpose
The user access-control ipv6-based enable command is used to configure the access control mode IPV6-based. To disable the access control feature, please use no user access-control command.

### Command Mode
Global Configuration Mode

### Syntax
```text
user access-control ipv6-based enable
no user access-control
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the access control mode as IPV6-based:
Switch(config)# user access-control ipv6-based enable
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## user access-control ipv6-based

### Purpose
The user access-control ipv6-based command is used to limit the IPV6-range of the users for login. Only the users within the IPV6-range you set here are allowed to login. You can add up to 30 IPV6-based entries. To cancel the user access limit, please use no user access-control ipv6-based command.

### Command Mode
Global Configuration Mode

### Syntax
```text
user access-control ipv6-based { ipv6-addr } [ snmp ] [ telnet ] [ ssh ] [ http ] [ https ] [ ping ] [ all ]
no user access-control ipv6-based index id
```

### Parameters
```text
Ipv6-addr
The source IP address. Only the users within the IPV6-range you set here are allowed for login.
[ snmp ] [ telnet ] [ ssh ] [ http ] [ https ] [ ping ] [ all ]
Specify the access interface. These interfaces are enabled by default.
Delete the specified IP-based entry that ranges from 1 to 30.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the access-control of the user whose IP address is fe80::1234 :
Switch(config)# user access-control ipv6-based fe80::1234
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
