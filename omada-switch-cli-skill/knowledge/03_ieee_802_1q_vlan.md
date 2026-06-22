# IEEE 802.1Q VLAN Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 20 IEEE 802.1Q VLAN Commands

Location: official printed page 216-224; actual PDF page 262-270

## Chapter Notes

Official documentation states: VLAN (Virtual Local Area Network) technology is developed for the switch to divide the LAN into multiple logical LANs flexibly. Hosts in the same VLAN can communicate with each other, regardless of their physical locations. VLAN can enhance performance by conserving bandwidth, and improve security by limiting traffic to specific domains.

Engineering interpretation:
- This chapter does not include `switchport mode access`, `switchport mode trunk` commands of this type.
- Omada uses the IEEE 802.1Q VLAN general-port configuration model here: `switchport general allowed vlan` controls which VLANs a port joins and whether the egress direction is `tagged` or `untagged`.
- Common access-like behavior usually depends on the combination of untagged VLAN and `switchport pvid`; however, this knowledge base cannot output an `access` command because the official documentation does not provide that command.
- Initial switch-port behavior: ports are members of VLAN 1 by default, with VLAN 1 as the default untagged/PVID VLAN. For interface or port-channel VLAN configuration that targets VLANs other than VLAN 1, remove VLAN 1 from the port unless the intended configuration explicitly uses or keeps VLAN 1.
- Common trunk-like behavior usually depends on tagged VLAN lists, or on the official `vlan_trunk` command; however, this knowledge base cannot output `switchport mode trunk` because the official documentation does not provide that command.
- If the user says colloquial phrases such as "access port" or "trunk port", convert the intent to the official command model in this chapter and explain that it is an equivalent configuration approach, not an official command name.

## vlan

### Purpose
Create an IEEE 802.1Q VLAN and enter VLAN Configuration Mode; use `no vlan` to delete an IEEE 802.1Q VLAN.

### Command Mode
Global Configuration Mode

### Syntax
```text
vlan vlan-list
no vlan vlan-list
```

### Parameters
- `vlan-list`: IEEE 802.1Q VLAN ID list, range: 2 to 4094, in formats such as `2-3, 5`. This parameter is multi-optional.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config)# vlan 2-10,100
Switch(config)# no vlan 2
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## name

### Purpose
Assign a description to a VLAN; use `no name` to clear the description.

### Command Mode
VLAN Configuration Mode (VLAN)

### Syntax
```text
name descript
no name
```

### Parameters
- `descript`: VLAN description string, up to 16 characters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config)# vlan 2
Switch(config-vlan)# name group1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## vlan_trunk (globally)

### Purpose
Enable VLAN Trunk globally; after it is enabled, the switch automatically creates all VLANs (2-4094). Use `no vlan_trunk` to disable VLAN Trunk.

### Command Mode
Global Configuration Mode

### Syntax
```text
vlan_trunk
no vlan_trunk
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config)#vlan_trunk
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- This is the global `VLAN Trunk` command in the official documentation, not `switchport mode trunk`.

## vlan_trunk (interface)

### Purpose
Enable VLAN Trunk on a specified port. After it is enabled, packets in all VLANs can pass through the port. For VLANs already added with `switchport general allowed vlan`, data is forwarded according to the configured egress rule. For VLANs not manually added, data is forwarded with the `tagged` egress rule. Use `no vlan_trunk` to disable VLAN Trunk.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
vlan_trunk
no vlan_trunk
```

### Parameters
No parameters.

### Default
disabled.

### Example
```text
Switch(config)#interface gigabitEthernet 1/0/3
Switch(config-if)#vlan_trunk
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- This command is used for port VLAN Trunk, not `switchport mode trunk`.
- Because interface `vlan_trunk` allows all VLANs to pass, use explicit tagged VLAN membership instead when the intended configuration should exclude VLAN 1.

## switchport general allowed vlan

### Purpose
Add a specified port to an IEEE 802.1Q VLAN, or remove the port from the corresponding VLAN.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
switchport general allowed vlan vlan-list { tagged | untagged }
no switchport general allowed vlan vlan-list
```

### Parameters
- `vlan-list`: VLAN ID list, range: 1 to 4094, in formats such as `2-3, 5`. This parameter is multi-optional. You can also enter `all` to indicate all configured VLANs.
- `tagged | untagged`: egress-rule. When `vlan-list` is `all`, the egress-rule defaults to `tagged` and cannot be modified.

### Default
Initial switch ports are access-like members of VLAN 1. When `vlan-list` is `all`, the egress-rule defaults to `tagged`. Other defaults are not explicitly specified in the official documentation.

### Example
```text
Switch(config)#interface gigabitEthernet 1/0/4
Switch(config-if)#switchport general allowed vlan 2 tagged
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- This is the core command for port VLAN membership and tagged / untagged egress rules.
- If the user asks for an access-like port, usually use `untagged` together with `switchport pvid`; if the user asks for a trunk-like port, usually use tagged VLAN lists or `vlan_trunk`. This is an engineering mapping, not official `access` / `trunk` mode commands.
- For interface or port-channel VLAN configuration that targets VLANs other than VLAN 1, remove the default VLAN 1 membership with `no switchport general allowed vlan 1`, unless the intended configuration explicitly uses or keeps VLAN 1.
- For access-like reassignment from VLAN 1 to another VLAN, add the target VLAN as `untagged`, set the matching PVID, then remove VLAN 1.
- For trunk-like explicit VLAN lists, add the target VLANs as `tagged`, then remove VLAN 1 unless VLAN 1 is explicitly part of the intended VLAN set.

## switchport pvid

### Purpose
Configure the PVID of switch ports.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
switchport pvid vlan-id
```

### Parameters
- `vlan-id`: VLAN ID, range: 1 to 4094.

### Default
Initial switch ports use VLAN 1 as the default PVID VLAN.

### Example
```text
Switch(config)# interface gigabitEthernet 1/0/2
Switch(config-if)# switchport pvid 2
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- In common access-like port configurations, the PVID usually needs to match the port's untagged VLAN; the official documentation here only states that this command configures PVID.

## switchport check ingress

### Purpose
Enable the Ingress Checking function for switch ports. After it is enabled, the port only accepts packets whose VLAN ID is in the port VLAN list and discards other packets. When disabled, the port forwards packets directly. Use `no switchport check ingress` to disable this function.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
switchport check ingress
no switchport check ingress
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config)# interface gigabitEthernet 1/0/2
Switch(config-if)# switchport check ingress
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## switchport acceptable frame

### Purpose
Specify the acceptable frame type of switch ports. Official documentation states that the port performs this operation before Ingress Checking. Use `no switchport acceptable frame` to restore the default setting.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet / interface port-channel / interface range port-channel)

### Syntax
```text
switchport acceptable frame { all | tagged }
no switchport acceptable frame
```

### Parameters
- `all | tagged`: acceptable frame type.

### Default
Not explicitly specified in the official documentation.

### Example
Official confirmation: `general` in the original PDF example is a documentation error and should be `tagged`.

```text
Switch(config)#interface gigabitEthernet 1/0/4
Switch(config-if)#switchport acceptable frame tagged
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- The original PDF example uses `general`, but official confirmation states this is a documentation error; use `all` or `tagged` according to the Syntax.

## show vlan summary

### Purpose
Display summarized information for IEEE 802.1Q VLAN.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show vlan summary
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config)# show vlan summary
```

### Notes
- Permission requirement: None.

## show vlan brief

### Purpose
Display brief information for IEEE 802.1Q VLAN.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show vlan brief
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config)# show vlan brief
```

### Notes
- Permission requirement: None.

## show vlan

### Purpose
Display IEEE 802.1Q VLAN information. When no parameter is provided, display detailed information for all VLANs.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show vlan [ id vlan-id ]
```

### Parameters
- `vlan-id`: IEEE 802.1Q VLAN ID, range: 1 to 4094. This parameter is multi-optional.

### Default
When no parameter is provided, display detailed information for all VLANs.

### Example
```text
Switch(config)# show vlan id 5
```

### Notes
- Permission requirement: None.

## show interface switchport

### Purpose
Display IEEE 802.1Q VLAN configuration information for a specified port / port channel. When no parameter is provided, display VLAN configuration information for all ports and port channels.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show interface switchport [ fastEthernet port | gigabitEthernet port | ten-gigabitEthernet port | port-channel port-channel-id ]
```

### Parameters
- `port`: The port number.
- `port-channel-id`: The ID of the port channel.

### Default
When no parameter is provided, display VLAN configuration information for all ports and port channels.

### Example
```text
Switch(config)# show interface switchport
```

### Notes
- Permission requirement: None.
- Official Syntax lists `fastEthernet`, `gigabitEthernet`, `ten-gigabitEthernet`, and `port-channel`; it does not list `two-gigabitEthernet`.
