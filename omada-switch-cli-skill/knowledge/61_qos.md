# QoS Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 61 QoS Commands

Location: extracted Word text lines 25628-26097

## Chapter Notes

Official documentation states: QoS (Quality of Service) function is used to optimize the network performance. It provides you with network service experience of a better quality. The switch implements three priority modes based on port, on 802.1p and on DSCP. Note: When data packets simultaneously meet the matching conditions of both the Switch QoS Rule and the OUI based VLAN, due to the priority of TCAM, only one of them will take effect.

- Use these commands only when the requested feature and target interface/VLAN/ring/session details are clear.

## qos trust mode

### Purpose
The qos trust mode command is used to configure the trust mode of CoS (Class of Service) function for the ports. The default trust mode is trust port priority.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
qos trust mode { dot1p | dscp | untrust }
```

### Parameters
```text
dot1p
Trust 802.1p mode. In this mode, data will be classified into different services based on the 802.1p priority.
dscp
Trust dscp mode. In this mode, data will be classified into different services based on the dscp priority.
untrust
Trust port mode. In this mode, data will be classified into different services based on the based on the port priority.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set the trust mode of port 1/0/3 as dscp:
Switch(config)# interface gigabitEthernet 1/0/3
Switch(config-if)# qos trust mode dscp
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## qos port-priority

### Purpose
The qos port-priority command is used to configure the port to 802.1p priority mapping for the desired port. To return to the default configuration, please use no qos port-priority command. When Port Priority is enabled, the packets will be mapped to different priority queues based on the ingress ports.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
qos port-priority { dot1p-priority }
no qos port-priority
```

### Parameters
```text
dot1p-priority
The 802.1p priority that the packets will be mapped to from the desired port. It ranges from 0 to 7, which represent 802.1p priority 0
7 respectively. By default, the priority is 0.
```

### Default
By default, the priority is 0.

### Example
```text
Configure the priority of port 5 as 3:
Switch(config)# interface gigabitEthernet 1/0/5
Switch(config-if)# qos port-priority 3
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## qos cos-map

### Purpose
The qos cos-map command is used to configure 802.1p to queue mapping globally. To return to the default configuration, please use no qos cos-map command. When 802.1P Priority is enabled, the packets with 802.1Q tag are mapped to different priority levels based on 802.1P priority.

### Command Mode
Global Configuration Mode

### Syntax
```text
qos cos-map { dot1p-priority } { tc-queue }
no qos cos-map
```

### Parameters
```text
dot1p-priority
The value of 802.1p priority. It ranges from 0 to 7, which represent 802.1p priority 0
7 respectively.
tc-queue
The number of TC queue that the 80.1p priority will be mapped to. It ranges from 0 to 7.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Map the 802.1p priority 5 to TC-2:
Switch (config)# qos cos-map 5 2
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## qos dot1p-remap

### Purpose
The qos dot1p-remap command is used to configure the 802.1p to 802.1p mappings. To return to the default configuration, please use no qos dot1p-remap command. When 802.1p remap is configured, the packets with the specific 802.1p priority will tagged with the desired new 802.1p priority.

### Command Mode
For some devices: Global Configuration Mode For other devices: Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
qos dot1p-remap { dot1p-priority } { new-dot1p-priority }
no qos dot1p-remap
```

### Parameters
```text
dot1p-priority
The original 802.1p priority. It ranges from 0 to 7, which represent 802.1p priority 0
7 respectively.
new-dot1p-priority
The new 802.1p priority. It ranges from 0 to 7.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
For some devices:
Remap 802.1p priority 5 to 802.1p priority 6:
Switch(config)#qos dot1p-remap 5 6
For other devices:
Remap 802.1p priority 5 to 802.1p priority 6 for port 1/0/1:
Switch(config)# interface gigabitEthernet 1/0/1
Switch(config-if)#qos dot1p-remap 5 6
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## qos dscp-map

### Purpose
The qos dscp-map command is used to configure the DSCP to 802.1p mapping. To return to the default configuration, please use no qos dscp-map command. DSCP (DiffServ Code Point) is a new definition to IP ToS field given by IEEE. This field is used to divide IP datagram into 64 priorities. When DSCP Priority is enabled, IP datagram are mapped to different priority levels based on DSCP priority.

### Command Mode
For some devices: Global Configuration Mode For other devices: Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
qos dscp-map { dscp-value-list } { dot1p-priority }
no qos dscp-map
```

### Parameters
```text
dscp-value-list
The DSCP value list in the format of
1-3,5,7
. The valid values are from 0 to 63.
dot1p-priority
The 802.1p priority to which the DSCP priority will be mapped. It ranges from 0 to 7, which represent 802.1p priority 0
7 respectively. By default, the priority is 0.
```

### Default
By default, the priority is 0.

### Example
```text
For some devices:
Map DSCP Priority 5 to 802.1p priority 2:
Switch(config)#qos dscp-map 5 2
For other devices:
Map DSCP Priority 5 to 802.1p priority 2 for port 1/0/1:
Switch(config)# interface gigabitEthernet 1/0/1
Switch(config-if)#qos dscp-map 5 2
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## qos dscp-remap

### Purpose
The qos dscp-remap command is used to configure the DSCP to DSCP mappings. To return to the default configuration, please use no qos dscp-remap command. When DSCP remap is configured, the packets with the specific DSCP priority will be changed to the desired new DSCP priority.

### Command Mode
For some devices: Global Configuration Mode For other devices: Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
qos queue dscp-map { dscp-value-list } { dscp-remap-value }
no qos queue dscp-map
```

### Parameters
```text
Dscp-value-list
The original DSCP value list in the format of
1-3,5,7
. The valid values are from 0 to 63.
Dscp-remap-value
The new DSCP value, which ranges from 0 to 63.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
For some devices:
Map DSCP values 10-12 to DSCP value 2:
Switch(config)# qos dscp-remap 10-12 2
For other devices:
Map DSCP values 10-12 to DSCP value 2 for port 1/0/2:
Switch(config)# interface gigabitEthernet 1/0/2
Switch(config-if)# qos dscp-remap 10-12 2
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## qos queue bandwidth

### Purpose
The qos queue bandwidth command is used to configure the minimum guaranteed bandwidth allocated to the specified queue. A value of 0 means there is no guaranteed minimum bandwidth in effect (best-effort service). The default value is 0. The sum of all bandwidth values for the queues must not exceed 100%. To return to the default configuration, please use no qos bandwidth command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
qos queue { tc-queue } bandwidth { rate }
no qos queue { tc-queue } bandwidth
```

### Parameters
```text
tc-queue
The egress queue ID. It ranges from 0 to 7, which represents TC queue from TC0 to TC7 respectively.
rate
The minimum bandwidth percentage for queue, ranging from 1 to 100 in increments of 1. By default, it is 0.
```

### Default
By default, it is 0.

### Example
```text
Set the minimum bandwidth of TC5 as 10% for port 1/0/1:
Switch(config)# interface gigabitEthernet 1/0/1
Switch(config-if)# qos queue 5 bandwidth 10
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Official note: This command is only available on certain devices

## qos queue mode

### Purpose
The qos queue mode command is used to configure the Scheduler Mode. When the network is congested, the program that many packets complete for resources must be solved, usually in the way of queue scheduling. The switch will control the forwarding sequence of the packets according to the priority queues and scheduling algorithms you set. On this switch, the priority levels are labeled as TC0, TC1, TC2 TC7.

### Command Mode
For some devices: Global Configuration Mode For other devices: Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
qos queue { tc-queue } mode { sp | wrr } [ weight weight ]
```

### Parameters
```text
tc-queue
The egress queue ID. It ranges from 0 to 7, which represents TC queue from TC0 to TC7 respectively.
Strict-Priority Mode. In this mode, the queue with higher priority will occupy the whole bandwidth. Packets in the queue with lower priority are sent only when the queue with higher priority is empty.
wrr
Weight Round Robin Mode. In this mode, packets in all the queues are sent in order based on the weight value for each queue. If you select this mode, you need to specify the queue weight at the same time.
weight
Configure the weight value of the specified TC queue. When the scheduler mode is specified as WRR, the weight value ranges from 1 to 127. The 8 queues will take up the bandwidth according to their ratio.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
For some devices:
Specify the Scheduler Mode of TC1 as WRR and set the queue weight as 10:
Switch(config)# qos queue 1 mode wrr weight 10
For other devices:
Specify the Scheduler Mode of TC1 as WRR and set the queue weight as 10 for port 1/0/1:
Switch(config)# interface gigabitEthernet 1/0/1
Switch(config-if)# qos queue 1 mode wrr weight 10
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## qos localPri

### Purpose
The qos localPri command is used to configure the egress queue of packets. After configuration, the packets of the corresponding VLAN will be assigned to the specified egress queue.

### Command Mode
VLAN Configuration Mode

### Syntax
```text
qos localPri queue
```

### Parameters
```text
queue: The egress queue of the packets.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the egress queue for VLAN 2:
Switch(config)#vlan 2
Switch(config-vlan)#qos localPri 3
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## qos cosPri

### Purpose
The qos cosPri command is used to configure the 802.1P priority carried by packets when they leave. After configuration, the packets of the corresponding VLAN will be assigned to the specified egress queue.

### Command Mode
VLAN Configuration Mode

### Syntax
```text
qos cosPri priority
```

### Parameters
```text
priority: 802.1P priority specified for the packets.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the 802.1P priority for VLAN 2:
Switch(config)#vlan 2
Switch(config-vlan)#qos cosPri 4
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## qos dscpPri

### Purpose
The qos dscpPri command is used to configure the egress queue of packets. After configuration, the packets of the corresponding VLAN will be assigned to the specified egress queue.

### Command Mode
VLAN Configuration Mode

### Syntax
```text
qos dscpPri dscp
```

### Parameters
```text
dscp: DSCP priority specified for the packets.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the DSCP priority for VLAN 2:
Switch(config)#vlan 2
Switch(config-vlan)#dscp localPri 10
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## qos wred-profile

### Purpose
The qos wred-profile command is used to configure the parameters of the WRED drop profile, including the lower threshold, upper threshold, and maximum drop percentage. To delete the corresponding WRED drop profile, please use the no qos wred-profile command.

### Command Mode
Global Configuration Mode

### Syntax
```text
qos wred-profile name low high drop-percentage
no qos wred-profile [name]
```

### Parameters
```text
name: WRED drop profile name.
low: Drop threshold lower limit.
high: Drop threshold upper limit.
drop-percentage: Maximum drop percentage.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Create a WRED drop profile:
Switch(config)#qos wred-profile test 40 80 500
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Official note: This command is only available on certain devices.

## qos wred-bind

### Purpose
The qos wred-bind command is used to bind the WRED drop template to the specified port. When traffic exits the port, the WRED policy will be implemented. To unbind the WRED drop profile, please use the no qos wred-bind command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
qos wred-bind name
no qos wred-bind
```

### Parameters
```text
name: WRED drop profile name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Bind the WRED drop profile to ports 1/0/1-4:
Switch(config)# interface range gigabitEthernet 1/0/1-4
Switch(config-if-range)#qos wred-bind test
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Official note: This command is only available on certain devices.

## show qos wred-profile

### Purpose
The show qos wred-profile command is used to view the WRED profile info.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show qos wred-profile [name]
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the WRED profile configuration:
Switch#show qos wred-profile
```

### Notes
- Permission requirement: None.
- Official note: This command is only available on certain devices.

## show qos wred-bind interface

### Purpose
The show qos wred-bind interface command is used to view the binding information of the WRED template.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show qos wred-bind interface [{fastEthernet | gigabitEthernet | hundred-gigabitEthernet | port-channel | ten-gigabitEthernet | twentyFive-gigabitEthernet | two-gigabitEthernet} interface-value]
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the information of the WRED template bound to bound to ports 1/0/1-3:
Switch#show qos wred-bind interface gigabitEthernet 1/0/1-3
```

### Notes
- Permission requirement: None.
- Official note: This command is only available on certain devices.

## show qos cos-map

### Purpose
The show qos cos-msp command is used to display the 802.1p priority to TC queue mappings.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show qos cos-map
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the 802.1p to queue mappings:
Switch# show qos cos-map
```

### Notes
- Permission requirement: None.

## show qos dot1p-remap interface

### Purpose
The show qos dot1p-remap interface command is used to display the 802.1p priority to 802.1p priority mappings.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show qos dot1p-remap interface [fastEthernet port | gigabitEthernet port | ten-gigabitEthernet port | port-channel port-channel-id ]
```

### Parameters
```text
port
The port number.
port-channel-id
The ID of the port channel.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the IEEE 802.1P remap configuration of all the ports:
Switch# show qos dot1p-remap interface
```

### Notes
- Permission requirement: None.
- Official note: This command is only available on certain devices.

## show qos dot1p-remap

### Purpose
The show qos dot1p-remap interface command is used to display the 802.1p priority to 802.1p priority mappings.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show qos dot1p-remap
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the IEEE 802.1P remap configuration:
Switch# show qos dot1p-remap
```

### Notes
- Permission requirement: None.
- Official note: This command is only available on certain devices.

## show qos dscp-map interface

### Purpose
The show qos dscp-map interface command is used to display the DSCP priority configuration of the ports.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show qos dscp-map interface [fastEthernet port | gigabitEthernet port | ten-gigabitEthernet port | port-channel port-channel-id ]
```

### Parameters
```text
port
The port number.
port-channel-id
The ID of the port channel.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display theDSCP priority configuration of all the ports:
Switch# show qos dscp-map interface
```

### Notes
- Permission requirement: None.
- Official note: This command is only available on certain devices.

## show qos dscp-map

### Purpose
The show qos dscp-map command is used to display the DSCP priority configuration.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show qos dscp-map
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the DSCP priority configuration:
Switch# show qos dscp-map
```

### Notes
- Permission requirement: None.
- Official note: This command is only available on certain devices.

## show qos dscp-remap interface

### Purpose
The show qos dscp-remap interface command is used to display the DSCP priority to DSCP priority mappings of the ports.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show qos dscp-remap interface [fastEthernet port | gigabitEthernet port | ten-gigabitEthernet port | port-channel port-channel-id ]
```

### Parameters
```text
port
The port number.
port-channel-id
The ID of the port channel.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the DSCP to DSCP mappings for all the ports:
Switch# show qos dscp-remap interface
```

### Notes
- Permission requirement: None.
- Official note: This command is only available on certain devices.

## show qos dscp-remap

### Purpose
The show qos dscp-remap command is used to display the DSCP priority to DSCP priority mappings.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show qos dscp-remap
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the DSCP to DSCP mappings:
Switch# show qos dscp-remap
```

### Notes
- Permission requirement: None.
- Official note: This command is only available on certain devices.

## show qos port-priority interface

### Purpose
The show qos port-priority interface command is used to display the port to 802.1p priority mappings for the ports.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show qos port-priority interface [fastEthernet port | gigabitEthernet port | ten-gigabitEthernet port | port-channel port-channel-id ]
```

### Parameters
```text
port
The port number.
port-channel-id
The ID of the port channel.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the port to 802.1p priority mappings for all the ports:
Switch# show qos port-priority interface
```

### Notes
- Permission requirement: None.

## show qos trust interface

### Purpose
The show qos trust interface command is used to display the trust mode of the ports.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show qos trust interface [fastEthernet port | gigabitEthernet port | ten-gigabitEthernet port | port-channel port-channel-id ]
```

### Parameters
```text
port
The port number.
port-channel-id
The ID of the port channel.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the trust mode of all the ports:
Switch# show qos trust interface
```

### Notes
- Permission requirement: None.

## show qos queue interface

### Purpose
The show qos queue interface command is used to display the scheduler settings of the ports.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show qos queue interface [fastEthernet port | gigabitEthernet port | ten-gigabitEthernet port | port-channel port-channel-id ]
```

### Parameters
```text
port
The port number.
port-channel-id
The ID of the port channel.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the scheduler settings of all the ports:
Switch# show qos queue interface
```

### Notes
- Permission requirement: None.

## show qos rule

### Purpose
The show qos rule command is used to display the configuration of applied QoS entries under the Controller mode (QoS rules can only be configured in Controller mode).

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show qos rule
```

### Parameters
```text
None.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the configuration of applied QoS entries under the Controller mode:
Switch# show qos rule
```

### Notes
- Permission requirement: None.
