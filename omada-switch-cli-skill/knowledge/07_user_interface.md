# User Interface

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 3 User Interface

Location: official printed page 28-34; actual PDF page 74-80

## enable

### Purpose
Access Privileged EXEC Mode from User EXEC Mode.

### Command Mode
User EXEC Mode

### Syntax
```text
enable
```

### Parameters
No parameters.

### Default
Not explicitly specified in this command section. Chapter 1 states that, in the default case, no password is needed to enter Privileged EXEC Mode from User EXEC Mode.

### Example
```text
Switch>enable
Enter password:
Switch#
```

### Notes
- Permission requirement: None.

## service password-encryption

### Purpose
Encrypt passwords when passwords are defined or when the configuration is written, using the symmetric encryption algorithm; use `no service password-encryption` to disable the global encryption function.

### Command Mode
Global Configuration Mode

### Syntax
```text
service password-encryption
no service password-encryption
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch(config)# service password-encryption
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- Encryption prevents the password from being readable in the configuration file.

## enable password

### Purpose
Set or change the password for users to access Privileged EXEC Mode from User EXEC Mode; use `no enable password` to remove the password.

### Command Mode
Global Configuration Mode

### Syntax
```text
enable password { [ 0 ] password | 7 encrypted-password }
no enable password
```

### Parameters
- `0`: Specify the encryption type. 0 indicates that an unencrypted password will follow. By default, the encryption type is 0.
- `password`: A string with 31 characters at most, which can contain only English letters (case-sensitive), digits, and 17 kinds of special characters. The special characters are `!$%'()*,-./[]_{|}`. By default, it is empty.
- `7`: Indicates a symmetric encrypted password with fixed length will follow.
- `encrypted-password`: A symmetric encrypted password with fixed length, which you can copy from another switch's configuration file. After the encrypted password is configured, use the corresponding unencrypted password if you re-enter this mode.

### Default
- Encryption type default: `0`.
- `password` default: empty.

### Example
```text
Switch(config)#enable password 0 admin
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- This command uses symmetric encryption.
- If the password configured here is unencrypted and the global encryption function is enabled by `service password-encryption`, the password in the configuration file will be displayed in symmetric encrypted form.
- If both `enable password` and `enable secret` are defined, only the latest configured password takes effect.

## enable secret

### Purpose
Set a secret password using an MD5 encryption algorithm for users to access Privileged EXEC Mode from User EXEC Mode; use `no enable secret` to return to the default configuration.

### Command Mode
Global Configuration Mode

### Syntax
```text
enable secret { [ 0 ] password | 5 encrypted-password | 8 encrypted-password | 9 encrypted-password }
no enable secret
```

### Parameters
- `0`: Specify the encryption type. 0 indicates that an unencrypted password will follow; the password will be encrypted by MD5. By default, the encryption type is 0.
- `password`: A string with 31 characters at most, which can contain only English letters (case-sensitive), digits, and 17 kinds of special characters. The special characters are `!$%'()*,-./[]_{|}`. By default, it is empty.
- `5`: Indicates an MD5 encrypted password with fixed length will follow.
- `8`: Indicates a PBKDF2 encrypted password with fixed length will follow.
- `9`: Indicates a SCRYPT encrypted password with fixed length will follow.
- `encrypted-password`: An MD5, SCRYPT, or PBKDF2 encrypted password with fixed length, which you can copy from another switch's configuration file. After the encrypted password is configured, use the corresponding unencrypted password if you re-enter this mode.

### Default
- Encryption type default: `0`.
- `password` default: empty.

### Example
```text
Switch(config)#enable secret 0 admin
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- If both `enable password` and `enable secret` are defined, only the latest configured password takes effect.

## configure

### Purpose
Access Global Configuration Mode from Privileged EXEC Mode.

### Command Mode
Privileged EXEC Mode

### Syntax
```text
configure
```

### Parameters
No parameters.

### Default
Not applicable.

### Example
```text
Switch# configure
Switch (config)#
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## exit

### Purpose
Return to the previous mode from the current mode.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
exit
```

### Parameters
No parameters.

### Default
Not applicable.

### Example
```text
Switch (config-if)# exit
Switch (config)#exit
Switch#
```

### Notes
- Permission requirement: None.

## end

### Purpose
Return to Privileged EXEC Mode.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
end
```

### Parameters
No parameters.

### Default
Not applicable.

### Example
```text
Switch (config-if)#end
Switch #
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## clipaging

### Purpose
Enable the pause function for screen display; use `no clipaging` to display all related switch information at once when using the `show` command.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
clipaging
no clipaging
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Switch (config)#no clipaging
```

### Notes
- Permission requirement: None.

## history

### Purpose
Show the latest 20 commands entered in the current mode since the switch was powered.

### Command Mode
Privileged EXEC Mode and any Configuration Mode

### Syntax
```text
history
```

### Parameters
No parameters.

### Default
Not applicable.

### Example
```text
Switch (config)# history
1 history
```

### Notes
- Permission requirement: None.

## history clear

### Purpose
Clear the commands entered in the current mode so they will not be shown next time `history` is used.

### Command Mode
Privileged EXEC Mode and any Configuration Mode

### Syntax
```text
history clear
```

### Parameters
No parameters.

### Default
Not applicable.

### Example
```text
Switch (config)#history clear
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
