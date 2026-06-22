# Dying Gasp Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 83 Dying Gasp Commands

Location: extracted Word text lines 29833-29909

## Chapter Notes

Official documentation states: Dying Gasp is a communication technology term, primarily used in broadband communications (e.g., DSL - Digital Subscriber Line). When a communication device (such as a DSL modem) experiences a power failure or malfunction, a Dying Gasp signal is sent to notify the service provider about the issue. Devices located at the network edge often have relatively poor power supply conditions, making them susceptible to unexpected power loss. Dying Gasp provides a mechanism for issuing an unexpected power failure alert to monitoring systems before the device loses connection. When a power failure event occurs, a hardware capacitor briefly delays the device shutdown. During this period, the device will send a Dying Gasp message to the configured syslog server or SNMP trap recipient. This information can be used to determine the cause of the problem and aid in troubleshooting. The purpose of the Dying Gasp signal is to allow network operators and service providers to quickly identify issues, thereby enabling more efficient fault handling and improving user satisfaction. This signal helps avoid prolonged fault detection and localization processes, accelerating service recovery.

- Use these commands only when the requested feature and target interface/VLAN/ring/session details are clear.

## dying-gasp enable oam

### Purpose
The dying-gasp enable oam command is used to enable the OAM packet notification for dying-gasp. To disable this function, please use no dying-gasp enable oam command.

### Command Mode
Global Configuration Mode

### Syntax
```text
dying-gasp enable oam [vlan vid]
no dying-gasp enable oam
```

### Parameters
```text
VLAN ID, ranging from 1 to 4094. The default is 1.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable OAM packet notification for VLAN 1:
Switch(config)# dying-gasp enable oam vlan 1
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## dying-gasp enable syslog

### Purpose
The dying-gasp enable syslog command is used to enable the syslog packet notification for dying-gasp. To disable this function, please use no dying-gasp enable syslog command. The destination server is the server configured with index=1 in the log host configuration.

### Command Mode
Global Configuration Mode

### Syntax
```text
dying-gasp enable syslog
no dying-gasp enable syslog
```

### Parameters
```text
None.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the syslog packet notification for dying-gasp:
Switch(config)# dying-gasp enable syslog
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## dying-gasp enable snmp

### Purpose
The dying-gasp enable snmp command is used to enable the SNMP trap notification for dying-gasp. To disable this function, please use no dying-gasp enable snmp command. The destination server is the server configured with index=1 in the SNMP server configuration.

### Command Mode
Global Configuration Mode

### Syntax
```text
dying-gasp enable snmp
no dying-gasp enable snmp
```

### Parameters
```text
None.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the SNMP trap notification for dying-gasp:
Switch(config)# dying-gasp enable snmp
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## show dying-gasp status

### Purpose
The show dying-gasp status command is used to view the status of the dying-gasp function.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show dying-gasp status
```

### Parameters
```text
None.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Check if the dying-gasp function is enabled:
Switch(config)# show dying-gasp status
```

### Notes
- Permission requirement: None.

## show dying-gasp packets

### Purpose
The show dying-gasp packets command is used to view the packet information for dying-gasp.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show dying-gasp packets
```

### Parameters
```text
None.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
View dying-gasp packet information:
Switch(config)# show dying-gasp packets
```

### Notes
- Permission requirement: None.
