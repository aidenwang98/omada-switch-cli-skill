# MPLS Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 87 MPLS Commands (Only for Certain Devices)

Location: extracted Word text lines 30377-30608

## Chapter Notes

Official documentation states: Multiprotocol Label Switching (MPLS) was initially developed to improve router forwarding speed. Compared to traditional IP routing, it analyzes IP packet headers only at the network edge during data forwarding, saving processing time by avoiding analysis at every hop. With the development of ASIC technology, route lookup speed is no longer a bottleneck for network development, rendering MPLS less of a significant advantage in improving forwarding speed. However, MPLS's support for multi-layer labeling and connection-oriented forwarding plane makes it widely used in Virtual Private Networks (VPNs), traffic engineering, and Quality of Service (QoS).

- This chapter is marked `Only for Certain Devices`; treat all configuration commands as model-dependent.

## mpls (global)

### Purpose
The mpls command enables the MPLS function globally. The no command deletes MPLS configuration information and disables MPLS globally. Global MPLS status controls whether the switch's global MPLS forwarding function is active.

### Command Mode
Global Configuration Mode

### Syntax
```text
mpls
no mpls
```

### Parameters
```text
None.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the MPLS function globally:
Switch(config)# mpls
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## mpls ttl-mode

### Purpose
The mpls ttl-mode command changes the TTL mode used by the switch for MPLS forwarding. The MPLS label contains an 8-bit TTL field, with the same meaning as the TTL field in the IP header. MPLS TTL processing is used not only to prevent routing loops but also to implement traceroute functionality. MPLS TTL processing includes two modes: Uniform and Pipe. Uniform: When an IP packet passes through an MPLS network, at the ingress node, the IP TTL is decremented by 1 and mapped to the MPLS TTL field. The packet is then processed according to standard TTL handling within the MPLS network. At the egress node, the MPLS TTL is decremented by 1 and mapped back to the IP TTL field. Pipe: At the ingress node, the IP TTL value is decremented by 1, while the MPLS TTL field remains a fixed value. The packet is then processed according to standard TTL handling within the MPLS network. At the egress node, the IP TTL field value is decremented by 1. In other words, when an IP packet passes through an MPLS network, regardless of the number of hops, the IP TTL is decremented by 1 only at both the ingress and egress nodes. By default, MPLS uses the Pipe mode for TTL processing.

### Command Mode
Global Configuration Mode

### Syntax
```text
mpls ttl-mode { pipe | uniform }
```

### Parameters
```text
pipe
Set the MPLS TTL mode to pipe.
uniform
Set the MPLS TTL mode to uniform.
```

### Default
By default, MPLS uses the Pipe mode for TTL processing.

### Example
```text
Set the MPLS TTL mode to uniform:
Switch(config)# mpls ttl-mode uniform
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## mpls ingress-lsp binding ipv4

### Purpose
The mpls ingress-lsp binding ipv4 command configures the ingress node for a static MPLS LSP tunnel. After packets pass through the tunnel ingress node, they will be tagged with the configured static MPLS label, which is used for subsequent forwarding by transit or egress nodes. The no command deletes the configuration information and cancels MPLS forwarding on the ingress node. You can specify a destination IPv4 address to delete ingress node configurations in batches.

### Command Mode
Not explicitly specified in the official documentation.

### Syntax
```text
mpls ingress-lsp binding ipv4 ip-address ip-mask out-label out-label nexthop nexthop-address
no mpls ingress-lsp binding ipv4 ip-address ip-m
onfigure the switch as an LSP ingress node, with LSP destination address 1.1.1.1, next hop 2.2.2.2, and outgoing label 50:
Switch(config)# mpls ingress-lsp binding ipv4 1.1.1.1 255.255.255.0 out-label 50 nexthop 2.2.2.2
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
Not explicitly specified in the official documentation.

### Notes
- Availability: Only for certain devices according to the official chapter title.

## mpls transmit-lsp binding ipv4

### Purpose
The mpls transmit-lsp binding ipv4 command configures the transit node for a static MPLS LSP tunnel. After a packet passes through the tunnel transit node, its MPLS static label is replaced or stripped for subsequent transit/egress nodes or IP forwarding. The no command deletes the configuration information and cancels MPLS forwarding on the transit node. You can specify a destination IPv4 address to delete transit node configurations in batches.

### Command Mode
Not explicitly specified in the official documentation.

### Syntax
```text
mpls transmit-lsp binding ipv4 ip-adddress ip-mask in-label in-label opcode { swap out-label | pop } nexthop nexthop-address
no mpls transmit-lsp binding ipv4 ip-adddress ip-mask [ in-label in-label opcode { swap out-label | pop } nexthop nexthop-address ] ]
```

### Parameters
```text
ip-address
The IP address of
Only Admin and Operator level users have access to these commands.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the switch as an LSP transit node with destination address 1.1.1.1, next hop 3.3.3.4, inbound label 50, and outbound label 60:
Switch(config)# mpls transit-lsp binding ipv4 1.1.1.1 255.255.255.255 in-label 50 opcode swap 60 nexthop 3.3.3.4
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## mpls egress-lsp binding

### Purpose
The mpls egress-lsp binding command configures the egress node for a static MPLS LSP tunnel. After a packet passes through the tunnel egress node, its MPLS static label is removed, and subsequent IP forwarding is performed. The no command deletes the configuration information and cancels MPLS forwarding on the egress node. You can specify a destination IPv4 address to delete egress node configurations in batches.

### Command Mode
Not explicitly specified in the official documentation.

### Syntax
```text
mpls egress-lsp binding ipv4 ip-address ip-mask in-label in-label
no mpls egress-lsp binding ipv4 ip-address ip-mask in-label in-label
```

### Parameters
```text
ip-address
The IP address of the st
Operator level users have access to these commands.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the switch as an LSP egress node, with LSP destination address 1.1.1.1 and inbound label 80:
Switch(config)# mpls egress-lsp binding ipv4 1.1.1.1 255.255.255.0 in-label 80
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## mpls (interface)

### Purpose
The mpls command enables the MPLS function on an interface. The no command deletes MPLS configuration information and disables MPLS on the interface. Interface MPLS status controls whether the current interface can participate in MPLS forwarding.

### Command Mode
Interface Configuration Mode

### Syntax
```text
mpls
no mpls
```

### Parameters
```text
None.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable MPLS on the interface:
Switch(config-if)# mpls
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## show mpls

### Purpose
The show mpls command is used to display the device's global MPLS status information and interface MPLS status information.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show mpls
```

### Parameters
```text
None.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the MPLS status information on the switch:
Switch(config-if)# show mpls
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## show mpls ftn

### Purpose
The show mpls ftn command is used to display FTN entry information, including forwarding and status information.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show mpls ftn
```

### Parameters
```text
None.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the FTN entry information on the switch:
Switch(config-if)# show mpls ftn
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## show mpls ilm

### Purpose
The show mpls ilm command is used to display ILM entry information, including forwarding and status information.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show mpls ilm
```

### Parameters
```text
None.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the ILM entry information on the switch:
Switch(config-if)# show mpls ilm
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## show mpls static-lsp

### Purpose
The show mpls static-lsp command displays the configuration information of a static LSP.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show mpls static-lsp [ ip-address/masklen ]
```

### Parameters
```text
ip-address
The destination IPv4 address for the static LSP, in dotted decimal notation.
masklen
The length of the IPv4 address mask.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the static LSP information on the switch:
Switch(config)# show mpls static-lsp
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## ping mpls ipv4

### Purpose
The ping mpls ipv4 command is used to check the connectivity of the LSP and whether the LSP can forward data normally.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
ping mpls ipv4 ip-address/mask-length [ source source-address ] [ destination destination-address ] [ repeat repeat-times ] [ timeout timeout ] [ interval interval ] [ ttl ttl ] [ reply-mode reply-mode ] [ fec-type fec-type ] [ detail ]
```

### Parameters
```text
ip-address
The destination address, in dotted decimal notation.
masklen
The mask length, integer, range 0-32.
sourece-address
The source IP address, in dotted decimal notation.
destination-address
The loopback address of the destination IP, in dotted decimal notation, default is 127.0.0.12.
repeat-times
Number of times packets are sent. Integer, range 1-10, default is 5.
time-out
Timeout period. Integer, range 1-10, default is 2, unit: seconds.
interval
Packet transmission interval. Integer, range 1-10, default is 1, unit: seconds.
ttl
TTL value. Integer, range 0-255, default is 255.
reply-mode
The response method after the peer end receives the message. Currently, the following response methods are supported:
No-reply: The peer does not receive a reply packet.
Ip-udp-reply: The peer receives a UDP reply packet.
Ip-udp-ra-reply: The peer receives a UDP packet in response to the router alert.
fec-type
The FEC type. Currently, the following FEC types are supported:
generic: General type
static: Static MPLS configuration
ldp: LDP generation
detail
Displays detailed information.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Perform an MPLS ping operation on the destination address 192.168.2.1/24, sending 8 request packets:
Switch# ping mpls ipv4 192.168.2.1/24 repeat 8
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## tracert mpls ipv4

### Purpose
The tracert mpls ipv4 command tests the path information from the source to the destination on an LSP (IPv4).

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
tracert mpls ipv4 ip-address/mask-length [ source source-address ] [ destination destination-address ] [ repeat repeat-times ] [ timeout timeout ] [ interval interval ] [ ttl ttl ] [ reply-mode reply-mode ] [ fec-type fec-type ] [ detail ]
```

### Parameters
```text
ip-address
The destination address, in dotted decimal notation.
masklen
The mask length, integer, range 0-32.
sourece-address
The source IP address, in dotted decimal notation.
destination-address
The loopback address of the destination IP, in dotted decimal notation, default is 127.0.0.12.
repeat-times
Number of times packets are sent. Integer, range 1-10, default is 5.
time-out
Timeout period. Integer, range 1-10, default is 2, unit: seconds.
interval
Packet transmission interval. Integer, range 1-10, default is 1, unit: seconds.
ttl
TTL value. Integer, range 0-255, default is 255.
reply-mode
The response method after the peer end receives the message. Currently, the following response methods are supported:
No-reply: The peer does not receive a reply packet.
Ip-udp-reply: The peer receives a UDP reply packet.
Ip-udp-ra-reply: The peer receives a UDP packet in response to the router alert.
fec-type
The FEC type. Currently, the following FEC types are supported:
generic: General type
static: Static MPLS configuration
ldp: LDP generation
detail
Displays detailed information.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Perform MPLS tracert operation on destination address 3.3.3.3/32:
Switch# tracert mpls ipv4 3.3.3.3/32
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.
