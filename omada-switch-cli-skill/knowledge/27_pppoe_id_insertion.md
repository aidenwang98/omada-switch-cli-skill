# PPPoE ID-Insertion Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 41 PPPoE ID-Insertion Commands (Only for Certain Devices)

Location: extracted Word text lines 18022-18124

## Chapter Notes

Official documentation states: Note: PPPoE ID-Insertion commands are only available on certain devices. The PPPoE ID-Insertion feature provides a way to extract a Vendor-specific tag as an identifier for the authentication, authorization, and accounting (AAA) access requests on an Ethernet interface. When enabled, the switch attaches a tag to the PPPoE discovery packets, which is called the PPPoE Vendor-Specific tag and it contains a unique line identifier. There are two formats of Vendor-specific tags: Circuit-ID format and Remote-ID format. The BRAS receives the tagged packet, decodes the tag, and uses the Circuit-ID/Remote-ID field of that tag as a NAS-Port-ID attribute in the RADIUS server for PPP authentication and AAA (authentication, authorization, and accounting) access requests. The switch will remove the Circuit-ID/Remote-ID tag from the received PPPoE Active Discovery Offer and Session-confirmation packets from the BRAS.

- This chapter is marked `Only for Certain Devices`; treat all configuration commands as model-dependent.
- When a command or note is device-specific in the official text, mention model and firmware dependency before recommending it.

## pppoe id-insertion (global)

### Purpose
The pppoe id-insertion command is used to enable the PPPoE ID-Insertion function globally. To disable the PPPoE ID-Insertion function, please use no pppoe id-insertion command.

### Command Mode
Global Configuration Mode

### Syntax
```text
pppoe id-insertion
no pppoe id-insertion
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the PPPoE ID-Insertion function:
Switch(config)# pppoe id-insertion
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## pppoe circuit-id (interface)

### Purpose
The pppoe circuit-id command is used to enable the PPPoE Circuit-ID Insertion function for a specified port. To disable the PPPoE Circuit-ID Insertion function on a specified port, please use no pppoe circuit-id command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet)

### Syntax
```text
pppoe circuit-id
no pppoe circuit-id
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the PPPoE Circuit-ID Insertion function for the Gigabit Ethernet port 1/0/1:
Switch (config)# interface gigabitEthernet 1/0/1
Switch (config-if)# pppoe circuit-id
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## pppoe circuit-id type

### Purpose
The pppoe circuit-id type command is used to configure the type of PPPoE Circuit-ID for a specified port. By default, the PPPoE Circuit-ID type is

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet)

### Syntax
```text
pppoe circuit-id type { mac | ip | udf [Value] | udf-only [Value] }
```

### Parameters
```text
mac | ip | udf | udf-only
The type of PPPoE Circuit-ID for the port.
mac: The MAC address of the switch will be used to encode the Circuit-ID option.
ip: The IP address of the switch will be used to encode the Circuit-ID option. This is the default value.
udf: A user specified string with the maximum length of 40 characters will be used to encode the Circuit-ID option.
udf-only: Only the user specified string with the maximum length of 40 will be used to encode the Circuit-ID option.
Value
The value of udf/udf-only. The maximum length is 40 characters.
```

### Default
By default, the PPPoE Circuit-ID type is mac | ip | udf | udf-only The type of PPPoE Circuit-ID for the port.

### Example
```text
Configure the type of PPPoE Circuit-ID as
for the Gigabit Ethernet port 1/0/1:
Switch (config)# interface gigabitEthernet 1/0/1
Switch (config-if)# pppoe circuit-id type mac
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## pppoe remote-id

### Purpose
The pppoe remote-id command is used to enable the PPPoE Remote-ID Insertion and configure the Remote-ID value for a specified port. To disable the PPPoE Remote-ID Insertion function on a specified port, please use no pppoe remote-id command. By default, the PPPoE Remote-ID Insertion is disabled.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet)

### Syntax
```text
pppoe remote-id [Value]
no pppoe remote-id
```

### Parameters
```text
Value
The value of UDF. The maximum length is 40 characters. If not specified, the default value will be the PPPoE client
s MAC address.
```

### Default
By default, the PPPoE Remote-ID Insertion is disabled.

### Example
```text
Configure the remote-ID as
for the Gigabit Ethernet port 1/0/1:
Switch (config)# interface gigabitEthernet 1/0/1
Switch (config-if)# pppoe remote-id mac
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## show pppoe id-insertion global

### Purpose
The show pppoe id-insertion global command is used to display the global configuration of PPPoE Circuit-ID Insertion function.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show pppoe id-insertion global
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the configuration of PPPoE Circuit-ID Insertion function globally:
Switch # show pppoe circuit-id global
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## show pppoe id-insertion interface

### Purpose
The show pppoe id-insertion interface command is used to display all ports or the specified port s configuration information of PPPoE Circuit-ID Insertion function.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show pppoe id-insertion interface [gigabitEthernet port ]
```

### Parameters
```text
port
The Fast/Gigabit Ethernet port number.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the configuration information of PPPoE Circuit-ID Insertion function of all Ethernet ports:
Switch# show pppoe id-insertion interface
Display the configuration of PPPoE Circuit-ID Insertion function of the Gigabit Ethernet port 1/0/1 :
Switch# show pppoe id-insertion interface gigabitEthernet 1/0/1
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.
