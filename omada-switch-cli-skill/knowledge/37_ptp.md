# PTP Configuration Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 6 PTP Configuration Commands (Only for Certain Devices)

Location: extracted Word text lines 8870-9305

## Chapter Notes

Official documentation states: The Precision Time Protocol (PTP) in network measurement and control systems is a protocol for synchronizing time (phase) and frequency across standard Ethernet devices. It is also known as IEEE 1588 (defined by IEEE) or 1588 for short. Its primary goal is to achieve high-precision clock synchronization within Local Area Networks (LAN) or Wide Area Networks (WAN) to meet the requirements of applications such as communication networks, industrial control, financial trading, and audio/video transmission. PTP defines the basic paradigm for network clock synchronization and imposes no strict requirements on the network environment, ensuring broad adaptability. Based on PTP, derived protocols such as 802.1as (also known as gPTP), G.8265.1, G.8275.1, G.8275.2, SMPTE, and AES67 have been developed. These protocols impose restrictions on network environments and PTP parameters for specific domains and can be seen as functional subsets of PTP (achievable through PTP's profile mechanism).

- This chapter is marked `Only for Certain Devices`; treat all configuration commands as model-dependent.

## ptp enable (Global View)

### Purpose
The ptp enable command is used to enable the PTP function globally. To disable this function globally, use the no ptp enable command. By default, PTP is disabled.

### Command Mode
Global Configuration Mode.

### Syntax
```text
ptp enable
no ptp enable
```

### Parameters
```text
None
```

### Default
By default, PTP is disabled.

### Example
```text
Enable the PTP function globally:
Switch(config)# ptp enable
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ptp profile

### Purpose
The ptp profile command is used to specify the PTP protocol standard. To restore the default protocol standard (1588v2), use the no ptp profile command.

### Command Mode
Global Configuration Mode.

### Syntax
```text
ptp profile { 1588v2 | 8021as}
no ptp profile
```

### Parameters
```text
1588v2 | 8021as
Specify the protocol standard (default: 1588v2).
Note
Changing the protocol standard will clear all existing configurations under the previous standard and reset PTP parameters to their default values for the new standard. The global ptp enable state is retained.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set the protocol to 802.1as:
Switch(config)# ptp profile 8021as
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ptp clock-type

### Purpose
The ptp clock-type command is used to configure the PTP node type. To remove the configuration, use the no ptp clock-type command. No node type is set by default.

### Command Mode
Global Configuration Mode.

### Syntax
```text
ptp clock-type {bc | oc | e2etc | p2ptc }
no ptp clock-type
```

### Parameters
```text
Node types vary by protocol:
1588v2: bc, oc, e2etc, p2ptc
802.1as: bc, oc, p2ptc
Note
Ensure compatibility with the configured protocol standard.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set the node type to bc under 1588v2:
Switch(config)# ptp clock-type bc
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ptp domain

### Purpose
The ptp domain command is used to specify the PTP clock domain. To restore the default domain for the current protocol, use the no ptp domain command. Only devices in the same domain can synchronize.

### Command Mode
Global Configuration Mode.

### Syntax
```text
ptp domain domain
no ptp domain
```

### Parameters
```text
domain
Domain ID (integer). Default varies by protocol.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set the domain to 1:
Switch(config)# ptp domain 1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ptp clock-class

### Purpose
The ptp clock-class command is used to set the clock quality class (lower values indicate higher priority in master election). Default: 248.

### Command Mode
Global Configuration Mode.

### Syntax
```text
ptp clock-class clock-class
no ptp clock-class
```

### Parameters
```text
clock-class
Integer (smaller values = higher priority).
Note
If <clock-class> < 128, the device cannot act as a slave. Configure carefully to avoid synchronization issues.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set clock class to 200:
Switch(config)# ptp clock-class 200
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ptp priority1

### Purpose
The ptp priority1 command is used to set Priority1 for master election (lower values = higher priority). Defaults vary by protocol.

### Command Mode
Global Configuration Mode.

### Syntax
```text
ptp priority1 priority1
no ptp priority1
```

### Parameters
```text
priority1
Integer (specific range depends on protocol).
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set Priority1 to 129:
Switch(config)# ptp priority1 129
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ptp priority2

### Purpose
The ptp priority2 command is used to set Priority2 for master election (lower values = higher priority). Defaults vary by protocol.

### Command Mode
Global Configuration Mode.

### Syntax
```text
ptp priority2 priority1
no ptp priority2
```

### Parameters
```text
priority2
Integer (specific range depends on protocol).
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set Priority2 to 129:
Switch(config)# ptp priority2 129
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ptp slave-only

### Purpose
The ptp slave-only command is used to OC-type ports to operate as slave-only. To restore the default behavior (master/member allowed), use the no ptp slave-only command.

### Command Mode
Global Configuration Mode.

### Syntax
```text
ptp slave-only
no ptp slave-only
```

### Parameters
```text
None
Note
Only applicable to OC node types.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure slave-only mode for OC under 1588v2:
Switch (config)# ptp profile 1588v2
Switch (config)# ptp clock-type oc
Switch (config)# ptp slave-only
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ptp utc-offset

### Purpose
The ptp utc-offset command is used to correct the deviation between UTC time and TAI time. Its no command is used to restore utc-offset to the default value. By default, the value of utc-offset is 37 seconds.

### Command Mode
Global Configuration Mode.

### Syntax
```text
ptp utc-offset utc-offset
no ptp utc-offset
```

### Parameters
```text
utc-offset
Specify the offset between UTC time and TAI time, in integer form, in seconds, with a default value of 37 seconds.
```

### Default
By default, the value of utc-offset is 37 seconds.

### Example
```text
Set the offset to 40 seconds:
Switch (config)# ptp utc-offset 40
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ptp virtual-id

### Purpose
The ptp virtual-id command is used to configure the virtual clock ID of the ptp device. Its no command is used to restore the default clock ID. The clock ID is unique and is used to distinguish other clock devices in the domain. By default, the clock ID is composed of the mac address of the device and 0xfffe.

### Command Mode
Global Configuration Mode.

### Syntax
```text
ptp virtual-id xxxxxx.xxxx.xxxxxx
no ptp virtual-id
```

### Parameters
```text
xxxxxx.xxxx.xxxxxx
Hexadecimal ID.
```

### Default
By default, the clock ID is composed of the mac address of the device and 0xfffe.

### Example
```text
Set virtual ID to 112233.4455.aabbcc:
Switch (config)# ptp virtual-id 112233.4455.aabbcc
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ptp enable (Interface View)

### Purpose
The ptp enable command is used to PTP functionality on a port, turning it into a PTP port. The no form disables PTP on the port. By default, PTP is disabled on ports.

### Command Mode
Interface Configuration Mode.

### Syntax
```text
ptp enable
no ptp enable
```

### Parameters
```text
None
```

### Default
By default, PTP is disabled on ports.

### Example
```text
Enable PTP on Ten-GigabitEthernet 1/0/1:
Switch (config)# interface ten-gigabitEthernet 1/0/1
Switch (config-if)# ptp enable
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ptp announce-interval

### Purpose
The ptp announce-interval command is used to configure the announce message transmission rate on a port. The no form restores the protocol-standard default. The default is protocol-specific.

### Command Mode
Interface Configuration Mode.

### Syntax
```text
ptp announce-interval announce-interval
no ptp announce-interval
```

### Parameters
```text
announce-interval
Transmission interval in seconds, calculated as 2 times the announce-interval in seconds.
Notes
Announce messages are used for clock source election and master-slave synchronization. Excessive rates may consume bandwidth and degrade synchronization. Configure this value carefully.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set announce messages to 1 per second on Ten-GigabitEthernet 1/0/1:
Switch (config)# interface ten-gigabitEthernet 1/0/1
Switch (config-if)# ptp announce-interval 0
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ptp announce-timeout

### Purpose
The ptp announce-interval command is used to configure the maximum allowed missed announce messages before triggering clock source re-election. The no form restores the default value 3.

### Command Mode
Interface Configuration Mode.

### Syntax
```text
ptp announce-timeout announce-timeout
no ptp announce-timeout
```

### Parameters
```text
announce-timeout
Timeout threshold (number of intervals).
Notes
Ensure compatibility between announce-timeout and announce-interval. Overly frequent intervals or low timeout values may cause instability.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set timeout to 4 on Ten-GigabitEthernet 1/0/1:
Switch (config)# interface ten-gigabitEthernet 1/0/1
Switch (config-if)# ptp announce-timeout 4
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ptp sync-interval

### Purpose
The ptp sync-interval command is used to configure the sync message transmission rate. The no form restores the protocol-standard default.

### Command Mode
Interface Configuration Mode.

### Syntax
```text
ptp sync-interval sync-interval
no ptp sync-interval
```

### Parameters
```text
sync-interval
Specify the sync message sending rate on this port. The sending interval is 2 times the sync-interval in seconds.
Notes
Sync messages affect synchronization accuracy. Balance precision and bandwidth usage.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set sync messages to 2 per second on Ten-GigabitEthernet 1/0/1:
Switch (config)# interface ten-gigabitEthernet 1/0/1
Switch (config-if)# ptp sync-interval -1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ptp delay-req-interval

### Purpose
The ptp delay-req-interval command is used to configure the minimum interval for sending delay_req packets on a port. The no command is used to restore the default value of the current protocol standard. By default, the default value is used.

### Command Mode
Interface Configuration Mode.

### Syntax
```text
ptp delay-req-interval delay-req-interval
no ptp delay-req-interval
```

### Parameters
```text
delay-req-interval
Specify the minimum interval for sending delay-req packets on this port. The interval is 2 times the delay-req-interval in seconds.
Notes
Used in request-response mode for path delay calculation. Balance accuracy and bandwidth.
```

### Default
By default, the default value is used.

### Example
```text
Set delay_req rate to 2 per second on Ten-GigabitEthernet 1/0/1:
Switch (config)# interface ten-gigabitEthernet 1/0/1
Switch (config-if)# ptp delay-req-interval -1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ptp pdelay-req-interval

### Purpose
The ptp pdelay-req-interval command is used to configure the minimum interval for sending pdelay_req packets on a port. The no command is used to restore the default value of the current protocol standard. By default, the default value is used.

### Command Mode
Interface Configuration Mode.

### Syntax
```text
ptp delay-req-interval pdelay-req-interval
no ptp delay-req-interval
```

### Parameters
```text
pdelay-req-interval
Specify the minimum interval for sending pdelay-req packets on this port. The interval is 2 times the pdelay-req-interval in seconds.
Notes
Used in peer-to-peer delay mechanism. Balance accuracy and bandwidth.
```

### Default
By default, the default value is used.

### Example
```text
Set pdelay_req rate to 2 per second on Ten-GigabitEthernet 1/0/1:
Switch (config)# interface ten-gigabitEthernet 1/0/1
Switch (config-if)# ptp pdelay-req-interval-1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ptp clock-step

### Purpose
The ptp clock-step command is used to configure the timestamp carrying mode of the message on the port. The no command is used to restore the default value under the current protocol standard.

### Command Mode
Interface Configuration Mode.

### Syntax
```text
ptp clock-step {one-step | two-step}
no ptp clock-step
```

### Parameters
```text
None
Notes
Not applicable for E2ETC/P2PTC node types.
Unavailable under IEEE 802.1AS.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set timestamp mode to two-step on Ten-GigabitEthernet 1/0/1:
Switch (config)# interface ten-gigabitEthernet 1/0/1
Switch (config-if)# ptp clock-step two-step
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ptp delay-mechanism

### Purpose
The ptp delay-mechanism command is used to configure the delay measurement mechanism used by the port. The no command is used to restore the default value under the current protocol standard.

### Command Mode
Interface Configuration Mode.

### Syntax
```text
ptp delay-mechanism {e2e | p2p}
no ptp delay-mechanism
```

### Parameters
```text
None
Notes
Not applicable for E2ETC/P2PTC node types.
Unavailable under IEEE 802.1AS.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set delay mechanism to P2P on Ten-GigabitEthernet 1/0/1:
Switch (config)# interface ten-gigabitEthernet 1/0/1
Switch (config-if)# ptp delay-mechanism p2p
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ptp asymmetry-correction

### Purpose
The ptp asymmetry-correction command is used to configure the asymmetric delay correction time for the port to send ptp messages. The no command is used to cancel the asymmetric delay correction time for the port to send ptp messages. By default, it is not configured.

### Command Mode
Interface Configuration Mode.

### Syntax
```text
ptp asymmetry-correction asymmetry-correction
no ptp asymmetry-correction
```

### Parameters
```text
asymmetry-correction
Specify the correction time in nanoseconds.
Notes
Corrects synchronization errors caused by unequal transmit/receive path delays.
```

### Default
By default, it is not configured.

### Example
```text
Set correction to 200 ns on Ten-GigabitEthernet 1/0/1:
Switch (config)# interface ten-gigabitEthernet 1/0/1
Switch (config-if)# ptp asymmetry-correction 200
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ptp eth-egress

### Purpose
The ptp eth-egress command is used to configure the layer 2 encapsulation for PTP messages. The no command is used to reset settings.

### Command Mode
Interface Configuration Mode.

### Syntax
```text
ptp mac-egress {destination-mac destination-mac | vlan vlan-id [priority priority]}
no ptp mac-egress { destination-mac | vlan }
```

### Parameters
```text
destination-mac
Destination MAC address of the packet in Layer 2 encapsulation.
vlan-id
VLAN ID of the packet in Layer 2 encapsulation.
priority
802.1p priority of the VLAN.
Notes
Invalid MACs (e.g., multicast) are rejected.
Disable UDP encapsulation first if configured.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set destination MAC to aa:bb:cc:11:22:33:
Switch (config)# interface ten-gigabitEthernet 1/0/1
Switch (config-if)# ptp mac-egress aa:bb:cc:11:22:33
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ptp udp-egress

### Purpose
The ptp udp-egress command is used to configure Layer 3 UDP encapsulation for PTP messages. The no command is used to reset settings.

### Command Mode
Interface Configuration Mode.

### Syntax
```text
ptp udp-egress {source-ip ip-address | destination-ip ip-address | destination-mac destination-mac | vlan vlan-id [priority priority] }
no ptp udp-egress {source-ip | destination-ip | destination-mac | vlan }
```

### Parameters
```text
source-ip
Source IP address of the Layer 3 packet encapsulation
destination-ip
Destination IP address of the Layer 3 packet encapsulation
destination-mac
Destination MAC address of the Layer 3 packet encapsulation.
vlan-id
VLAN ID of the Layer 3 packet encapsulation.
priority
802.1p priority of the VLAN.
Notes
When configuring UDP encapsulation, you need to configure the source IP address first.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the source IP address of UDP encapsulation to 192.168.1.5 on Ten-GigabitEthernet 1/0/1:
Switch (config)# interface ten-gigabitEthernet 1/0/1
Switch (config-if)# ptp udp-egress source-ip 192.168.1.5
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ptp reset-statistics

### Purpose
The ptp reset-statistics command is used to clear the statistics of the port's message transmission and reception.

### Command Mode
Interface Configuration Mode.

### Syntax
```text
ptp reset-statistics
```

### Parameters
```text
None
Notes
Once the message transmission and reception statistics are cleared, they cannot be restored.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Clear message statistics on Ten-GigabitEthernet 1/0/1:
Switch (config)# interface ten-gigabitEthernet 1/0/1
Switch (config-if)# ptp reset-statistics
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## show ptp all

### Purpose
The show ptp all command is used to view the running status of the PTP protocol.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ptp all
```

### Parameters
```text
None
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the the running status of the PTP protocol:
Switch (config)# show ptp all
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## show ptp interface

### Purpose
The show ptp interface command is used to view the running status and statistics of the PTP port.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ptp all
```

### Parameters
```text
None
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the running status and statistics of the PTP port on Ten-GigabitEthernet 1/0/1:
Switch (config)# show ptp interface ten-gigabitEthernet 1/0/1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.
