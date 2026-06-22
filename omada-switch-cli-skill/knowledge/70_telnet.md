# Telnet Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 69 Telnet Commands

Location: extracted Word text lines 27020-27078

## Chapter Notes

- Use these commands only when the requested feature and target interface/VLAN/ring/session details are clear.

## telnet

### Purpose
The telnet command is used to log in and manage other devices via telnet.

### Command Mode
Privileged EXEC Mode

### Syntax
```text
telnet ip-addr
```

### Parameters
```text
ip-addr
The IP address of the device you want to log in.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Log in to a device with the IP address of 192.168.0.10:
Switch# telnet 192.168.0.10
```

### Notes
- Permission requirement: None.
- User guidelines: Make sure the switch can access the device, and the device can be logged in via telnet.

## telnet enable

### Purpose
The telnet enable command is used to enable the Telnet function. To disable the Telnet function, please use the telnet disable command. This function is enabled by default.

### Command Mode
Global Configuration Mode

### Syntax
```text
telnet enable
telnet disable
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Disable the Telnet function:
Switch(config)# telnet disable
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## telnet port

### Purpose
The telnet port command is used to configure the telent port number. To restore the setting, please use the no telnet port command.

### Command Mode
Global Configuration Mode

### Syntax
```text
telnet port port
no telnet port
```

### Parameters
```text
port
The number of telnet port.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the telnet port number as 566:
Switch(config)# telnet port 566
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## show telnet-status

### Purpose
The show telnet-status command is used to display the configuration information of the Telnet function.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show telnet-status
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display whether the Telnet function is enabled:
Switch(config)# show telnet-status
```

### Notes
- Permission requirement: None.
