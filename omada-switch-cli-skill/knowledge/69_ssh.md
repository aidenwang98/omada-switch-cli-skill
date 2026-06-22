# SSH Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 68 SSH Commands

Location: extracted Word text lines 26879-27019

## Chapter Notes

Official documentation states: SSH (Security Shell) can provide the unsecured remote management with security and powerful authentication to ensure the security of the management information.

- Use these commands only when the requested feature and target interface/VLAN/ring/session details are clear.

## ip ssh server

### Purpose
The ip ssh server command is used to enable SSH function. To disable the SSH function, please use no ip ssh server command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip ssh server
no ip ssh server
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the SSH function:
Switch(config)# ip ssh server
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip ssh port

### Purpose
The ip ssh port command is used to configure the port for SSH service. To set the value to the default, please use no ip ssh port command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip ssh port port
no ip ssh port
```

### Parameters
```text
port
Set the port number. It ranges from 1 to 65535. The default value is 22.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the SSH port number as 22:
Switch(config)# ip ssh port 22
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip ssh algorithm

### Purpose
The ip ssh algorithm command is used to configure the algorithm in SSH function. To disable the specified algorithm, please use no ip ssh algorithm command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip ssh algorithm { AES-CBC | 3DES-CBC | AES-GCM | AES-CTR | HMAC-SHA1 | HMAC-SHA2 | HMAC-MD5 | UMAC }
no ip ssh algorithm
```

### Parameters
```text
AES-CBC | 3DES-CBC | AES-GCM | AES-CTR | HMAC-SHA1 | HMAC-SHA2 | HMAC-MD5 | UMAC
Specify the SSH algorithm.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Specify the SSH algorithm as AES-CBC:
Switch(config)# ip ssh algorithm AES-CBC
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip ssh algorithm compatibility

### Purpose
The ip ssh algorithm compatibility command is used to configure enable compatibility configuration to allow SSH to use unsafe encryption algorithms.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
ip ssh algorithm compatibility
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable compatibility configuration to allow SSH to use unsafe encryption algorithms:
Switch#ip ssh algorithm compatibility
This command will synchronously enable unsafe algorithms such as AES-CBC, 3DES-CBC, HMAC-SHA1, HMAC-MD5, etc. (yes/no)
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip ssh timeout

### Purpose
The ip ssh timeout command is used to specify the idle-timeout time of SSH. To restore to the factory defaults, please use ip ssh timeout command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip ssh timeout value
no ip ssh timeout
```

### Parameters
```text
value
The Idle-timeout time. During this period, the system will automatically release the connection if there is no operation from the client. It ranges from 1 to 120 in seconds. By default, this value is 120 seconds.
```

### Default
By default, this value is 120 seconds.

### Example
```text
Specify the idle-timeout time of SSH as 30 seconds:
Switch(config)# ip ssh timeout 30
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip ssh max-client

### Purpose
The ip ssh max-client command is used to specify the maximum number of the connections to the SSH server. To return to the default configuration, please use no ip ssh max-client command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip ssh max-client num
no ip ssh max-client
```

### Parameters
```text
num
The maximum number of the connections to the SSH server. It ranges from 1 to 5. By default, this value is 5.
```

### Default
By default, this value is 5.

### Example
```text
Specify the maximum number of the connections to the SSH server as 3:
Switch(config)# ip ssh max-client 3
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip ssh download

### Purpose
The ip ssh download command is used to download the SSH key file from TFTP server.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip ssh download { v2 } key-file ip-address ip-addr [vrf vrf-name]
```

### Parameters
```text
Select the type of SSH public key as SSH-2.
key-file
The name of the key-file which is selected to download. The length of the name ranges from 1 to 25 characters. The key length of the downloaded file must be in the range of 512 to 3072 bits.
ip-addr
The IP address of the TFTP server. Both IPv4 and IPv6 addresses are supported, for example 192.168.0.1 or fe80::1234.
vrf-name
VRF instance name (1-15 characters).
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Download an SSH-2 type key file named ssh-key from TFTP server with the IP address 192.168.0.148:
Switch(config)# ip ssh download v2 ssh-key ip-address 192.168.0.148
Download an SSH-2 type key file named ssh-key from TFTP server with the IP address fe80::1234:
Switch(config)# ip ssh download v2 ssh-key ip-address fe80::1234
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## remove public-key

### Purpose
The remove public-key command is used to remove the SSH public key from the switch.

### Command Mode
Privileged EXEC Mode

### Syntax
```text
remove public-key { v2 }
```

### Parameters
```text
Select the type of SSH public key as SSH-2.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Remove the SSH-2 type public key from the switch:
Switch# remove public-key v2
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## show ip ssh

### Purpose
The show ip ssh command is used to display the global configuration of SSH.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip ssh
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the global configuration of SSH:
Switch(config)# show ip ssh
```

### Notes
- Permission requirement: None.
