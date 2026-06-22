# SDM Template Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 10 SDM Template Commands

Location: Word document text export, Chapter 10, after Chapter 9 EEE Configuration Commands and before Chapter 11 Time Range Commands.

## Chapter Notes

This chapter describes how to configure Switch Database Management (SDM) templates to allocate hardware resources for different uses. Template changes do not take effect until the switch reboots.

## sdm prefer

### Purpose

Specify the SDM template to be used. The SDM template allocates system resources to support the features used in the application. Use `sdm prefer default` to return to the default template.

### Command Mode

Global Configuration Mode

### Syntax

```text
sdm prefer { default | enterpriseV4 | enterpriseV6 | extacl | enterpriseMix | pca-default }
```

### Parameters

- `default`: Specify the SDM template used in the switch as `default`.
- `enterpriseV4`: Specify the SDM template used in the switch as `enterpriseV4`.
- `enterpriseV6`: Specify the SDM template used in the switch as `enterpriseV6`.
- `extacl`: Specify the SDM template used in the switch as `extacl`, which provides more ACL support.
- `enterpriseMix`: Specify the SDM template used in the switch as `enterpriseMix`, which provides both IPv4/IPv6-ACL support and IMPBv4/v6 support.
- `pca-default`: Specify the SDM template used in the switch as `pca-default`, which provides packet-content-ACL support.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Switch(config)# sdm prefer enterpriseV4
```

### Notes

- Privilege requirement: Only Admin level users have access to these commands.
- Some models may not support the `pca-default` template.
- Changes to SDM preferences cannot take effect until the switch is rebooted.

## show sdm prefer

### Purpose

Display resource allocation of the current SDM template in use, or display templates that can be used.

### Command Mode

Privileged EXEC Mode and Any Configuration Mode

### Syntax

```text
show sdm prefer { used | default | enterpriseV4 | enterpriseV6 | extacl | enterpriseMix | pca-default}
```

### Parameters

- `used`: Display the resource allocation of the template currently in use, and the template that will become active after a reboot.
- `default`: Display the resource allocation of the default template.
- `enterpriseV4`: Display the resource allocation of the `enterpriseV4` template.
- `enterpriseV6`: Display the resource allocation of the `enterpriseV6` template.
- `extacl`: Display the resource allocation of the `extacl` template.
- `enterpriseMix`: Display the resource allocation of the `enterpriseMix` template.
- `pca-default`: Display the resource allocation of the `pca-default` template.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Switch(config)#show sdm prefer used
```

### Notes

- Privilege requirement: Only Admin level users have access to these commands.
