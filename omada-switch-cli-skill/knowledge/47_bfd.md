# BFD Configuration Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 47 BFD Configuration Commands (Only for Certain Devices)

Location: extracted Word text lines 20128-20364

## Chapter Notes

Official documentation states: Bidirectional Forwarding Detection (BFD) is a unified network detection mechanism used for rapidly detecting and monitoring the forwarding connectivity status of links or IP routes in a network. In order to minimize the impact of device failures on business operations and enhance network reliability, network devices need to promptly detect communication failures with neighboring devices to take timely action and ensure uninterrupted services. In existing networks, some links are often monitored for faults through hardware detection signals such as SDH alarms; however, not all mediums can provide hardware detection. In such cases, applications rely on the upper-layer protocol s own Hello message mechanism for fault detection. The fault detection time of upper-layer protocols typically exceeds 1 second, which is intolerable for certain applications. In L3 networks, the Hello message detection mechanism cannot detect faults for all routes, such as static routes, posing challenges in diagnosing faults in interconnection between systems. BFD facilitates rapid detection and monitoring of forwarding connectivity status for links or IP routes in a network, thereby improving network performance. By swiftly identifying communication failures between neighboring systems, users can establish backup channels promptly for communication recovery, ensuring network reliability.

- This chapter is marked `Only for Certain Devices`; treat all configuration commands as model-dependent.

## bfd-template

### Purpose
This command is used to create a BFD template. To delete the BFD template, please use the no bfd-template command.

### Command Mode
Global Configuration Mode

### Syntax
```text
bfd-template template
no bfd-template template
```

### Parameters
```text
template
Template name, the value range is 1 to 32 characters.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Create a BFD template named b1:
Switch(config)#bfd-template b1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## detect-multiplier

### Purpose
This command is used to specify the detect-multiplier of the BFD template. To restore the detect-multiplier of the BFD template to the default, please use the no detect-multiplier command.

### Command Mode
BFD Template Configuration Mode

### Syntax
```text
detect-multiplier multiplier
no detect-multiplier
```

### Parameters
```text
multiplier
The detect-multiplier of the BFD template. The value range is an integer between 3 to 50, and the default value is 3.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the detect-multiplier of BFD template b1 to 10:
Switch(config)#bfd-template b1
Switch(config-bfd)#detect-multiplier 10
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## receive-interval

### Purpose
This command is used to configure the receive interval for BFD packets. To restore the default value, please use the no receive-interval command.

### Command Mode
BFD Template Configuration Mode

### Syntax
```text
receive-interval interval
no receive-interval
```

### Parameters
```text
interval
The receive interval for BFD packets. The value range is an integer between 100 to 1000 milliseconds, and the default value is 300.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the receive interval of BFD template b1 to 500 milliseconds:
Switch(config)#bfd-template b1
Switch(config-bfd)#receive-interval 500
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## transmit-interval

### Purpose
This command is used to configure the transmit interval for BFD packets. To restore the default value, please use the no transmit-interval command.

### Command Mode
BFD Template Configuration Mode

### Syntax
```text
transmit-interval interval
no transmit-interval
```

### Parameters
```text
interval
The transmit interval for BFD packets. The value range is an integer between 100 to 1000 milliseconds, and the default value is 300.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the transmit interval of BFD template b1 to 500 milliseconds:
Switch(config)#bfd-template b1
Switch(config-bfd)#transmit-interval 500
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## transmit-interval (2)

### Purpose
This command is used to disable BFD session detection (enabled by default) and put it into AdminDown state. To enable the session, please use the no shutdown command

### Command Mode
BFD Template Configuration Mode

### Syntax
```text
shutdown
no shutdown
```

### Parameters
```text
none
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Disable the BFD session detection of BFD template b1:
Switch(config)#bfd-template b1
Switch(config-bfd)#shutdown
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## passive-mode

### Purpose
This command is used to enable the passive mode of the BFD session (disabled by default). When it is enabled, the local BFD will not actively send BFD packets. To disable the passive mode of the BFD session, please use the no passive-mode command.

### Command Mode
BFD Template Configuration Mode

### Syntax
```text
passive-mode
no passive-mode
```

### Parameters
```text
None
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the passive mode of BFD template b1:
Switch(config)#bfd-template b1
Switch(config-bfd)#passive mode
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip ospf bfd

### Purpose
This command is used to enable the BFD feature on a specific OSPF interface (disabled by default). When it is enabled, the default BFD session parameters are used. To disable BFD feature on the interface, please use the no ip ospf bfd command.

### Command Mode
interface Configuration Mode

### Syntax
```text
passive-mode
no passive-mode
```

### Parameters
```text
None
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable BFD on interface vlan 10:
Switch(config)#interface vlan 10
Switch (config-if)#ip ospf bfd
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ip ospf bfd template

### Purpose
This command is used to bind a BFD template to a specific interface with OSPF enabled. The BFD template to be bound must exist. To cancel the binding and restore the BFD session parameters to the default values, please use the no ip ospf bfd template command. By default, no BFD template is bound to a specific interface with OSPF enabled.

### Command Mode
interface Configuration Mode

### Syntax
```text
ip ospf bfd template template
no ip ospf bfd template
```

### Parameters
```text
template
Template name. It should be configured BFD template
```

### Default
By default, no BFD template is bound to a specific interface with OSPF enabled.

### Example
```text
Create BFD template b1, set the minimum sending interval to 400 ms, the minimum receiving interval to 400 ms, and the local detection multiplier to 4, enable BFD on interface vlan 10, and bind BFD template b1:
Switch(config)#bfd-template b1
Switch(config-bfd)#detect-multiplier 4
Switch(config-bfd)#receive-interval 400
Switch(config-bfd)#transmit-interval 400
Switch(config-bfd)#exit
Switch(config)#interface vlan 10
Switch(config-if)#ip ospf bfd
Switch(config-if)#ip ospf bfd template b1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ipv6 ospf bfd

### Purpose
This command is used to enable the BFD feature on a specific OSPFv3 interface (disabled by default). When it is enabled, the default BFD session parameters are used. To disable BFD feature on the interface, please use the no ipv6 ospf bfd command.

### Command Mode
interface Configuration Mode

### Syntax
```text
ipv6 ospf bfd
no ipv6 ospf bfd
```

### Parameters
```text
template
Template name. It should be configured BFD template
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable BFD on interface vlan 10:
Switch(config)#interface vlan 10
Switch(config-if)#ipv6 ospf bfd
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ipv6 ospf bfd (2)

### Purpose
This command is used to bind a BFD template to a specific interface with OSPF enabled. The BFD template to be bound must exist. To cancel the binding and restore the BFD session parameters to the default values, please use the no ipv6 ospf bfd template command. By default, no BFD template is bound to a specific interface with OSPF enabled.

### Command Mode
interface Configuration Mode

### Syntax
```text
ipv6 ospf bfd template template
no ipv6 ospf bfd template
```

### Parameters
```text
None
```

### Default
By default, no BFD template is bound to a specific interface with OSPF enabled.

### Example
```text
Create BFD template b1, set the minimum sending interval to 400 ms, the minimum receiving interval to 400 ms, and the local detection multiplier to 4, enable BFD on interface vlan 10, and bind BFD template b1:
Switch(config)#bfd-template b1
Switch(config-bfd)#detect-multiplier 4
Switch(config-bfd)#receive-interval 400
Switch(config-bfd)#transmit-interval 400
Switch(config-bfd)#exit
Switch(config)#interface vlan 10
Switch(config-if)#ip ospfv6 bfd
Switch(config-if)#ip ospfv6 bfd template b1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## isis bfd

### Purpose
This command is used to configure BFD features or bind a BFD template on a specific interface with IS-IS enabled. The BFD template to be bound must exist. To disable the BFD features on the interface or cancel the binding to restore the BFD session parameters to default values, please use the no isis bfd command. By default, the BFD feature is disabled on a specific interface with IS-IS enabled.

### Command Mode
Interface Configuration Mode

### Syntax
```text
isis bfd [template]
no isis bfd [template]
```

### Parameters
```text
template
Template name. It should be configured BFD template.
```

### Default
By default, the BFD feature is disabled on a specific interface with IS-IS enabled.

### Example
```text
Create a BFD template b1, set the minimum sending interval to 400 ms, the minimum receiving interval to 400 ms, and the local detection multiplier to 4, enable BFD on interface vlan 10, and bind BFD template b1 to the interface:
Switch(config)#bfd-template b1
Switch(config-bfd)#detect-multiplier 4
Switch((config-bfd)#receive-interval 400
Switch((config-bfd)#transmit-interval 400
Switch((config-bfd)#exit
Switch((config)#interface vlan 10
Switch((config-if)#ipv6 enable
Switch((config-if)#isis bfd
Switch((config-if)#isis bfd b1
Switch(config)#end
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## show bfd counters

### Purpose
This command is used to view the statistics of BFD sessions (such as the number of sent and received packets).

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show bfd counters
```

### Parameters
```text
None
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the statistics of BFD sessions:
Switch# show bfd counters
```

### Notes
- Permission requirement: None
- Availability: Only for certain devices according to the official chapter title.

## show bfd neighbors

### Purpose
This command is used to display the information of BFD sessions. The details command is used to display the detailed information. The ipv4 command is used to display the neighbor information of a BFD session.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show bfd neighbors
show bfd neighbors details
show bfd neighbors ipv4 [ip]
```

### Parameters
```text
IPv4 address.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the neighbor information of 192.168.0.100:
Switch# show bfd neighbors ipv4 192.168.0.100
```

### Notes
- Permission requirement: None
- Availability: Only for certain devices according to the official chapter title.
