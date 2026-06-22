# Bandwidth Control Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 62 Bandwidth Control Commands

Location: extracted Word text lines 26098-26234

## Chapter Notes

Official documentation states: Bandwidth Control functions to control the traffic rate and traffic threshold on each port to ensure network performance. Rate limit functions to limit the ingress/egress traffic rate on each port. Storm Control function allows the switch to monitor broadcast packets, multicast packets and Unknown unicast frames in the network.

- Use these commands only when the requested feature and target interface/VLAN/ring/session details are clear.

## storm-control rate-mode

### Purpose
The storm-control rate-mode command is used to configure the storm control mode of the interface. To return to the default configuration, please use no storm-control rate-mode command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
storm-control rate-mode { kbps | ratio | pps }
no storm-control rate-mode
```

### Parameters
```text
kbps
Select the storm control mode of the interface as kbps. The switch will limit the maximum speed of the specific kinds of traffic in kilo-bits per second.
ratio
Select the storm control mode of the interface as ratio. The switch will limit the percentage of bandwidth utilization for specific kinds of traffic.
pps
The switch will limit the maximum number of packets per second for specific kinds of traffic.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set the storm control mode as kbps on port 1/0/5:
Switch(config)# interface gigabitEthernet 1/0/5
Switch(config-if)# storm-control rate-mode kbps
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- User guidelines: This command should be used along with the storm-control command to enable the storm control function and specify the detailed parameters.
- Official note: pps is only available on certain devices.

## storm-control

### Purpose
The storm-control command is used to enable the broadcast, multicast, or unknown unicast strom control function and to set threshold levels on an interface. To return to the default configuration, please use no storm-control command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
storm-control { broadcast | multicast | unicast } { rate }
no storm-control { broadcast | multicast | unicast }
```

### Parameters
```text
broadcast | multicast | unicast
Select the mode of the storm control on the interface.
rate
Specify the bandwidth for receiving packets on the port. The specified type of packet traffic exceeding the bandwidth will be processed according to the configuration of storm-control exceed command. For kbps, the rate ranges from 1 to 1000000 kbps, and is rounded off to the nearest multiple of 64. For ratio, the rate ranges from 1 to 100 percent. For pps, the rate ranges from 1 to 1488000 packets per second.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the broadcast storm control rate as 1024 kbps on port 1/0/5:
Switch(config)# interface gigabitEthernet 1/0/5
Switch(config-if)# storm-control rate-mode kbps
Switch(config-if)# storm-control broadcast 1024
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- User guidelines: Before you configure the storm-control type as kbps or ratio, pelease ensure that the port is not in pps mode.

## storm-control exceed

### Purpose
The storm-control exceed command is used to configure the action that the switch will perform when the storm exceeds the defined limit on an interface.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
storm-control exceed { drop | shutdown } [ revocer-time time ]
```

### Parameters
```text
drop
Set the Action as Drop. The port will drop the subsequent packets when the traffic exceeds the limit.
shutdown
Set the Action as Shutdown. The port will be shutdown when the traffic exceeds the limit.
time
Specify the recover time for the port. It takes effect only when the action is set as shutdown. The valid values are from 0 to 3600 and the default value is 0. When the port is shutdown, it can recover to its normal state after the recover time passed. If the recover time is specified as 0, which means the port will not recover to its normal state automatically and you can recover the port manually using storm-control recover command.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the action as drop on port 1/0/5:
Switch(config)# interface gigabitEthernet 1/0/5
Switch(config-if)# storm-control exceed drop
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## storm-control recover

### Purpose
The storm-control recover command is used to recover the port manually after the port is shutdown because of the storm. When the recover time is specified as 0, the port will not recover to its normal state automatically. In this condition, you need to use this command to recover the port manually.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
storm-control recover
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Recover port 1/0/5 manually:
Switch(config)# interface gigabitEthernet 1/0/5
Switch(config-if)# storm-control recover
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## bandwidth

### Purpose
The bandwidth command is used to configure the bandwidth limit for an Ethernet port. To disable the bandwidth limit, please use no bandwidth command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
bandwidth {[ ingress ingress-rate ] [ egress egress-rate ]}
no bandwidth { all | ingress | egress }
```

### Parameters
```text
ingress-rate
Specify the upper rate limit for receiving packets. The rate ranges from 1 to 1000000 kbps for the gigaport and 1 to 100000 kbps for the fast port, and is rounded off to the nearest multiple of 64.
egress-rate
Specify the upper rate limit for sending packets. The rate ranges from 1 to 1000000 kbps for the gigaport and 1 to 100000 kbps for the fast port, and is rounded off to the nearest multiple of 64.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the ingress-rate as 5120Kbps and egress-rate as 1024Kbps for port 1/0/5:
Switch(config)# interface gigabitEthernet 1/0/5
Switch(config-if)# bandwidth ingress 5120 egress 1024
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## show storm-control

### Purpose
The show storm-control command is used to display the storm-control information of Ethernet ports.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show storm-control interface [ fastEthernet port | gigabitEthernet port-list ten-gigabitEthernet port | port-channel port-channel-id-list ]
```

### Parameters
```text
port-list
The list of Ethernet ports.
port-channel-id-list
The list of port channels.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the storm-control information of port 4, 5, 6, and 7:
Switch(config)# show storm-control interface gigabitEthernet 1/0/4-7
```

### Notes
- Permission requirement: None.

## show bandwidth

### Purpose
The show bandwidth command is used to display the bandwidth-limit information of Ethernet ports.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show bandwidth interface [ fastEthernet port | gigabitEthernet port-list ten-gigabitEthernet port | port-channel port-channel-id-list ]
```

### Parameters
```text
port-list
The list of Ethernet ports.
port-channel-id-list
The list of port channels.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the bandwidth-limit information of port 1/0/4:
Switch(config)# show bandwidth interface gigabitEthernet 1/0/4
```

### Notes
- Permission requirement: None.
