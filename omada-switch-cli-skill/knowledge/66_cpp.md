# CPP Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 35 CPP Commands

Location: extracted Word text lines 15930-16190

## Chapter Notes

Official documentation states: CPP (CPU Protect Policy) is a feature designed to prevent a large volume of service packets or malicious attack packets from overwhelming CPU resources, thereby avoiding a sharp increase in CPU utilization that could degrade device performance and ensuring the normal operation of device functions. This feature employs a three-level rate limiting mechanism at the protocol, queue, and CPU port levels to strictly control the number of packets sent to the CPU within a unit of time, guaranteeing efficient CPU processing of normal service traffic.

- Use these commands only when the requested feature and target interface/VLAN/ring/session details are clear.

## cpp-policy

### Purpose
This command enters the CPP policy configuration view. If the specified policy does not exist, it will be created first. A maximum of 12 policies can be created. Its no command deletes a previously created policy. If the policy being deleted is the currently applied one, the default policy will be automatically applied upon deletion. When creating a new policy, its parameters are initially the same as the default policy.

### Command Mode
Global Configuration Mode

### Syntax
```text
cpp-policy policyName
no cpp-policy policyName
```

### Parameters
```text
policyName
Policy name. Only numbers, letters, and the following symbols are allowed: _@:/.+#. Length is limited to 1
31 characters, and the policy name cannot start with "default".
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Create a policy named "policy_1" and enter its configuration view:
Switch(config)#cpp-policy policy_1
Delete the policy named "policy_1":
Switch(config)#no cpp-policy policy_1
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## rate-limit protocol

### Purpose
This command sets the rate limit value for a specified protocol within the currently configured policy, or prohibits packets of that protocol from being sent to the CPU. Its no command restores the rate limit setting to the default value. If the configured policy is the currently applied one, the new rate limit value takes effect immediately without needing to re-apply the policy.

### Command Mode
CPP Policy Configuration Mode

### Syntax
```text
rate-limit protocol { 8021x | arp | bfd | bgp | bgpv6 | dns | dhcp-client | dhcp-server | dhcpv6-client | dhcpv6-server | dldp | efm | erps | ftp | tftp | gvrp | http | https | isis | lacp | lbd | ldp | lldp | mdns | mld-gmq | mld-gmrpt | mld-gmdone | mld-mlr | mpls-uc | mpls-bc | nd-rs | nd-ra | nd-ns | nd-na | nd-redirect | ospf | ospfv3 | pim | pimv6 | pppoe | ntp | ptp | rpvst | radius | rip | ripng | stp | snmp | ssh | tacplus | telnet | vrrp | vrrpv6 | icmp | icmpv6 | igmp | tcp-other | udp-other | other } { deny | cir cirValue [ cbs cbsValue ] }
no rate-limit protocol { 8021x | arp | bfd | bgp | bgpv6 | dns | dhcp-client | dhcp-server | dhcpv6-client | dhcpv6-server | dldp | efm | erps | ftp | tftp | gvrp | http | https | isis | lacp | lbd | ldp | lldp | mdns | mld-gmq | mld-gmrpt | mld-gmdone | mld-mlr | mpls-uc | mpls-bc | nd-rs | nd-ra | nd-ns | nd-na | nd-redirect | ospf | ospfv3 | pim | pimv6 | pppoe | ntp | ptp | rpvst | radius | rip | ripng | stp | snmp | ssh | tacplus | telnet | vrrp | vrrpv6 | icmp | icmpv6 | igmp | tcp-other | udp-other | other }
```

### Parameters
```text
cirValue
Committed Information Rate (kbit/s), indicating the long-term average data transfer rate committed by the device.
cbsValue
Committed Burst Size (byte), indicating the maximum burst data volume allowed in a short period, used to handle traffic peaks. If not set, the system automatically sets it to 125 times the cirValue.
protocol
Protocol type, used to select the protocol for which the rate limit is to be configured.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Create a policy named "policy_1", enter its view, and set the CIR for ARP packets to 128 kbps within this policy:
Switch(config)# cpp-policy policy_1
Switch(config-cpp-policy)# rate-limit protocol arp cir 128
Restore the rate limit setting for IGMP in this policy to its default value:
Switch(config-cpp-policy)# no rate-limit protocol igmp
Prohibit ICMP packets from being sent to the CPU in this policy:
Switch(config-cpp-policy)# rate-limit protocol icmp deny
Set the CIR for BGP packets to 400 kbps and CBS to 400,000 bytes within this policy:
Switch(config-cpp-policy)# rate-limit protocol bgp cir 400 cbs 400000
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## rate-limit queue-rate (only for certain devices)

### Purpose
This command sets the rate limit value for a specified queue within the currently configured policy. Its no command restores the rate limit setting to the default value. If the configured policy is the currently applied one, the new rate limit value takes effect immediately without needing to re-apply the policy.

### Command Mode
CPP Policy Configuration Mode

### Syntax
```text
rate-limit queue-rate queueId cir cirValue cbs cbsValue
no rate-limit queue-rate queueId
```

### Parameters
```text
queueId
Queue ID. 0
7 correspond to Queue 0 to Queue 7.
cirValue
Committed Information Rate (kbit/s), indicating the long-term average data transfer rate committed by the device.
cbsValue
Committed Burst Size (byte), indicating the maximum burst data volume allowed in a short period, used to handle traffic peaks. If not set, the system automatically sets it to 125 times the cirValue.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Create a policy named "policy_1", enter its view, and set the CIR for Queue 0 to 10,000 kbps and CBS to 100 * 4KB within this policy:
Switch(config)# cpp-policy policy_1
Switch(config-cpp-policy)# rate-limit queue-rate 0 cir 10000 cbs 100
Restore the rate limit setting for Queue 1 in this policy to its default value:
Switch(config-cpp-policy)# no rate-limit queue-rate 1
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## rate-limit cpu-rate (only for certain devices)

### Purpose
This command sets the rate limit value for the CPU port within the currently configured policy. Its no command restores the rate limit setting to the default value. If the configured policy is the currently applied one, the new rate limit value takes effect immediately without needing to re-apply the policy.

### Command Mode
CPP Policy Configuration Mode

### Syntax
```text
rate-limit cpu-rate cir cirValue cbs cbsValue
no rate-limit cpu-rate
```

### Parameters
```text
cirValue
Committed Information Rate (kbit/s), indicating the long-term average data transfer rate committed by the device.
cbsValue
Committed Burst Size (byte), indicating the maximum burst data volume allowed in a short period, used to handle traffic peaks. If not set, the system automatically sets it to 125 times the cirValue.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Create a policy named "policy_1", enter its view, and set the CIR for the CPU port to 10,000 kbps and CBS to 100 * 4KB within this policy:
Switch(config)# cpp-policy policy_1
Switch(config-cpp-policy)# rate-limit cpu-rate cir 10000 cbs 100
Restore the rate limit setting for the CPU port in this policy to its default value:
Switch(config-cpp-policy)# no rate-limit cpu-rate
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## cpp-policy-apply default-policy

### Purpose
This command applies the default policy, making its three-level rate limiting take effect on the switch chip.

### Command Mode
Global Configuration Mode

### Syntax
```text
cpp-policy-apply default-policy
```

### Parameters
```text
None.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Apply the default policy:
Switch(config)# cpp-policy-apply default-policy
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## cpp-policy-apply policy

### Purpose
This command applies a specified policy, making its three-level rate limiting take effect on the switch chip. Its no command deactivates the specified policy and re-applies the default policy.

### Command Mode
Global Configuration Mode

### Syntax
```text
cpp-policy-apply policy policyName
no cpp-policy-apply policy policyName
```

### Parameters
```text
policyName
Policy name. Only numbers, letters, and the following symbols are allowed: _@:/.+#. Length is limited to 1
31 characters, and the policy name cannot start with "default". A user-defined policy must be created using cpp-policy policyName before it can be applied.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Apply the policy named "policy_1":
Switch(config)# cpp-policy-apply policy policy_1
Deactivate the policy named "policy_1" and re-apply the default policy:
Switch(config)# no cpp-policy-apply policy policy_1
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## show cpp all

### Purpose
This command is used to display all CPP policy-related information, including the remaining number of configurable policies, the name of the currently running policy, and the configured parameter values for the three-level rate limiting of existing policies.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show cpp all
```

### Parameters
```text
None.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display all information related to the CPP policy:
Switch# show cpp all
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## show cpp default-policy

### Purpose
This command is used to display information about the CPP default policy, including the policy status (whether it is applied) and the parameter values for its three-level rate limiting.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show cpp default-policy
```

### Parameters
```text
None.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display information about the CPP default policy:
Switch# show cpp default-policy
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## show cpp policy

### Purpose
This command is used to display information about a specified CPP policy, including the policy status (whether it is applied) and the parameter values for its three-level rate limiting.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show cpp policy policyName
```

### Parameters
```text
policyName
Policy name. Only numbers, letters, and the following symbols are allowed: _@:/.+#. Length is limited to 1
31 characters, and the policy name cannot start with "default".
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display information about the CPP policy named "policy_1":
Switch# show cpp policy policy_1
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## show cpp statistics all (only for certain devices)

### Purpose
This command is used to display statistics for packets sent to the CPU for all protocols supported by the CPP rate limiting policy. The statistics include passed packet count, dropped packet count, passed byte count, dropped byte count, real-time rate, and packet loss rate. Statistics are refreshed every 5 seconds. The rate is a real-time value, while the other statistical items are cumulative historical values.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show cpp statistics all
```

### Parameters
```text
None.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display packet statistics for all protocols sent to the CPU supported by CPP rate limiting policies:
Switch# show cpp statistics all
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## show cpp statistics protocol (only for certain devices)

### Purpose
This command is used to display statistics for packets of a specified protocol sent to the CPU. The statistics include passed packet count, dropped packet count, passed byte count, dropped byte count, real-time rate, and packet loss rate. Statistics are refreshed every 5 seconds. The rate is a real-time value, while the other statistical items are cumulative historical values.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show cpp statistics protocol { 8021x | arp | bfd | bgp | bgpv6 | dns | dhcp-client | dhcp-server | dhcpv6-client | dhcpv6-server | dldp | efm | erps | ftp | tftp | gvrp | http | https | isis | lacp | lbd | ldp | lldp | mdns | mld-gmq | mld-gmrpt | mld-gmdone | mld-mlr | mpls-uc | mpls-bc | nd-rs | nd-ra | nd-ns | nd-na | nd-redirect | ospf | ospfv3 | pim | pimv6 | pppoe | ntp | ptp | rpvst | radius | rip | ripng | stp | snmp | ssh | tacplus | telnet | vrrp | vrrpv6 | icmp | icmpv6 | igmp | tcp-other | udp-other | other }
```

### Parameters
```text
protocol
Protocol type, used to select the protocol for which statistics are to be displayed.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display statistics for ARP packets sent to the CPU:
Switch# show cpp statistics protocol arp
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## show cpp statistics cpu-rate

### Purpose
This command is used to display packet statistics received by the CPU over a 5-second interval, including the passed packet count, passed byte count, and real-time rate for each queue and the CPU port.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show cpp statistics cpu-rate
```

### Parameters
```text
None.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display packet statistics received by the CPU over a 5-second interval:
Switch# show cpp statistics cpu-rate
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## clear cpp statistics all (only for certain devices)

### Purpose
This command is used to clear the statistics for packets sent to the CPU for all protocols supported by the CPP rate limiting policy.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
clear cpp statistics all
```

### Parameters
```text
None.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Clear packet statistics for all protocols sent to the CPU supported by CPP rate limiting policies:
Switch# clear cpp statistics all
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## clear cpp statistics protocol (only for certain devices)

### Purpose
This command is used to clear the statistics for packets of a specified protocol sent to the CPU.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
clear cpp statistics protocol { 8021x | arp | bfd | bgp | bgpv6 | dns | dhcp-client | dhcp-server | dhcpv6-client | dhcpv6-server | dldp | efm | erps | ftp | tftp | gvrp | http | https | isis | lacp | lbd | ldp | lldp | mdns | mld-gmq | mld-gmrpt | mld-gmdone | mld-mlr | mpls-uc | mpls-bc | nd-rs | nd-ra | nd-ns | nd-na | nd-redirect | ospf | ospfv3 | pim | pimv6 | pppoe | ntp | ptp | rpvst | radius | rip | ripng | stp | snmp | ssh | tacplus | telnet | vrrp | vrrpv6 | icmp | icmpv6 | igmp | tcp-other | udp-other | other }
```

### Parameters
```text
protocol
Protocol type, used to select the protocol for which statistics are to be cleared.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Clear statistics for ARP packets sent to the CPU:
Switch# clear cpp statistics protocol arp
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## debug cpp-apply protocol

### Purpose
This command is used to debug and quickly modify rate limiting settings for a single specified protocol.

### Command Mode
CPP Policy Configuration Mode

### Syntax
```text
debug cpp-apply protocol { 8021x-bc | 8021x-other | arp | dhcp |dhcpv6 | dldp | erps | tftp | gvrp | http | https | lacp | lbd | lldp | mdns| netbios | mld-gmq | mld-gmrpt | mld-gmdone | mld-mlr | nd-rs | nd-ra | nd-ns | nd-na | nd-rr | pppoe | ntp | pvst | radius | rip | stp | snmp | ssh | tacplus | tcmp | tddp | telnet | icmp | igmp } cir cirValue [ cbs cbsValue ]
```

### Parameters
```text
cirValue
Committed Information Rate (kbit/s), indicating the long-term average data transfer rate committed by the device.
cbsValue
Committed Burst Size (byte), indicating the maximum burst data volume allowed in a short period, used to handle traffic peaks. If not set, the system automatically sets it to 125 times the cirValue.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Debug and configure a CIR of 128 kbps for ARP protocol packets:
Switch# debug cpp-apply protocol arp cir 128
Debug and configure a CIR of 400 kbps and a CBS of 400000 bytes for DHCP protocol packets:
Switch# debug cpp-apply protocol dhcp cir 400 cbs 400000
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
