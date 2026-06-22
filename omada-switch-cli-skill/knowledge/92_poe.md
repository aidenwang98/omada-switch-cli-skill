# PoE Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 92 PoE Commands (Only for Certain Devices)

Location: extracted Word text lines 31876-32196

## Chapter Notes

Official documentation states: Note: PoE commands are only available on certain devices. PoE (Power over Ethernet) technology describes a system to transmit electrical power along with data to remote devices over standard twisted-pair cable in an Ethernet network. It is especially useful for supplying power to IP telephones, wireless LAN access points, cameras and so on.

- This chapter is marked `Only for Certain Devices`; treat all configuration commands as model-dependent.

## power inline consumption (global)

### Purpose
The power inline consumption command is used to configure the max power the PoE switch can supply globally.

### Command Mode
Global Configuration Mode

### Syntax
```text
power inline consumption power-limit
```

### Parameters
```text
power-limit
The max power the PoE switch can supply.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the max power the PoE switch can supply as 160 W:
Switch(config)# power inline consumption 160
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## power profile

### Purpose
The power profile command is used to create a PoE profile for the switch. To delete the configured PoE profile configuration, please use no power profile command. PoE Profile is a short cut for the configuration of the PoE port. In a PoE profile, the PoE status, PoE priority and power limit are configured. You can specify a PoE profile for each PoE port individually.

### Command Mode
Global Configuration Mode

### Syntax
```text
power profile name
[supply {enable | disable} [priority {low | middle | high} [consumption { power-limit | auto | class1 | class2 | class3 | class4 } ] ] ]
no power profile name
```

### Parameters
```text
name
The PoE profile name, ranging from 1 to 16 characters. If the name being assigned contains spaces then put it inside double quotes.
supply
The PoE status of the port in the profile. By default, the PoE status is
enable
priority
The PoE priority of the port in the profile. The priority levels include
high
middle
and
in descending order. When the supply power exceeds the system power limit, the PD linked to the port with lower priority will be disconnected. By default, the PoE priority is
consumption
The max power the port in the profile can supply, with five options:
power-limit
auto
class1
class2
class3
and
class4
Power-limit
indicates you can manually enter a value ranging from 1 to 300. The value is in the unit of 0.1 watt. For instance, if you want to configure the max power as 5w, you should enter 50.
Auto
indicates the value is assigned automatically by the PoE switch.
Class1
represents 4w.
Class2
represents 7w.
Class3
represents 15.4w.
Class4
represents 30w.
```

### Default
By default, the PoE status is enable priority The PoE priority of the port in the profile. By default, the PoE priority is consumption The max power the port in the profile can supply, with five options: power-limit auto class1 class2 class3 and class4 Power-limit indicates you can manually enter a value ranging from 1 to 300.

### Example
```text
Create a PoE profile named
IP Camera
whose PoE status is
enable
, PoE priority is
and the power limit is
Switch(config)# power profile
IP Camera
supply enable priority low consumption 50
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## power inline consumption (interface)

### Purpose
The power inline consumption command is used to configure the power limit the corresponding port can supply.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet)

### Syntax
```text
power inline consumption { power-limit | auto | class1 | class2 | class3 | class4 }
```

### Parameters
```text
power-limit
The max power the port in the profile can supply, with five options:
power-limit
auto
class1
class2
class3
and
class4
Power-limit
indicates you can manually enter a value ranging from 1 to 300. The value is in the unit of 0.1 watt. For instance, if you want to configure the max power as 5w, you should enter 50.
Auto
indicates the value is assigned automatically by the PoE switch.
Class1
represents 4w.
Class2
represents 7w.
Class3
represents 15.4w.
Class4
represents 30w.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the power limit as
for port 2:
Switch(config)# interface gigabitEthernet 1/0/2
Switch(config-if)# power inline consumption 50
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## power inline consumption (unit)

### Purpose
The power inline unit consumption command is used to specify the maximum power a stack unit can supply.

### Command Mode
Global Configuration Mode

### Syntax
```text
power inline unit {unit id} consumption {power-limit}
```

### Parameters
```text
unit id
Stack unit ID, ranging from 1-4
power-limit
Specify the maximum power the PoE switch can supply, which depends on actual power usage.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Specify the maximum power unit 1 can supply to 402W:
Switch(config)#power inline unit 1 consumption 402
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## power inline priority

### Purpose
The power inline priority command is used to configure the PoE priority for the corresponding port

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet)

### Syntax
```text
power inline priority { low | middle | high }
```

### Parameters
```text
priority
The PoE priority of the port. The priority levels include
high
middle
and
in descending order. When the supply power exceeds the system power limit, the PD linked to the port with lower priority will be disconnected. By default, the priority level is
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the PoE priority as
for port 2:
Switch(config)# interface gigabitEthernet 1/0/2
Switch(config-if)# power inline priority low
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## power inline supply

### Purpose
The power inline supply command is used to configure the PoE status of the corresponding port.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet)

### Syntax
```text
power inline supply { enable | disable }
```

### Parameters
```text
enable | disable
The PoE status of the port. By default, the PoE status is
enable
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the PoE feature for port 2:
Switch(config)# interface gigabitEthernet 1/0/2
Switch(config-if)# power inline supply enable
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## power inline profile

### Purpose
The power inline profile command is used to bind a PoE profile to the corresponding port. To cancel the bind relation, please use no power inline profile command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet)

### Syntax
```text
power inline profile name
no power inline profile
```

### Parameters
```text
name
The name of the PoE profile to be bound to the port. If the name being assigned contains spaces then put it inside double quotes.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Bind the PoE profile named
IP Camera
to port 2:
Switch(config)# interface gigabitEthernet 1/0/2
Switch(config-if)# power inline profile
IP Camera
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## power inline time-range

### Purpose
The power inline time-range command is used to bind a PoE time-range to the corresponding port. To cancel the bind relation, please use no power inline time-range command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
power inline time-range name
no power inline time-range
```

### Parameters
```text
name
The name of the PoE time-range to be bound to the port.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Bind the PoE time-range named
tRange2" to port 2:
Switch(config)# interface gigabitEthernet 1/0/2
Switch(config-if)# power inline time-range tRange2
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## show power inline

### Purpose
The show power inline command is used to display the global PoE information of the system.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show power inline
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the PoE information of the system:
Switch# show power inline
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## show power inline configuration interface

### Purpose
The show power inline configuration interface command is used to display the PoE configuration of the certain port.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show power inline configuration interface [ fastEthernet port | gigabitEthernet port | ten-gigabitEthernet port ]
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
Display the PoE configuration of all ports:
Switch# show power inline configuration interface
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## show power inline information interface

### Purpose
The show power inline information command is used to display the PoE information of the certain port.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show power inline information interface [ fastEthernet port | gigabitEthernet port | ten-gigabitEthernet port ]
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
Display the PoE information of all ports:
Switch# show power inline information interface
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## show power profile

### Purpose
The show power profile command is used to display the defined PoE profile.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show power profile
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the defined PoE profile:
Switch# show power profile
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## power recovery status enable

### Purpose
The power recovery status enable command is used to enable the power auto recovery function globally. To disable this function, please use power recovery status disable command

### Command Mode
Global Configuration Mode

### Syntax
```text
power recovery status enable
power recovery status disable
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the power auto recovery function globally:
Switch(config)# power recovery status enable
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## power recovery status

### Purpose
The power recovery ststus command is used to configure the power recovery status and parameters of a specified port..

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet)

### Syntax
```text
power recovery ststus {disable|enable} ip ipv4_addr startup startup delay interval ping interval retry failure thresholdbreak break time
```

### Parameters
```text
ipv4_addr
Ipv4 address, in string format, for example, 192.168.0.1.
startup delay
Feature startup delay(S), ranging from 30 to 600.
ping interval
Ping package interval(S), ranging from 10 to 120.
failure threshold
Number of ping failures, ranging from 1 to 10.
break time
Break time after detecting abnormal POE status(S), ranging from 3 to 120.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the power recovery status of port 2 and configure relevant parameters:
Switch(config)# interface gigabitEthernet 1/0/2
Switch(config-if)# power recovery status enable ip 192.168.0.1 startup 60 interval 60 retry 5 break 60
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## show power recovery

### Purpose
The show power recovery command is used to display all POE auto recovery configurations.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show power recovery
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display all POE auto recovery configurations:
Switch(config)#show power recovery
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## show power recovery interface

### Purpose
The show power recovery interface command is used to display power auto recovery configurations of the selected port.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show power recovery interface [fastEthernet | gigabitEthernet | two-gigabitEthernet | ten-gigabitEthernet] port list
```

### Parameters
```text
interface
Port type.
port list
Port number list.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display power auto recovery configurations of:
Switch(config)#show power recovery
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.
