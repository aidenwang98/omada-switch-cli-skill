# RIPng Configuration Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 44 RIPng Configuration Commands (Only for Certain Devices)

Location: extracted Word text lines 18785-18963

## Chapter Notes

Official documentation states: RIPng (RIP next generation) is a routing protocol that improves the RIP protocol in order to solve the compatibility problem between the RIP protocol and IPv6.

- This chapter is marked `Only for Certain Devices`; treat all configuration commands as model-dependent.

## router ripng

### Purpose
This router ripng command is used to enable the RIPng function. Only when the RIPng function is enabled can'the global configuration of the RIPng function be performed. When the RIPng function is disabled, the global configuration of the RIPng function will be cleared. To disable this function, please use the no router ripng command. You can specify to create a RIPng instance under a certain VRF.

### Command Mode
Global Configuration Mode

### Syntax
```text
router ripng [vrf vrf-name]
no router ripng [vrf vrf-name]
```

### Parameters
```text
vrf-name: VRF instance name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the RIPng function in VRF v1:
Switch(config)#router ripng vrf v1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ipv6 rip enable

### Purpose
The ipv6 rip enable command is used to enable the ripng function of the interface. This command only takes effect after the global switch of RIPng is enabled.To disable this function, please use no ipv6 rip enable command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ipv6 rip enable
no ipv6 rip enable
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the RIPng function of VLAN 1:
Switch(config)#interface vlan 1
Switch(config-if)# ipv6 rip enable
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## timer basic

### Purpose
The timer basic command is used to configure the RIPng timer. To restore the timer configuration to its default, please use the no timer basic command.

### Command Mode
Router Configuration Mode

### Syntax
```text
timer basic update-value timeout-value garbage-collect-value
no network
```

### Parameters
```text
update-value: Routing table update time, ranging from 5 to 86400 seconds. The default value is 30.
timeout-value: Routing table aging time, ranging from 5 to 86400 seconds. The default value is 180.
garbage-collect-value: The expiration time after the routing entry is unreachable. When the entry is unreachable, the routing entry is removed from the routing table after the expiration time. The range is 5~86400 seconds, and the default value is 120.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set the routing table update time to 50 seconds, the routing table aging time to 100 seconds, and the routing entry expiration time to 100 seconds:
Switch(config-router)#timer basic 50 100 100
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## default-metric

### Purpose
The default-metric command is used to set the default metric for redirect routes. To restore the default configuration, please use the no default-metric command.

### Command Mode
Router Configuration Mode

### Syntax
```text
default-metric metric
no default-metric
```

### Parameters
```text
metric: The default metric of the redirect route, ranging from 1 to 15, and the default value is 1.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set the default metric for redirection routes to 5:
Switch(config-router)#default-metric 5
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## redistribute

### Purpose
The redistribute command is used to set RIPng to redirect external routes. Its no command has two forms: if it does not contain the metric parameter, it is used to disable the redirection function of the corresponding external route. If it contains the metric parameter, it is used to restore the metric used for redirect routes to the default value.

### Command Mode
Router Configuration Mode

### Syntax
```text
redistribute { ospfv3 | static } [ metric metric-value ]
no redistribute { ospfv3 | static } [ metric ]
```

### Parameters
```text
ospfv3: Enable RIPng redirect OSPFv3 routing function.
static: Enable RIPng redirect static routing function.
metric-value: The metric of the redirect route.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set RIPng to redirect OSPFv3, and set metric to 3:
Switch(config-router)#redistribute ospfv3 metric 3
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## allow-ecmp

### Purpose
The allow-ecmp command is used to enable the ECMP function. To disable this function, please use the no allow-ecmp command.

### Command Mode
Router Configuration Mode

### Syntax
```text
allow-ecmp
no allow-ecmp
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the ECMP function of RIPng:
Switch(config-router)#allow-ecmp
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## default-information originate

### Purpose
The default-information originate command is used to introduce a default route into RIPng. To disable this function, please use the no default-information originate command.

### Command Mode
Router Configuration Mode

### Syntax
```text
default-information originate
no default-information originate
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Introduce a default route into RIPng:
Switch(config-router)#default-information originate
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## passive-interface

### Purpose
The passive-interface command is used to configure the interface not to send RIPng packets but only to receive RIPng packets. A unicast response will be sent out when a neighbor is configured at the same time.To disable this function, please use the no passive-interface command.

### Command Mode
Router Configuration Mode

### Syntax
```text
passive-interface interface { fastEthernet | gigabitEthernet | hundred-gigabitEthernet | loopback | port-channel | ten-gigabitEthernet | twentyFive-gigabitEthernet | two-gigabitEthernet | vlan } interface-value
no passive-interface interface { fastEthernet | gigabitEthernet | hundred-gigabitEthernet | loopback | port-channel | ten-gigabitEthernet | twentyFive-gigabitEthernet | two-gigabitEthernet | vlan } interface-value
```

### Parameters
```text
interface-value: Specify the interface to be configured as passive-interface.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure VLAN 2 as passive-interface:
Switch(config-router)# passive-interface interface vlan 2
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip rip split-horizon

### Purpose
The ipv6 rip split-horizon command is used to configure the split horizon function of the interface. This function is enabled by default. When this function is enabled, RIPng will not send routing entries learned from this interface out of this interface. When this function is disabled, RIPng will only send routing entries according to the routing table. To disable this function, please use the no ipv6 rip split-horizon command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
ipv6 rip split-horizon [ poison-reverse ]
no ipv6 rip split-horizon
```

### Parameters
```text
poison-reverse: Enable the poison-reverse function of the interface. After this function is enabled, the entries learned from the interface will have the metric set to 16 before being sent out. Disable the poison reversal function by configuring the ipv6 rip split-horizon command.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the poison-reverse function of VLAN 1:
Switch (config)#interface vlan 1
Switch (config-if)#ipv6 rip split-horizon poison-reverse
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## show ipv6 rip

### Purpose
The show ipv6 rip command is used to display the RIPng routing table.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ipv6 rip [vrf vrf-name]
```

### Parameters
```text
vrf-name: VRF instance name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the RIPng routing table in VRF v1:
Switch#show ipv6 rip vrf v1
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## show ipv6 rip status

### Purpose
The show ipv6 rip status command is used to display the RIPng status.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ipv6 rip [vrf vrf-name] status
```

### Parameters
```text
vrf-name: VRF instance name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the RIPng status in VRF v1:
Switch#show ipv6 rip status vrf v1
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## clear ipv6 rip

### Purpose
The clear ipv6 rip command is used to clear the routing entries for RIPng learning and re-request routing information from other devices.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
clear ipv6 rip [vrf vrf-name]
```

### Parameters
```text
vrf-name: VRF instance name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Clear the routing entries for RIPng learning and rerequest routing information from other devices:
Switch#clear ipv6 rip vrf v1
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.
