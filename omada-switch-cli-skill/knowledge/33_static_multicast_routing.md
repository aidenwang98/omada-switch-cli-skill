# Static Multicast Routing Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 31 Static Multicast Routing Commands (Only for Certain Devices)

Location: extracted Word text lines 15096-15127

## Chapter Notes

Official documentation states: Multicast routing creates multicast routing table entries based on existing unicast routing information or multicast static routing. When creating multicast routing table entries, multicast routing protocols use the RPF (Reverse Path Forward) checking mechanism to ensure that multicast data can be forwarded along the correct path. Multicast static route entries are one of the important basis for RPF inspection and are mainly used to change or connect RPF routes.

- This chapter is marked `Only for Certain Devices`; treat all configuration commands as model-dependent.

## ip mroute

### Purpose
The ip mroute command is used to add/modify static multicast routing entries globally. To delete the specified static multicast routing entry, please use the no ip mroute command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip mroute { source-address } {mask} { rpf-address } [ distance ]
no ip mroute { source-address } {mask}
```

### Parameters
```text
source-address: IP address of the multicast source, in the format 192.168.0.1
mask: Subnet mask for the multicast source IP address
rpf-address: Specify the ingress interface of the RPF entry
distance: Management parameters of static multicast routing entries, ranging from 0 to 255. The smaller the value, the higher the priority. If the value of the static multicast route is smaller than the value of other RPF entries, the static multicast route takes effect. The default value is 1.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Add a static multicast routing entry with the source address 192.168.0.1, the subnet mask 255.255.255.255, the incoming interface of the RPF entry 192/168.1.1, and the management parameter 1:
Switch(config)#ip mroute 192.168.0.1 255.255.255.255 192.168.1.1 1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## show ip mroute static

### Purpose
The show ip mroute static command is used to display the IP mroute static information.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip mroute static { source source-ip }
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display all static multicast routing entries:
Switch(config)#show ip mroute static
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.
