# Serial Port Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 70 Serial Port Commands

Location: extracted Word text lines 27079-27097

## Chapter Notes

Official documentation states: Note: Serial Port commands are only available on certain devices.

- Use these commands only when the requested feature and target interface/VLAN/ring/session details are clear.

## serial_port baud_rate

### Purpose
The serial_port baud_rate command is used to configure the communication baud rate on the console port. To return to the default baud rate, please use no serial_port command.

### Command Mode
Global Configuration Mode

### Syntax
```text
serial_port baud_rate { 9600 | 19200 | 38400 | 57600 | 115200 }
no serial_port
```

### Parameters
```text
9600 | 19200 | 38400 | 57600 | 115200
Specify the communication baud rate on the console port. The default baud rate is 38400 bps.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set the communication baud rate on the console port to 115200 bps:
Switch(config)# serial_port baud_rate 115200

Restore the communication baud rate on the console port to the default value:
Switch(config)# no serial_port
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
