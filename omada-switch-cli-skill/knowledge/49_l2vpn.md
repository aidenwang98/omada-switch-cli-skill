# L2VPN Configuration Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 49 L2VPN Configuration Commands (Only for Certain Devices)

Location: extracted Word text lines 22589-22885

## Chapter Notes

Official documentation states: VPWS (Virtual Private Wire Service) is a point-to-point Layer 2 Virtual Private Network (L2VPN) technology. By establishing a logical connection between two Customer Edge (CE) devices, it enables communication similar to a traditional leased line connection. VPLS (Virtual Private LAN Service) is a Layer 2 Virtual Private Network (L2VPN) solution based on MPLS and Ethernet technologies. It is designed to simulate a local area network (LAN) over a wide area network (WAN) environment. Unlike the point-to-point communication of VPWS, VPLS provides point-to-multipoint communication. In a VPLS network, the PE device learns source MAC addresses while forwarding packets to establish a MAC address forwarding table. This maps MAC addresses to user-side Access Circuits (AC interfaces) and Pseudo Wires (PW). VPLS uses VSI instances to differentiate between forwarding domains, requiring MAC address table management based on these VSI instances.

- This chapter is marked `Only for Certain Devices`; treat all configuration commands as model-dependent.

## xconnect vc-id

### Purpose
This command is used to create a VPWS connection under an interface and bind it to that interface. The no version of this command is used to delete the configuration information and cancel the configured VPWS connection on the device. When creating a VPWS connection, label values can be manually assigned or dynamically negotiated using the LDP protocol.

### Command Mode
Interface Configuration Mode

### Syntax
```text
xconnect vc-id peer peer-ip [ in-label in-label out-label out-label ] raw/tagged
no xconnect
```

### Parameters
```text
vc-id
The index value of the VPWS connection, an integer ranging from <1-4294967295>.
peer-ip
The IP address of the peer device for the VPWS connection, in dotted-decimal format.
in-label
The value of the incoming label for the VPWS connection on this device, an integer ranging from <16-1024>.
out-label
The value of the outgoing label for the VPWS connection on this device, an integer ranging from <16-1048575>.
raw
The encapsulation mode of the VPWS connection is Ethernet.
tagged
The encapsulation mode of the VPWS connection is VLAN.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure a VPWS connection under the Interface VLAN 10:
Switch(config)# interface vlan10
Switch(config-if)# xconnect 10 peer 2.2.2.2 in-label 30 out-label 40 raw
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## show mpls vc

### Purpose
This command is used to display the forwarding information and status information of the VPWS connections already created on the device.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show mpls vc [ statistics | vc-id ]
```

### Parameters
```text
statistics
Displays statistical information for VPWS connections.
vc-id
The index value of the VPWS connection, used to display specific information for the corresponding connection.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
The device displays the specific information for VPWS connection 10:
Switch(config)# show mpls vc 10
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## vsi name vsi-id vpls-id

### Purpose
This command is used to create a VSI (Virtual Switch Instance) for VPLS forwarding. The no version of this command is used to delete the configuration and cancel the configured VSI instance.

### Command Mode
Global Configuration Mode

### Syntax
```text
vsi vpls-name vsi-id vpls-id
no vsi vpls-name vsi-id vpls-id
```

### Parameters
```text
vsi-name
The name of the VSI instance being created, in string format, with a length range of <1-32>.
vpls-id
The index of the VSI instance being created, in integer format, with a range of <1-4294967295>.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Create a VSI instance named a1 with a vsi-id of 200:
Switch(config)# vsi a1 vsi-id 200
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## description

### Purpose
This command is used to configure a description for the VSI instance. The no version is used to delete the description.

### Command Mode
VPLS Instance Configuration Mode

### Syntax
```text
description vpls-description
```

### Parameters
```text
vpls-description
Description information for the VSI instance, string format, length <1-32>.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Create VSI instance a1 and add a description:
Switch(config)# vsi a1 vsi-id 200
Switch(l2vpn-vpls)# description instance
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## signaling

### Purpose
This command is used to configure the signaling protocol for the VSI instance. Signaling protocols are used to negotiate label values; by default, no protocol is used (static labels).

### Command Mode
VPLS Instance Configuration Mode

### Syntax
```text
signaling [ ldp | static ]
```

### Parameters
```text
ldp
Sets the signaling protocol to LDP.
static
Configures the instance to use no signaling protocol (static).
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set the signaling protocol of VSI instance a1 to LDP:
Switch(config)# vsi a1 vsi-id 200
Switch(l2vpn-vpls)# signaling ldp
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ecapsulation

### Purpose
This command is used to configure the encapsulation mode (Ethernet or VLAN) for the VSI instance. This applies to every VPLS connection in the instance unless overridden by specific connection settings.

### Command Mode
VPLS Instance Configuration Mode

### Syntax
```text
encapsulation [ raw | tagged ]
no encapsulation
```

### Parameters
```text
raw
Sets the encapsulation mode to Ethernet.
tagged
Sets the encapsulation mode to VLAN.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set the encapsulation mode of VSI instance a1 to VLAN:
Switch(config)# vsi a1 vsi-id 200
Switch(l2vpn-vpls)# encapsulation tagged
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## peer

### Purpose
This command is used to create a VPLS connection under a VSI instance. When creating a VPLS connection, you can manually specify static label values or rely on signaling protocols for dynamic negotiation. Note that dynamic negotiation depends on the signaling protocol configured for the VSI instance. The default encapsulation mode is tagged. If no specific encapsulation is configured for the connection, it adopts the global configuration of the VSI instance. However, a specific connection-level configuration will override the global setting. Two types of VPLS connections can be created (Mesh peer is the default): Mesh peer: Used for full-mesh connectivity between devices and features split horizon functionality. Spoke peer: Used for connecting to a single device without split horizon; suitable for H-VPLS services. The no version of this command deletes the configuration and cancels the existing VPLS connection.

### Command Mode
VPLS Instance Configuration Mode

### Syntax
```text
peer peer-ip [ encapsulation raw/tagged ] [ in-label in-label out-label out-label ] [ spoke ]
no peer peer-ip
```

### Parameters
```text
peer-ip
The IP address of the VPLS peer, in dotted-decimal format.
in-label
The incoming label value for this device, an integer ranging from <16-1024>.
out-label
The outgoing label value for this device, an integer ranging from <16-1048575>.
raw
Sets the encapsulation mode to Ethernet.
tagged
Sets the encapsulation mode to VLAN.
spoke
Designates the connection as a spoke type.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Create VSI instance a1, and configure a mesh peer with peer IP 3.3.3.3, in-label 120, out-label 220, and raw encapsulation:
Switch(config)# vsi a1 vsi-id 200
Switch(l2vpn-vpls)# peer 3.3.3.3 encapsulation raw in-label 120 out-label 220
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## shutdown

### Purpose
This command is used to disable forwarding for all VPLS connections under the VSI instance. Use no shutdown to re-enable forwarding.

### Command Mode
VPLS Instance Configuration Mode

### Syntax
```text
shutdown
no shutdown
```

### Parameters
```text
None.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Disable forwarding for VSI instance a1:
Switch(config)# vsi a1 vsi-id 200
Switch(l2vpn-vpls)# shutdown
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## show vpls

### Purpose
This command is used to display the information of VSI instances created on the device, including the VPLS connection forwarding information and status information under the VSI instance.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show vpls name vpls-name [ peer | spoke spoke-peer ]
```

### Parameters
```text
vpls-name
The name of the VSI instance, in string format, with a length range of <1-32>.
peer
The IP address of the mesh peer connection's remote end, in dotted-decimal format; used to filter mesh peer information.
spoke peer
The IP address of the spoke peer connection's remote end, in dotted-decimal format; used to filter spoke peer information.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
The device displays all information under VSI instance a1:
Switch(config)# show vpls name a1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## mac learning

### Purpose
This command is used to control the MAC address learning function of a VSI instance. MAC learning is enabled for VSI by default. The no version of this command is used to delete the configuration and disable MAC address learning for the VSI.

### Command Mode
VPLS Instance Configuration Mode

### Syntax
```text
mac learning
no mac learning
```

### Parameters
```text
None.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Create VSI instance a1 and enable its MAC address learning function:
Switch(config)# vsi a1 vsi-id 10
Switch(l2vpn-vpls)# mac learning
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## mac aging-time

### Purpose
This command is used to configure the aging time for dynamic MAC addresses learned by the VSI instance. If the aging time is set to 0, the addresses will never age out. The no version deletes the configuration and restores the aging time to the default value.

### Command Mode
VPLS Instance Configuration Mode

### Syntax
```text
mac aging-time aging-time
no mac aging-time
```

### Parameters
```text
aging-time
The MAC address aging time, in integer format. The default value is 300s, with a range of <0 | 10-63000 >
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Create VSI instance a1 and set the MAC address aging time to 400s:
Switch(config)# vsi a1 vsi-id 10
Switch(l2vpn-vpls)# mac aging time 400
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## mac security

### Purpose
This command is used to configure security functions for MAC address learning in a VSI instance, including the maximum number of learned MAC addresses and the handling behavior for packets with unknown source MAC addresses once the limit is reached. The no version restores settings to default.

### Command Mode
VPLS Instance Configuration Mode

### Syntax
```text
mac security max-learn max-learn
mac security drop
no mac security max-learn
no mac security drop
no mac security
```

### Parameters
```text
max-learn
The maximum number of learned MAC addresses, in integer format. Default is 1000, range <0-2000>.
drop
Drops packets with unknown source MAC addresses after the learning limit is reached. The default behavior is to forward them.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Create VSI instance a1, set the learning limit to 300, and enable the MAC drop function:
Switch(config)# vsi a1 vsi-id 10
Switch(l2vpn-vpls)# mac security max-learn 300
Switch(l2vpn-vpls)# mac security drop
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## mac filtering

### Purpose
This command is used to configure blackhole MAC addresses for a VSI instance. Packets with source MAC addresses matching the blackhole addresses will be filtered (dropped). The no version removes the blackhole MAC address configuration.

### Command Mode
VPLS Instance Configuration Mode

### Syntax
```text
mac filtering mac-addr
no mac filtering [ mac-addr ]
```

### Parameters
```text
mac-addr
The blackhole MAC address, formatted as colon-separated hexadecimals.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Create VSI instance a1 and configure blackhole MAC address 10:7C:61:B1:2F:6B:
Switch(config)# vsi a1 vsi-id 10
Switch(l2vpn-vpls)# mac filtering 10:7C:61:B1:2F:6B
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## mac static

### Purpose
This command is used to configure the static MAC addresses for a VSI instance. Static MAC addresses are categorized into two types: This command is used to configure static MAC addresses for a VSI instance. Static MAC addresses are divided into two types: Static AC MAC: Bound to an AC interface. Static PW MAC: Bound to a remote PEER. When a static MAC address conflicts with a dynamically learned one, the static entry overrides the dynamic one. The no version deletes the static MAC address entry.

### Command Mode
Global Configuration Mode

### Syntax
```text
mac addess-table static mac-addr vsi vsi-id interface interface-type interface-num [ vlan vlan-id ]
mac addess-table static mac-addr vsi vsi-id peer peer-ip
no mac addess-table static mac-addr vsi vsi-id interface interface-type interface-num [ vlan vlan-id ]
no mac addess-table static mac-addr vsi vsi-id peer peer-ip
```

### Parameters
```text
mac-addr
The MAC address, formatted as colon-separated hexadecimals.
vsi-id
The index of the VSI instance, an integer ranging from <1-4294967295>.
interface-type
The type of the interface.
interface-num
The index of the interface.
vlan-id
The VLAN ID, required if the interface is a vlanIf interface.
peer-ip
The IP address of the VPLS peer, in dotted-decimal format.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure static MAC address 10:7C:61:B1:2F:6B, binding it to vlanIf 20 of VSI instance a1 and remote peer 3.3.3.3 of VSI instance a2:
Switch(config)# vsi a1 vsi-id 10
Switch(l2vpn-vpls)# exit
Switch(config)# vsi a2 vsi-id 20
Switch(l2vpn-vpls)# exit
Switch(config)# mac address-table static 10:7C:61:B1:2F:6B vsi 10 interface gigabitEthernet 1/0/11 vlan 20
Switch(config)# mac address-table static 10:7C:61:B1:2F:6B vsi 20 peer 3.3.3.3
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.
