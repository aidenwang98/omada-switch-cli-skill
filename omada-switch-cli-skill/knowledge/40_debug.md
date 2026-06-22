# Debug Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 38 Debug Commands

Location: extracted Word text lines 17052-17628

## Chapter Notes

- Use these commands only when the requested feature and target interface/VLAN/ring/session details are clear.

## debug tppacket packet-dump cpu-traffic position

### Purpose
The debug tppacket packet-dump cpu-traffic position command is used to specify packets capture position.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
debug tppacket packet-dump cpu-traffic position { all | sdk-rx | module-rx | kernel-rx | sdk-tx | module-tx | kernel-tx | rule-own }
```

### Parameters
```text
sdk-rx: Captures raw packets obtained from the SDK, which can be used to debug whether packets enter the CPU. Additional information: tppacket structure descriptor.
module-rx: Captures packets that have been processed by tppacket rules and are forwarded to the corresponding module. It can be used to debug whether the module matches the packets. Additional information: tppacket structure descriptor, rule node information.
kernel-rx: Captures packets sent to the kernel. Additional information: tppacket structure descriptor.
sdk-tx: Captures all packets sent through the SDK, which can be used to verify whether packets are successfully delivered to the MAC.
module-tx: Captures packets sent by the module via the tpPacketSend function. Additional information: tppacket structure descriptor.
kernel-tx: Captures packets sent from the kernel. Additional information: tppacket structure descriptor.
rule-own: Captures packets processed by tppacket rules, forwarded to the corresponding module, and owned (own) by it. Additional information: tppacket structure descriptor, rule node information.
all: Captures packets at all the above locations (default).
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable packets capture at all positions:
Switch# debug tppacket packet-dump cpu-traffic position all
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- User guidelines: This command may cause network connections to be interrupted and some functions may not work properly. Please don't open it at will.

## debug tppacket packet-dump cpu-traffic dst-mac

### Purpose
The debug tppacket packet-dump cpu-traffic dst-mac command is used to set the destination MAC address filter.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
debug tppacket packet-dump cpu-traffic dst-mac mac address
```

### Parameters
```text
mac address: The destination MAC address, in the format of xx:xx:xx:xx:xx:xx.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch# debug tppacket packet-dump cpu-traffic dst-mac 00:1a:2b:3c:4d:5e
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- User guidelines: This command may cause network connections to be interrupted and some functions may not work properly. Please don't open it at will.

## debug tppacket packet-dump cpu-traffic src-mac

### Purpose
The debug tppacket packet-dump cpu-traffic src-mac command is used to set the source MAC address filter.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
debug tppacket packet-dump cpu-traffic src-mac mac address
```

### Parameters
```text
mac address: The source MAC address, in the format of xx:xx:xx:xx:xx:xx.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch# debug tppacket packet-dump cpu-traffic src-mac 00:1a:2b:3c:4d:5e
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- User guidelines: This command may cause network connections to be interrupted and some functions may not work properly. Please don't open it at will.

## debug tppacket packet-dump cpu-traffic len-type

### Purpose
The debug tppacket packet-dump cpu-traffic len-type command is used to set the length type filter.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
debug tppacket packet-dump cpu-traffic len-type length type
```

### Parameters
```text
length type: Specify the length, in decimal or hexadecimal format (range: 0 - 65535).
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch# debug tppacket packet-dump cpu-traffic len-type 1500
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- User guidelines: This command may cause network connections to be interrupted and some functions may not work properly. Please don't open it at will.

## debug tppacket packet-dump cpu-traffic ip-protocol

### Purpose
The debug tppacket packet-dump cpu-traffic ip-protocol command is used to set the IP protocol type filter.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
debug tppacket packet-dump cpu-traffic ip-protocol ip protocol type
```

### Parameters
```text
ip protocol type: Specify the IP protocol type, in decimal or hexadecimal format (range: 0 - 255).
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch# debug tppacket packet-dump cpu-traffic ip-protocol 6
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- User guidelines: This command may cause network connections to be interrupted and some functions may not work properly. Please don't open it at will.

## debug tppacket packet-dump cpu-traffic dst-ipv4

### Purpose
The debug tppacket packet-dump cpu-traffic dst-ipv4 command is used to set the destination IPv4 address filter.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
debug tppacket packet-dump cpu-traffic dst-ipv4 address
```

### Parameters
```text
address: The IPv4 address, in the format of a.b.c.d.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch# debug tppacket packet-dump cpu-traffic dst-ipv4 192.168.1.100
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- User guidelines: This command may cause network connections to be interrupted and some functions may not work properly. Please don't open it at will.

## debug tppacket packet-dump cpu-traffic src-ipv4

### Purpose
The debug tppacket packet-dump cpu-traffic src-ipv4 command is used to set the source IPv4 address filter.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
debug tppacket packet-dump cpu-traffic src-ipv4 address
```

### Parameters
```text
address: The IPv4 address, in the format of a.b.c.d.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch# debug tppacket packet-dump cpu-traffic src-ipv4 10.0.0.50
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- User guidelines: This command may cause network connections to be interrupted and some functions may not work properly. Please don't open it at will.

## debug tppacket packet-dump cpu-traffic dst-ipv6

### Purpose
The debug tppacket packet-dump cpu-traffic dst-ipv6 command is used to set the destination IPv6 address filter.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
debug tppacket packet-dump cpu-traffic dst-ipv6 address
```

### Parameters
```text
address: The IPv6 address, in the format of xxxx:xxxx:xxxx:xxxx:xxxx:xxxx:xxxx:xxxx.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch# debug tppacket packet-dump cpu-traffic dst-ipv6 2001:0db8:85a3:0000:0000:8a2e:0370:7334
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- User guidelines: This command may cause network connections to be interrupted and some functions may not work properly. Please don't open it at will.

## debug tppacket packet-dump cpu-traffic src-ipv4 (2)

### Purpose
The debug tppacket packet-dump cpu-traffic src-ipv6 command is used to set the source IPv6 address filter.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
debug tppacket packet-dump cpu-traffic src-ipv6 address
```

### Parameters
```text
address: The IPv6 address, in the format of xxxx:xxxx:xxxx:xxxx:xxxx:xxxx:xxxx:xxxx.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch# debug tppacket packet-dump cpu-traffic src-ipv6 fe80:0000:0000:0000:0202:b3ff:fe1e:8329
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- User guidelines: This command may cause network connections to be interrupted and some functions may not work properly. Please don't open it at will.

## debug tppacket packet-dump cpu-traffic dst-port

### Purpose
The debug tppacket packet-dump cpu-traffic dst-port command is used to set the transport layer destination port filter.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
debug tppacket packet-dump cpu-traffic dst-port transport port
```

### Parameters
```text
transport port: The destination port number, ranging from 0 to 65535.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch# debug tppacket packet-dump cpu-traffic dst-port 443
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- User guidelines: This command may cause network connections to be interrupted and some functions may not work properly. Please don't open it at will.

## debug tppacket packet-dump cpu-traffic src-port

### Purpose
The debug tppacket packet-dump cpu-traffic src-port command is used to set the transport layer source port filter.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
debug tppacket packet-dump cpu-traffic src-port transport port
```

### Parameters
```text
transport port: The source port number, ranging from 0 to 65535.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch# debug tppacket packet-dump cpu-traffic src-port 55000
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- User guidelines: This command may cause network connections to be interrupted and some functions may not work properly. Please don't open it at will.

## debug tppacket packet-dump cpu-traffic tail

### Purpose
The debug tppacket packet-dump cpu-traffic tail command is used to set the packet tail data filter. This configuration checks if the 5th, 6th, and 7th bytes from the end of the packet simultaneously equal the specified tail value (e.g., adding ten 0x88 bytes to the packet tail would allow capture using this filter). Packets not matching are not captured.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
debug tppacket packet-dump cpu-traffic tail value
```

### Parameters
```text
value: The tail value, in decimal or hexadecimal format (range: 0 - 255).
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch# debug tppacket packet-dump cpu-traffic tail 1
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- User guidelines: This command may cause network connections to be interrupted and some functions may not work properly. Please don't open it at will.

## debug tppacket packet-dump cpu-traffic rx-port

### Purpose
The debug tppacket packet-dump cpu-traffic rx-port command is used to set the switch receive port filter. This configuration checks if if the rxPort field in the tppacket structure equals the specified rx-port. Packets not matching are not captured.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
debug tppacket packet-dump cpu-traffic rx-port value
```

### Parameters
```text
value: Received port.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch# debug tppacket packet-dump cpu-traffic rx-port 1/0/1
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- User guidelines: This command may cause network connections to be interrupted and some functions may not work properly. Please don't open it at will.

## debug tppacket packet-dump cpu-traffic tx-port

### Purpose
The debug tppacket packet-dump cpu-traffic tx-port command is used to set the switch send port filter. This configuration checks if the uportList in the tppacket structure contains the specified tx-port. Packets not containing it are not captured.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
debug tppacket packet-dump cpu-traffic tx-port value
```

### Parameters
```text
value: Send port.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch# debug tppacket packet-dump cpu-traffic tx-port
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- User guidelines: This command may cause network connections to be interrupted and some functions may not work properly. Please don't open it at will.

## debug tppacket packet-dump cpu-traffic count limit

### Purpose
The debug tppacket packet-dump cpu-traffic count limit command is used to set the maximum number of packets to dump.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
debug tppacket packet-dump cpu-traffic count limit limit
```

### Parameters
```text
limit: The count limit value, ranging from 0 to 2^32. The default value is 128.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch# debug tppacket packet-dump cpu-traffic count limit 100
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- User guidelines: This command may cause network connections to be interrupted and some functions may not work properly. Please don't open it at will.

## debug tppacket packet-dump cpu-traffic dump-to

### Purpose
The debug tppacket packet-dump cpu-traffic dump-to command is used to specify the packet dump location.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
debug tppacket packet-dump cpu-traffic dump-to { stdout | txt-file | txt-ring-file | pcap-file | pcap-ring-file }
```

### Parameters
```text
tdout: (Default) Dumps packets to standard output (serial port), includes extra information (tppacket info, etc.).
txt-file: Dumps packets to a text file, includes extra information (tppacket info, etc.).
pcap-file: Dumps packets to a pcap file, contains no extra information, can be viewed with Wireshark.
txt-ring-file: Dumps packets to a ring (circular) text file. For example, if count-limit is set to 100, when the number of captured packets exceeds 100, the file is cleared and capturing starts anew.
pcap-ring-file: Dumps packets to a ring (circular) pcap file. For example, if count-limit is set to 100, when the number of captured packets exceeds 100, the file is cleared and capture restarts.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch# debug tppacket packet-dump cpu-traffic dump-to txt-file
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- User guidelines: This command may cause network connections to be interrupted and some functions may not work properly. Please don't open it at will.

## debug tppacket packet-dump port-rx rx-port dst-mac

### Purpose
The debug tppacket packet-dump port-rx rx-port command is used to capture all packets received on a specific port of a switch, regardless of whether the packet was originally intended to enter the CPU or was directly forwarded. The debug tppacket packet-dump port-rx rx-port dst-mac command is used to set the destination MAC address filter.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
debug tppacket packet-dump port-rx rx-port value dst-mac mac address
```

### Parameters
```text
value: Receive port number.
mac address: The destination MAC address, in the format of xx:xx:xx:xx:xx:xx.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch# debug tppacket packet-dump port-rx rx-port 1/0/1 dst-mac 00:1a:2b:3c:4d:5e
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- User guidelines: This command may cause network connections to be interrupted and some functions may not work properly. Please don't open it at will.

## debug tppacket packet-dump port-rx rx-port src-mac

### Purpose
The debug tppacket packet-dump port-rx rx-port src-mac command is used to set the source MAC address filter.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
debug tppacket packet-dump port-rx rx-port value src-mac mac address
```

### Parameters
```text
value: Receive port number.
mac address: The source MAC address, in the format of xx:xx:xx:xx:xx:xx.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch# debug tppacket packet-dump port-rx rx-port 1/0/1 src-mac 00:1a:2b:3c:4d:5e
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- User guidelines: This command may cause network connections to be interrupted and some functions may not work properly. Please don't open it at will.

## debug tppacket packet-dump port-rx rx-port len-type

### Purpose
The debug tppacket packet-dump port-rx rx-port len-type command is used to set the length type filter.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
debug tppacket packet-dump port-rx rx-port value len-type length type
```

### Parameters
```text
value: Receive port number.
length type: Specify the length, in decimal or hexadecimal format (range: 0 - 65535).
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch# debug tppacket packet-dump port-rx rx-port 1/0/1 len-type 1500
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- User guidelines: This command may cause network connections to be interrupted and some functions may not work properly. Please don't open it at will.

## debug tppacket packet-dump port-rx rx-port ip-protocol

### Purpose
The debug tppacket packet-dump port-rx rx-port ip-protocol command is used to set the IP protocol type filter.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
debug tppacket packet-dump port-rx rx-port value ip-protocol ip protocol type
```

### Parameters
```text
value: Receive port number.
ip protocol type: Specify the IP protocol type, in decimal or hexadecimal format (range: 0 - 255).
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch# debug tppacket packet-dump port-rx rx-port 1/0/1 ip-protocol 6
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- User guidelines: This command may cause network connections to be interrupted and some functions may not work properly. Please don't open it at will.

## debug tppacket packet-dump port-rx rx-port dst-ipv4

### Purpose
The debug tppacket packet-dump port-rx rx-port dst-ipv4 command is used to set the destination IPv4 address filter.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
debug tppacket packet-dump port-rx rx-port value dst-ipv4 address
```

### Parameters
```text
value: Receive port number.
address: The IPv4 address, in the format of a.b.c.d.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch# debug tppacket packet-dump port-rx rx-port 1/0/1 dst-ipv4 192.168.1.100
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- User guidelines: This command may cause network connections to be interrupted and some functions may not work properly. Please don't open it at will.

## debug tppacket packet-dump port-rx rx-port src-ipv4

### Purpose
The debug tppacket packet-dump port-rx rx-port value src-ipv4 command is used to set the source IPv4 address filter.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
debug tppacket packet-dump port-rx rx-port value src-ipv4 address
```

### Parameters
```text
value: Receive port number.
address: The IPv4 address, in the format of a.b.c.d.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch# debug tppacket packet-dump port-rx rx-port 1/0/1 src-ipv4 10.0.0.50
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- User guidelines: This command may cause network connections to be interrupted and some functions may not work properly. Please don't open it at will.

## debug tppacket packet-dump port-rx rx-port dst-ipv6

### Purpose
The debug tppacket packet-dump port-rx rx-port dst-ipv6 command is used to set the destination IPv6 address filter.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
debug tppacket packet-dump port-rx rx-port value dst-ipv6 address
```

### Parameters
```text
value: Receive port number.
address: The IPv6 address, in the format of xxxx:xxxx:xxxx:xxxx:xxxx:xxxx:xxxx:xxxx.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch# debug tppacket packet-dump port-rx rx-port 1/0/1 dst-ipv6 2001:0db8:85a3:0000:0000:8a2e:0370:7334
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- User guidelines: This command may cause network connections to be interrupted and some functions may not work properly. Please don't open it at will.

## debug tppacket packet-dump port-rx rx-port src-ipv4 (2)

### Purpose
The debug tppacket packet-dump port-rx rx-port src-ipv6 command is used to set the source IPv6 address filter.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
debug tppacket packet-dump port-rx rx-port value src-ipv6 address
```

### Parameters
```text
value: Receive port number.
address: The IPv6 address, in the format of xxxx:xxxx:xxxx:xxxx:xxxx:xxxx:xxxx:xxxx.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch# debug tppacket packet-dump port-rx rx-port 1/0/1 src-ipv6 fe80:0000:0000:0000:0202:b3ff:fe1e:8329
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- User guidelines: This command may cause network connections to be interrupted and some functions may not work properly. Please don't open it at will.

## debug tppacket packet-dump port-rx rx-port dst-port

### Purpose
The debug tppacket packet-dump port-rx rx-port dst-port command is used to set the transport layer destination port filter.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
debug tppacket packet-dump port-rx rx-port value dst-port transport port
```

### Parameters
```text
value: Receive port number.
transport port: The destination port number, ranging from 0 to 65535.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch# debug tppacket packet-dump port-rx rx-port 1/0/1 dst-port 443
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- User guidelines: This command may cause network connections to be interrupted and some functions may not work properly. Please don't open it at will.

## debug tppacket packet-dump port-rx rx-port src-port

### Purpose
The debug tppacket packet-dump port-rx rx-port src-port command is used to set the transport layer source port filter.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
debug tppacket packet-dump port-rx rx-port value src-port transport port
```

### Parameters
```text
value: Receive port number.
transport port: The source port number, ranging from 0 to 65535.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch# debug tppacket packet-dump port-rx rx-port 1/0/1 src-port 55000
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- User guidelines: This command may cause network connections to be interrupted and some functions may not work properly. Please don't open it at will.

## debug tppacket packet-dump port-rx rx-port tail

### Purpose
The debug tppacket packet-dump port-rx rx-port tail command is used to set the packet tail data filter. This configuration checks if the 5th, 6th, and 7th bytes from the end of the packet simultaneously equal the specified tail value (e.g., adding ten 0x88 bytes to the packet tail would allow capture using this filter). Packets not matching are not captured.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
debug tppacket packet-dump port-rx rx-port value tail value
```

### Parameters
```text
value: Receive port number.
value: The tail value, in decimal or hexadecimal format (range: 0 - 255).
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch# debug tppacket packet-dump port-rx rx-port 1/0/1 tail 1
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- User guidelines: This command may cause network connections to be interrupted and some functions may not work properly. Please don't open it at will.

## debug tppacket packet-dump port-rx rx-port count limit

### Purpose
The debug tppacket packet-dump port-rx rx-port count limit command is used to set the maximum number of packets to dump.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
debug tppacket packet-dump port-rx rx-port value count limit limit
```

### Parameters
```text
value: Receive port number.
limit: The count limit value, ranging from 0 to 2^32. The default value is 128.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch# debug tppacket packet-dump port-rx rx-port 1/0/1 count limit 100
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- User guidelines: This command may cause network connections to be interrupted and some functions may not work properly. Please don't open it at will.

## debug tppacket packet-dump port-rx rx-port dump-to

### Purpose
The debug tppacket packet-dump port-rx rx-port dump-to command is used to specify the packet dump location.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
debug tppacket packet-dump port-rx rx-port value dump-to { stdout | txt-file | txt-ring-file | pcap-file | pcap-ring-file }
```

### Parameters
```text
value: Receive port number.
tdout: (Default) Dumps packets to standard output (serial port), includes extra information (tppacket info, etc.).
txt-file: Dumps packets to a text file, includes extra information (tppacket info, etc.).
pcap-file: Dumps packets to a pcap file, contains no extra information, can be viewed with Wireshark.
txt-ring-file: Dumps packets to a ring (circular) text file. For example, if count-limit is set to 100, when the number of captured packets exceeds 100, the file is cleared and capturing starts anew.
pcap-ring-file: Dumps packets to a ring (circular) pcap file. For example, if count-limit is set to 100, when the number of captured packets exceeds 100, the file is cleared and capturing starts anew.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch# debug tppacket packet-dump port-rx rx-port 1/0/1 dump-to txt-file
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- User guidelines: This command may cause network connections to be interrupted and some functions may not work properly. Please don't open it at will.

## debug tppacket packet-dump download-txt-file

### Purpose
The debug tppacket packet-dump download-txt-file command is used to download the dumped packet text file via a TFTP server. A server IPv4 address must be specified. Note that the TFTP server must have write permission; otherwise, the transfer will fail.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
debug tppacket packet-dump download-txt-file server-ip ipv4 address
```

### Parameters
```text
ipv4 address: Specify the server IPv4 address.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch# debug tppacket packet-dump download-txt-file server-ip 192.168.1.100
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- User guidelines: This command may cause network connections to be interrupted and some functions may not work properly. Please don't open it at will.

## debug tppacket packet-dump download-pcap-file

### Purpose
The debug tppacket packet-dump download-pcap-file command is used to download the dumped packet pcap file via a TFTP server. A server IPv4 address must be specified. Note that the TFTP server must have write permission; otherwise, the transfer will fail.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
debug tppacket packet-dump download-pcap-file server-ip ipv4 address
```

### Parameters
```text
ipv4 address: Specify the server IPv4 address.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch# debug tppacket packet-dump download-pcap-file server-ip 192.168.1.100
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- User guidelines: This command may cause network connections to be interrupted and some functions may not work properly. Please don't open it at will.

## debug tppacket packet-dump show-txt-file

### Purpose
The debug tppacket packet-dump show-txt-file command is used to display the content of the dumped packet text file.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
debug tppacket packet-dump show-txt-file
```

### Parameters
```text
None,
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch# debug tppacket packet-dump show-txt-file
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- User guidelines: This command may cause network connections to be interrupted and some functions may not work properly. Please don't open it at will.

## no debug tppacket packet-dump

### Purpose
The no debug tppacket packet-dump command is used to disable the packet capture functionality. Note that the existing txt and pcap files are retained and will be overwritten the next time packet capture is enabled.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
no debug tppacket packet-dump
```

### Parameters
```text
None,
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch# no debug tppacket packet-dump
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- User guidelines: This command may cause network connections to be interrupted and some functions may not work properly. Please don't open it at will.

## debug tppacket packet-print (only for certain devices)

### Purpose
The debug tppacket packet-print command is used to enable the message printing function, which will only happen on the serial port and will affect switch performance. To disable this function, please use no debug tppacket packet-print command.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
debug tppacket packet-print
no tppacket packet-print
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the message printing function:
Switch# debug tppacket packet-print
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- User guidelines: This command may cause network connections to be interrupted and some functions may not work properly. Please don't open it at will.

## debug spanning-tree

### Purpose
The debug spanning-tree command is used to enable debugging of spanning-tree activities. To disable the debugging function, please use no debug spanning-tree command.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

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
