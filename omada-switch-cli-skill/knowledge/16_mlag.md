# MLAG Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 18 MLAG Commands (Only for Certain Devices)

Location: extracted Word text lines 10847-11147

## Chapter Notes

Official documentation states: MLAG (Multi-Chassis Link Aggregation) enables two network switches to act as a single logical entity, bonding their physical links into a shared aggregated connection. This setup enhances redundancy and bandwidth while preventing traffic disruption if one switch fails. Commonly used in data centers, MLAG ensures seamless failover, simplifies network management, and avoids single points of failure without requiring complex protocols like stacking.

- This chapter is marked `Only for Certain Devices`; treat all configuration commands as model-dependent.
- When a command or note is device-specific in the official text, mention model and firmware dependency before recommending it.

## mlag enable

### Purpose
The mlag enable command is used to enable and configure the MLAG domain name.

### Command Mode
Global Configuration Mode

### Syntax
```text
mlag enable {domainName}
```

### Parameters
```text
domainName
The MLAG group domain name, domainName, is used to uniquely identify an MLAG system. An MLAG system can only be established between two devices if they share the same domainName. The allowed range for this parameter is a string of 1 to 31 characters.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable MLAG and configure the domain name as 1:
Switch(config)# mlag enable 1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## mlag disable

### Purpose
The mlag disable command is used to disable the MLAG function.

### Command Mode
Global Configuration Mode

### Syntax
```text
mlag disable retain-mlag-config
```

### Parameters
```text
retain-mlag-config
Indicates whether to retain MLAG-related configurations. If the retain-mlag-config parameter is specified, existing MLAG parameters will be preserved; otherwise, all MLAG-related configurations will be cleared, including MLAG member ports (while aggregation groups will remain intact). By default, configurations will not be retained.
```

### Default
By default, configurations will not be retained.

### Example
```text
Disable the MLAG function:
Switch(config)# mlag disable
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## interface

### Purpose
The interface command is used to configure the peer-link port for the internal control link of MLAG.

### Command Mode
MLAG-domain Configuration Mode

### Syntax
```text
interface {peer-link-port}
```

### Parameters
```text
peer-link-port
Specifies the peer-link port list. Only the highest-rate optical ports are allowed to be configured as peer-links. Multiple ports can be configured to form a peer-link group when specified collectively.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the peer-link port of 1/0/29-30:
Switch(config)#mlag domain 1
Switch(mlag-domain)#interface 1/0/29-30
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## priority

### Purpose
The priority command is used to configure the device's priority during MLAG pairing. A higher priority increases the likelihood of becoming the primary device.

### Command Mode
MLAG-domain Configuration Mode

### Syntax
```text
priority {priority}
```

### Parameters
```text
priority
The priority value. The default is 5, with a higher value being more likely to become the primary device. The valid range is 1 to 255.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the device's priority as 100:
Switch(config)#mlag domain 1
Switch(mlag-domain)# priority 100
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## dad interface

### Purpose
The dad interface command is used to configure the DAD interface.

### Command Mode
MLAG-domain Configuration Mode

### Syntax
```text
dad interface {dadInterface}
```

### Parameters
```text
dadInterface
MLAG dual-primary detection interface. Only one physical port can be configured as the dad-interface. To replace the existing configuration, you must first delete the existing configuration before adding a new one.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the DAD interface 1/0/29:
Switch(config)#mlag domain 1
Switch(mlag-domain)# dad interface 1/0/29
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## dad param

### Purpose
The dad param command is used to configure DAD intercommunication parameters. The MLAG dual-active detection function operates at Layer 3, therefore IP addresses and related parameters need to be configured for this feature. Ensure DAD IP addresses between peer devices reside in the same subnet and can communicate, and avoid conflicts with other interface subnets.

### Command Mode
MLAG-domain Configuration Mode

### Syntax
```text
dad param peer-ip-address {peerIpAddr } src-ip-address {localIpAddr } port {l4Port}
```

### Parameters
```text
peerIpAddr
DAD-IP address of the MLAG peer device (IPv4). Must be in the same subnet as the local DAD IP with connectivity, and must not conflict with other interface subnets.
localIpAddr
Local DAD-IP address for this MLAG device (IPv4). Must be in the same subnet as the peer DAD IP with connectivity, and must not conflict with other interface subnets.
l4Port
(Optional) Communication port for MLAG DAD. Valid range: 50000-60000. Default: 50000 when unconfigured.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the DAD intercommunication parameters:
Switch(config)#mlag domain 1
Switch(mlag-domain)# dad param peer-ip-address 192.168.2.1 src-ip-address 192.168.2.2 port 60000
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## dad tx-interval

### Purpose
The dad tx-interval command is used to configure the DAD message transmission interval. Both devices in the MLAG domain must use the same value; otherwise, DAD may malfunction if one device s transmission interval is shorter than the peer s timeout duration.

### Command Mode
MLAG-domain Configuration Mode

### Syntax
```text
dad tx-interval {intervalTime}
```

### Parameters
```text
intervalTime
The interval for MLAG dual-active detection messages, in milliseconds (ms). Default: 3000 ms. Configurable range: 3s to 10s (note: the interval must not exceed the DAD timeout).
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the DAD message transmission interval as 3000ms:
Switch(config)#mlag domain 1
Switch(mlag-domain)# dad tx-interval 3000
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## dad timeout

### Purpose
The dad timeout command is used to configure the DAD timeout duration. Both devices in the MLAG domain must use the same value; otherwise, DAD may malfunction if one device s transmission interval is shorter than the peer s timeout.

### Command Mode
MLAG-domain Configuration Mode

### Syntax
```text
dad timeout { timeoutTime }
```

### Parameters
```text
timeoutTime
The timeout duration for MLAG dual-active detection, in milliseconds (ms). Default: 4000 ms. Configurable range: 4s to 15s (note: the message interval must not exceed the DAD timeout).
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the DAD timeout duration as 4000ms:
Switch(config)#mlag domain 1
Switch(mlag-domain)# dad timeout 4000
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## dad enable

### Purpose
The dad enable command is used to enable the DAD function. DAD-interface and DAD parameters must be fully configured before enabling DAD. To disable this function, please use the no dad enable command.

### Command Mode
MLAG-domain Configuration Mode

### Syntax
```text
dad enable
no dad enable
```

### Parameters
```text
None
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Disable the DAD function
Switch(config)#mlag domain 1
Switch(mlag-domain)# no dad enable
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## keep-alive interval

### Purpose
The keep-alive interval command is used to configure the keep-alive message interval (must be less than 1/3 of the KA timeout).

### Command Mode
MLAG-domain Configuration Mode

### Syntax
```text
keep-alive interval {kaInterval}
```

### Parameters
```text
kaInterval
Keep-alive message interval, in milliseconds (ms). Default: 500 ms. Configurable range: 300 to 5000.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the keep-alive message interval as 500ms:
Switch(config)#mlag domain 1
Switch(mlag-domain)# keep-alive interval 500
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## keep-alive timeout

### Purpose
The keep-alive timeout command is used to configure the keep-alive timeout (must be greater than 3 the KA interval).

### Command Mode
MLAG-domain Configuration Mode

### Syntax
```text
keep-alive timeout {kaTimeout }
```

### Parameters
```text
kaTimeout
Keep-alive timeout duration, in milliseconds (ms). Default: 7000 ms. Configurable range: 900 to 15000, with the timeout being at least 3
the interval.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the timeout as 7000ms:
Switch(config)#mlag domain 1
Switch(mlag-domain)# keep-alive timeout 7000
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## mlag

### Purpose
The mlag command is used to configure a regular aggregation group as an MLAG member port. Only MLAG member ports support cross-device link aggregation. MLAG systems pair identical aggregation groups (same lagid) from both devices into the same MLAG member group. To add/remove ports, use standard aggregation group commands. Use no mlag to revert an MLAG member group to a regular aggregation group. Prerequisites: 1. MLAG is enabled. 2. The aggregation group is configured.

### Command Mode
Interface Configuration Mode

### Syntax
```text
mlag
```

### Parameters
```text
None
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure interface 1 as an MLAG member port:
Switch(config)# interface port-channel 1
Switch(config-if)# mlag
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## mlag config-consistency-check

### Purpose
The mlag config-consistency-check command is used to enable MLAG configuration consistency checks. This function is enabled by default. A 120-second log silence period applies after MLAG pairing to suppress consistency alerts; users should resolve any mismatches promptly. To disable this function, use the no mlag config-consistency-check command. If disabled, users must manually ensure configuration consistency.

### Command Mode
Global Configuration Mode

### Syntax
```text
mlag config-consistency-check
no mlag config-consistency-check
```

### Parameters
```text
None
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable MLAG configuration consistency checks:
Switch(config)# mlag config-consistency-check
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## mlag config-consistency-check mode

### Purpose
The mlag config-consistency-check mode command is used to enable the MLAG configuration consistency check feature, which is enabled by default. A 120-second alert log suppression period for consistency checks begins immediately after MLAG pairing is completed. Users must promptly adjust configurations on both ends if inconsistencies are detected. To disable this feature, use the mlag config-consistency-check mode command. If the MLAG configuration consistency check is disabled, users are solely responsible for manually ensuring configuration consistency between both devices.

### Command Mode
Gloabl Configuration Mode

### Syntax
```text
mlag config-consistency-check mode
no mlag config-consistency-check mode
```

### Parameters
```text
None
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config)# mlag config-consistency-check
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## show mlag info

### Purpose
The show mlag info command is used to view the basic MLAG domain information.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show mlag info
```

### Parameters
```text
None
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the basic MLAG domain information:
Switch(config)# show mlag info
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## show mlag dual-active

### Purpose
The show mlag dual-active command is used to view the MLAG dual-active detection details.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show mlag dual-active
```

### Parameters
```text
None
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the MLAG dual-active detection details:
Switch(config)# show mlag dual-active
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## show mlag keep-alive

### Purpose
The show mlag keep-alive command is used to view the MLAG keep-alive heartbeat status.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show mlag keep-alive
```

### Parameters
```text
None
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the MLAG keep-alive heartbeat status:
Switch(config)# show mlag keep-alive
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## show mlag members-info

### Purpose
The show mlag members-info command is used to view the MLAG member port details.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show mlag members-info
```

### Parameters
```text
None
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the MLAG member port details:
Switch(config)# show mlag members-info
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## show mlag config-consistency-check

### Purpose
The show mlag config-consistency-check command is used to view the MLAG configuration consistency check status.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show mlag config-consistency-check
```

### Parameters
```text
None
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the MLAG configuration consistency check status:
Switch(config)# show mlag config-consistency-check
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.
