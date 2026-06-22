# sFlow Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 85 sFlow Commands (Only for Certain Devices)

Location: extracted Word text lines 29977-30100

## Chapter Notes

Official documentation states: Note: sFlow commands are only available on certain devices. sFlow (Sampled Flow) is a technology for accurately monitoring network traffic at high speeds. The sFlow monitoring system consists of a sFlow agent (embedded in a switch or router or in a standalone probe) and a central sFlow collector. The sFlow agent is a virtual entity using sampling technology to capture traffic statistics from the device it is monitoring. The sFlow collector can be a host receiving sFlow datagrams from the sFlow agent. The sFlow feature is implemented as follows: the sFlow sampler take samples of traffic statistics and send sFlow datagrams to the sFlow agent for processing. The sFlow agent will forward sFlow datagrams to the sFlow collector for analysis. The analytic results can be displayed on the sFlow collector.

- This chapter is marked `Only for Certain Devices`; treat all configuration commands as model-dependent.

## sflow address

### Purpose
The sflow address command is used to configure the sFlow agent s IP address. To delete the configured address, please use no sflow address command.

### Command Mode
Global Configuration Mode

### Syntax
```text
sflow address { ipv4-addr }
no sflow address { ipv4-addr }
```

### Parameters
```text
ipv4-addr
The IP address of the sFlow agent. The type of the IP address should be IPv4. For example, you can set the switch
s management IP as the IP address of the sFlow agent.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the sFlow agent with the IP address as 192.168.0.1:
Switch(config)#sflow address 192.168.0.1
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## sflow enable

### Purpose
The sflow enable command is used to enable sFlow function. To disable the sFlow function, please use no sflow enable command.

### Command Mode
Global Configuration Mode

### Syntax
```text
sflow enable
no sflow enable
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable sFlow function globally:
Switch(config)#sflow enable
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- User guidelines: A valid agent address should be assigned to the sFlow agent embedded in the switch before you enable the sFlow function.
- Availability: Only for certain devices according to the official chapter title.

## sflow collector collector-ID

### Purpose
The sflow collector collector-ID command is used to configure the parameters about the sFlow collector.

### Command Mode
Global Configuration Mode

### Syntax
```text
sflow collector collector-ID value { [descript descript ] | [ ip ip ] | [ port port ] | [ maxData maxData ] | [ timeout timeout ] }
```

### Parameters
```text
value
The ID of the sFlow collector you desire to configure. The value ranges from 1 to 4.
descript
Give a Description to the sFlow collector, which contains 16 characters at most.
The IP address of the sFlow collector. The type of the IP address should be IPv4, for example 192.168.0.100.
port
The number of the udp port which is selected for the sFlow collector.
maxData
Specify the maximum number of data bytes that can be sent in a single sample datagram. The value ranges from 300 to 1400 and the default value is 300 bytes.
timeout
Specify the aging time of the sFlow collector, ranging from 0 to 2000000 seconds. When the timeout is set to 0, it means the life cycle of the collector is infinite.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Specify the ip of the sFlow collector 1 as 192.168.0.100, the port as 3000:
Switch(config)# sflow collector collector-ID 1 ip 192.168.0.100
Switch(config)# sflow collector collector-ID 1 port 3000
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## sflow sampler

### Purpose
The sflow sampler command is used to configure the parameters about the sFlow sampler.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet)

### Syntax
```text
sflow sampler { [ collector-ID value ] | [ ingRate ingress-rate ] [ egRate egress-rate ] | [ maxHeader maxHeader ] }
```

### Parameters
```text
value
The ID of the sFlow collector which the sFlow sampler will send sFlow datagrams to. The value ranges from 0 to 4. When the value is zero, it means no collector is selected.
ingress-rate
Specify the ingress sampling frequency of the sFlow sampler. When a sample is taken, the value indicates how many packets to skip before the next sample is taken. The value ranges from 1024 to 65535 and the default value is 0 which means no packets will be sampled.
egress-rate
Specify the egress sampling frequency of the sFlow sampler. When a sample is taken, the value indicates how many packets to skip before the next sample is taken. The value ranges from 1024 to 65535 and the default value is 0 which means no packets will be sampled.
maxHeader
Specify the maximum number of bytes that should be copied from a sampled packet. The value ranges from 18 to 256 and the default value is 128 bytes.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure Gigabit Ethernet port 1 as the sFlow sampler: specify the Collector-ID as 1, the ingress rate as 1024:
Switch(config)#interface gigabitEthernet 1/0/1
Switch(config-if)#sflow sampler collector-ID 1
For L2/L2+ switches:
Switch(config-if)#sflow sampler ingRate 1024
For L3 switches:
Switch(config)#sflow sampler ingRate 1024
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## show sflow global

### Purpose
The show sflow global command is used to display the global configuration of sFlow.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show sflow global
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the global configuration of sFlow:
Switch#show sflow global
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## show sflow collector

### Purpose
The show sflow collector command is used to display the global configuration of the sFlow collector.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show sflow collector
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the global configuration of the sFlow collector:
Switch#show sflow collector
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.

## show sflow sampler

### Purpose
The show sflow sampler command is used to display the global configuration of the sFlow sampler.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show sflow sampler
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the global configuration of the sFlow sampler:
Switch#show sflow sampler
```

### Notes
- Permission requirement: None.
- Availability: Only for certain devices according to the official chapter title.
