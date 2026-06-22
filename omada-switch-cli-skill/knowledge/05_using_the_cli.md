# Using the CLI

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 1 Using the CLI

Location: official printed page 9-25; actual PDF page 55-71

## Chapter Notes

Chapter 1 explains CLI access methods, command modes, privilege levels, and formatting conventions. It is primarily operational guidance rather than a command reference chapter.

Do not treat this file as approval to generate Telnet, SSH, user-management, or routing-interface configuration commands. Those commands belong to their own official chapters and should only be generated after the corresponding knowledge files are added.

## CLI Access Methods

### Purpose
Explain the official methods for logging on to the switch and accessing the CLI.

### Command Mode
Not applicable.

### Syntax
Official documentation does not define a CLI syntax item in this section.

### Parameters
Official documentation does not define parameters in this section.

### Default
Not applicable.

### Example
Official documentation describes these access methods:

- Console port login.
- Telnet login through an Ethernet port.
- SSH login through an Ethernet port.

### Notes
- Console port availability depends on device model.
- Some devices provide both RJ-45 console and Micro-USB console ports.
- Console output is active on devices connected to both console ports, but console input is active on only one console port at a time.
- By default, the Micro-USB connector takes precedence over the RJ-45 connector.
- The first login should be followed by a password change to better protect the network and devices.
- Chapter 1 includes an SSH enable screenshot, but SSH service commands belong to the SSH command chapter and are not organized in this file.

## Console Login Settings

### Purpose
Record the official terminal-emulation settings for console login.

### Command Mode
Not applicable.

### Syntax
Official documentation does not define a CLI syntax item in this section.

### Parameters
Official documentation lists these terminal settings:

- Baud rate: `38400 bps`
- Data bits: `8`
- Parity: `none`
- Stop bits: `1`
- Flow control: `none`

### Default
Not applicable.

### Example
Official documentation shows login through a terminal-emulation program such as HyperTerminal, PuTTY, or Tera Term.

### Notes
- On macOS or Linux, the official documentation says no USB driver is needed for USB console connection.
- On Windows, the Micro-USB console port requires the TP-Link USB Console Driver.

## CLI Command Modes

### Purpose
Explain the official CLI command modes, prompts, and mode transitions.

### Command Mode
Not applicable.

### Syntax
Official documentation mentions the following mode transition commands:

```text
enable
disable
configure
exit
end
#
interface gigabitEthernet port
interface range gigabitEthernet port-list
interface port-channel port-channel-id
vlan vlan-list
no switchport
switchport
interface vlan vlan-id
interface loopback id
router rip
router ripng
```

### Parameters
- `port`: Ethernet port number.
- `port-list`: Ethernet port list.
- `port-channel-id`: Port-channel ID.
- `vlan-list`: VLAN list.
- `vlan-id`: VLAN ID.
- `id`: Loopback interface ID.

### Default
Not explicitly specified in the official documentation.

### Example
Official documentation describes these prompts:

```text
Switch>
Switch#
Switch(config)#
Switch(config-if)#
Switch(config-if-range)#
Switch(config-router)
Switch(config-vlan)#
```

### Notes
- User EXEC Mode is the primary mode after connection to the switch.
- `enable` enters Privileged EXEC Mode from User EXEC Mode.
- `configure` enters Global Configuration Mode from Privileged EXEC Mode.
- `exit`, `end`, `Ctrl+Z`, and `#` are used for returning from configuration modes as described in the official mode table.
- `#` can return directly from a deeper configuration view to Global Configuration Mode / `Switch(config)#`, so it is useful after finishing configuration inside one view before starting another feature.
- Global Configuration Mode, Interface Configuration Mode, and VLAN Configuration Mode are only available in standalone mode.
- Each command mode has its own specific commands; access the corresponding command mode before configuring a command.
- Read the prompt before interpreting a command. For example, `Switch(config)#` is Global Configuration Mode, `Switch(config-if)#` is Interface Configuration Mode, and `Switch(config-vlan)#` is VLAN Configuration Mode. The same command or no-form can have different scope in different views.
- The commands listed in this section are mode-transition references. Generate a command only when its detailed syntax is covered by a corresponding knowledge file.

## Privilege Restrictions

### Purpose
Explain the official privilege-level model.

### Command Mode
Not applicable.

### Syntax
Official documentation does not define a standalone syntax item in this section.

### Parameters
Official documentation lists four privilege levels:

- User level
- Power User level
- Operator level
- Admin level

### Default
In the default case, no password is needed to enter Privileged EXEC Mode from User EXEC Mode.

### Example
Official documentation states that users can enter Privileged EXEC Mode from User EXEC Mode by using the `enable` command.

### Notes
- Different privilege levels have access to specified commands.
- Command-level access is documented in the "Privilege Requirement" section of each command.
- Password configuration for Admin-level access to Privileged EXEC Mode is handled by `enable password` in Chapter 3.
- Username/password configuration belongs to Chapter 4 User Management Commands and is not covered in this file.

## Format Conventions

### Purpose
Record the official CLI syntax conventions used across the guide.

### Command Mode
Not applicable.

### Syntax
Official documentation gives these convention examples:

```text
speed {10 | 100 | 1000}
show logging
mode {dynamic | static | permanent}
bridge aging-time aging-time
```

### Parameters
- Items in square brackets `[ ]` are optional.
- Items in braces `{ }` are required.
- Alternative items are grouped in braces and separated by vertical bars.
- Bold text indicates an unalterable keyword.
- Normal font indicates a constant option.
- Italic font indicates a variable that must be assigned an actual value.

### Default
Not applicable.

### Example
Official documentation provides `speed {10 | 100 | 1000}` as an example of grouped required alternatives.

### Notes
- For character strings, the following six characters cannot be input: `"`, `<`, `>`, `,`, `\`, `&`.
- If a blank is contained in a character string, single or double quotation marks should be used.
- MAC addresses must use the format `xx:xx:xx:xx:xx:xx`.
- One or several values can be typed for a `port-list` or a `vlan-list` using commas.
- Use a hyphen to designate a range of values; for example, `1/0/1,1/0/3-5,1/0/7`.
