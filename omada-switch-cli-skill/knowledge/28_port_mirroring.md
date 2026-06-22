# Port Mirroring Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 75 Port Mirroring Commands

Location: extracted Word text lines 28463-28566

## Chapter Notes

Official documentation states: Port Mirroring allows the switch to send a copy of the traffic that passes through specified sources (ports, LAGs or the CPU) to a destination port. It does not affect the switching of network traffic on source ports, LAGs or the CPU. Usually, the monitoring port is connected to data diagnose device, which is used to analyze the monitored packets for monitoring and troubleshooting the network.

- Port mirroring can affect troubleshooting and packet visibility. Confirm source, destination, direction, and RSPAN VLAN before generating commands.

## monitor session destination interface

### Purpose
The monitor session destination interface command is used to configure the monitoring port. Each monitor session has only one monitoring port. To change the monitoring port, please use the monitor session destination interface command by changing the port value. The no monitor session command is used to delete the corresponding monitoring port or monitor session.

### Command Mode
Global Configuration Mode

### Syntax
```text
monitor session session_num destination interface gigabitEthernet port
no monitor session session_num destination interface gigabitEthernet port
no monitor session session_num
```

### Parameters
```text
session_num
The monitor session number, can only be specified as 1.
port
The monitoring port number.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Create monitor session 1 and configure port 1/0/1 as the monitoring port:
Switch(config)# monitor session 1 destination interface gigabitEthernet 1/0/1
Delete the monitoring port 1/0/2 from monitor session 1:
Switch(config)# no monitor session 1 destination interface gigabitEthernet 1/0/2
Delete the monitor session 1:
Switch(config)# no monitor session 1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## monitor session source

### Purpose
The monitor session source command is used to configure the monitored interface. To delete the corresponding monitored interface, please use no monitor session source command.

### Command Mode
Global Configuration Mode

### Syntax
```text
monitor session session_num source { cpu cpu_number | interface gigabitEthernet port-list | interface port-channel port-channel-id } mode
no monitor session session_num source { cpu cpu_number | interface gigabitEthernet port-list | interface port-channel port-channel-id } mode
```

### Parameters
```text
session_num
The monitor session number. It can only be specified as 1.
cpu_number
The CPU number. It can only be specified as 1.
port-list
List of the Ethernet port number. It is multi-optional.
lag-list
List of LAG interfaces. It is multi-optional.
mode
The monitor mode. There are three options: rx, tx and both. Rx (ingress monitoring mode), means the incoming packets received by the monitored interface will be copied to the monitoring port. Tx (egress monitoring mode), indicates the outgoing packets sent by the monitored interface will be copied to the monitoring port. Both (ingress and egress monitoring), presents the incoming packets received and the outgoing packets sent by the monitored interface will both be copied to the monitoring port.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Create monitor session 1, then configure port 4, 5, 7 as monitored port and enable ingress monitoring:
Switch(config)# monitor session 1 source interface gigabitEthernet 1/0/4-5,1/0/7 rx
Delete port 4 in monitor session 1 and its configuration:
Switch(config)# no monitor session 1 source interface gigabitEthernet 1/0/4 rx
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- User guidelines: The monitoring port is corresponding to current interface configuration mode. Monitored ports number is not limited, but it can't be the monitoring port at the same time. Whether the monitoring port and monitored ports are in the same VLAN or not is not demanded strictly. The monitoring port and monitored ports cannot be link-aggregation member.

## monitor session 1 destination remote vlan

### Purpose
The monitor session 1 destination remote vlan command is used to configure the RSPAN VLAN for remote port monitoring of egress packets. Please set the destination port before using this command. To disable this function, please use the no monitor session 1 destination remote vlan command.

### Command Mode
Global Configuration Mode

### Syntax
```text
monitor session 1 destination remote vlan vlanid
no monitor session 1 destination remote vlan vlanid
```

### Parameters
```text
vlanid
Remote port monitoring export message VLAN. The value ranges from 2 to 4094 and is mutually exclusive with voice VLAN and internal VLAN.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the RSPAN VLAN for remote port monitoring of egress packets:
Switch(config)#monitor session 1 destination remote vlan 4094
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## monitor session 1 source remote vlan

### Purpose
The monitor session 1 source remote vlan command is used to monitor the packets added to the RSPAN VLAN port. To disable this function, use the no monitor session 1 source remote vlan command.

### Command Mode
Global Configuration Mode

### Syntax
```text
monitor session 1 source remote vlan vlanid
no monitor session 1 source remote vlan vlanid
```

### Parameters
```text
vlanid
Remote port monitoring export message VLAN. The value ranges from 2 to 4094 and is mutually exclusive with voice VLAN and internal VLAN.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Monitor the packets added to the RSPAN VLAN port:
Switch(config)#monitor session 1 source remote vlan 4094
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## show monitor session

### Purpose
The show monitor session command is used to display the configuration of port monitoring.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show monitor session [session_num]
```

### Parameters
```text
session_num
The monitor session number, can only be specified as 1. It is optional.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the monitoring configuration of monitor session 1:
Switch(config)# show monitor session 1
```

### Notes
- Permission requirement: None.
