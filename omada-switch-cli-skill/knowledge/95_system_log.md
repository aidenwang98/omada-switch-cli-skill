# System Log Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 95 System Log Commands

Location: extracted Word text lines 32513-32821

## Chapter Notes

Official documentation states: The log information will record the settings and operation of the switch respectively for you to monitor operation status and diagnose malfunction.

- Use these commands only when the requested feature and target interface/VLAN/ring/session details are clear.

## logging buffer

### Purpose
The logging buffer command is used to store the system log messages to an internal buffer. To disable the log buffer function, please use the no logging buffer command. Local Log is the system log information saved in the switch. It has two output channels, that is, it can be saved to two different positions, log buffer and log flash memory. The log buffer indicates the RAM for saving system log and the information in the log buffer can be got by show logging buffer command. It will be lost when the switch is restarted.

### Command Mode
Global Configuration Mode

### Syntax
```text
logging buffer
no logging buffer
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the system log buffer:
Switch(config)#logging buffer
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## logging buffer level

### Purpose
The logging buffer level command is used to configure the severity level and the status of the configuration input to the log buffer. To return to the default configuration, please use no logging buffer level command.

### Command Mode
Global Configuration Mode

### Syntax
```text
logging buffer level level
no logging buffer level
```

### Parameters
```text
level
Severity level of the log information output to each channel. There are 8 severity levels marked with values 0-7. The smaller value has the higher priority. Only the log with the same or smaller severity level value will be output. By default, it is 6 indicating that the log information with level 0-6 will be saved in the log buffer.
```

### Default
By default, it is 6 indicating that the log information with level 0-6 will be saved in the log buffer.

### Example
```text
Set the severity level as 5:
Switch(config)#logging buffer level 5
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## logging file flash

### Purpose
The logging file flash command is used to store the log messages in a file in the flash on the switch. To disable the log file flash function, please use no logging file flash command. This function is disabled by default. The log file flash indicates the flash sector for saving system log. The information in the log file of the flash will not be lost after the switch is restarted and can be got by the show logging flash command.

### Command Mode
Global Configuration Mode

### Syntax
```text
logging file flash
no logging file flash
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the log file flash function:
Switch(config)#logging file flash
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## logging file flash frequency

### Purpose
The logging file flash frequency command is used to specify the frequency to synchronize the system log file in the log buffer to the flash. To resume the default synchronizing frequency, please use the no logging file flash frequency command.

### Command Mode
Global Configuration Mode

### Syntax
```text
logging file flash frequency { periodic periodic | immediate }
no logging file flash frequency
```

### Parameters
```text
periodic
The frequency to synchronize the system log file in the log buffer to the flash, ranging from 1 to 48 hours. By default, the synchronization process takes place every 24 hours.
immediate
The system log file in the buffer will be synchronized to the flash immediately. This option will reduce the life of the flash and is not recommended.
```

### Default
By default, the synchronization process takes place every 24 hours.

### Example
```text
Specify the log file synchronization frequency as 10 hours:
Switch(config)#logging file flash frequency periodic10
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## logging file flash level

### Purpose
The logging file flash level command is used to specify the system log message severity level. Messages will a severity level equal to or higher than this value will be stored to the flash. To restore to the default level, please use no logging file flash level command.

### Command Mode
Global Configuration Mode

### Syntax
```text
logging file flash level level
no logging file flash level
```

### Parameters
```text
level
Severity level of the log message. There are 8 severity levels marked with values 0
7. The smaller value has the higher priority. Only the log with the same or smaller severity level value will be saved to the flash. By default, it is 3 indicating that the log message marked with 0
3 will be saved in the log flash.
```

### Default
By default, it is 3 indicating that the log message marked with 0 3 will be saved in the log flash.

### Example
```text
Save the log messages with their severities equal or higher than 7 to the flash :
Switch(config)#logging file flash level 7
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## logging host index

### Purpose
The logging host index command is used to configure the Log Host. To clear the configuration of the specified Log Host, please use no logging host index command. Log Host is to receive the system log from other devices. You can remotely monitor the settings and operation status of other devices through the log host.

### Command Mode
Global Configuration Mode

### Syntax
```text
logging host index index ip-address level [ port ]
logging host index index ip-address protocol { udp|tcp|tls|dtls } [ port port ] level level
no logging host index idx
```

### Parameters
```text
index
Index of the syslog server, range 1
ip-address
IP address of the syslog server, supports IPv4 and IPv6.
level
Filter level for syslogs sent to this server. Syslogs with a severity higher than this level will be filtered out.
port
Listening port of the syslog server, range 1
65535.
protocol
Transport protocol used for communication with the syslog server. Supports four protocols: udp, tcp, dtls, and tls.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Create a logging host without specifying a transport protocol:
Switch(config)# logging host index 1 192.168.0.148 5
Create a logging host specifying TLS as the transport protocol:
Switch(config)# logging host index 1 192.168.0.148 protocol tls level 5
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## logging host verify-peer

### Purpose
The logging host verify-peer command only applies to log hosts using TLS or DTLS transport protocols. It configures whether the device verifies the legitimacy of the peer syslog server s certificate. Verification is enabled by default.

### Command Mode
Global Configuration Mode

### Syntax
```text
logging host verify-peer
no logging host verify-peer
```

### Parameters
```text
None.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the device to not verify the syslog server
s certificate legitimacy, only using the encryption feature of TLS:
Switch(config)# no logging host verify-peer
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## logging host download

### Purpose
The logging host download command is used to download the root certificate, client certificate, and client private key to the device through TFTP.

### Command Mode
Global Configuration Mode

### Syntax
```text
logging host download ip-address ip-address [ ca-cert ca-cert ] [ client-cert client-cert ] [client-key client-key ]
```

### Parameters
```text
ip-address
IP address of the TFTP server.
ca-cert
Root certificate file name stored on the TFTP server.
client-cert
Client certificate file name stored on the TFTP server.
client-key
Client private key file name stored on the TFTP server.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Download a client certificate named client.crt from a TFTP server with IP address 192.168.0.148:
switch(config)# logging host download ip-address 192.168.0.148 client-cert client.crt
Download the root certificate, client certificate, and client private key named root.crt, client.crt, and client.key respectively from a TFTP server with IP address 192.168.0.148:
switch(config)# logging host download ip-address 192.168.0.148 ca-cert root.crt client-cert client.crt client-key client.key
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## logging host remove

### Purpose
The logging host remove command is used to delete certificates downloaded to the device for use by log hosts.

### Command Mode
Global Configuration Mode

### Syntax
```text
logging host remove [ ca-cert ] [ client-cert ] [ client-key ]
```

### Parameters
```text
ca-cert
Root certificate stored on the device.
client cert
Client certificate stored on the device.
client-key
Client private key stored on the device.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Simultaneously delete the root certificate, client certificate, and client private key downloaded to the device:
switch(config)# logging host remove ca-cert client-cert client-key
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## logging console

### Purpose
The logging console command is used to send the system logs to the console port. To disable logging to the console, please use no logging console command. This function is enabled by default.

### Command Mode
Global Configuration Mode

### Syntax
```text
logging console
no logging console
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable logging to the console port:
Switch(config)# logging console
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## logging console level

### Purpose
The logging console level command is used to limit messages logged to the console port. System logs no higher than the set threshold level will be displayed on the console port. To restore the threshold level to default value, please use no logging console level command.

### Command Mode
Global Configuration Mode

### Syntax
```text
logging console level level
no logging console level
```

### Parameters
```text
level
Severity level of the log information output to the console port. There are 8 severity levels marked with values 0
7. The smaller value has the higher priority. Only the log with the same or smaller severity level value will be output to the terminal devices. By default, it is 5 indicating that all the log information between level 0
5 will be output to the terminal devices.
```

### Default
By default, it is 5 indicating that all the log information between level 0 5 will be output to the terminal devices.

### Example
```text
Output the log information with severity levels between 0
7 to the console port:
Switch(config)# logging console level 7
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## logging monitor

### Purpose
The logging monitor command is used to display the system logs on the terminal devices. To disable logging to the terminal, please use no logging monitor command. This function is enabled by default.

### Command Mode
Global Configuration Mode

### Syntax
```text
logging monitor
no logging monitor
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Disable logging to the terminal devices:
Switch(config)# no logging monitor
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## logging monitor level

### Purpose
The logging monitor level command is used to limit messages logged to the terminal devices. System logs no higher than the set threshold level will be displayed on the terminal devices. To restore the threshold level to default value, please use no logging monitor level command.

### Command Mode
Global Configuration Mode

### Syntax
```text
logging monitor level level
no logging monitor level
```

### Parameters
```text
level
Severity level of the log information output to the terminal devices. There are 8 severity levels marked with values 0
7. The smaller value has the higher priority. Only the log with the same or smaller severity level value will be output to the terminal devices. By default, it is 5 indicating that all the log information between level 0
5 will be output to the terminal devices.
```

### Default
By default, it is 5 indicating that all the log information between level 0 5 will be output to the terminal devices.

### Example
```text
Output the log information with severity levels between 0
7 to the terminal devices:
Switch(config)# logging monitor level 7
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## clear logging

### Purpose
The clear logging command is used to clear the information in the log buffer and log file.

### Command Mode
Global Configuration Mode

### Syntax
```text
clear logging [ buffer | flash ]
```

### Parameters
```text
buffer | flash
The output channels: buffer and flash. Clear the information of the two channels, by default.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Clear the information in the log file:
Switch(config)# clear logging buffer
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## show logging local-config

### Purpose
The show logging local-config command is used to display the configuration of the Local Log output to the console, the terminal, the log buffer and the log file.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show logging local-config
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the configuration of the Local Log:
Switch(config)# show logging local-config
```

### Notes
- Permission requirement: None.

## show logging

### Purpose
The show logging command is used to display all filtered logs from both the buffer and flash storage.

### Command Mode
Global Configuration Mode

### Syntax
```text
show logging | [include include] [exclude exclude]
```

### Parameters
```text
include
A string that the log message must contain. Length range: 1-255 characters.
exclude
A string that the log message must not contain. Length range: 1-255 characters.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Filter for all logs that contain the string "SNMP" but do not contain the string "Add"
Switch(config)# show logging | include SNMP exclude Add
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## show logging loghost

### Purpose
The show logging loghost command is used to display the configuration of the log host.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show logging loghost [ index ]
```

### Parameters
```text
index
The index of the log host whose configuration will be displayed, ranging from 1 to 4. Display the configuration of all the log hosts by default.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the configuration of the log host 2:
Switch(config)# show logging loghost 2
```

### Notes
- Permission requirement: None.

## show logging loghost certificate-files

### Purpose
The show logging loghost certificate-files command is used to display the digest information of certificates related to log hosts on the device.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show logging loghost certificate-files
```

### Parameters
```text
None.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display digest informat
```

### Notes
- Permission requirement: None.
