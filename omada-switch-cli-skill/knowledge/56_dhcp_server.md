# DHCP Server Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 56 DHCP Server Commands

Location: extracted Word text lines 24513-25052

## Chapter Notes

Official documentation states: DHCP (Dynamic Host Configuration Protocol) is a network configuration protocol for hosts on TCP/IP networks, and it provides a framework for distributing configuration information to hosts. DHCP server assigns IP addresses from specified address pools on a switch or router to DHCP clients and manages them.

- Use these commands only when the requested feature and target interface/VLAN/ring/session details are clear.

## service dhcp server

### Purpose
The service dhcp server command is used to enable DHCP service globally. To disable DHCP server service, please use no service dhcp server command.

### Command Mode
Global Configuration Mode

### Syntax
```text
service dhcp server
no service dhcp server
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable DHCP server service globally:
Switch(config)# service dhcp server
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip dhcp server extend-option capwap-ac-ip

### Purpose
The ip dhcp server extend-option capwap-ac-ip command is used to specify the Option 138, which should be configured as the management IP address of an AC (Access Control) device. If the APs in the local network request this option, the server will inform the APs of the AC s IP address by sending a packet containing this option. To delete the Option 138, please use no ip dhcp server extend-option capwap-ac-ip command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip dhcp server extend-option capwap-ac-ip ip-address
no ip dhcp server extend-option capwap-ac-ip
```

### Parameters
```text
ip-address
Specify the management IP address of an AC (Access Control) device.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set the remote DHCP server
s IP address as 192.168.3.1:
Switch(config)# ip dhcp server extend-option capwap-ac-ip 192.168.3.1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip dhcp server extend-option vendor-class-id

### Purpose
The ip dhcp server extend-option vendor-class-id command is used to configure the class ID of the packets from DHCP server in a different network segment. To delete the class ID settings, please use no ip dhcp server extend-option vendor-class-id command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip dhcp server extend-option vendor-class-id class-id
no ip dhcp server extend-option vendor-class-id
```

### Parameters
```text
class-id
Specify the class ID of the DHCP packets from another network segment.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set the class ID of the DHCP packets from another network segment as 34:
Switch(config)# ip dhcp server extend-option vendor-class-id 34
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip dhcp server excluded-address

### Purpose
The ip dhcp server excluded-address command is used to specify the reserved IP addresses which are forbidden to allocate, such as the gateway address, the network segment broadcast address, the server address etc. To delete the reserved IP addresses, please use no ip dhcp server excluded-address command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip dhcp server excluded-address start-ip-address end-ip-address
no ip dhcp server excluded-address start-ip- address end-ip-address
```

### Parameters
```text
start-ip-address
Specify the start IP address of the reserved IP pool.
end-ip-address
Specify the end IP address of the reserved IP pool. Only one IP address will be reserved if the end IP address and the start IP address are the same.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set the reserved IP addresses from 192.168.1.1 to 192.168.1.9:
Switch(config)# ip dhcp server excluded-address 192.168.1.1 192.168.1.9
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip dhcp server pool

### Purpose
The ip dhcp server pool command is used to create the address pool of DHCP Server and enter the dhcp configuration mode. To delete the address pool, please use no ip dhcp server pool command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip dhcp server pool pool-name
no ip dhcp server pool pool-name
```

### Parameters
```text
pool-name
Specify the address pool name, ranging from 1 to 8 characters.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Create the address pool of name POOL1:
Switch(config)# ip dhcp server pool POOL1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip dhcp server ping timeout

### Purpose
The ip dhcp server ping timeout command is used to specify the timeout of PING process. To resume the default value, please use no ip dhcp server ping timeout command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip dhcp server ping timeout value
no ip dhcp server ping timeout
```

### Parameters
```text
value
Specify the timeout value, ranging from 100 to 10000ms. The default value is 100ms.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set the timeout of PING as 200ms:
Switch(config)# ip dhcp server ping timeout 200
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip dhcp server ping packets

### Purpose
The ip dhcp server ping packets command is used to specify the number of PING packets sent. If this value is set to 0, the PING process will be disabled. To resume the default value, please use no ip dhcp server ping packets command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip dhcp server ping packets num
no ip dhcp server ping packets
```

### Parameters
```text
num
Specify the PING packets
number, ranging from 0 to 10. By default it
s 1.
```

### Default
By default it s 1.

### Example
```text
Specify the PING packets
number as 2:
Switch(config)# ip dhcp server ping packets 2
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip dhcp client gateway-detect

### Purpose
The ip dhcp client gateway-detect command is used to enable the gateway-detect function. When enabled, the device will initiate gateway probing tasks on all VLANs configured with DHCP client mode. To disable this function, please use no ip dhcp client gateway-detect command. By default, this function is disabled. Note that the gateway mentioned in this function description is not limited to gateway devices, but refers to the routing gateway obtained by DHCP.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip dhcp client gateway-detect
no ip dhcp client gateway-detect
```

### Parameters
```text
None.
```

### Default
By default, this function is disabled.

### Example
```text
Enable the gateway-detect function:
Switch(config)# ip dhcp client gateway-detect
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## network

### Purpose
The network command is used to specify the address and subnet of the network pool. The vrf command is used to modify the vrf instance to which the network segment of a specific address pool belongs.

### Command Mode
DHCP Configuration Mode DHCP Configuration Mode

### Syntax
```text
network { network-address subnet-mask } [vrf-name]
vrf [vrf-name]
```

### Parameters
```text
network-address
Specify the network address of the pool, with the format A.B.C.D. All the IP addresses in the same subnet are allocatable except the reserved addresses and specific addresses.
subnet-mask
Specify the subnet mask of the pool, with the format A.B.C.D.
vrf-name
VRF instance name
vrf-name
VRF instance name
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Specify the address pool
product
as 192.168.1.0 255.255.255.0:
Switch(config)# ip dhcp server pool p1
Switch(dhcp-config)# network 192.168.1.0 255.255.255.0 vrf1
Switch(config)# ip dhcp server pool p1
Switch(dhcp-config)# vrf vrf1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands. Only Admin, Operator and Power User level users have access to these commands.

## lease

### Purpose
The lease command is used to specify the lease time of the address pool.

### Command Mode
DHCP Configuration Mode

### Syntax
```text
lease lease-time
```

### Parameters
```text
lease-time
Specify the lease time of the pool, ranging from 1 to 2880 minutes. The default value is 120 minutes.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Specify the lease time of address pool
product
as 10 minutes:
Switch(config)# ip dhcp server pool product
Switch(dhcp-config)# lease 10
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## address hardware-address

### Purpose
The address hardware-address command is used to reserve the static address bound with hardware address in the address pool. To delete the binding, please use no address hardware-address.

### Command Mode
DHCP Configuration Mode

### Syntax
```text
address ip-address hardware-address hardware-address hardware-type { ethernet | ieee802 }
no address ip-address
```

### Parameters
```text
ip-address
Specify the static binding IP address.
hardware-address
Specify the hardware address, in the format XX:XX:XX:XX:XX:XX.
ethernet | ieee802
Specify the hardware type.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Reserve the IP address 192.168.0.10 in the address pool
product
for the device with the MAC address as 5e:4c:a6:31:24:01 and the hardware type as ethernet:
Switch(config)# ip dhcp server pool product
Switch(dhcp-config)# address 192.168.0.10 hardware-address 5e:4c:a6:31:24:01 hardware-type ethernet
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## address client-identifier

### Purpose
The address client-identifier command is used to specify the static address bound with client ID in the address pool. To delete the binding, please use no address command.

### Command Mode
DHCP Configuration Mode

### Syntax
```text
address ip-address client-identifier client-id [ascii]
no address ip-address
```

### Parameters
```text
ip-address
Specify the static binding IP address.
client-id
Specify the client ID, in the format of hex value.
ascii
The client ID is entered with ASCII characters.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Reserve the IP address 192.168.0.10 in the address pool
product
for the device with the client ID as abc in ASCII:
Switch(config)# ip dhcp pool product
Switch(dhcp-config)# address 192.168.0.10 client-identifier abc ascii
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## default-gateway

### Purpose
The default-gateway command is used to specify the default gateway of the address pool. To delete the configuration, please use no default-gateway.

### Command Mode
DHCP Configuration Mode

### Syntax
```text
default-gateway gateway-list
no default-gateway
```

### Parameters
```text
gateway-list
Specify the gateway list, with the format of A.B.C.D,E.F.G.H. At most 8 gateways can be configured, separated by comma.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Specify the address pool product
s default gateways as 192.168.0.1 and 192.168.1.1:
Switch(config)# ip dhcp server pool product
Switch(dhcp-config)# default-gateway 192.168.0.1,192.168.1.1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## dns-server

### Purpose
The dns-server command is used to specify the DNS server of the address pool. To delete this configuration, please use no dns-server command.

### Command Mode
DHCP Configuration Mode

### Syntax
```text
dns-server dns-list
no dns-server
```

### Parameters
```text
dns-list
Specify the DNS server list, with the format of A.B.C.D,E.F.G.H. At most 8 DNS servers can be configured, separated by comma.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Specify the address pool
s DNS servers as 192.168.0.1 and 192.168.1.1:
Switch(config)# ip dhcp server pool product
Switch(dhcp-config)# dns-server 192.168.0.1,192.168.1.1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip dns-address

### Purpose
The ip dns-address command is used to configure the IPv4 DNS address.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip dns-address primary primary-dns
ip dns-address secondary secondary-dns
ip dns-address primary secondary secondary-dns
no ip dns-address primary
no ip dns-address secondary
no ip dns-address
```

### Parameters
```text
primary-dns
IPv4 address of primary DNS.
secondary-dns
IPv4 address of secondary DNS.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Specify DNS as 8.8.8.8 and 8.8.4.4:
Switch(config)# ip dns-address primary 8.8.8.8 secondary 8.8.4.4
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ipv6 dns-address

### Purpose
The ipv6 dns-address command is used to configure the IPv6 DNS address.

### Command Mode
Global Configuration Mode

### Syntax
```text
ipv6 dns-address primary primary-dns
ipv6 dns-address secondary secondary-dns
ipv6 dns-address primary secondary secondary-dns
no ipv6 dns-address primary
no ipv6 dns-address secondary
no ipv6 dns-address
```

### Parameters
```text
primary-dns
IPv6 address of primary DNS.
secondary-dns
IPv6 address of secondary DNS.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Specify DNS as 2001:4860:4860::8888 and 2001:4860:4860::8844.
Switch (config)# ipv6 dns-address primary 2001:4860:4860::8888
Switch (config)# ipv6 dns-address secondary 2001:4860:4860::8844
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## netbios-name-server

### Purpose
The netbios-name-server command is used to specify the Netbios server s IP address. To delete the Netbios servers, please use no netbios-name-server command.

### Command Mode
DHCP Configuration Mode

### Syntax
```text
netbios-name-server NBNS-list
no netbios-name-server
```

### Parameters
```text
NBNS-list
Specify the Netbios server list, with the format of A.B.C.D,E.F.G.H. At most 8 Netbios servers can be configured, separated by comma.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Specify the address pool
s Netbios servers as 192.168.0.1 and 192.168.1.1:
Switch(config)# ip dhcp server pool product
Switch(dhcp-config)# netbios-name-server 192.168.0.1,192.168.1.1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## netbios-node-type

### Purpose
The netbios-node-type command is used to specify the Netbios server s node type. To delete the node type setttings, please use no netbios-node-type command.

### Command Mode
DHCP Configuration Mode

### Syntax
```text
netbios-node-type type
no netbios-node-type
```

### Parameters
```text
type
Specify the node type as b-node, h-node, m-node or p-node.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Specify the address pool
s Netbios server type as b-node:
Switch(config)# ip dhcp server pool product
Switch(dhcp-config)# netbios-node-type b-node
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## next-server

### Purpose
The next-server command is used to specify the next DHCP server s address during the DHCP boot process. To delete the next server, please use no next-server command.

### Command Mode
DHCP Configuration Mode

### Syntax
```text
next-server ip-address
next-server
```

### Parameters
```text
ip-address
Specify the IP address of the next server.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Specify the next server
s IP address as 192.168.2.1:
Switch(config)# ip dhcp server pool product
Switch(dhcp-config)# next-server 192.168.2.1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## domain-name

### Purpose
The domain-name command is used to specify the domain name for the DHCP client. To delete the domain name, please use no domain-name command.

### Command Mode
DHCP Configuration Mode

### Syntax
```text
domain-name domainname
no domain-name
```

### Parameters
```text
domainname
Specify the domain name for the DHCP client.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Specify the DHCP client
s domain name as edu:
Switch(config)# ip dhcp server pool product
Switch(dhcp-config)# domain-name edu
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## bootfile

### Purpose
The bootfile command is used to specify the name of the DHCP client s bootfile. To delete the bootfile, please use no bootfile command.

### Command Mode
DHCP Configuration Mode

### Syntax
```text
bootfile file-name
no bootfile
```

### Parameters
```text
file-name
Specify the name of the DHCP client
s bootfile.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Specify the name of the DHCP client
s bootfile as boot1:
Switch(config)# ip dhcp server pool product
Switch(dhcp-config)# bootfile boot1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## option

### Purpose
The option command is used to specify an option for the DHCP client. To delete the option, please use no option command.

### Command Mode
DHCP Configuration Mode

### Syntax
```text
option code [HEX | IP | STRING] value
no option
```

### Parameters
```text
value
Option value, ranging from 1 to 254.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Specify the option for the DHCP client as IP 1:
Switch(config)# ip dhcp server pool product
Switch(dhcp-config)# option code 1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## show ip dhcp server status

### Purpose
The show ip dhcp server status command is used to display the status of the DHCP service.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip dhcp server status
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the status of DHCP service:
Switch(config)# show ip dhcp server status
```

### Notes
- Permission requirement: None.

## show ip dhcp server statistics

### Purpose
The show ip dhcp server statistics command is used to display the DHCP packets received and sent by DHCP server.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip dhcp server statistics
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the statistics of DHCP packets received and sent by the DHCP server:
Switch(config)# show ip dhcp server statistics
```

### Notes
- Permission requirement: None.

## show ip dhcp server extend-option

### Purpose
The show ip dhcp server extend-option command is used to display the configuration of the remote DCHP servers.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip dhcp server extend-option
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the configurations of the remote DCHP servers:
Switch(config)# show ip dhcp server extend-option
```

### Notes
- Permission requirement: None.

## show ip dhcp server pool

### Purpose
The show ip dhcp server pool command is used to display the configuration of the address pool.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip dhcp server pool
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the configured address pool:
Switch(config)# show ip dhcp server pool
```

### Notes
- Permission requirement: None.

## show ip dhcp server excluded-address

### Purpose
The show ip dhcp server excluded-address command is used to display the configuration of reserved addresses.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip dhcp server excluded-address
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the configured reserved addresses:
Switch(config)# show ip dhcp server excluded-address
```

### Notes
- Permission requirement: None.

## show ip dhcp server manual-binding

### Purpose
The show ip dhcp server manual-binding command is used to display the configuration of static binding address.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip dhcp server manual-binding
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the configured static binding address:
Switch(config)# show ip dhcp server manual-binding
```

### Notes
- Permission requirement: None.

## show ip dhcp server binding

### Purpose
The show ip dhcp server binding command is used to display the binding entries.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip dhcp server binding [ ip ip-address ]
```

### Parameters
```text
ip-address
Specify the binding IP address.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the address binding entries:
Switch(config)# show ip dhcp server binding
```

### Notes
- Permission requirement: None.

## clear ip dhcp server statistics

### Purpose
The clear ip dhcp server statistics command is used to clear the statistics information of DHCP packets.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
clear ip dhcp server statistics
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Clear the packet statistics:
Switch(config)# clear ip dhcp server statistics
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## clear ip dhcp server binding

### Purpose
The clear ip dhcp server binding command is used to clear the binding information.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
clear ip dhcp server binding [ ip-address ]
```

### Parameters
```text
ip-address
Specify the binding IP address.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Clear all the binding addresses:
Switch(config)# clear ip dhcp server binding
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
