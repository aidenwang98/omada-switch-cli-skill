# DDM Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 16 DDM Commands (Only for Certain Devices)

Location: extracted Word text lines 10460-10668

## Chapter Notes

Official documentation states: Note: DDM commands are only available on certain devices. The DDM (Digital Diagnostic Monitoring) function allows the user to monitor the status of the SFP modules inserted into the SFP ports on the switch. The user can choose to shut down the monitoring SFP port automatically when specified parameter exceeds the alarm threshold or warning threshold. The monitoring parameters include: Temperature, Voltage, Bias Current, Tx Power and Rx Power.

- This chapter is marked `Only for Certain Devices`; treat all configuration commands as model-dependent.

## ddm state enable

### Purpose
The ddm state enable command is used to enable the DDM function on the specified SFP port. Use the no ddm state enable command to disable the DDM function on this port.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet)

### Syntax
```text
ddm state enable
no ddm state enable
```

### Parameters
No parameters.

### Default
Enabled on all the SFP ports.

### Example
```text
Enable DDM function on port 1/0/25:
Switch(config)#interface gigabitEthernet 1/0/25
Switch(config-if)#ddm state enable
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## ddm shutdown

### Purpose
The ddm shutdown command is used to configure whether to shut down the port when an exceeding alarm threshold or warning threshold event is encountered.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet )

### Syntax
```text
ddm shutdown { none | warning | alarm }
```

### Parameters
```text
none
The port will never be shut down regardless of the exceeding alarm threshold and warning threshold events.
warning
Shut down the port when an exceeding warning threshold event is encountered.
alarm
Shut down the port when an exceeding alarm threshold event is encountered.
```

### Default
none, which means the port will never be shut down regardless of the exceeding alarm threshold and warning threshold events.

### Example
```text
Shut down the port 1/0/25 when an exceeding warning threshold event is encountered:
Switch(config)#interface gigabitEthernet 1/0/25
Switch(config-if)#ddm shutdown warning
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## ddm temperature_threshold

### Purpose
The ddm temperature_threshold command is used to configure the threshold of the DDM temperature value.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet )

### Syntax
```text
ddm temperature_threshold { high_alarm | high_warning | low_alarm | low_warning } value
```

### Parameters
```text
high_alarm
Specify the highest threshold for the alarm. When the operating parameter rises above the value hereinafter, action associated with the alarm will be taken.
high_warning
Specify the highest threshold for the warning. When the operating parameter rises above the value hereinafter, action associated with the warning will be taken.
low_alarm
Specify the lowest threshold for the alarm. When the operating parameter falls below the value hereinafter, action associated with the alarm will be taken.
low_warning
Specify the lowest threshold for the warning. When the operating parameter falls below the value hereinafter, action associated with the warning will be taken.
value
Enter the threshold value in Celsius.
```

### Default
None.

### Example
```text
Configure the high_alarm threshold of DDM temperature on the port 1/0/25 as 5:
Switch(config)#interface gigabitEthernet 1/0/25
Switch(config-if)#ddm temperature_threshold high_alarm 5
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## ddm voltage_threshold

### Purpose
The ddm voltage_threshold command is used to configure the threshold of the DDM voltage value.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet )

### Syntax
```text
ddm voltage_threshold { high_alarm | high_warning | low_alarm | low_warning } value
```

### Parameters
```text
high_alarm
Specify the highest threshold for the alarm. When the operating parameter rises above the value hereinafter, action associated with the alarm will be taken.
high_warning
Specify the highest threshold for the warning. When the operating parameter rises above the value hereinafter, action associated with the warning will be taken.
low_alarm
Specify the lowest threshold for the alarm. When the operating parameter falls below the value hereinafter, action associated with the alarm will be taken.
low_warning
Specify the lowest threshold for the warning. When the operating parameter falls below the value hereinafter, action associated with the warning will be taken.
value
Enter the threshold value in Volt.
```

### Default
None.

### Example
```text
Configure the high_alarm threshold of DDM voltage on the port 1/0/25 as 5:
Switch(config)#interface gigabitEthernet 1/0/25
Switch(config-if)#ddm voltage_threshold high_alarm 5
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## ddm bias_current_threshold

### Purpose
The ddm bias_current_threshold command is used to configure the threshold of the DDM Bias Current value.

### Command Mode
Interface Configuration Mode (interface fastEthernet / interface range fastEthernet / interface gigabitEthernet / interface range gigabitEthernet)

### Syntax
```text
ddm bias_current_threshold { high_alarm | high_warning | low_alarm | low_warning } value
```

### Parameters
```text
high_alarm
Specify the highest threshold for the alarm. When the operating parameter rises above the value hereinafter, action associated with the alarm will be taken.
high_warning
Specify the highest threshold for the warning. When the operating parameter rises above the value hereinafter, action associated with the warning will be taken.
low_alarm
Specify the lowest threshold for the alarm. When the operating parameter falls below the value hereinafter, action associated with the alarm will be taken.
low_warning
Specify the lowest threshold for the warning. When the operating parameter falls below the value hereinafter, action associated with the warning will be taken.
value
Enter the threshold value in mA.
```

### Default
None.

### Example
```text
Configure the high_alarm threshold of DDM Bias Current on the port 1/0/25 as 5:
Switch(config)#interface gigabitEthernet 1/0/25
Switch(config-if)#ddm bias_current_threshold high_alarm 5
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## ddm tx_power_threshold

### Purpose
The ddm tx_power_threshold command is used to configure the threshold of the DDM Tx Power value.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet )

### Syntax
```text
ddm tx_power_threshold { high_alarm | high_warning | low_alarm | low_warning } value
```

### Parameters
```text
high_alarm
Specify the highest threshold for the alarm. When the operating parameter rises above the value hereinafter, action associated with the alarm will be taken.
high_warning
Specify the highest threshold for the warning. When the operating parameter rises above the value hereinafter, action associated with the warning will be taken.
low_alarm
Specify the lowest threshold for the alarm. When the operating parameter falls below the value hereinafter, action associated with the alarm will be taken.
low_warning
Specify the lowest threshold for the warning. When the operating parameter falls below the value hereinafter, action associated with the warning will be taken.
value
Enter the threshold value in mW.
```

### Default
None.

### Example
```text
Configure the high_alarm threshold of DDM Tx Power on the port 1/0/25 as 5:
Switch(config)#interface gigabitEthernet 1/0/25
Switch(config-if)#ddm tx_power_threshold high_alarm 5
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## ddm rx_power_threshold

### Purpose
The ddm rx_power_threshold command is used to configure the threshold of the DDM Rx Power value.

### Command Mode
Interface Configuration Mode (interface gigabitEthernet / interface range gigabitEthernet )

### Syntax
```text
ddm rx_power_threshold { high_alarm | high_warning | low_alarm | low_warning } value
```

### Parameters
```text
high_alarm
Specify the highest threshold for the alarm. When the operating parameter rises above the value hereinafter, action associated with the alarm will be taken.
high_warning
Specify the highest threshold for the warning. When the operating parameter rises above the value hereinafter, action associated with the warning will be taken.
low_alarm
Specify the lowest threshold for the alarm. When the operating parameter falls below the value hereinafter, action associated with the alarm will be taken.
low_warning
Specify the lowest threshold for the warning. When the operating parameter falls below the value hereinafter, action associated with the warning will be taken.
value
Enter the threshold value in mW.
```

### Default
None.

### Example
```text
Configure the high_alarm threshold of DDM Rx Power on the port 1/0/25 as 5:
Switch(config)#interface gigabitEthernet 1/0/25
Switch(config-if)#ddm rx_power_threshold high_alarm 5
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## show ddm configuration

### Purpose
The show ddm configuration command is used to display the DDM configuration.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ddm configuration { state | temperature | voltage | bias_current | tx_power | rx_power | tx_rx_power }
```

### Parameters
```text
state
Display the DDM configuration state.
temperature
Displays the threshold of the DDM temperature value.
voltage
Displays the threshold of the DDM Voltage value.
bias_current
Displays the threshold of the DDM Bias Current value.
tx_power
Displays the threshold of the DDM Tx Power value.
rx_power
Displays the threshold of the DDM Rx Power value.
tx_rx_power
Displays the threshold of the DDM Tx and Rx Power value.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the DDM configuration state:
Switch(config)#show ddm configuration state
View the threshold of the DDM Voltage value:
Switch(config)#show ddm configuration voltage
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## show ddm status

### Purpose
The show ddm status command is used to display the DDM status, which is the digital diagnostic monitoring status of SFP modules inserting into the switch s SFP ports.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ddm status
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
View the DDM status:
Switch(config)#show ddm status
```

### Notes
- Availability: Only for certain devices according to the official chapter title.

## show fiber-ports

### Purpose
The show fiber-ports command is used to display the information of all fiber ports.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show fiber-ports
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the information of all fiber ports:
Switch(config)# show fiber-ports
```

### Notes
- Permission requirement: None.
- Official note: This command is only available on certain devices.
- Availability: Only for certain devices according to the official chapter title.
