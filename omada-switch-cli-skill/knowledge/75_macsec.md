# MACsec Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 74 MACsec Commands (Only for Certain Devices)

Location: extracted Word text lines 28277-28462

## Chapter Notes

Official documentation states: Media Access Control Security (MACsec) defines a method for secure data communication on IEEE 802 local area networks. MACsec provides users with secure MAC layer data transmission and reception services, including user data encryption, data frame integrity verification, and data source authenticity validation.

- This chapter is marked `Only for Certain Devices`; treat all configuration commands as model-dependent.

## macsec mka-policy

### Purpose
This command is used to configure a macsec policy template. When users configure the macsec function of a specific port, they can apply the corresponding template to simplify the configuration process. To delete the template, please use the no command.

### Command Mode
Global Configuration Mode

### Syntax
```text
macsec mka-policy policy-name [confidentiality-offset offset | replay-protection [window-size window-size] | validation-mode mode]
no macsec mka-policy policy-name [confidentiality-offset | replay-protection [window-size] | validation-mode]
```

### Parameters
```text
policy-name: MACsec policy template name.
offset: MACsec message encryption position offset. The value range is {0 | 30 | 50}, and the default value is 0.
window-size: The window size of the replay-protection function, ranging from 0 to 4294967295, and the default value is 0
mode: MACsec key matching mode, the value range is {check | strict}, and the default value is check
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Create a MACsec policy configuration template named test and set the validation-mode of the template to strict mode:
Switch(config)#macsec mka-policy test
Switch(config)#macsec mka-policy test validation-mode strict
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## macsec apply-policy

### Purpose
This command is used to apply the MACsec policy template configuration to the corresponding interface. To delete the policy, please use the no macsec apply-policy command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
macsec apply-policy policyName
no macsec apply-policy
```

### Parameters
```text
policy-name: MACsec policy template name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the MACsec function on port 1/0/2, and apply the MACsec policy template named test:
Switch(config)#interface gigabitEthernet 1/0/2
Switch(config-if)#macsec apply-policy test
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## macsec cipher_suite

### Purpose
This command is used to configure the MACsec packet encryption algorithm. To disable this function, please use the no macsec cipher_suite command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
macsec cipher_suite type
no macsec cipher_suite
```

### Parameters
```text
type: The encryption algorithm type used, the value is {gcm-aes-128 | gcm-aes-256}, the default value is gcm-aes-128.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the MACsec function on port 1/0/2, and set the cipher_suite to the gcm-aes-128 algorithm:
Switch(config)#interface gigabitEthernet 1/0/2
Switch(config-if)#macsec cipher_suite gcm-aes-128
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## macsec confidentiality-offset

### Purpose
This command is used to configure the cheap byte count when the macsec function encrypts packets, that is, the number of bytes after which the encryption of the packet data begins. To disable this function, please use the no macsec confidentiality-offset command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
macsec confidentiality-offset offset
no macsec confidentiality-offset
```

### Parameters
```text
offset: The MACsec message encryption position offset. The value is {0 | 30 | 50}, and the default value is 0
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the MACsec function on port 1/0/2, and set the encryption offset to 30:
Switch(config)#interface gigabitEthernet 1/0/2
Switch(config-if)#macsec confidentiality-offset 30
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## macsec desire

### Purpose
This command is used to enable the packet encryption function. To disable this function, please use the no macsec desire command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
macsec desire
no macsec desire
```

### Parameters
```text
None
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the MACsec packet encryption function on port 1/0/2:
Switch(config)#interface gigabitEthernet 1/0/2
Switch(config-if)#macsec desire
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## macsec mka

### Purpose
This command is used to enable the MKA negotiation function. To disable this function, please use the no macsec mka command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
macsec mka
no macsec mka
```

### Parameters
```text
None
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enable the MKA negotiation function on port 1/0/2:
Switch(config)#interface gigabitEthernet 1/0/2
Switch(config-if)#macsec mka
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## macsec mka priority

### Purpose
This command is used to configure the weight of the local end in the mka negotiation. During the MKA session establishment process, the one with the lower priority value will be elected as the key server. To restore the default value, please use the no macsec mka priority command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
macsec mka priority priority
no macsec mka priority
```

### Parameters
```text
priority: The priority of the local end in the MKA negotiation, ranging from 0 to 255. The default value is 255
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the MACsec function on port 1/0/2, and set the MKA negotiation priority to 20:
Switch(config)#interface gigabitEthernet 1/0/2
Switch(config-if)#macsec mka priority 20
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## macsec mka psk

### Purpose
This command is used to configure the local pre-configured security connection associated key information in the MKA negotiation. To disable this function, please use the no macsec mka psk ckn cak command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
macsec mka psk ckn name cak string
no macsec mka psk ckn cak
```

### Parameters
```text
name: The name of the local pre-configured security connection association key used for MKA negotiation.
string: The value of the local pre-configured security connection association key used for MKA negotiation
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the MACsec function on port 1/0/2, and set the pre-configured security connection association key name to
test
and its value to
abcdefg
Switch(config)#interface gigabitEthernet 1/0/2
Switch(config-if)#macsec mka psk ckn test cak abcdefg
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## macsec mka timer

### Purpose
This command is used to configure the mka session keepalive time that times out due to failure to receive mka messages from the peer. To disable this function, please use the no macsec mka timer mka-life command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
macsec mka timer mka-life seconds
no macsec mka timer mka-life
```

### Parameters
```text
seconds: MKA session timeout keepalive time, ranging from 6-60s. The default value is 21s.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the MACsec function on port 1/0/2, and set the timeout keepalive time to 6s:
Switch(config)#interface gigabitEthernet 1/0/2
Switch(config-if)#macsec mka timer mka-life 6
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## macsec replay-protection

### Purpose
This command is used to enable replay-protection and the window range for allowing packets to pass. When replay-protection is disabled, out-of-order packets will not be received; when it is enabled, out-of-order packets within the window range will be received. To disable this function, please use the no macsec replay-protection [window-size] command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
macsec replay-protection [window-size size-value]
no macsec replay-protection [window-size]
```

### Parameters
```text
size-value: Window size, ranging from 0 to 4294967295. The default value is 0.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the MACsec function on port 1/0/2, enable replay-protection and set the window size to 10:
Switch(config)#interface gigabitEthernet 1/0/2
Switch(config-if)#macsec replay-protection
Switch(config-if)#macsec replay-protection window-size 10
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.

## macsec validation-mode

### Purpose
This command is used to set the validation mode of ick information in the MKA negotiation process. When configured in strict mode, the ICK information will be strictly matched. When the ICK information carried in the received MKA message is inconsistent with that of the local end, the message will be discarded; when configured in check mode, only the ICK information is checked. When the ICK information carried in the received MKA message is inconsistent with that of the local end, it will still be parsed normally, but the MKA session will not be established. To disable this function, please use the no macsec validation-mode command.

### Command Mode
Interface Configuration Mode

### Syntax
```text
macsec validation-mode mode
no macsec validation-mode
```

### Parameters
```text
mode: The matching mode of ICK information in the MKA negotiation, the value range is {check | strict}, and the default value is check.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the MACsec function on port 1/0/2, and set validation-mode to strict mode:
Switch(config)#interface gigabitEthernet 1/0/2
Switch(config-if)#macsec validation-mode strict
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.
- Availability: Only for certain devices according to the official chapter title.
