# EEE Configuration Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 9 EEE Configuration Commands

Location: Word document text export, Chapter 9, after Chapter 8 Management Port Configuration Commands and before Chapter 10 SDM Template Commands.

## Chapter Notes

EEE (Energy Efficient Ethernet) is used to save switch power consumption during periods of low data activity. This chapter contains the interface command for EEE behavior and a display command for EEE configuration.

## eee

### Purpose

Enable EEE on a port. Use `no eee` to disable EEE on the port, according to the command description.

### Command Mode

Interface Configuration Mode

### Syntax

```text
eee
no eee
```

### Parameters

Official documentation does not explicitly specify parameters.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Switch(config)#interface gigabitEthernet 1/0/1
Switch(config-if)#eee
```

### Notes

- Privilege requirement: Only Admin, Operator and Power User level users have access to these commands.

## show interface eee

### Purpose

Display the EEE configuration on each port.

### Command Mode

Privileged EXEC Mode and Any Configuration Mode

### Syntax

```text
show interface eee [ fastEthernet port | gigabitEthernet port | two-gigabitEthernet port | ten-gigabitEthernet port ]
```

### Parameters

- `port`: Ethernet port number for the selected interface type.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Switch# show interface eee
```

### Notes

- Privilege requirement: None.
