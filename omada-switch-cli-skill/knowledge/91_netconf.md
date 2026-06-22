# NETCONF Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 91 NETCONF Commands (Only for Certain Devices)

Location: extracted Word text lines 31858-31875

## Chapter Notes

Official documentation states: Note: NETCONF commands are only available on certain devices. The Network Configuration Protocol (NETCONF) defines a simple mechanism for managing network devices by allowing the retrieval of configuration data information and enabling the uploading and manipulation of new configuration data. This protocol permits devices to expose a full-fledged formal Application Programming Interface (API). Applications can utilize this straightforward API to send and receive complete or partial sets of configuration.

- This chapter is marked `Only for Certain Devices`; treat all configuration commands as model-dependent.

## netconf ssh

### Purpose
The netconf ssh command is used to enable the NETCONF SSH connection function. Only when the NETCONF SSH connection function is enabled can'the network administrator configure and manage the switch through NETCONF through port 830. To disable NETCONF SSH connection, please use the no netconf ssh command.

### Command Mode
Global Configuration Mode

### Syntax
```text
netconf ssh
no netconf ssh
```

### Parameters
```text
None
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the NETCONF SSH connection on the switch:
Switch(config)#netconf ssh
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.
