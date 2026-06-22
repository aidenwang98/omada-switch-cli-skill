# Port Security Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 73 Port Security Commands (Only for Certain Devices)

Location: extracted Word text lines 28222-28276

## Chapter Notes

Official documentation states: You can use the Port Security feature to limit the number of MAC addresses that can be learned on each port, thus preventing the MAC address table from being exhausted by the attack packets. In addtion, the switch can send a notification if the number of learned MAC addresses on the port exceeds the limit.

- This chapter is marked `Only for Certain Devices`; treat all configuration commands as model-dependent.

## mac address-table max-mac count

### Purpose
The mac address-table max-mac-count command is used to enable the port security feature of the port and configure the related parameters. To disable the feature and restore the parameters to defaults on the port, please use no mac address-table max-mac-count command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
mac address-table max-mac-count { [ max-number num ] [ exceed-max-learned enable | disable ] [ mode { dynamic | static | permanent } ] [ status { forward | drop | disable } ] }
no mac address-table max-mac-count [ max-number | mode | status ]
```

### Parameters
```text
num: The maximum number of MAC addresses that can be learned on a port, ranging from 0 ~ 64. The default value is 64.
status: Select the action to be taken when the number of MAC addresses reaches the maximum number of MAC addresses learned on the port. By default, this function is disabled.
forward: Forward but not learn packets after reaching the upper limit of secure addresses.
drop: Discard packets after reaching the upper limit of secure addresses.
disable: Disable port security.
exceed-max-learned {enable | disable}: When the upper limit is reached, an SNMP message will be generated and sent to the network administrator.
```

### Default
By default, this function is disabled.

### Example
```text
Set the maximum number of MAC addresses that can be learned on port 1/0/1 as 30, enable exceed-max-leaned feature and configure the mode as permanent and the status as drop:
Switch (config)#interface gigabitEthernet 1/0/1
Switch(config-if)#mac address-table max-mac-count max-number 30 exceed-max-learned enable mode permanent status drop
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## mac address-table sticky mac

### Purpose
mac address-table sticky mac command is used to configure sticky MAC mannually. To delete the specified sticky MAC entry, please use the no mac address-table sticky mac command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
mac address-table sticky mac mac-address vip vlan-id interface { fastEthernet port | gigabitEthernet port | hundred-gigabitEthernet port | ten-gigabitEthernet port | twentyFive-gigabitEthernet port | two-gigabitEthernet port }
no mac address-table sticky mac mac-address vip vlan-id
```

### Parameters
```text
mac-address: The MAC address of the entry to be added.
vlan-id: The VLAN ID of the entry to be added. The range is 1 to 4094.
port: The port of the entry to be added.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Add a sticky address 00:02:58:4f:6c:23 and bind it to sticky mode port 1, VLAN 1:
Switch(config)#mac address-table sticky mac 00:02:58:4f:6c:23 vid 1 interface gigabitEthernet 1/0/1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## mac address-table sticky save-time

### Purpose
mac address-table sticky save-time command is used to configure the interval for saving sticky MAC. To restore the default configuration, please use the no mac address-table sticky save-time command.

### Command Mode
Global Configuration Mode

### Syntax
```text
mac address-table sticky save-time time
no mac address-table sticky save-time
```

### Parameters
```text
time: The interval for saving sticky MAC, which is 600s by default.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the save-time to 50S:
Switch(config)# mac address-table sticky save-time 50
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.
