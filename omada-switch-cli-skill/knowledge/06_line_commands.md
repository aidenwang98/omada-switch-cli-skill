# Line Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 2 Line Commands (Only for Certain Devices)

Location: official printed page 26-27; actual PDF page 72-73

## Chapter Notes

Line Commands are only available on certain devices.

## line

### Purpose
Enter Line Configuration Mode and make related configurations for the desired user or users.

### Command Mode
Global Configuration Mode

### Syntax
```text
line { console linenum | vty startlinenum endlinenum }
```

### Parameters
- `linenum`: The number of users allowed to login through console port. Its value is 0 in general because console input is active on only one console port at a time.
- `startlinenum`: The start serial number of the login user selected to configure the login mode and password, ranging from 0 to 15. 0 means the first login user number, 1 means the second, and the rest can be done in the same manner.
- `endlinenum`: The end serial number of the login user selected to configure the login mode and password, ranging from 0 to 15. 0 means the first login user number, 1 means the second, and the rest can be done in the same manner.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config)#line console 0
```

```text
Switch(config)#line vty 0 5
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- `line console 0` enters Console port configuration mode and configures console port 0.
- `line vty 0 5` enters Virtual Terminal configuration mode for virtual terminal 0 to 5.
- This chapter does not provide password or login-mode commands for line users; do not invent them.

## media-type rj45

### Purpose
Configure the console media type as RJ-45 for input; use `no media-type rj45` to return to the default configuration.

### Command Mode
Line Configuration Mode

### Syntax
```text
media-type rj45
no media-type rj45
```

### Parameters
No parameters.

### Default
By default, the Micro-USB connector takes precedence over the RJ-45 connector.

### Example
```text
Switch(config)# line console 0
Switch(config-line)# media-type rj45
```

```text
Switch(config)# line console 0
Switch(config-line)# no media-type rj45
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- The switch has two console ports available: an RJ-45 console port and a Micro-USB console port.
- Console input is active on only one console port at a time.
- By default, when both RJ-45 console and Micro-USB console connections are valid, input from the RJ-45 console is disabled and input from the Micro-USB console is enabled.
