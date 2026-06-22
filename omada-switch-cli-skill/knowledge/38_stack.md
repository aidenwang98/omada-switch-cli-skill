# Stack Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 15 Stack Commands (Only for Certain Devices)

Location: extracted Word text lines 10197-10459

## Chapter Notes

Official documentation states: Stack is a device virtualization technology that connects two and above switches supporting stack features via cables through their stack ports, which logically virtualize them to one device as a whole to forward data in the network in Layer 2 and Layer 3 protocols. Through this feature, switches can be stacked to improve reliablity, expand port numbers, increase bandwidth, simplify networking, and etc. In a stack system, the switches can be categorized mainly into two roles: Master Switch and Member Switch. The master switch manages and controls devices in the whole stack system while the member switch only forwards data as a standby device of the master switch. As the following figure shows, the switches are connected to form a stack which works as a unified system that enables multiple devices to collaborate under the management of the master switch as a whole.

- This chapter is marked `Only for Certain Devices`; treat all configuration commands as model-dependent.

## switch stack-name

### Purpose
The switch stack-name command is used to specify the name of the stack system.

### Command Mode
Global Configuration Mode

### Syntax
```text
switch stack-name {name}
```

### Parameters
```text
name
Specify the name of the stack system.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Specify the name of the stack system:
Switch(config)#switch stack-name
test
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## switch stack-group

### Purpose
The switch stack-group command is used to access the viewing page of a specified stack port group configuration of the specified device.

### Command Mode
Global Configuration Mode

### Syntax
```text
switch {unitid} stack-group {groupid}
```

### Parameters
```text
unitid
Device ID in the stack system, ranging from 1-12.
groupid
ID of the stack port group, ranging from 1-12.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enter the viewing page of a stack port group 1 on switch 1:
Switch(config)#switch 1 stack-group 1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## group-info

### Purpose
The group-info command is used to view the specified stack port group configuration of the specified device.

### Command Mode
Stack-Group Mode

### Syntax
```text
group-info
```

### Parameters
```text
group-info
Display the information of the stack group.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the inforamtion of the stack port group 1 on switch 2.
Switch(config)# switch 2 stack-group 1
Switch(stack-group)#group-info
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## interface port

### Purpose
The interface port command is used to enable the stack function for a specified slot. To disable this function, please use the no interface port command.

### Command Mode
Stack-Group Mode

### Syntax
```text
interface port
no interface port
```

### Parameters
```text
port
Port which the stack function to be enabled/disabled on
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure 1/0/28 as a stack port and join stack-group 1 of uinit 2:
Switch(stack-group)# interface 1/0/28
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## switch priority

### Purpose
The switch priority command is used to configure the stack priority of the device with specified unit ID.

### Command Mode
Global Configuration Mode

### Syntax
```text
switch {unitid} priority {priority}
```

### Parameters
```text
unitid
Device ID in the stack system, ranging from 1 to 12.
Priority
Stack priority. The higher the priority, the more likely the device is to become the master device. The value ranges from 1 to 255.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the stack priority of unit 1 as 5:
Switch(config)#switch 1 priority 5
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## switch renumber

### Purpose
The switch renumber command is used to modify the stack unit ID of a specified device, which will take effect after the switch reboots.

### Command Mode
Global Configuration Mode

### Syntax
```text
switch {unitid} renumber {new-unitid}
```

### Parameters
```text
unitid
ID in the stack system, ranging from 1 to 12.
new-unitid
New device ID to be configured, ranging from 1 to 12.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Renumber the stack unit ID of unit 1 as 2:
Switch(config)# switch 1 renumber 2
WARNING: Changing the Unit number may result in a configuration change for that unit. The interface configuration associated with the old unit number will remain as a provisioned configuration. Do you want to continue?[Y/N] y
Changing Unit Number 1 to Unid Number 1. New Unit Number will be effective after next reboot
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## switch provision

### Purpose
The switch provision command is used to create a preconfigured entry specifying unitid and device-type. After creation, you can use other configuration commands to configure the unit. The configuration will take effect after the stack is connected. To delete the entry, please use the no switch provision command.

### Command Mode
Global Configuration Mode

### Syntax
```text
switch {unitid} provision {device-type}
no switch {unitid} provision {device-type}
```

### Parameters
```text
unitid
Device ID, which should be less than 32 characters and range from 1 to 12.
device-type
Device type. The provision device needs to be of the same type as the connected device.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure provision entries:
Switch(config)#switch 1 provision 3
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## switch mac-delay

### Purpose
The switch mac-delay command is used to enable or disable the virtual MAC feature. To disable this feature, please use the parameter immediately

### Command Mode
Global Configuration Mode

### Syntax
```text
switch mac-delay { delay-time | immediately }
```

### Parameters
```text
delay-time: The delay time for virtual MAC switching(in minutes), ranging from 0-60 minutes. 0 indicates never switching the stack MAC. The default value is 10 minutes. If the original master switch in the stacking system temporarily leaves and returns within the switching time, the stack MAC address will not change. However, if the master siwtch does not return to the stacking system within the switching time, the stacking system will use the MAC address of the current master switch as the new MAC address.
immediately: When the stacking system changes, the stacking system MAC changes immediately, that is, the virtual MAC feature is not enabled.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the virtual MAC switching time to 5 minutes:
Switch(config)# switch mac-delay 5
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## switch mad enable

### Purpose
The switch mad enable command is used to enable Multi-Active Detection (MAD) globally. MAD is a protocol for detecting and handling stack splits, primarily used in stack systems to monitor operational status, detect stack splits, resolve conflicts, and recover from faults, thereby minimizing service disruption. It is a sub-feature of the stacking module, with configuration and display commands located under the stacking module. When the management channel of a stack system fails, the stack splits. The original logical device divides into multiple devices, which may retain identical system parameters and cause conflicts. To prevent this, split devices will "self-terminate" by erroring down all service ports except stacking member ports, reserved ports, and MAD-configured ports.

### Command Mode
Global Configuration Mode

### Syntax
```text
switch mad enable
```

### Parameters
```text
None.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable MAD globally:
Switch(config)# switch mad enable
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## switch mad disable

### Purpose
The switch mad disable command is used to disable MAD globally. The retain-config parameter preserves MAD-related configurations while disabling the feature.

### Command Mode
Global Configuration Mode

### Syntax
```text
switch mad disable { retain-config }
```

### Parameters
```text
retain-config
Disables MAD but retains all related configurations.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable MAD globally:
Switch(config)# switch mad disable
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## switch mad restore

### Purpose
The switch mad restore command is used to restore a stack system in recovery state by re-enabling error-down ports.

### Command Mode
Global Configuration Mode

### Syntax
```text
switch mad restore
```

### Parameters
```text
None
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Restore a stack system in recovery state by re-enabling error-down ports:
Switch(config)# switch mad restore
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## switch mad detect mode direct interface

### Purpose
The switch mad detect mode direct interface command is used to configure direct ports for MAD detection. MAD ports are blocked and cannot carry service traffic.

### Command Mode
Global Configuration Mode

### Syntax
```text
switch mad detect mode direct interface { portList }
no switch mad detect mode direct interface
```

### Parameters
```text
portList
Physical ports of the switch, e.g. (1/0/1-2, 2/0/1). The MAD port will be blocked and services cannot be performed. Please avoid performing other configurations on this port. The LAG port cannot be configured and is mutually exclusive with the stack port. That is, the stack port cannot be configured as a MAD port, and the MAD port cannot be configured as a stack port.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure port 1/0/1 for MAD detection:
Switch(config)# switch mad detect mode direct interface 1/0/1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## switch mac-delay show

### Purpose
The switch mac-delay show command is used to display the MAC-delay switching time of the current stacking system.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
switch mac-delay show
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the MAC-delay switching time of the current stacking system:
Switch# switch mac-delay show
```

### Notes
- Permission requirement: None
- Availability: Only for certain devices according to the official chapter title.

## show switch mad detail

### Purpose
The show switch mad detail command is used to display the relevant configuration of the MAD function and the current status of the switch.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show switch mad detail
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the relevant configuration of the MAD function and the current status of the switch:
Switch# show switch mad detail
```

### Notes
- Permission requirement: None
- Availability: Only for certain devices according to the official chapter title.

## show switch stack-ports

### Purpose
The show switch stack-ports command is used to display the stack port information of all members of the stack group.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show switch stack-ports
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the stack port information of all members of the stack group:
Switch#show switch stack-ports
```

### Notes
- Permission requirement: None
- Availability: Only for certain devices according to the official chapter title.

## show switch

### Purpose
The show switch command is used to display the information of all devices in the stack system.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show switch unit-id
```

### Parameters
```text
unitid: Device ID in the stack system, ranging from 1 to 12
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the information of member switch 2:
Switch#show switch 2
```

### Notes
- Permission requirement: None
- Availability: Only for certain devices according to the official chapter title.

## show switch neighbors

### Purpose
The show switch neighbors command is used to display the group ID of the stack port and the unit ID of its neighboring member device in the current stack system.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show switch neighbors
```

### Parameters
```text
None
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the unit ID of the current stack system:
Switch#show switch neghbors
```

### Notes
- Permission requirement: None
- Availability: Only for certain devices according to the official chapter title.
