# MSTP Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 37 MSTP Commands

Location: extracted Word text lines 16423-17051

## Chapter Notes

Official documentation states: MSTP (Multiple Spanning Tree Protocol), compatible with both STP and RSTP and subject to IEEE 802.1s, can disbranch a ring network. STP is to block redundant links and backup links as well as optimize paths.

- This chapter contains the official Omada STP/RSTP/MSTP command model. Do not replace it with Cisco-style `spanning-tree portfast` or other vendor syntax.

## debug spanning-tree

### Purpose
The debug spanning-tree command is used to enable debugging of spanning-tree activities. To disable the debugging function, please use no debug spanning-tree command.

### Command Mode
Privileged EXEC Mode

### Syntax
```text
debug spanning-tree { all | bpdu receive | bpdu transmit | cmpmsg | errors | flush | init | migration | proposals | roles | state | tc }
no debug spanning-tree { all | bpdu receive | bpdu transmit | cmpmsg | errors | flush | init | migration | proposals | roles | state | tc }
```

### Parameters
```text
all
Display all the spanning-tree debug messages.
bpdu receive
Display the debug messages of the received spanning-tree bridge protocol data unit (BPDU).
bpdu transmit
Display the debug messages of the sent spanning-tree BPDU.
cmpmsg
Display the message priority debug messages.
errors
Display the MSTP error debug messages.
flush
Display the address table flushing debug messages.
init
Display the data structure initialization debug messages.
migration
Display the version migration debug messages.
proposals
Display the MSTP handshake debug messages.
roles
Display the MSTP interface role switchling debug messages.
state
Display the MSTP interface state change debug messages.
Display the MSTP topology event debug messages.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display all the spanning-tree debug messages:
Switch# debug spanning-tree all
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## spanning-tree (global)

### Purpose
The spanning-tree command is used to enable STP function globally. To disable the STP function, please use no spanning-tree command.

### Command Mode
Global Configuration Mode

### Syntax
```text
spanning-tree
no spanning-tree
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the STP function:
Switch(config)# spanning-tree
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## spanning-tree (interface)

### Purpose
The spanning-tree command is used to enable STP function for a port. To disable the STP function, please use no spanning-tree command.

### Command Mode
Interface Configuration Mode ({ fastEthernet | gigabitEthernet | two-gigabitEthernet | ten-gigabitEthernet | twentyFive-gigabitEthernet | hundred-gigabitEthernet | port-channel / interface range port-channel)

### Syntax
```text
spanning-tree
no spanning-tree
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the STP function for port 1/0/2:
Switch(config)# interface gigabitEthernet 1/0/2
Switch(config-if)# spanning-tree
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## spanning-tree priority

### Purpose
The spanning-tree priority command is used to configure the bridge priority. To return to the default value of bridge priority, please use no spanning-tree priority command.

### Command Mode
Global Configuration Mode

### Syntax
```text
spanning-tree priority pri
no spanning-tree priority
```

### Parameters
```text
pri
The bridge priority value, which must be a multiple of 4096. It ranges from 0 to 61440, and the default value is 32768. A lower value indicates a higher priority, with 0 being the highest priority.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the bridge priority as 4096:
Switch(config)# spanning-tree priority 4096
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## spanning-tree common-config

### Purpose
The spanning-tree common-config command is used to configure the parameters of the ports for comparison in the CIST and the common parameters of all instances. To return to the default configuration, please use no spanning-tree common-config command. CIST (Common and Internal Spanning Tree) is the spanning tree in a switched network, connecting all devices in the network.

### Command Mode
Interface Configuration Mode ({ fastEthernet | gigabitEthernet | two-gigabitEthernet | ten-gigabitEthernet | twentyFive-gigabitEthernet | hundred-gigabitEthernet | port-channel / interface range port-channel)

### Syntax
```text
spanning-tree common-config [ port-priority pri ] [ ext-cost ext-cost ] [ int-cost int-cost ] [ portfast { enable | disable }] [ point-to-point { auto | open | close }]
no spanning-tree common-config
```

### Parameters
```text
pri
Port Priority, which must be multiple of 16 ranging from 0 to 240. By default, the port priority is 128. Port Priority is an important criterion on determining if the port connected to this port will be chosen as the root port. In the same condition, the port with the highest priority will be chosen as the root port. The lower value has the higher priority.
ext-cost
External Path Cost, which is used to choose the path and calculate the path costs of ports in different MST regions. It is an important criterion on determining the root port. The lower value has the higher priority. It ranges from o to 2000000. By default, it is 0 which is mean auto.
int-cost
Internal Path Cost, which is used to choose the path and calculate the path costs of ports in an MST region. It is an important criterion on determining the root port. The lower value has the higher priority. By default, it is automatic. It ranges from o to 2000000. By default, it is 0 which is mean auto.
portfast
Enable/ Disable Edge Port. By default, it is disabled. The edge port can transit its state from blocking to forwarding rapidly without waiting for forward delay.
point-to-point
The P2P link status, with auto, open and close options. By default, the option is auto. If the two ports in the P2P link are root port or designated port, they can transit their states to forwarding rapidly to reduce the unnecessary forward delay.
```

### Default
By default, the port priority is 128. By default, it is 0 which is mean auto. By default, it is automatic. By default, it is 0 which is mean auto. By default, it is disabled. By default, the option is auto.

### Example
```text
Enable the STP function of port 1, and configure the Port Priority as 64, ExtPath Cost as 100, IntPath Cost as 100, and then enable Edge Port:
Switch(config)# interface gigabitEthernet 1/0/1
Switch(config-if)# spanning-tree common-config port-priority 64 ext-cost 100 int-cost 100 portfast enable point-to-point open
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## spanning-tree mode

### Purpose
The spanning-tree mode command is used to configure the STP mode of the switch. To return to the default configurations, please use no spanning-tree mode command.

### Command Mode
Global Configuration Mode

### Syntax
```text
spanning-tree mode { stp | rstp | mstp | rpvst }
no spanning-tree mode
```

### Parameters
```text
stp
Spanning Tree Protocol, the default value.
rstp
Rapid Spanning Tree Protocol
mstp
Multiple Spanning Tree Protocol
rpvst
Per-Vlan Spanning Tree Protocol
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the spanning-tree mode as rpvst:
Switch(config)# spanning-tree mode rpvst
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## spanning-tree vlan

### Purpose
The spanning-tree mode command is used to enable the RPVST function for the specified VLAN(s).To disable this function, please use no spanning-tree vlan command.

### Command Mode
Global Configuration Mode

### Syntax
```text
spanning-tree vlan vlan-id { 1 | 1-2 }
no spanning-tree vlan vlan-id { 1 | 1-2 }
```

### Parameters
```text
vlan-id
The VLAN ID.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable RPVST mode for VLAN 1:
Switch(config)# spanning-tree vlan 1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## spanning-tree vlan <vlanStr> priority

### Purpose
This command is used to configure the RPVST priority for the specified VLAN(s). To restore the default value, use the no spanning-tree vlan <vlan-list> priority command. If there are L2 switches from our company in the topology running in RSTP mode, ensure that the VLAN 1 priority on the L3 switch is set higher than that on the L2 switches.

### Command Mode
Global Configuration Mode

### Syntax
```text
spanning-tree vlan vlanStr priority <prio>
no spanning-tree vlan vlanStr priority
```

### Parameters
```text
vlan-list
The VLAN list.
priority
The VLAN priority value.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the RPVST priority for VLAN 1 to 0:
Switch(config)# spanning-tree vlan 1 priority 0
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## spanning-tree extend-system-id

### Purpose
This command is used to enable the RPVST Extended System-ID feature. To disable the feature, use no spanning-tree extend-system-id command.

### Command Mode
Global Configuration Mode

### Syntax
```text
spanning-tree extend-system-id
no spanning-tree extend-system-id
```

### Parameters
```text
None.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the RPVST Extended System-ID feature:
Switch(config)# spanning-tree extend-system-id
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## spanning-tree vlan <vlanStr>

### Purpose
This command is used to configure the port priority and port path cost for the specified VLAN(s) on the interface. To restore defaults, use the no spanning-tree vlan <vlanStr> command.

### Command Mode
Interface Configuration Mode ({ fastEthernet | gigabitEthernet | two-gigabitEthernet | ten-gigabitEthernet | twentyFive-gigabitEthernet | hundred-gigabitEthernet | port-channel / interface range port-channel)

### Syntax
```text
Spanning-tree vlan <vlanStr> port-priority <prio> cost <cost>
Spanning-tree vlan <vlanStr> port-priority <prio>
Spanning-tree vlan <vlanStr> cost <cost>
no spanning-tree vlan
```

### Parameters
```text
vlanStr
The VLAN List
Prio
The Vlan Priority
cost
Port Path Cost
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure port priority as 0 and path cost as 2000 for VLAN 1 on port 1:
Switch(config-if)# spanning-tree vlan 1 port-priority 0 cost 2000
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## spanning-tree mst configuration

### Purpose
The spanning-tree mst configuration command is used to access MST configuration mode from Global Configuration Mode, as to configure the VLAN-Instance mapping, region name and revision level. To return to the default configuration of the corresponding Instance, please use no spanning-tree mst configuration command.

### Command Mode
Global Configuration Mode

### Syntax
```text
spanning-tree mst configuration
no spanning-tree mst configuration
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enter into the MST configuration mode:
Switch(config)# spanning-tree mst configuration
Switch(Config-mst)#
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## instance

### Purpose
The instance command is used to configure the VLAN-Instance mapping. To remove the VLAN-instance mapping or disable the corresponding instance, please use no instance command. When an instance is disabled, the related mapping VLANs will be removed.

### Command Mode
MST configuration mode

### Syntax
```text
instance instance-id vlan vlan-id
no instance instance-id [ vlan vlan-id ]
```

### Parameters
```text
instance-id
Instance ID.
vlan-id
The VLAN ID selected to mapping with the corresponding instance.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Map the VLANs 1-100 to Instance 1:
Switch(config)# spanning-tree mst configuration
Switch(config-mst)# instance 1 vlan 1-100
Disable instance 1, namely remove all the mapping VLANs 1-100:
Switch(config)# spanning-tree mst configuration
Switch(config-mst)# no instance 1
Remove VLANs 1-50 in mapping VLANs 1-100 for instance 1:
Switch(config)# spanning-tree mst configuration
Switch(config-mst)# no instance 1 vlan 1-50
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## name

### Purpose
The name command is used to configure the region name of MST instance.

### Command Mode
MST configuration mode

### Syntax
```text
name name
```

### Parameters
```text
name
The region name, used to identify MST region. It ranges from 1 to 32 characters.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the region name of MST as
region1
Switch(config)# spanning-tree mst configuration
Switch(config-mst)# name region1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## revision

### Purpose
The revision command is used to configure the revision level of MST instance.

### Command Mode
MST configuration mode

### Syntax
```text
revision revision
```

### Parameters
```text
revision
The revision level for MST region identification, ranging from 0 to 65535.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the revision level of MST as 100:
Switch(config)# spanning-tree mst configuration
Switch(config-mst)# revision 100
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## spanning-tree mst instance

### Purpose
The spanning-tree mst instance command is used to configure the priority of MST instance. To return to the default value of MST instance priority, please use no spanning-tree mst instance command.

### Command Mode
Global Configuration Mode

### Syntax
```text
spanning-tree mst instance instance-id priority pri
no spanning-tree mst instance instance-id priority
```

### Parameters
```text
instance-id
Instance ID.
pri
MSTI Priority, which must be multiple of 4096 ranging from 0 to 61440. By default, it is 32768. MSTI priority is an important criterion on determining if the switch will be chosen as the root bridge in the specific instance.
```

### Default
By default, it is 32768.

### Example
```text
Enable the MST Instance 1 and configure its priority as 4096:
Switch(config)# spanning-tree mst instance 1 priority 4096
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## spanning-tree mst

### Purpose
The spanning-tree mst command is used to configure MST Instance Port. To return to the default configuration of the corresponding Instance Port, please use no spanning-tree mst command. A port can play different roles in different spanning tree instance. You can use this command to configure the parameters of the ports in different instance IDs as well as view status of the ports in the specified instance.

### Command Mode
Interface Configuration Mode ({ fastEthernet | gigabitEthernet | two-gigabitEthernet | ten-gigabitEthernet | twentyFive-gigabitEthernet | hundred-gigabitEthernet | port-channel / interface range port-channel)

### Syntax
```text
spanning-tree mst instance instance-id {[ port-priority pri ] | [ cost cost ]}
no spanning-tree mst instance instance-id
```

### Parameters
```text
instance-id
Instance ID.
pri
Port Priority, which must be multiple of 16 ranging from 0 to 240. By default, it is 128. Port Priority is an important criterion on determining if the port will be chosen as the root port by the device connected to this port.
cost
Path Cost, ranging from 0 to 200000. The lower value has the higher priority. Its default value is 0 meaning
auto
```

### Default
By default, it is 128.

### Example
```text
Configure the priority of port 1 in MST Instance 1 as 64, and path cost as 2000:
Switch(config)# interface gigabitEthernet 1/0/1
Switch(config-if)# spanning-tree mst instance 1 port-priority 64 cost 2000
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## spanning-tree timer

### Purpose
The spanning-tree timer command is used to configure forward-time, hello-time and max-age of Spanning Tree. To return to the default configurations, please use no spanning-tree timer command.

### Command Mode
Global Configuration Mode

### Syntax
```text
spanning-tree timer {[ forward-time forward-time ] [ hello-time hello-time ] [ max-age max-age ]}
no spanning-tree timer
```

### Parameters
```text
forward-time
Forward Delay, which is the time for the port to transit its state after the network topology is changed. Forward Delay ranges from 4 to 30 in seconds and it is 15 by default. Otherwise, 2 * (Forward Delay - 1) >= Max Age.
hello-time
Hello Time, which is the interval to send BPDU packets, and used to test the links. Hello Time ranges from 1 to 10 in seconds and it is 2 by default. Otherwise, 2 * (Hello Time + 1) <= Max Age.
max-age
The maximum time the switch can wait without receiving a BPDU before attempting to reconfigure, ranging from 6 to 40 in seconds. By default, it is 20.
```

### Default
By default, it is 20.

### Example
```text
Configure forward-time, hello-time and max-age for Spanning Tree as 16 seconds, 3 seconds and 22 seconds respectively:
Switch(config)# spanning-tree timer forward-time 16 hello-time 3 max-age 22
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## spanning-tree hold-count

### Purpose
The spanning-tree hold-count command is used to configure the maximum number of BPDU packets transmitted per Hello Time interval. To return to the default configurations, please use no spanning-tree hold-count command.

### Command Mode
Global Configuration Mode

### Syntax
```text
spanning-tree hold-count value
no spanning-tree hold-count
```

### Parameters
```text
value
The maximum number of BPDU packets transmitted per Hello Time interval, ranging from 1 to 20 in pps. By default, it is 5.
```

### Default
By default, it is 5.

### Example
```text
Configure the hold-count of STP as 8pps:
Switch(config)# spanning-tree hold-count 8
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## spanning-tree max-hops

### Purpose
The spanning-tree max-hops command is used to configure the maximum number of hops that occur in a specific region before the BPDU is discarded. To return to the default configurations, please use no spanning-tree max-hops command.

### Command Mode
Global Configuration Mode

### Syntax
```text
spanning-tree max-hops value
no spanning-tree max-hops
```

### Parameters
```text
value
The maximum number of hops that occur in a specific region before the BPDU is discarded, ranging from 1 to 40 in hop. By default, it is 20.
```

### Default
By default, it is 20.

### Example
```text
Configure the max-hops of STP as 30:
Switch(config)# spanning-tree max-hops 30
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## spanning-tree bpdufilter

### Purpose
The spanning-tree bpdufilter command is used to enable the BPDU filter function for a port. With the BPDU Filter function enabled, the port does not forward BPDUs from the other switches. To disable the BPDU filter function, please use no spanning-tree bpdufilter command.

### Command Mode
Interface Configuration Mode ({ fastEthernet | gigabitEthernet | two-gigabitEthernet | ten-gigabitEthernet | twentyFive-gigabitEthernet | hundred-gigabitEthernet | port-channel / interface range port-channel)

### Syntax
```text
spanning-tree bpdufilter
no spanning-tree bpdufilter
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the BPDU filter function for port 1/0/2:
Switch(config)# interface gigabitEthernet 1/0/2
Switch(config-if)# spanning-tree bpdufilter
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## spanning-tree bpduflood

### Purpose
The spanning-tree bpduflood command is used to enable the BPDU forward function for a port. With the function enabled, the port still can forward spanning tree BPDUs when the spanning tree function is disabled on this port. To disable the BPDU filter function, please use no spanning-tree bpduflood command.

### Command Mode
Interface Configuration Mode ({ fastEthernet | gigabitEthernet | two-gigabitEthernet | ten-gigabitEthernet | twentyFive-gigabitEthernet | hundred-gigabitEthernet | port-channel / interface range port-channel)

### Syntax
```text
spanning-tree bpduflood
no spanning-tree bpduflood
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the BPDU forward function for port 1/0/2:
Switch(config)# interface gigabitEthernet 1/0/2
Switch(config-if)# spanning-tree bpduflood
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## spanning-tree bpduguard

### Purpose
The spanning-tree bpduguard command is used to enable the BPDU Guard for edge ports. When enabled, if an edge port receives a BPDU packet, the port will automatically be set to an ERROR-PORT, disabling its forwarding functionality. Note that this feature only takes effect on edge ports and does not apply to other port types, such as root ports. In this mode, to restore the port status, manual intervention is required; otherwise, the port will remain in the ERROR-PORT state. There are two methods for manual recovery: Restart the spanning tree feature: no spanning-tree, spanning-tree. Disable BPDU Guard: no spanning-tree bpduguard.

### Command Mode
Interface Configuration Mode ({ fastEthernet | gigabitEthernet | two-gigabitEthernet | ten-gigabitEthernet | twentyFive-gigabitEthernet | hundred-gigabitEthernet | port-channel / interface range port-channel)

### Syntax
```text
spanning-tree bpduguard
no spanning-tree bpduguard
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the BPDU protect function for port 1/0/2:
Switch(config)# interface gigabitEthernet 1/0/2
Switch(config-if)# spanning-tree bpduguard
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## spanning-tree guard loop

### Purpose
The spanning-tree guard loop command is used to enable the Loop Protect function for a port. Loop Protect is to prevent the loops in the network brought by recalculating STP because of link failures and network congestions. To disable the Loop Protect function, please use no spanning-tree guard loop command.

### Command Mode
Interface Configuration Mode ({ fastEthernet | gigabitEthernet | two-gigabitEthernet | ten-gigabitEthernet | twentyFive-gigabitEthernet | hundred-gigabitEthernet | port-channel / interface range port-channel)

### Syntax
```text
spanning-tree guard loop
no spanning-tree guard loop
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the Loop Protect function for port 2:
Switch(config)# interface gigabitEthernet 1/0/2
Switch(config-if)# spanning-tree guard loop
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## spanning-tree guard root

### Purpose
The spanning-tree guard root command is used to enable the Root Protect function for a port. With the Root Protect function enabled, the root bridge will set itself automatically as ERROR-PORT when receiving BPDU packets with higher priority, in order to maintain the role of root ridge. To disable the Root Protect function, please use no spanning-tree guard root command.

### Command Mode
Interface Configuration Mode ({ fastEthernet | gigabitEthernet | two-gigabitEthernet | ten-gigabitEthernet | twentyFive-gigabitEthernet | hundred-gigabitEthernet | port-channel / interface range port-channel)

### Syntax
```text
spanning-tree guard root
no spanning-tree guard root
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the Root Protect function for port 2:
Switch(config)# interface gigabitEthernet 1/0/2
Switch(config-if)# spanning-tree guard root
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## spanning-tree guard tc

### Purpose
The spanning-tree guard tc command is used to enable the TC Protect of Spanning Tree function for a port. To disable the TC Protect of Spanning Tree function, please use no spanning-tree guard tc command. A switch removes MAC address entries upon receiving TC-BPDUs. If a malicious user continuously sends TC-BPDUs to a switch, the switch will be busy with removing MAC address entries, which may decrease the performance and stability of the network. With the Protect of Spanning Tree function enabled, you can configure the number of TC-BPDUs in a required time, so as to avoid the process of removing MAC addresses frequently.

### Command Mode
Interface Configuration Mode ({ fastEthernet | gigabitEthernet | two-gigabitEthernet | ten-gigabitEthernet | twentyFive-gigabitEthernet | hundred-gigabitEthernet | port-channel / interface range port-channel)

### Syntax
```text
spanning-tree guard tc
no spanning-tree guard tc
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the TC Protect of Spanning Tree for port 2:
Switch(config)# interface gigabitEthernet 1/0/2
Switch(config-if)# spanning-tree guard tc
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## spanning-tree mcheck

### Purpose
The spanning-tree mcheck command is used to enable mcheck.

### Command Mode
Interface Configuration Mode ({ fastEthernet | gigabitEthernet | two-gigabitEthernet | ten-gigabitEthernet | twentyFive-gigabitEthernet | hundred-gigabitEthernet | port-channel / interface range port-channel)

### Syntax
```text
spanning-tree mcheck
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable mcheck for port 2:
Switch(config)# interface gigabitEthernet 1/0/2
Switch(config-if)# spanning-tree mcheck
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## show spanning-tree active

### Purpose
The show spanning-tree active command is used to display the active information of spanning-tree.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show spanning-tree active
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the active information of spanning-tree:
Switch(config)# show spanning-tree active
```

### Notes
- Permission requirement: None.

## show spanning-tree bridge

### Purpose
The show spanning-tree bridge command is used to display the bridge parameters.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show spanning-tree bridge [ forward-time | hello-time | hold-count | max-age | max-hops | mode | priority | state ]
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the bridge parameters:
Switch(config)# show spanning-tree bridge
```

### Notes
- Permission requirement: None.

## show spanning-tree interface

### Purpose
The show spanning-tree interface command is used to display the spanning-tree information of all ports or a specified port.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show spanning-tree interface [ gigabitEthernet port | port-channel port-channel-id ] [ edge | ext-cost | int-cost | mode | p2p | priority | role | state | status ]
```

### Parameters
```text
port
The Ethernet port number.
port-channel-id
The ID of the port channel.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the spanning-tree information of all ports:
Switch(config)# show spanning-tree interface
Display the spanning-tree information of port 1/0/2:
Switch(config)# show spanning-tree interface gigabitEthernet 1/0/2
Display the spanning-tree mode information of port 1/0/2:
Switch(config)# show spanning-tree interface gigabitEthernet 1/0/2 mode
```

### Notes
- Permission requirement: None.

## show spanning-tree interface tcn-tx

### Purpose
The show spanning-tree interface tcn-tx command is used to individually display the TCN transmission count for all interfaces.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show spanning-tree interface tcn-tx
```

### Parameters
```text
None.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the TCN transmission count for all interfaces:
Switch(config)# show spanning-tree interface tcn-tx
```

### Notes
- Permission requirement: None.

## show spanning-tree interface tcn-rx

### Purpose
The show spanning-tree interface tcn-rx command is used to individually display the TCN receive count for all interfaces.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show spanning-tree interface tcn-rx
```

### Parameters
```text
None.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the TCN receive count for all interfaces:
Switch(config)# show spanning-tree interface tcn-rx
```

### Notes
- Permission requirement: None.

## show spanning-tree interface port-type port-index tcn-tx

### Purpose
The show spanning-tree interface port-type port-index tcn-tx command is used to individually display the TCN transmission count information for a specific interface.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show spanning-tree interface port-type port-index tcn-tx
```

### Parameters
```text
port-type
Port type: gigabitEthernet, two-gigabitEthernet, ten-gigabitEthernet, fastEthernet.
port-index
Port number. Example: 1/0/1.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Individually display the TCN transmission count information for interface 1/0/1:
show spanning-tree interface gigabitEthernet 1/0/1 tcn-tx
```

### Notes
- Permission requirement: None.

## show spanning-tree interface port-type port-index tcn-rx

### Purpose
The show spanning-tree interface port-type port-index tcn-rx command is used to individually display the TCN receive count information for a specific interface.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show spanning-tree interface port-type port-index tcn-rx
```

### Parameters
```text
port-type
Port type: gigabitEthernet, two-gigabitEthernet, ten-gigabitEthernet, fastEthernet.
port-index
Port number. Example: 1/0/1.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Individually display the TCN receive count information for interface 1/0/1:
show spanning-tree interface gigabitEthernet 1/0/1 tcn-rx
```

### Notes
- Permission requirement: None.

## show spanning-tree vlan

### Purpose
The show Spanning-tree vlan command is used to display the RPVST spanning tree calculation status for the specified VLAN.

### Command Mode
Global Configuration Mode

### Syntax
```text
Show Spanning-tree vlan <vlanId>
```

### Parameters
```text
vlanId
The VLAN ID.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the RPVST spanning tree calculation status for VLAN 1:
Switch(config)# show spanning-tree vlan 1
```

### Notes
- Permission requirement: None.

## show spanning-tree interface-security

### Purpose
The show spanning-tree interface-security command is used to display the protect information of all ports or a specified port.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show spanning-tree interface-security [ gigabitEthernet port | port-channel port-channel-id ] [ bpdufilter | bpduflood | bpduguard | loop | root | tc ]
```

### Parameters
```text
port
The Ethernet port number.
port-channel-id
The ID of the port channel.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the protect information of all ports:
Switch(config)# show spanning-tree interface-security
Display the protect information of port 1:
Switch(config)# show spanning-tree interface-security gigabitEthernet 1/0/1
Display the interface security bpdufilter information:
Switch(config)# show spanning-tree interface-security bpdufilter
```

### Notes
- Permission requirement: None.

## show spanning-tree mst

### Purpose
The show spanning-tree mst command is used to display the related information of MST Instance.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show spanning-tree mst { configuration [ digest ] | instance instance-id [ interface [ gigabitEthernet port | port-channel port-channel-id ] ] }
```

### Parameters
```text
instance-id
Instance ID desired to show.
port
The Ethernet port number.
port-channel-id
The ID of the port channel.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the region information and mapping information of VLAN and MST Instance:
Switch(config)#show spanning-tree mst configuration
Display the related information of MST Instance 1:
Switch(config)#show spanning-tree mst instance 1
Display all the ports information of MST Instance 1:
Switch(config)#show spanning-tree mst instance 1 interface
```

### Notes
- Permission requirement: None.
