# DLDP Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 89 DLDP Commands (Only for Certain Devices)

Location: extracted Word text lines 31050-31161

## Chapter Notes

Official documentation states: DLDP (Device Link Detection Protocol) is used to monitor the link state of fiber-optic or twisted-pair Ethernet cables. When a unidirectional link is detected, the corresponding port will be shut down automatically or manually (depending on the shut mode configured).

- This chapter is marked `Only for Certain Devices`; treat all configuration commands as model-dependent.

## dldp (global)

### Purpose
The dldp command is used to enable the DLDP function globally. To disable it, please use no dldp command.

### Command Mode
Global Configuration Mode

### Syntax
```text
dldp
no dldp
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the DLDP function globally:
Switch(config)# dldp
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## dldp interval

### Purpose
The dldp interval command is used to define the interval of sending advertisement packets on ports that are in the advertisement state.

### Command Mode
Global Configuration Mode

### Syntax
```text
dldp interval interval-time
```

### Parameters
```text
interval-time
The interval of sending advertisement packets. It ranges from 1 to 30 seconds. By default, it is 5 seconds.
```

### Default
By default, it is 5 seconds.

### Example
```text
Specify the interval of sending advertisement packets as 10 seconds:
Switch(config)# dldp interval 10
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## dldp shut-mode

### Purpose
The dldp shut-mode command is used to configure the shutdown mode when a unidirectional link is detected.

### Command Mode
Global Configuration Mode

### Syntax
```text
dldp shut-mode { auto | manual }
```

### Parameters
```text
auto
The switch automatically shuts down ports when a unidirectional link is detected. By default, the shut-mode is auto.
manual
The switch displays an alert when a unidirectional link is detected. The operation to shut down the unidirectional link ports is accomplished by the users.
```

### Default
By default, the shut-mode is auto.

### Example
```text
Configure the shut-mode as manual:
Switch(config)# dldp shut-mode manual
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## dldp reset (global)

### Purpose
The dldp reset command is used to reset all the unidirectional links and restart the link detect process.

### Command Mode
Global Configuration Mode

### Syntax
```text
dldp reset
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Reset the DLDP function globally:
Switch(config)# dldp reset
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Official note: This command is only available on certain devices
- Availability: Only for certain devices according to the official chapter title.

## dldp(interface)

### Purpose
The dldp command is used to enable the DLDP function of the specified port. To disable it, please use no dldp command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet)

### Syntax
```text
dldp
no dldp
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the DLDP function of ports 1/0/2-4:
Switch (config)# interface range gigabitEthernet 1/0/2-4
Switch (config-if-range)# dldp
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## dldp reset (interface)

### Purpose
The dldp reset command is used to reset the specified port and restart the link detect process.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet)

### Syntax
```text
dldp reset
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Reset the DLDP function of ports 2-4:
Switch (config)# interface range gigabitEthernet 1/0/2-4
Switch (config-if-range)# dldp reset
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Official note: This command is only available on certain devices
- Availability: Only for certain devices according to the official chapter title.

## show dldp

### Purpose
The show dldp command is used to display the global configuration of DLDP function such as DLDP global state, DLDP interval and shut mode.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show dldp
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the global configuration of DLDP function:
Switch# show dldp
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## show dldp interface

### Purpose
The show dldp interface command is used to display the configuration and state of all ports. By default, the configuration and state of all the ports will be displayed.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show dldp interface
```

### Parameters
No parameters.

### Default
By default, the configuration and state of all the ports will be displayed.

### Example
```text
Display the configuration and state of all ports:
Switch# show dldp interface
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.
