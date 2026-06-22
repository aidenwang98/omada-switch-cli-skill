# LDP Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 88 LDP Commands (Only for Certain Devices)

Location: extracted Word text lines 30609-31049

## Chapter Notes

Official documentation states: LDP (Label Distribution Protocol) is a key protocol in MPLS (Multi-Protocol Label Switching) networks, used for dynamic label allocation and management. MPLS supports multi-layer labels and is connection-oriented, offering high scalability for various services over a unified MPLS/IP infrastructure. Through LDP, Label Switched Routers (LSRs) map network layer routing information directly to data link layer switching paths, dynamically establishing Label Switched Paths (LSPs).

- This chapter is marked `Only for Certain Devices`; treat all configuration commands as model-dependent.

## mpls ldp

### Purpose
This command is used to enable LDP globally. The no version deletes the configuration and disables global LDP. This control determines whether the LDP function is active for the entire switch.

### Command Mode
Global Configuration Mode

### Syntax
```text
mpls ldp
no mpls ldp
```

### Parameters
```text
None.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable LDP globally:
Switch(config)# mpls ldp
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## lsr-id

### Purpose
This command is used to configure the LSR-ID used for LDP protocol interaction between devices. The device uses this ID as an identifier for discovering and recognizing LDP neighbors. The no command deletes the LSR-ID configuration.

### Command Mode
LDP Configuration View

### Syntax
```text
lsr-id address
no lsr-id
```

### Parameters
```text
address
The global LSR-ID for LDP, in dotted-decimal format.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the LDP LSR-ID as 1.1.1.1:
Switch(config)# mpls ldp
Switch(config-ldp)# lsr-id 1.1.1.1
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## transport-address

### Purpose
This command configures the source IP address used by LDP when establishing TCP connections. This address must be the IP of a loopback interface on the device. The no command removes the set transport address.

### Command Mode
LDP Configuration View

### Syntax
```text
transport-address ip-address
no transport-address
```

### Parameters
```text
address
The global LSR-ID for LDP, in dotted-decimal format.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the LDP transport address as 1.1.1.1:
Switch(config)# mpls ldp
Switch(config-ldp)# transport-address 1.1.1.1
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## explicit-null

### Purpose
This command configures LDP to assign an explicit-null label when allocating the penultimate hop label. The no command cancels the assignment of the explicit-null label.

### Command Mode
LDP Configuration View

### Syntax
```text
explicit-null
no explicit-null
```

### Parameters
```text
None.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the device to allocate an explicit-null label for the penultimate hop:
Switch(config)# mpls ldp
Switch(config-ldp)# explicit-null
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## timer

### Purpose
This command sets the hold-time and interval for global LDP protocol messages. The no version restores the default values. Note: For certain message types (e.g., LDP Hello), the interval must be at least one-third of the hold-time.

### Command Mode
LDP Configuration View

### Syntax
```text
timer hello hold hello-hold
timer hello interval hello-interval
timer keepalive hold keepalive-hold
timer keepalive interval keepalive-interval
timer targeted-hello hold tgt-hello-hold
timer targeted-hello interval tgt-hello-hold
no timer hello hold
no timer hello interval
no timer keepalive hold
no timer keepalive interval
no timer target-hello hold
no timer target-hello interval
```

### Parameters
```text
hello-hold
Global LDP Hello hold-time, range 3 - 65535. The default value is 15s.
hello-interval
Global LDP Hello send interval, range 1- 65535. The default value is 5s.
keepalive-hold
Global LDP Keepalive hold-time, range 30 - 65535. The default value is 30s.
keepalive-interval
Global LDP Keepalive send interval, range 1 - 65535. The default value is 10s.
tgt-hello-hold
Global Targeted-Hello hold-time, range 3 - 65535. The default value is 15s.
tgt-hello-interval
Global Targeted-Hello send interval, range 1- 65535. The default value is 45s.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set Hello interval to 10s/hold 30s; Keepalive interval 20s/hold 60s; and Targeted-Hello interval 10s/hold 30s:
Switch(config)# mpls ldp
Switch(config-ldp)# timer hello hold 30
Switch(config-ldp)# timer hello interval 10
Switch(config-ldp)# timer keepalive hold 60
Switch(config-ldp)# timer keepalive interval 20
Switch(config-ldp)# timer targeted-hello hold 30
Switch(config-ldp)# timer targeted-hello interval 10
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## targeted-peer

### Purpose
This command is used to configure remote LDP neighbors to establish remote LDP sessions. The no command removes the configuration.

### Command Mode
LDP Configuration View

### Syntax
```text
targeted-peer ip-address
no targeted-peer
```

### Parameters
```text
ip-address
The address of the remote neighbor, in dotted-decimal format.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure a remote neighbor with the address 3.3.3.3:
Switch(config)# mpls ldp
Switch(config-ldp)# taegeted-peer 3.3.3.3
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## pwe3

### Purpose
This command is used to configure the LDP PWE3 (Pseudo Wire Emulation Edge-to-Edge) mode, which is an extension of L2VPN. The no command disables the PWE3 mode.

### Command Mode
LDP Configuration View

### Syntax
```text
pwe3
no pwe3
```

### Parameters
```text
None.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable LDP PWE3 mode:
Switch(config)# mpls ldp
Switch(config-ldp)# pwe3
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## label control-mode

### Purpose
This command is used to configure the LDP label distribution mode. The LDP label distribution modes include the following two types: Independent: This device can independently allocate a label and bind it to a certain FEC, then notify the upstream devices without waiting for labels from downstream devices. Ordered: For a label mapping of a certain FEC on the device, the device can only send the label mapping for this FEC to the upstream devices when the device already has the label mapping message for the next hop of this FEC, or if this device itself is the egress node for this FEC. The default LDP label distribution mode is Independent. The no command is used to delete the configuration and restore the LDP label distribution mode to the default mode.

### Command Mode
LDP Configuration View

### Syntax
```text
label control-mode { ordered | independent }
no label control-mode
```

### Parameters
```text
ordered
Sets the LDP label distribution mode to ordered.
independent
Sets the LDP label distribution mode to independent.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the device's LDP label distribution mode to ordered:
Switch(config)# mpls ldp
Switch(config-ldp)# label control-mode ordered
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## mpls ldp (2)

### Purpose
This command enables LDP packet forwarding on a specific interface. The no version disables it.

### Command Mode
Interface Configuration Mode

### Syntax
```text
mpls ldp
no mpls ldp
```

### Parameters
```text
None.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable MPLS LDP capability on Interface VLAN 10:
Switch(config)# interface vlan 10
Switch(config-if)# mpls
Switch(config-if)# mpls ldp
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## LDP Interface Timer

### Purpose
This command configures the hold-time and interval for LDP protocol messages at the interface level. Interface-level settings override global settings. For Hello messages, the interval must be at least one-third of the hold-time.

### Command Mode
Interface Configuration Mode

### Syntax
```text
mpls ldp timer hello hold hello-hold
mpls ldp timer hello interval hello-interval
mpls ldp timer keepalive hold keepalive-hold
mpls ldp timer keepalive interval keepalive-interval
no mpls ldp timer hello
no mpls ldp timer keepalive
```

### Parameters
```text
hello-hold
Interface Hello hold-time, range 3 - 65535. The default value is 15s.
hello-interval
Interface Hello interval, range 1-65535s The default value is 5s.
keepalive-hold
Interface Keepalive hold-time, range 30 - 65535. The default value is 30s.
keepalive-interval
Interface Keepalive interval, range 1-65535. The default value is 30s.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure interface vlan 10 with Hello interval 10s/hold 30s and Keepalive interval 20s/hold 60s:
Switch(config)# interface vlan 10
Switch(config-if)# mpls ldp timer hello hold 30
Switch(config-if)# mpls ldp timer hello interval 10
Switch(config-if)# mpls ldp timer keepalive hold 60
Switch(config-if)# mpls ldp timer keepalive interval 20
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## show mpls ldp global

### Purpose
This command used to display global LDP configuration and status information.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show mpls ldp global
```

### Parameters
```text
None.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display global LDP configuration:
Switch(config)# show mpls ldp global
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands
- Availability: Only for certain devices according to the official chapter title.

## show mpls ldp instance

### Purpose
This command used to display the information about created LDP instances.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show mpls ldp instance [ detail ]
```

### Parameters
```text
detail
Displays detailed information.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display LDP instance information:
Switch(config)# show mpls ldp instance
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands
- Availability: Only for certain devices according to the official chapter title.

## show mpls ldp fec

### Purpose
This command used to display FEC (Forwarding Equivalence Class) entry information.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show mpls ldp fec [ ipv4 ip-address/masklen ]
```

### Parameters
```text
ip-address
The IP address of the FEC, in dotted-decimal format.
masklen
The length of the subnet mask.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display FEC table entries:
Switch(config)# show mpls ldp fec
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands
- Availability: Only for certain devices according to the official chapter title.

## show mpls ldp route

### Purpose
This command used to display routing information received by LDP.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show mpls ldp route [ ipv4 ip-address/masklen ]
```

### Parameters
```text
ip-address
The IP prefix of the routing information, in dotted-decimal format.
masklen
The length of the subnet mask.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display routing information received via LDP:
Switch(config)# show mpls ldp route
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands
- Availability: Only for certain devices according to the official chapter title.

## show mpls ldp adjacency

### Purpose
This command used to display information about all LDP adjacencies established by the device.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show mpls ldp adjacency [ ip-address ]
```

### Parameters
```text
ip-address
The IP address of the adjacency, in dotted-decimal format.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display discovered LDP adjacencies:
Switch(config)# show mpls ldp adjacency
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands
- Availability: Only for certain devices according to the official chapter title.

## show mpls ldp session

### Purpose
This command used to display information about the LDP sessions established by the device.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show mpls ldp session [ ip-address ]
```

### Parameters
```text
ip-address
The IP address of the session peer, in dotted-decimal notation.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the established LDP session information on the device:
Switch(config)# show mpls ldp session
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands
- Availability: Only for certain devices according to the official chapter title.

## show mpls ldp interface

### Purpose
This command used to display the LDP interface enablement information on the device.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show mpls ldp interface [ interface-type interface-number ]
```

### Parameters
```text
Interface-type
Interface type.
Interface-number
Interface identifier.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the LDP interface enablement information on the device:
Switch(config)# show mpls ldp interface
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands
- Availability: Only for certain devices according to the official chapter title.

## show mpls ldp upstream

### Purpose
This command used to display the label information sent upstream by the device to the LDP session.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show mpls ldp upstream [ session session-address | fec fec-address/masklen ]
```

### Parameters
```text
session-address
The IP address of the session peer, in dotted-decimal notation. Displays detailed information.
fec-address
The IP address of the FEC, in dotted-decimal notation. Displays detailed information.
masklen
The mask length of the IP address.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the label information allocated upstream by the LDP session on the device:
Switch(config)# show mpls ldp upstream
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands
- Availability: Only for certain devices according to the official chapter title.

## show mpls ldp downstream

### Purpose
This command is used to display the label information received by the device from the LDP session downstream.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show mpls ldp downstream [ session session-address | fec fec-address/masklen ]
```

### Parameters
```text
session-address
The IP address of the session peer, in dotted-decimal notation. Displays detailed information.
fec-address
The IP address of the FEC, in dotted-decimal notation. Displays detailed information.
masklen
The mask length of the IP address.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the label information allocated downstream by the LDP session on the device:
Switch(config)# show mpls ldp downstream
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands
- Availability: Only for certain devices according to the official chapter title.

## show mpls ldp targeted-peer

### Purpose
This command is used to display neighbor information for the LDP remote sessions established by the device.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show mpls ldp targeted-peer [ ip-address ]
```

### Parameters
```text
ip-address
The IP address of the remote session peer, in dotted-decimal notation. Displays detailed information.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the neighbor information for LDP remote sessions on the device:
Switch(config)# show mpls ldp targeted-peer
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands
- Availability: Only for certain devices according to the official chapter title.

## show mpls ldp entity

### Purpose
This command is used to display the LDP entity information created by the device.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show mpls ldp entity [ interface interface-type interface-number |
remote ip-address ]
```

### Parameters
```text
Interface-type
Interface type.
Interface-number
Interface identifier.
ip-address
The IP address of the remote session, in dotted-decimal notation.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display all created LDP entity information on the device:
Switch(config)# show mpls ldp entity
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands
- Availability: Only for certain devices according to the official chapter title.

## show mpls ldp label-sapce

### Purpose
This command is used to display the label space information used by LDP on the device.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show mpls ldp label-sapce [ ip-address ]
```

### Parameters
```text
ip-address
The IP route address prefix for the session, in dotted-decimal notation.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the label space information used by LDP on the device:
Switch(config)# show mpls ldp label-space
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands
- Availability: Only for certain devices according to the official chapter title.

## show mpls ldp vc

### Purpose
This command is used to display dynamic VPWS information created by LDP on the device.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show mpls ldp vc [ vc-id | statistics ]
```

### Parameters
```text
vc-id
The VC-ID used for the VPWS connection. Displays detailed VC connection information.
statistics
Displays statistics for dynamic VPWS connections.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the dynamic VPWS connection information created by LDP on the device:
Switch(config)# show mpls ldp vc
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands
- Availability: Only for certain devices according to the official chapter title.

## show mpls ldp vpls

### Purpose
This command is used to display dynamic VPLS connection information created by LDP.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show mpls ldp vpls [ detail ]
```

### Parameters
```text
detail
Displays detailed dynamic VPLS connection information.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display all dynamic VPLS connection information created by LDP on the device:
Switch(config)# show mpls ldp vpls
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands
- Availability: Only for certain devices according to the official chapter title.
