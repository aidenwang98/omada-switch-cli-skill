# DoS Defend Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 84 DoS Defend Commands

Location: extracted Word text lines 29910-29976

## Chapter Notes

Official documentation states: DoS (Denial of Service) Attack is to occupy the network bandwidth maliciously by the network attackers or the evil programs sending a lot of service requests to the Host. With the DoS Defend enabled, the switch can analyze the specific field of the received packets and provide the defend measures to ensure the normal working of the local network.

- Use these commands only when the requested feature and target interface/VLAN/ring/session details are clear.

## ip dos-prevent

### Purpose
The ip dos-prevent command is used to enable the DoS defend function globally. To disable the DoS defend function, please use no ip dos-prevent command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip dos-prevent
no ip dos-prevent
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the DoS defend function globally:
Switch(config)#ip dos-prevent
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip dos-prevent type

### Purpose
The ip dos-prevent type command is used to select the DoS Defend Type. To disable the corresponding Defend Type, please use no ip dos-prevent type command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip dos-prevent type { land | scan-synfin | xma-scan | null-scan | port-less-1024 | blat | ping-flood | syn-flood | win-nuke | ping-of-death | smurf }
no ip dos-prevent type { land | scan-synfin | xma-scan | null-scan | port-less-1024 | blat | ping-flood | syn-flood | win-nuke | ping-of-death | smurf }
```

### Parameters
```text
land
The attacker sends a specific fake SYN (synchronous) packet to the destination host. Because both of the source IP address and the destination IP address of the SYN packet are set to be the IP address of the host, the host will be trapped in an endless circle of building the initial connection.
scan-synfin
The attacker sends the packet with its SYN field and the FIN field set to 1. The SYN field is used to request initial connection whereas the FIN field is used to request disconnection. Therefore, the packet of this type is illegal.
xma-scan
The attacker sends the illegal packet with its TCP index, FIN, URG and PSH field set to 1.
null-scan
The attacker sends the illegal packet with its TCP index and all the control fields set to 0. During the TCP connection and data transmission, the packets with all control fields set to 0 are considered illegal.
port-less-1024
The attacker sends the illegal packet with its TCP SYN field set to 1 and source port smaller than 1024.
blat
The attacker sends the illegal packet with the same source port and destination port on Layer 4 and with its URG field set to 1. Similar to the Land Attack, the system performance of the attacked host is reduced because the Host circularly attempts to build a connection with the attacker.
ping-flood
The attacker floods the destination system with Ping packets, creating a broadcast storm that makes it impossible for the system to respond to legal communication.
syn-flood
The attacker uses a fake IP address to send TCP request packets to the server. Upon receiving the request packets, the server responds with SYN-ACK packets. Since the IP address is fake, no response will be returned. The server will keep on sending SYN-ACK packets. If the attacker sends overflowing fake request packets, the network resource will be occupied maliciously and the requests of the legal clients will be denied.
win-nuke
Because the Operation System with bugs cannot correctly process the URG (Urgent Pointer) of TCP packets, the attacker sends this type of packets to the TCP port139 (NetBIOS) of the host with the Operation System bugs, which will cause the host with a blue screen.
ping-of-death
Ping of Death attack means that the attacker sends abnormal ping packets larger than 65535 bytes to cause system crash on the target computer.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the DoS Defend Type named Land attack:
Switch(config)#ip dos-prevent type land
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Official note: ping-of-death is only available on certain devices. smurf Smurf attack is a distributed denial-of-service attack in which large numbers of Internet Control Message Protocol (ICMP) packets with the intended victim s spoofed source IP are broadcast to a computer network using an IP broadcast address. Most devices on a network will, by default, respond to this by sending a reply to the source IP address. If the number of machines on the network that receive and respond to these packets is very large, the victim s computer will be flooded with traffic. smurf is only available on certain devices.

## show ip dos-prevent

### Purpose
The show ip dos-prevent command is used to display the DoS information of the detected DoS attack, including enable/disable status, the DoS Defend Type, the count of the attack, etc.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip dos-prevent
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the DoS information of the detected DoS attack globally:
Switch(config)#show ip dos-prevent
```

### Notes
- Permission requirement: None.
