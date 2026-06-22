# Management Port Configuration Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 8 Management Port Configuration Commands

Location: Word document text export, Chapter 8, after Chapter 7 File System Configuration Commands and before Chapter 9 EEE Configuration Commands.

## Chapter Notes

Management Port Configuration Commands configure IPv4/IPv6 behavior and display configuration for a dedicated management port on supported devices. The official chapter title says these commands are only available on certain devices; do not assume every Omada switch model has a dedicated management port.

## management-port protocol

### Purpose

The management-port protocol command is used to enable or disable the IPv4 DHCP funtion on the management port.

### Command Mode

Global Configuration Mode

### Syntax

```text
management-port protocol {dhcp|none}
```

### Parameters

- dhcp
- Enable the DHCP function
- none
- Disable the DHCP function

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Enable the IPv4 DHCP funtion on the management port:
Switch(config)#management-port protocol dhcp
```

### Notes
- Privilege requirement: Only Admin, Operator and Power User level users have access to these commands.

## management-port ip

### Purpose

The management-port ip command is used to configure the IPv4 address of the management port. To delete the address, please use the no management-port ip command.

### Command Mode

Global Configuration Mode

### Syntax

```text
management-port ip {ip-addr}{mask}
no management-port ip
```

### Parameters

- ip-addr
- IPv4 address
- mask
- IP mask

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Configure the IPv4 address of the management port:
Switch(config)#management-port ip 192.168.10.1 255.255.255.0
```

### Notes
- Privilege requirement: Only Admin, Operator and Power User level users have access to these commands.

## management-port ipv6 enable

### Purpose

The management-port ipv6 enable command is used to enable the management-port ipv6 funtion. To disable the function, please use the no management-port ipv6 enable command.

### Command Mode

Global Configuration Mode

### Syntax

```text
management-port ipv6 enable
no management-port ipv6 enable
```

### Parameters

Official documentation does not explicitly specify parameters.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Enable the management-port ipv6 funtion:
Switch(config)#management-port ipv6 enable
```

### Notes
- Privilege requirement: Only Admin, Operator and Power User level users have access to these commands.

## management-port ipv6 address

### Purpose

The management-port ipv6 address command is used to configure the IPv6 address of the management port. To delete the address, please use the no management-port ipv6 address command.

### Command Mode

Global Configuration Mode

### Syntax

```text
management-port ipv6 address {ipv6-addr} [eui64]
no management-port ipv6 address {ipv6-addr} [eui64]
```

### Parameters

- ipv6-addr
- IPv6 address, you need to specify the prefix length.
- eui64
- Create the address in eui64 mode.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Configure the IPv6 address of the management port:
Switch(config)#management-port ipv6 address 2001::1/64 eui64
```

### Notes
- Privilege requirement: Only Admin, Operator and Power User level users have access to these commands.

## show management-port

### Purpose

The show management-port command is used to display the configuration information of the management port.

### Command Mode

Privileged EXEC Mode and Any Configuration Mode

### Syntax

```text
show management-port
```

### Parameters

Official documentation does not explicitly specify parameters.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Display the configuration information of the management port:
Switch# show management-port
```

### Notes
- Privilege requirement: None.
