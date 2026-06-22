# LLDP Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 39 LLDP Commands

Location: extracted Word text lines 17629-17913

## Chapter Notes

Official documentation states: LLDP function enables network devices to advertise their own device information periodically to neighbors on the same LAN. The information of the LLDP devices in the LAN can be stored by its neighbor in a standard MIB, so it is possible for the information to be accessed by a Network Management System (NMS) using SNMP.

- Use these commands only when the requested feature and target interface/VLAN/ring/session details are clear.

## lldp

### Purpose
The lldp command is used to enable LLDP function. To disable the LLDP function, please use no lldp command.

### Command Mode
Global Configuration Mode

### Syntax
```text
lldp
no lldp
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable LLDP function globally:
Switch(config)#lldp
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## lldp forward_message

### Purpose
The lldp forward_message command is used to enable the switch to forward LLDP messages when LLDP function is disabled. To disable the LLDP messages forwarding function, please use no lldp forward_message command.

### Command Mode
Global Configuration Mode

### Syntax
```text
lldp forward_message
no lldp forward_message
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the switch to forward LLDP messages when LLDP function is disabled globally:
Switch(config)#lldp forward_message
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## lldp hold-multiplier

### Purpose
The lldp hold-multiplier command is used to configure the Hold Multiplier parameter. The aging time of the local information in the neighbor device is determined by the actual TTL value used in the sending LLDPDU. TTL = Hold Multiplier * Transmit Interval. To return to the default configuration, please use no lldp hold-multiplier command.

### Command Mode
Global Configuration Mode

### Syntax
```text
lldp hold-multiplier multiplier
no lldp hold-multiplier
```

### Parameters
```text
multiplier
Configure the Hold Multiplier parameter. It ranges from 2 to 10. By default, it is 4.
```

### Default
By default, it is 4.

### Example
```text
Specify Hold Multiplier as 5:
Switch(config)#lldp hold-multiplier 5
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## lldp timer

### Purpose
The lldp timer command is used to configure the parameters about transmission. To return to the default configuration, please use no lldp timer command.

### Command Mode
Global Configuration Mode

### Syntax
```text
lldp timer { tx-interval tx-interval | tx-delay tx-delay | reinit-delay reinit-delay | notify-interval notify-interval | fast-count fast-count }
no lldp timer { tx-interval | tx-delay | reinit-delay | notify-interval | fast-count }
```

### Parameters
```text
tx-interval
Configure the interval for the local device to transmit LLDPDU to its neighbors. The value ranges from 5 to 32768 and the default value is 30 seconds.
tx-delay
Configure a value from 1 to 8192 in seconds to specify the time for the local device to transmit LLDPDU to its neighbors after changes occur so as to prevent LLDPDU being sent frequently. By default, it is 2 seconds.
reinit-delay
This parameter indicates the amount of delay from when LLDP status becomes "disable" until re-initialization will be attempted. The value ranges from 1 to 10 and the default value is 2.
notify-interval
Specify the interval of Trap message which will be sent from local device to network management system. The value ranges from 5 to 3600 and the default value is 5 seconds.
fast-count
When the port's LLDP state transforms from Disable (or Rx_Only) to Tx&Rx (or Tx_Only), the fast start mechanism will be enabled, that is, the transmit interval will be shorten to a second, and several LLDPDUs will be sent out (the number of LLDPDUs equals this parameter). The value ranges from 1 to 10 and the default value is 3.
```

### Default
By default, it is 2 seconds.

### Example
```text
Specify the Transmit Interval of LLDPDU as 45 seconds and Trap message to NMS as 120 seconds:
Switch(config)#lldp timer tx-interval 45
Switch(config)#lldp timer notify-interval 120
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## lldp receive

### Purpose
The lldp receive command is used to enable the designated port to receive LLDPDU. To disable the function, please use no lldp receive command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet)

### Syntax
```text
lldp receive
no lldp receive
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable port 1/0/1 to receive LLDPDU:
Switch(config)#interface gigabitEthernet 1/0/1
Switch(config-if)#lldp receive
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## lldp transmit

### Purpose
The lldp transmit command is used to enable the designated port to transmit LLDPDU. To disable the function, please use no lldp transmit command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet)

### Syntax
```text
lldp transmit
no lldp transmit
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable Gigabit Ethernet port 1/0/1 to transmit LLDPDU:
Switch(config)# interface gigabitEthernet 1/0/1
Switch(config-if)#lldp transmit
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## lldp snmp-trap

### Purpose
The lldp snmp-trap command is used to enable the port s SNMP notification. If enabled, the port will notify the trap event to network management system. To disable the ports' SNMP notification, please use no lldp snmp-trap command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet)

### Syntax
```text
lldp snmp-trap
no lldp snmp-trap
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the SNMP notification for Gigabit Ethernet port 1/0/1:
Switch(config)#interface gigabitEthernet 1/0/1
Switch(config-if)#lldp snmp-trap
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## lldp tlv-select

### Purpose
The lldp tlv-select command is used to configure TLVs to be included in outgoing LLDPDU. To exclude TLVs, please use no lldp tlv-select command. By default, All TLVs are included in outgoing LLDPDU.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet)

### Syntax
```text
lldp tlv-select { [ port-description ] [ system-capability ] [ system-description ] [ system-name ] [ management-address ] [ port-vlan ] [ protocol-vlan ] [ vlan-name ] [ link-aggregation ] [ mac-phy-cfg ] [ max-frame-size ] [ power ] [ all ] }
no lldp tlv-select { [ port-description ] [ system-capability ] [ system-description ] [ system-name ] [ management-address ] [ port-vlan ] [ protocol-vlan ] [ vlan-name ] [ link-aggregation ] [ mac-phy-cfg ] [ max-frame-size ] [ power ] [ all ] }
```

### Parameters
No parameters.

### Default
By default, All TLVs are included in outgoing LLDPDU.

### Example
```text
Exclude
management-address
and
port-vlan-id
TLVs in LLDPDU outgoing from Gigabit Ethernet port 1/0/1:
Switch(config)# interface gigabitEthernet 1/0/1
Switch(config-if)# no lldp tlv-select management-address port-vlan
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## lldp management-address

### Purpose
The lldp management-address command is used to configure the port s management address to be included in management address TLV. The NMS uses management addresses to identify the devices. To delete the port s management address, please use no lldp management address command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet)

### Syntax
```text
lldp management-address { ip-address }
no lldp management-address
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the port
s management address as 192.168.1.100 for port 1/0/1:
Switch(config)# interface gigabitEthernet 1/0/1
Switch(config-if)# lldp management-address 192.168.0.100
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## lldp med-fast-count

### Purpose
The lldp med-fast-count command is used to configure the number of the LLDP-MED frames that will be sent out. When LLDP-MED fast start mechanism is activated, multiple LLDP-MED frames will be transmitted based on this parameter. The default value is 4. To return to the default configuration, please use no lldp med-fast-count command.

### Command Mode
Global Configuration Mode

### Syntax
```text
lldp med-fast-count count
no lldp med-fast-count
```

### Parameters
```text
count
Configure the Fast Start Count parameter. It ranges from 1 to 10. By default, it is 4.
```

### Default
By default, it is 4.

### Example
```text
Specify Fast Start Count as 5:
Switch(config)# lldp med-fast-count 5
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## lldp med-status

### Purpose
The lldp med-status command is used to enable the LLDP-MED feature for the corresponding port. After the LLDP-MED feature is enabled, the port's Admin Status will be changed to Tx&Rx. To disable the LLDP-MED feature for the corresponding port, please use no lldp med-status command.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet)

### Syntax
```text
lldp med-status
no lldp med-status
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the LLDP-MED feature for port 1/0/2:
Switch(config)# interface gigabitEthernet 1/0/2
Switch(config-if)# lldp med-status
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## lldp med-tlv-select

### Purpose
The lldp med-tlv-select command is used to configure LLDP-MED TLVs to be included in outgoing LLDPDU for the corresponding port. To exclude LLDP-MED TLVs, please use no lldp med-tlv-select command. By default, All TLVs are included in outgoing LLDPDU.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet)

### Syntax
```text
lldp med-tlv-select { [inventory-management] [location] [network-policy] [power-management] [all] }
no lldp med-tlv-select { [inventory-management] [location] [network-policy] [power-management] [all] }
```

### Parameters
No parameters.

### Default
By default, All TLVs are included in outgoing LLDPDU.

### Example
```text
Exclude
network policy
and
inventory
TLVs in LLDPDU outgoing from port 1/0/2:
Switch(config)# interface gigabitEthernet 1/0/2
Switch(config-if)# no lldp med-tlv-select network-policy inventory- management
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## lldp med-location

### Purpose
The lldp med-location command is used to configure the Location Identification TLV's content in outgoing LLDPDU of the port.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet)

### Syntax
```text
lldp med-location { emergency-number identifier | civic-address [ [ language language ] [ province-state province-state ] [ lci-county-name county-name ] [ lci-city city ] [ street street ] [ house-number house-number ] [name name ] [ postal-zipcode postal-zipcode ] [ room-number room-number ] [ post-office-box post-office-box ] [ additional additional ] [ country-code country-code ] [ what { dhcp-server | endpoint | switch } ] ] }
```

### Parameters
```text
emergency-number
Emergency Call Service ELIN identifier, which is used during emergency call setup to a traditional CAMA or ISDN trunk-based PSAP. The length of this field ranges from 10 to 25 characters.
civic-address
The civic address is defined to reuse the relevant sub-fields of the DHCP option for civic Address based Location Configuration Information as specified by IETF.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the civic address in the Location Identification TLV's content in outgoing LLDPDU of port 1/0/2. Configure the language as English and city as London:
Switch(config)# interface gigabitEthernet 1/0/2
Switch(config-if)# lldp med-location civic-address language English lci-city London
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## show lldp

### Purpose
The show lldp command is used to display the global configuration of LLDP.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show lldp
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the global configuration of LLDP:
Switch#show lldp
```

### Notes
- Permission requirement: None.

## show lldp interface

### Purpose
The show lldp interface command is used to display LLDP configuration of the corresponding port. By default, the LLDP configuration of all the ports will be displayed.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show lldp interface [ gigabitEthernet port ]
```

### Parameters
```text
port
The Ethernet port number.
```

### Default
By default, the LLDP configuration of all the ports will be displayed.

### Example
```text
Display the LLDP configuration of Gigabit Ethernet port 1/0/1:
Switch#show lldp interface gigabitEthernet 1/0/1
```

### Notes
- Permission requirement: None.

## show lldp local-information interface

### Purpose
The show lldp local-information interface command is used to display the LLDP information of the corresponding port. By default, the LLDP information of all the ports will be displayed.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show lldp local-information interface [ gigabitEthernet port ]
```

### Parameters
```text
port
The Ethernet port number.
```

### Default
By default, the LLDP information of all the ports will be displayed.

### Example
```text
Display the LLDP information of 1/0/1:
Switch#show lldp local-information interface gigabitEthernet 1/0/1
```

### Notes
- Permission requirement: None.

## show lldp neighbor-information interface

### Purpose
The show lldp neighbor-information interface command is used to display the neighbor information of the corresponding port. By default, the neighbor information of all the ports will be displayed.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show lldp neighbor-information interface [ gigabitEthernet port ]
```

### Parameters
```text
port
The Ethernet port number.
```

### Default
By default, the neighbor information of all the ports will be displayed.

### Example
```text
Display the neighbor information of Gigabit Ethernet port 1/0/1:
Switch#show lldp neighbor-information interface gigabitEthernet 1/0/1
```

### Notes
- Permission requirement: None.

## show lldp traffic interface

### Purpose
The show lldp traffic interface command is used to display the LLDP statistic information between the local device and neighbor device of the corresponding port. By default, the LLDP statistic information of all the ports will be displayed.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show lldp traffic interface [ gigabitEthernet port ]
```

### Parameters
```text
port
The Ethernet port number.
```

### Default
By default, the LLDP statistic information of all the ports will be displayed.

### Example
```text
Display the LLDP statistic information of Gigabit Ethernet port 1/0/1:
Switch#show lldp traffic interface gigabitEthernet 1/0/1
```

### Notes
- Permission requirement: None.
