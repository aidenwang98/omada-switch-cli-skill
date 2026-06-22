# VRRP Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 55 VRRP Commands (Only for Certain Devices)

Location: extracted Word text lines 24202-24512

## Chapter Notes

Official documentation states: VRRP (Virtual Routing Redundancy Protocol) is a function on the switch that dynamically assigns responsibility for a virtual router to one of the VRRP routers on a LAN. The VRRP router that controls the IP address associated with a virtual router is called the Master and will forward packets sent to this IP address. This will allow any Virtual Router IP address on the LAN to be used as the default first hop router by end hosts.

- This chapter is marked `Only for Certain Devices`; treat all configuration commands as model-dependent.

## ip vrrp vrid

### Purpose
The ip vrrp vrid command is used to enable the VRRP-V2 protocol on the interface and specify the virtual router ID for it. To disable the protocol on the interface, please use the no ip vrrp vrid command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip vrrp vrid vrid-index
no ip vrrp vrid vrid-index
```

### Parameters
```text
vrid-index
Virtual router ID, ranging from 1 to 255.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the VRRP-V2 protocol on VLAN 2 and specify the virtual router ID as 5:
Switch(config)#interface vlan 2
Switch(config-if)#ip vrrp vrid 5
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ipv6 vrrp vrid

### Purpose
The ipv6 vrrp vrid command is used to enable the VRRP-V3 protocol on the interface and specify the virtual router ID for it. To disable the protocol on the interface, please use the no ipv6 vrrp vrid command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ipv6 vrrp vrid vrid-index
no ipv6 vrrp vrid vrid-index
```

### Parameters
```text
vrid-index
Virtual router ID, ranging from 1 to 255.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the VRRP-V3 protocol on VLAN 2 and specify the virtual router ID as 5:
Switch(config)#interface vlan 2
Switch(config-if)#ipv6 vrrp vrid 5
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip vrrp vrid authentication-mode

### Purpose
The ip vrrp vrid authentication-mode command is used to configure the authentication mode of the virtual router on the specified interface. To restore to the default authentication mode, please use the no ip vrrp vrid authentication-mode command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip vrrp vrid vrid-index authentication-mode {simple | md5} password
no ip vrrp vrid vrid-index authentication-mode
```

### Parameters
```text
vrid-index
Virtual router ID, ranging from 1 to 255.
simple | md5
Authentication mode, by default it is None and no authentication will be performed.
simple
refers to using a text password for authentication, and
refers to using a text password to perform the authentication of MD5, which has a higher security than Simple mode.
password
Password, a string of 1 to 8 alphabets, numbers or symbols. Passwords are casesensitive, spaces allowed but leading spaces ignored, and cannot contain question marks. It is empty by default.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the md5 authentication mode on the VLAN 2, specify the password as 123 and the virtual router ID as 5:
Switch(config)#interface vlan 2
Switch(config-if)#ip vrrp vrid 5 authentication-mode md5 123
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip vrrp vrid description

### Purpose
The ip vrrp vrid description command is used to configure and modify the description for the virtual router. To delete the description, please use the no ip vrrp vrid description command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip vrrp vrid vrid-index description description
```

### Parameters
```text
vrid-index
Virtual router ID, ranging from 1 to 255.
description
A string describing the virtual router, containing up to 256 characters, consisting only of numbers, English letters, and dashes.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the virtual router desceiption as vr5 and the virtual router ID as 5 on the VLAN 2:
Switch(config)#interface vlan 2
Switch(config-if)#ip vrrp vrid 5 description vr5
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip vrrp vrid preempt-mode

### Purpose
The ip vrrp vrid preempt-mode command is used to configure the preemption mode and delay time of the specified virtual router on the interface. To set the specified virtual router on the interface to non-preempt mode, please use the no ip vrrp vrid preempt-mode command. By default, the virtual router is in preempt mode.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip vrrp vrid vrid-index preempt-mode [ timer-delay delay-value ]
no ip vrrp vrid vrid-index preempt-mode
```

### Parameters
```text
vrid-index
Virtual router ID, ranging from 1 to 255.
delay-value
When the current primary router is deemed unavailable, the backup router waits before switching to the primary router. The value ranges from 0 to 255 seconds, and the default is 0.
```

### Default
By default, the virtual router is in preempt mode.

### Example
```text
Configure the virtual router preemption time to 12 seconds and the virtual router ID to 5 on VLAN 2:
Switch(config)#interface vlan 2
Switch(config-if)#ip vrrp vrid 5 preempt-mode timer-delay 12
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip vrrp vrid priority

### Purpose
The ip vrrp vrid priority command is used to configure the priority of the specified virtual router on the interface. To restore the default priority, please use the no ip vrrp vrid priority command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip vrrp vrid vrid-index priority priority
no ip vrrp vrid vrid-index priority
```

### Parameters
```text
vrid-index
Virtual router ID, ranging from 1 to 255.
priority
Priority, value ranges from 1 to 254. The default priority is 100.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the virtual router priority to 1110 and the virtual router ID to 5 on VLAN 2:
Switch(config)#interface vlan 2
Switch(config-if)#ip vrrp vrid 5 priority 110
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip vrrp vrid timer-advertise

### Purpose
The ip vrrp vrid timer-advertise command is used to configure the frequency at which the specified virtual router sends advertisements on the interface. To restore the default advertisement interval, please use the no ip vrrp vrid timer-advertise command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip vrrp vrid vrid-index timer-advertise adver-interval
no ip vrrp vrid vrid-index timer-advertise
```

### Parameters
```text
vrid-index
Virtual router ID, ranging from 1 to 255.
adver-interval
Advertisement interval, for VRRP-V2, the value range is 1~255, the unit is seconds, the default is 1 second; for VRRP-V3, the value range is 100~4095, the unit is centiseconds, the default is 100 centiseconds.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the virtual router advertisement interval to 12 seconds and the virtual router ID to 5 on VLAN 2:
Switch(config)#interface vlan 2
Switch(config-if)#ip vrrp vrid 5 timer-advertise 12
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip vrrp vrid track

### Purpose
The ip vrrp vrid track command is used to configure the specified virtual router on the interface to add a tracking interface. To delete the tracking interface, please use the no ip vrrp vrid track command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip vrrp vrid vrid-index track interface {{fastEthernet | gigabitEthernet | hundred-gigabitEthernet | ten-gigabitEthernet | twentyFive-gigabitEthernet | two-gigabitEthernet } port / port-channel portchannel-id / vlan vlan-id} [reduce-priority priority]
no ip vrrp vrid vrid-index track interface {{fastEthernet | gigabitEthernet | hundred-gigabitEthernet | ten-gigabitEthernet | twentyFive-gigabitEthernet | two-gigabitEthernet } port / port-channel portchannel-id / vlan vlan-id}
```

### Parameters
```text
vrid-index
Virtual router ID, ranging from 1 to 255.
fastEthernet | gigabitEthernet | hundred-gigabitEthernet | ten-gigabitEthernet | twentyFive-gigabitEthernet | two-gigabitEthernet
Port type, which must be a layer 3 interface.
port
Port number.
portchannel-id
LAG group number.
vlan-id
Decreasing priority of the tracked interface, ranging from 1 to 254, and the default is 10.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the virtual router to track VLAN 3 on the VLAN 2 with a decreasing priority of 20 and a virtual router ID of 5:
Switch(config)#interface vlan 2
Switch(config-if)#ip vrrp vrid 5 track interface vlan 3 reduce-priority 20
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip vrrp vrid version

### Purpose
The ip vrrp vrid version command is used to configure or switch the VRRP version of the specified virtual router on the interface. The default is VRRP-V2.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip vrrp vrid vrid-index version vrrp-version
```

### Parameters
```text
vrid-index
Virtual router ID, ranging from 1 to 255.
vrrp-version
VRRP protocol version, the value is 2 or 3. Due to the differences between VRRP-V2 and VRRP-V3, version switching is only allowed when authentication is not configured, ipv6 virtual address is not configured, and the default notification time is used.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch the virtual router on the VALN 2 to VRRP-V3, and the virtual router ID to 5:
Switch(config)#interface vlan 2
Switch(config-if)#ip vrrp vrid 5 version 3
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip vrrp vrid virtual-ip

### Purpose
The ip vrrp vrid virtual-ip command is used to add a primary virtual IPv4 address to a virtual router. Each virtual router has only one primary virtual IP that cannot be deleted. If the virtual router does not exist, a VRRP-V2 version of the virtual router will be automatically created.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip vrrp vrid vrid-index virtual-ip virtual-ip
```

### Parameters
```text
vrid-index
Virtual router ID, ranging from 1 to 255.
virtual-ip
The virtual IP address of the virtual router, which must be in the same network segment as the interface.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Add virtual IP address 192.168.0.10 on VALN 2 with the virtual router ID 5:
Switch(config)#interface vlan 2
Switch(config-if)#ip vrrp vrid 5 virtual-ip 192.168.0.10
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip vrrp vrid virtual-ip secondary

### Purpose
The ip vrrp vrid virtual-ip secondary command is used to add a secondary virtual IPv4 address to a virtual router. Each virtual router can be configured with up to 32 IP addresses. To delete the corresponding secondary virtual IP address, use the no ip vrrp vrid virtual-ip secondary command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ip vrrp vrid vrid-index virtual-ip virtual-ip secondary
no ip vrrp vrid vrid-index virtual-ip virtual-ip secondary
```

### Parameters
```text
vrid-index
Virtual router ID, ranging from 1 to 255.
virtual-ip
The virtual IP address of the virtual router, which must be in the same network segment as the interface.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Add secondary virtual IP address 192.168.0.11 on VALN 2 with the virtual router ID 5:
Switch(config)#interface vlan 2
Switch(config-if)#ip vrrp vrid 5 virtual-ip 192.168.0.10 secondary
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ipv6 vrrp vrid address link-local

### Purpose
The ipv6 vrrp vrid address link-local command is used to add a virtual ipv6 local link address to a virtual router. Each virtual router has only one virtual link-local address. If the virtual router does not exist, a VRRP-V3 version of the virtual router will be automatically created. To delete the virtual link-local address, use the no ipv6 vrrp vrid address link-local command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ipv6 vrrp vrid vrid-index address virtual-linklocal link-local
no ipv6 vrrp vrid vrid-index address virtual-linklocal link-local
```

### Parameters
```text
vrid-index
Virtual router ID, ranging from 1 to 255.
virtual-linklocal
The virtual link-local address of the virtual router. The address prefix should be the fe80::/10 standard ipv6 address.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Add virtual ipv6 link-local address fe80::10 on VALN 2 with the virtual router ID 5:
Switch(config)#interface vlan 2
Switch(config-if)#ipv6 vrrp vrid 5 address fe80::10 link-local
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ipv6 vrrp vrid address

### Purpose
The ipv6 vrrp vrid address command is used to add a virtual ipv6 address to a virtual router. Each virtual router can be configured with up to 32 ipv6 addresses. To delete the virtual address, use the no ipv6 vrrp vrid address command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ipv6 vrrp vrid vrid-index address virtual-ipv6
no ipv6 vrrp vrid vrid-index address virtual-ipv6
```

### Parameters
```text
vrid-index
Virtual router ID, ranging from 1 to 255.
virtual-ipv6
The global ipv6 address of the virtual router, which must be in the same network segment as the interface ipv6 address.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Add virtual ipv6 global address 3001::1 on VALN 2 with the virtual router ID 5:
Switch(config)#interface vlan 2
Switch(config-if)#ipv6 vrrp vrid 5 address 3001::1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## show ip vrrp

### Purpose
The show ip vrrp command is used to display basic configuration information of all virtual routers or a specified virtual router.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip vrrp [vrid vrid-index] [interface {{fastEthernet | gigabitEthernet | hundred-gigabitEthernet | ten-gigabitEthernet | twentyFive-gigabitEthernet | two-gigabitEthernet } port / port-channel portchannel-id / vlan vlan-id}]
```

### Parameters
```text
vrid-index
Virtual router ID, ranging from 1 to 255.
fastEthernet | gigabitEthernet | hundred-gigabitEthernet | ten-gigabitEthernet | twentyFive-gigabitEthernet | two-gigabitEthernet
Port type, which must be a layer 3 interface.
port
Port number.
portchannel-id
LAG group number.
vlan-id
VLAN value.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the configuration information of the virtual router ID 5 on VLAN 2:
Switch(config)#show ip vrrp vrid 5 interface vlan 2
```

### Notes
- Permission requirement: None
- Availability: Only for certain devices according to the official chapter title.

## show ip vrrp statistics

### Purpose
The show ip vrrp statistics command is used to display statistics for all virtual routers or a specified virtual router.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip vrrp statistics [vrid vrid-index] [interface {{fastEthernet | gigabitEthernet | hundred-gigabitEthernet | ten-gigabitEthernet | twentyFive-gigabitEthernet | two-gigabitEthernet } port / port-channel portchannel-id / vlan vlan-id}]
```

### Parameters
```text
vrid-index
Virtual router ID, ranging from 1 to 255.
fastEthernet | gigabitEthernet | hundred-gigabitEthernet | ten-gigabitEthernet | twentyFive-gigabitEthernet | two-gigabitEthernet
Port type, which must be a layer 3 interface.
port
Port number.
portchannel-id
LAG group number.
vlan-id
VLAN value.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display statistics of the virtual router ID 5 on VLAN 2:
Switch(config)#show ip vrrp statistics vrid 5 interface vlan 2
```

### Notes
- Permission requirement: None
- Availability: Only for certain devices according to the official chapter title.

## clear ip vrrp statistics

### Purpose
The clear ip vrrp statistics command is used to clear the statistics of all virtual routers on the switch.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
clear ip vrrp statistics
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Clear the statistics of all virtual routers on the switch:
Switch(config)#clear ip vrrp statistics
```

### Notes
- Permission requirement: None
- Availability: Only for certain devices according to the official chapter title.
