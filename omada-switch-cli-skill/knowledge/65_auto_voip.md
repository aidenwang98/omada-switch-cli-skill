# Auto VoIP Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 65 Auto VoIP Commands

Location: extracted Word text lines 26390-26507

## Chapter Notes

Official documentation states: The Auto VoIP feature is used to prioritize the transmission of voice traffic. Voice over Internet Protocol (VoIP) enables telephone calls over a data network, and the Auto VoIP feature helps provide a classification mechanism for voice packets. When Auto VoIP is configured on a port that receives both voice and data traffic, this feature can help ensure that the sound quality of an IP phone does not deteriorate when data traffic on the port is heavy.

- Use these commands only when the requested feature and target interface/VLAN/ring/session details are clear.

## auto-voip

### Purpose
The auto-voip command is used to enable the Auto VoIP function globally. To disable the Auto VoIP function, use no auto-voip command.

### Command Mode
Global Configuration Mode

### Syntax
```text
auto-voip
no auto-voip
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the Auto VoIP function globally:
Switch(config)# auto-voip
```

## auto-voip (interface)

### Purpose
The auto-voip command is used to specify the interface mode as VLAN ID for the ports. In this mode, the voice devices will send voice packets with desired VLAN tag.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
auto-voip vlan-id
```

### Parameters
```text
vlan-id
Specify the Auto VoIP VLAN ID. The valid values are from 2 to 4094.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set Auto VoIP VLAN 3 for port 3:
Switch(config)# interface gigabitEthernet 1/0/3
Switch(config-if)# auto-voip 3
```

## auto-voip dot1p

### Purpose
The auto-voip dot1p command is used to specify the interface mode as dat1p for the ports. In this mode, the voice devices will send voice packets with desired 802.1p priority.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
auto-voip dot1p dot1p
```

### Parameters
```text
dot1p
Set the 802.1p priority of Auto VoIP on specified ports. It ranges from 0 to 7.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set the 802.1p priority as 5 for the port:
Switch(config)# interface gigabitEthernet 1/0/3
Switch(config-if)# auto-voip dot1p 5
```

## auto-voip untagged

### Purpose
The auto-voip untagged command is used to specify the interface mode as untagged for the ports. In this mode, the voice devices will send untagged voice packets.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
auto-voip untagged
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set the interface mode as untagged for port 1/0/3:
Switch(config)# interface gigabitEthernet 1/0/3
Switch(config-if)# auto-voip untagged
```

## auto-voip none

### Purpose
The auto-voip none command is used to specify the interface mode as none for the ports. In this mode, the switch allows the voice devices to use its own configuration to send voice traffic.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
auto-voip none
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Instruct voice devices that are connected to port 3 to send the packets according to its own configuration:
Switch(config)# interface gigabitEthernet 1/0/3
Switch(config-if)# auto-voip none
```

## no auto-voip (interface)

### Purpose
The no auto-voip command is used to specify the interface mode as disabled for the ports, which means the Auto VoIP function is disabled on the corresponding port.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
no auto-voip
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Disable the Auto VoIP function on port 1/0/3:
Switch(config)# interface gigabitEthernet 1/0/3
Switch(config-if)# no auto-voip
```

## auto-voip dscp

### Purpose
The auto-voip dscp command is used to set the DSCP value of Auto VoIP on specified ports.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
auto-voip dscp value
```

### Parameters
```text
value
Set the DSCP value of Auto VoIP on specified ports. It ranges from 0 to 63. By default, it is 0.
```

### Default
By default, it is 0.

### Example
```text
Set DSCP value of Auto VoIP on port 3 as 33:
Switch(config)# interface gigabitEthernet 1/0/3
Switch(config-if)# auto-voip dscp 33
```

## auto-voip data priority

### Purpose
The auto-voip data priority command is used to enable or disable the CoS Override Mode on specified ports.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
auto-voip data priority { trust | untrust }
```

### Parameters
```text
trust
In this mode, the switch will then put the voice packets in the corresponding TC queue according to the 802.1p priority of the packets.
untrust
In this mode, the switch will ignore the 802.1p priority in the voice packets and put the packets in TC-5 directly.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set the CoS Override Mode as trust for port 1/0/3:
Switch(config)# interface gigabitEthernet 1/0/3
Switch(config-if)# auto-voip data priority trust
```

## show auto-voip

### Purpose
The show auto-voip command is used to display the Auto VoIP configuration information.

### Command Mode
Privileged EXEC Mode and any Configuration Mode

### Syntax
```text
show auto-voip [ interface ]
```

### Parameters
```text
interface
Displays the Auto VoIP configuration information of ports. When no parameter is entered, displays the global Auto VoIP configuration information.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Displays the global Auto VoIP configuration information:
Switch (config)# show auto-voip
```
