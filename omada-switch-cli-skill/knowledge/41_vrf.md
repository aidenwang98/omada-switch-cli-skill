# VRF Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 32 VRF Commands (Only for Certain Devices)

Location: extracted Word text lines 15128-15216

## Chapter Notes

Official documentation states: Virtual Routing and Forwarding (VRF) allows multiple instances of routing tables to coexist on the same rgateway (switch). Each VRF can be considered a virtual router, which includes the following elements: An independent routing table (including an independent address space); A set of interfaces belonging to this VRF; Routing protocols dedicated to this VRF; Each device can maintain one or more VRFs alongside a public routing table (global routing table). Multiple VRF instances are isolated and independent. Purpose: VRF enhances functionality by enabling the division of network paths without requiring multiple devices, effectively transforming one physical router into multiple virtual routers. Benefits: Because routing instances are independent, identical or overlapping IP addresses can be used without conflict. VRF improves network security through automatic traffic isolation and can eliminate the need for encryption or authentication. VRF is commonly used by ISPs to create separate VPNs for customers, hence it is often called VPN Routing and Forwarding. Description The vrf command is used to create a VRF instance and enters its configuration view. To delete the instance, please use the no vrf command. Syntax vrf vrf-name no vrf vrf-name Parameter vrf-name: VRF instance name (1-15 characters). Command Mode Global Configuration Mode Privilege Requirement Only Admin, Operator and Power User level users have access to these commands. Example Create a VRF instance named vrf1: Switch(config)#vrf vrf1

- This chapter is marked `Only for Certain Devices`; treat all configuration commands as model-dependent.

## address-family

### Purpose
The address-family command is used to enable the specified address family (IPv4/IPv6) for the VRF and enter its configuration view. To disable the address family, please use the no address-family command.

### Command Mode
VRF Instance View

### Syntax
```text
address-family {ipv4 | ipv6}
no address-family {ipv4 | ipv6}
```

### Parameters
```text
None
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable IPv4 for the vrf1 instance:
Switch(config)#vrf vrf1
Switch (config-vrf)#address-family ipv4
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## exit-address-family

### Purpose
The exit-address-family command is used to exit the VRF address family view and returns to the VRF configuration view.

### Command Mode
VRF Address Family View

### Syntax
```text
exit-address-family
```

### Parameters
```text
None
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Exit the IPv4 view of vrf1:
Switch(config)#vrf vrf1
Switch (config-vrf)#address-family ipv4
Switch (config-vrf-af)#exit-address-family
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## vrf forwarding

### Purpose
The vrf forwarding command is used to assign a L3 interface to a VRF instance. To remove the interface from the VRF and returns it to the global routing table, please use the no vrf forwarding command. Note: Switching VRFs deletes all existing interface configurations.

### Command Mode
L3 Interface Configuration Mode

### Syntax
```text
vrf forwarding vrf-name
no vrf forwarding vrf-name
```

### Parameters
```text
vrf-name: VRF instance name (1-15 characters).
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Assign interface VLAN 1 to the vrf1 instance:
Switch(config) # interface vlan 1
Switch(config-if)# vrf forwarding vrf1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## show vrf

### Purpose
The show vrf command is used to view the configured VRF instance information.

### Command Mode
Privileged EXEC Mode or Any Configuration Mode

### Syntax
```text
show vrf {brief | interface | name vrf-name }
```

### Parameters
```text
vrf-name: VRF instance name
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the configured VRF instance information:
Switch (config)# show vrf brief
Switch (config)# show vrf interface
Switch (config)# show vrf name vrf1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.
