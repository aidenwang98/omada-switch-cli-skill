# User Management Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 4 User Management Commands

Location: Word document text export, Chapter 4, after Chapter 3 User Interface and before Chapter 5 System Configuration Commands.

## Chapter Notes

User Management Commands manage user login information for Web, Telnet, or SSH access. Use these commands only for user account, password, password-complexity, and user/client display workflows. Password-recovery and password-complexity subcommands marked by the official document as only available on certain devices should be treated as model-dependent.

## user name (password)

### Purpose

The user name command is used to add a new user or modify the existed users information. To delete the existed users, please use no user name command. This command uses the symmetric encryption.

### Command Mode

Global Configuration Mode

### Syntax

```text
user name name [ privilege admin | operator | power_user | user ] password { [ 0 ] password | 7 encrypted-password }
no user name name
```

### Parameters

- name
- Type a name for users' login. It contains 16 characters at most, composed of digits, English letters and symbols. No spaces, question marks and double quotation marks are allowed.
- admin | operator | power_user | user
- Access level.
- admin
- means that you can edit, modify and view all the settings of different functions.
- operator
- means that you can edit, modify and view most of the settings of different functions.
- power-user
- means that you can edit, modify and view some of the settings of different functions.
- user
- means that you can only view some of the settings of different functions without the right to edit or modify. It is
- admin
- by default. For more details about privilege restrictions, please refer to the Privilege Requirement part in each command.
- Specify the encryption type. 0 indicates that an unencrypted password will follow. By default, the encryption type is 0.
- password
- Users
- login password, a string with 6
- 31 alphanumeric characters (case-sensitive) and symbols. No spaces are allowed.
- Indicates a symmetric encrypted password with fixed length will follow.
- encrypted-password
- A symmetric encrypted password with fixed length, which you can copy from another switch
- s configuration file. After the encrypted password is configured, you should use the corresponding unencrypted password if you re-enter this mode.

### Default

- It is admin by default.
- By default, the encryption type is 0.

### Example

```text
Add and enable a new admin user named
tplink
, of which the password is
admin
and unencrypted:
Switch(config)#user name tplink privilege admin password 0 admin
```

### Notes
- Privilege requirement: Only Admin level users have access to these commands.
- If the password you configured here is unencrypted and the global encryption function is enabled in
- service password-encryption
- , the password in the configuration file will be displayed in the symmetric encrypted form.
- If both the user name (password) and user name (secret) are defined, only the latest configured password will take effect.

## user name (algorithm-type)

### Purpose

The user name command is used to add a new user or modify the existed users information. To delete the existed users, please use no user name command. This command uses the symmetric encryption.

### Command Mode

Global Configuration Mode

### Syntax

```text
user name name [ privilege admin | operator | power_user | user ] algorithm-type { md5 | sha256 | scrypt } secret password
no user name name
```

### Parameters

- name
- Type a name for users' login. It contains 16 characters at most, composed of digits, English letters and symbols. No spaces, question marks and double quotation marks are allowed.
- admin | operator | power_user | user
- Access level.
- admin
- means that you can edit, modify and view all the settings of different functions.
- operator
- means that you can edit, modify and view most of the settings of different functions.
- power-user
- means that you can edit, modify and view some of the settings of different functions.
- user
- means that you can only view some of the settings of different functions without the right to edit or modify. It is
- admin
- by default.
- md5 | scrypt | sha256
- algorithm-type. Specifies the algorithm to use for hashing the plaintext secret for the user. md5: Encodes the password using the MD5 algorithm; sha256: Encodes the password using the PBKDF2 hashing algorithm; scrypt: Encodes the password using the SCRYPT hashing algorithm.

### Default

- It is admin by default.

### Example

```text
Create an admin user named tplink and set the password to dsaoM#3210, which is encrypted in SCRYPT mode:
Switch (config)# user name tplink privilege admin algorithm-type scrypt secret dsaoM#3210
```

### Notes
- Privilege requirement: Only Admin level users have access to these commands.
- If the password you configured here is unencrypted and the global encryption function is enabled in
- service password-encryption
- , the password in the configuration file will be displayed in the symmetric encrypted form.
- If both the user name (password) and user name (secret) are defined, only the latest configured password will take effect.

## user name (secret)

### Purpose

The user name command is used to add a new user or modify the existed users information. To delete the existed users, please use no user name command. This command uses the MD5 encryption.

### Command Mode

Global Configuration Mode

### Syntax

```text
user name name [ privilege admin | operator | power_user | user ] secret { [ 0 ] password | 5 encrypted-password | 8 encrypted-password | 9 encrypted-password }
no user name name
```

### Parameters

- name
- Type a name for users' login. It contains 16 characters at most, composed of digits, English letters and symbols. No spaces, question marks and double quotation marks are allowed.
- admin | operator | power_user | user
- Access level.
- admin
- means that you can edit, modify and view all the settings of different functions.
- operator
- means that you can edit, modify and view most of the settings of different functions.
- power-user
- means that you can edit, modify and view some of the settings of different functions.
- user
- means that you can only view some of the settings of different functions without the right to edit or modify. It is
- admin
- by default.
- Specify the encryption type. 0 indicates that an unencrypted password will follow. By default, the encryption type is 0.
- password
- Users
- login password, a string with 6
- 31 alphanumeric characters (case-sensitive) and symbols. No spaces are allowed.
- Indicates an MD5 encrypted password with fixed length will follow.
- encrypted-password
- An MD5 encrypted password with fixed length, which you can copy from another switch
- s configuration file.
- Indicates an PBKDF2 encrypted password with fixed length will follow.
- Indicates a SCRYPT encrypted password with fixed length will follow.
- encrypted-password
- An/A MD5/SCRYPT/PBKDF2 encrypted password with fixed length, which you can copy from another switch
- s configuration file.

### Default

- It is admin by default.
- By default, the encryption type is 0.

### Example

```text
Add and enable a new admin user named
tplink
, of which the password is
admin
. The password will be displayed in the encrypted form.
Switch (config)#user name tplink privilege admin secret 0 admin
```

### Notes
- Privilege requirement: Only Admin level users have access to these commands.
- If both the user name (password) and user name (secret) are defined, only the latest configured password will take effect.

## service password-recovery

### Purpose

The service password-recovery command is used to enable the password-recovery feature. To disable the password-recovery feature, please use no service password-recovery command. With password-recovery enabled, you can connect to the switch s console port and delete all your previous set accounts. You need to set a new password before logging into the switch after its startup.

### Command Mode

Global Configuration Mode

### Syntax

```text
service password-recovery
no service password-recovery
```

### Parameters

Official documentation does not explicitly specify parameters.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Enable the switch
s password-recovery feature:
Switch(config)# service password-recovery
```

### Notes
- Privilege requirement: Only Admin level users have access to these commands.

## service passwd-complexity

### Purpose

The service passwd-complexity command is used to enable the global switch of password complexity, which is enabled by default. If the switch is disabled, when the user sets the password, only the password length entered by the user is checked to see if it is between 6 and 64 characters. Other complexity parameters are invalid, and the function of limiting the number of login attempts is disabled. If the switch is enabled, when the user sets the password, the password will be checked according to the parameters set by the user. For specific user settings, see the subsequent command description. At the same time, the login limit will take effect according to the user configuration. To disable this function, please use no service passwd-complexity command.

### Command Mode

Global Configuration Mode

### Syntax

```text
service passwd-complexity
no service passwd-complexity
```

### Parameters

Official documentation does not explicitly specify parameters.

### Default

- The service passwd-complexity command is used to enable the global switch of password complexity, which is enabled by default.

### Example

```text
Enable global password complexity:
Switch(config)# service passwd-complexity
```

### Notes
- Privilege requirement: Only Admin level users have access to these commands.

## service passwd-complexity min-length

### Purpose

The service passwd-complexity min-length command is used to configure the minimum password length, which is 10 by default.

### Command Mode

Global Configuration Mode

### Syntax

```text
service passwd-complexity min-length min-length
```

### Parameters

- min-length
- minimum password length, the value range is 9~64, the default value is 10.

### Default

- The service passwd-complexity min-length command is used to configure the minimum password length, which is 10 by default.

### Example

```text
Set minimum length to 12:
Switch(config)#service passwd-complexity min-length 12
```

### Notes
- Privilege requirement: Only Admin level users have access to these commands.

## service passwd-complexity min-class-number

### Purpose

The service passwd-complexity min-class-number command is used to configure the minimum number of character classes (digits, lowercase, uppercase, special characters) required in passwords.

### Command Mode

Global Configuration Mode

### Syntax

```text
service passwd-complexity min-class-number min-class-number
```

### Parameters

- min-class-number
- The minimum character class contained in the password, the value range is 0~4, the default value is 3; if it is set to 0, it means no restriction.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Require all 4 character classes:
Switch(config)# service passwd-complexity min-class-number 4
```

### Notes
- Privilege requirement: Only Admin level users have access to these commands.

## service passwd-complexity max-repeat-number

### Purpose

The service passwd-complexity max-repeat-number command is used to configure the maximum allowed consecutive identical characters.

### Command Mode

Global Configuration Mode

### Syntax

```text
service passwd-complexity max-repeat-number max-repeat-number
```

### Parameters

- max-repeat-number
- The maximum number of times the same character can be repeated in a password. The value range is 0 to 16. The default value is 1, which means that the password is not allowed to contain consecutive repeated characters. If it is set to 0, it means there is no limit.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Allow up to 2 consecutive repeats:
Switch(config)# service passwd-complexity max-repeat-number 2
```

### Notes
- Privilege requirement: Only Admin level users have access to these commands.

## service passwd-complexity max-keyboard-consecutive-num

### Purpose

The service passwd-complexity max-keyboard-consecutive-num command is used to configure the maximum consecutive keyboard-aligned characters (case-insensitive, excludes special characters).

### Command Mode

Global Configuration Mode

### Syntax

```text
service passwd-complexity max-keyboard-consecutive-num max-keyboard-consecutive-num
```

### Parameters

- max-keyboard-consecutive-num
- The maximum number of characters that cannot be included in the password from left to right in the main keyboard area (excluding special characters). Letters are not case sensitive. The value range is 0 to 10. The default value is 4, which means that the password is not allowed to contain consecutive characters such as aSdf and 1234 in the main keyboard area. If it is set to 0, it means there is no limit.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Block sequences longer than 3 characters (e.g., 123, Asd):
Switch(config)#service passwd-complexity max-keyboard-consecutive-num 3
```

### Notes
- Privilege requirement: Only Admin level users have access to these commands.

## service passwd-complexity not-current

### Purpose

The service passwd-complexity not-current command is used to configure that a new password cannot be set as the currently active password. When enabled, users cannot configure a new password identical to their current active password. When disabled, users are allowed to set a new password that matches their currently active password. To disable the restriction that prevents newly set passwords from being the same as the current password, use the no service passwd-complexity not-current command.

### Command Mode

Global Configuration Mode

### Syntax

```text
service passwd-complexity not-current
no service passwd-complexity not-current
```

### Parameters

- None

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Enable check to block reuse of current password:
Switch(config)# service passwd-complexity not-current
```

### Notes
- Privilege requirement: Only Admin level users have access to these commands.

## service passwd-complexity not-username

### Purpose

The service passwd-complexity not-username command is used to configure the policy that newly set passwords cannot be the username or its variants (including reversed or case-changed versions). When enabled, newly configured user passwords cannot match the username or its variants; when disabled, users may configure passwords identical to the username or its variants. To disable the restriction preventing new passwords from being username variants, use the no service passwd-complexity not-username command.

### Command Mode

Global Configuration Mode

### Syntax

```text
service passwd-complexity not-username
no service passwd-complexity not-username
```

### Parameters

- None

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

Official documentation does not provide an example.

### Notes
- No additional notes are explicitly provided in the official documentation.

## service passwd-complexity not-manufacturer-name

### Purpose

The service passwd-complexity not-manufacturer-name command is used to configure that new passwords cannot be set as the manufacturer name or its variants (including reversed or case-altered forms, where manufacturer names include tplink and tp-link). When enabled, users cannot configure new passwords using manufacturer names or their variants; when disabled, users are permitted to use manufacturer names and their variants as new passwords. To disable the restriction on using manufacturer names and their variants as new passwords, use the no service passwd-complexity not-manufacturer-name command.

### Command Mode

Global Configuration Mode

### Syntax

```text
service passwd-complexity not-manufacturer-name
no service passwd-complexity not-manufacturer-name
```

### Parameters

- None

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Block manufacturer name variants:
Switch(config)# service passwd-complexity not-manufacturer-name
```

### Notes
- Privilege requirement: Only Admin level users have access to these commands.

## service passwd-cycle

### Purpose

The service passwd-cycle command is used to set the time period during which previously used old passwords cannot be reused, determining the cycle before a password becomes available for reuse. If the switch is reset, this configuration will revert to default settings and previous configurations will become invalid.

### Command Mode

Global Configuration Mode

### Syntax

```text
service passwd-cycle days
```

### Parameters

- days
- The time that a used password can be used again, in days, with a value range of 0-356, and a default value of 90, which means that if an old password is used and a new password is set, the old password cannot be used again within 90 days. 0 means no limit.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Set reuse cooldown to 120 days:
Switch(config)# service passwd-cycle 120
```

### Notes
- Privilege requirement: Only Admin level users have access to these commands.

## show user account-list

### Purpose

The show user account-list command is used to display the information of the current users.

### Command Mode

Privileged EXEC Mode and Any Configuration Mode

### Syntax

```text
show user account-list
```

### Parameters

Official documentation does not explicitly specify parameters.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Display the information of the current users:
Switch (config)# show user account-list
```

### Notes
- Privilege requirement: Only Admin level users have access to these commands.

## show user configuration

### Purpose

The show user configuration command is used to display the security configuration information of the users, including access-control, max-number and the idle-timeout, etc.

### Command Mode

Privileged EXEC Mode and Any Configuration Mode

### Syntax

```text
show user configuration
```

### Parameters

Official documentation does not explicitly specify parameters.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Display the security configuration information of the users:
Switch (config)# show user configuration
```

### Notes
- Privilege requirement: None.

## show client all

### Purpose

The show client all command is used to display the detailed information about all clients.

### Command Mode

Privileged EXEC Mode and Any Configuration Mode

### Syntax

```text
show client
```

### Parameters

- all
- Displays more detailed information, such as client type, hardware model, vendor, port traffic data, etc.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Display the detailed information about all clients:
Switch (config)# show client all
```

### Notes
- Privilege requirement: None.
