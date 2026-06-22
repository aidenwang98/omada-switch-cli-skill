# System Configuration Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 5 System Configuration Commands

Location: Word document text export, Chapter 5, after Chapter 4 User Management Commands and before Chapter 6 PTP Configuration Commands.

## Chapter Notes

Chapter 5 covers system time, system identity, management VLAN and Layer 3 interface addressing, controller adoption helpers, reset/reboot, configuration copy and backup, file transfer helpers, firmware/image/patch operations, auto-install, connectivity tests, system display commands, cable diagnostics, and power-related commands. This file now expands the earlier save/show-only coverage to the full Chapter 5 command set. Treat destructive or service-affecting commands such as reset, reboot, firmware upgrade, rollback, clear config interface, and boot/patch operations as high-risk and explain that they are suggestions only.

Note: Confirmed documentation typos have been corrected in this file. Remaining syntax/example inconsistencies are recorded in `pdf_uncertainties.md`.

## #

### Purpose

Return directly from a port view or another deeper configuration view to Global Configuration Mode / config view.

### Command Mode

Interface Configuration Mode, VLAN Configuration Mode, interface range Configuration Mode, interface port-channel Configuration Mode, or another deeper configuration view.

### Syntax

```text
#
```

### Parameters

Official documentation does not explicitly specify parameters.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Switch(config)# interface gigabitEthernet 1/0/5
Switch(config-if)# description Port_5
Switch(config-if)# #
Switch(config)#
```

### Notes
- Privilege requirement: Official mode-transition table in Chapter 1 describes # as a return-to-global-config command from deeper configuration modes.
- Use after finishing configuration in a nested configuration view before continuing with the next global configuration block.

## system-time manual

### Purpose

The system-time manual command is used to configure the system time manually.

### Command Mode

Global Configuration Mode

### Syntax

```text
system-time manual time
```

### Parameters

- time
- Set the date and time manually, MM/DD/YYYY-HH:MM:SS. The valid value of the year ranges from 2000 to 2037.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Configure the system mode as manual, and the time is 12/20/2010 17:30:35
Switch (config)# system-time manual 12/20/2010-17:30:35
```

### Notes
- Privilege requirement: Only Admin and Operator level users have access to these commands.

## system-time ntp

### Purpose

The system-time ntp command is used to configure the time zone and the IP address or hostname for the NTP Server. The switch will get UTC automatically if it has connected to an NTP Server.

### Command Mode

Global Configuration Mode

### Syntax

```text
system-time ntp { timezone } { ntp-server } { backup-ntp-server } { fetching-rate }
system-time ntp vrf vrf-name
```

### Parameters

- timezone
- Your local time-zone, and it ranges from UTC-12:00 to UTC+13:00.
- The detailed information that each time-zone means are displayed as follow:
- UTC-12:00
- TimeZone for International Date Line West.
- UTC-11:00
- TimeZone for Coordinated Universal Time-11.
- UTC-10:00
- TimeZone for Hawaii.
- UTC-09:00
- TimeZone for Alaska.
- UTC-08:00
- TimeZone for Pacific Time(US Canada).
- UTC-07:00
- TimeZone for Mountain Time(US Canada).
- UTC-06:00
- TimeZone for Central Time(US Canada).
- UTC-05:00
- TimeZone for Eastern Time(US Canada).
- UTC-04:30
- TimeZone for Caracas.
- UTC-04:00
- TimeZone for Atlantic Time(Canada).
- UTC-03:30
- TimeZone for Newfoundland.
- UTC-03:00
- TimeZone for Buenos Aires, Salvador, Brasilia.
- UTC-02:00
- TimeZone for Mid-Atlantic.
- UTC-01:00
- TimeZone for Azores, Cape Verde Is.
- UTC
- TimeZone for Dublin, Edinburgh, Lisbon, London.
- UTC+01:00
- TimeZone for Amsterdam, Berlin, Bern, Rome, Stockholm, Vienna.
- UTC+02:00
- TimeZone for Cairo, Athens, Bucharest, Amman, Beirut, Jerusalem.
- UTC+03:00
- TimeZone for Kuwait, Riyadh, Baghdad.
- UTC+03:30
- TimeZone for Tehran.
- UTC+04:00
- TimeZone for Moscow, St.Petersburg, Volgograd, Tbilisi, Port Louis.
- UTC+04:30
- TimeZone for Kabul.
- UTC+05:00
- TimeZone for Islamabad, Karachi, Tashkent.
- UTC+05:30
- TimeZone for Chennai, Kolkata, Mumbai, New Delhi.
- UTC+05:45
- TimeZone for Kathmandu.
- UTC+06:00
- TimeZone for Dhaka,Astana, Ekaterinburg.
- UTC+06:30
- TimeZone for Yangon (Rangoon).
- UTC+07:00
- TimeZone for Novosibrisk, Bangkok, Hanoi, Jakarta.
- UTC+08:00
- TimeZone for Beijing, Chongqing, Hong Kong, Urumqi, Singapore.
- UTC+09:00
- TimeZone for Seoul, Irkutsk, Osaka, Sapporo, Tokyo.
- UTC+09:30
- TimeZone for Darwin, Adelaide.
- UTC+10:00
- TimeZone for Canberra, Melbourne, Sydney, Brisbane.
- UTC+11:00
- TimeZone for Solomon Is., New Caledonia, Vladivostok.
- UTC+12:00
- TimeZone for Fiji, Magadan, Auckland, Welington.
- UTC+13:00
- TimeZone for Nuku'alofa, Samoa.
- ntp-server
- The IP address or domain name for the Primary NTP Server.
- backup-ntp-server
- The IP address or domain name for the Secondary NTP Server.
- fetching-rate
- Specify the rate fetching time from NTP server.
- vrf-name
- VRF instance name (1
- 15 characters).

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Configure the system time mode as NTP, the time zone is UTC-12:00, the primary NTP server is 133.100.9.2 and the secondary NTP server is 139.78.100.163, the fetching-rate is 11 hours, and specify the VRF instance named vrf1:
Switch(config)# system-time ntp UTC-12:00 133.100.9.2 139.79.100.163 11
Switch (config)# system-time ntp vrf vrf1
```

### Notes
- Privilege requirement: Only Admin and Operator level users have access to these commands.

## system-time dst predefined

### Purpose

The system-time dst predefined command is used to select a daylight saving time configuration from the predefined mode. The configuration can be used recurrently. To disable DST function, please use no system-time dst command.

### Command Mode

Global Configuration Mode

### Syntax

```text
system-time dst predefined [ USA | Australia | Europe | New-Zealand ]
no system-time dst
```

### Parameters

- USA | Australia | Europe | New-Zealand
- The mode of daylight saving time. There are 4 options which are USA, Australia, Europe and New-Zealand respectively. The default value is Europe.
- Following are the time ranges of each option:
- USA
- Second Sunday in March, 02:00
- First Sunday in November, 02:00.
- Australia
- First Sunday in October, 02:00
- First Sunday in April, 03:00.
- Europe
- Last Sunday in March, 01:00
- Last Sunday in October, 01:00.
- New Zealand
- Last Sunday in September, 02:00
- First Sunday in April, 03:00.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Configure the daylight saving time as USA standard:
Switch(config)#system-time dst predefined USA
```

### Notes
- Privilege requirement: Only Admin and Operator level users have access to these commands.

## system-time dst date

### Purpose

The system-time dst date command is used to configure the one-off daylight saving time. The start date is in the current year by default. The time range of the daylight saving time must shorter than one year, but you can configure it spanning years. To disable DST function, please use no system-time dst command.

### Command Mode

Global Configuration Mode

### Syntax

```text
system-time dst date {smonth } {sday } {stime } {syear } {emonth } {eday } {etime } {eyear }[offset ]
no system-time dst
```

### Parameters

- smonth
- The start month of the daylight saving time. There are 12 values showing as follows: Jan, Feb, Mar, Apr, May, Jun, Jul, Aug, Sep, Oct, Nov, Dec.
- sday
- the start day of the daylight saving time, ranging from 1 to 31. Here you should show special attention to February and the differences between a solar month and a lunar month.
- stime
- the start moment of the daylight saving time, hh:mm.
- syear
- The start year of the daylight saving time.
- emonth
- The end month of the daylight saving time. There are 12 values showing as follows: Jan, Feb, Mar, Apr, May, Jun, Jul, Aug, Sep, Oct, Nov, Dec.
- eday
- The end day of the daylight saving time, ranging from q to 31. Here you should show special attention to February and the differences between a solar month and a lunar month.
- etime
- The end moment of the daylight saving time, hh:mm.
- eyear
- The end year of the daylight saving time.
- offset
- The number of minutes to add during the daylight saving time. It is 60 minutes by default.

### Default

- The start date is in the current year by default.
- It is 60 minutes by default.

### Example

```text
Configure the daylight saving time from zero clock, Apr 1st to zero clock Oct 1st and the offset is 30 minutes in 2015:
Switch(config)# system-time dst date  Apr 1 00:00 2015 Oct 1 00:00 2015 30
```

### Notes
- Privilege requirement: Only Admin and Operator level users have access to these commands.

## system-time dst recurring

### Purpose

The system-time dst recurring command is used to configure the recurring daylight saving time. It can be configured spanning years. To disable DST function, please use no system-time dst command.

### Command Mode

Global Configuration Mode

### Syntax

```text
system-time dst recurring {sweek} {sday} {smonth} {stime} {eweek} {eday} {emonth} {etime} [offset]
no system-time dst
```

### Parameters

- sweek
- The start week of the daylight saving time. There are 5 values showing as follows: first, second, third, fourth, last.
- sday
- the start day of the daylight saving time. There are 7 values showing as follows: Sun, Mon, Tue, Wed, Thu, Fri, Sat.
- smonth
- The start month of the daylight saving time. There are 12 values showing as follows: Jan, Feb, Mar, Apr, May, Jun, Jul, Aug, Sep, Oct, Nov, Dec.
- stime
- the start moment of the daylight saving time, hh:mm.
- eweek
- The end week of the daylight saving time. There are 5 values showing as follows: first, second, third, fourth, last.
- eday
- The end day of the daylight saving time. There are 5 values showing as follows: Sun, Mon, Tue, Wed, Thu, Fri, Sat.
- emonth
- The end month of the daylight saving time. There are 12 values showing as following: Jan, Feb, Mar, Apr, May, Jun, Jul, Aug, Sep, Oct, Nov, Dec.
- etime
- The end moment of the daylight saving time, hh:mm.
- offset
- The number of minutes to add during the daylight saving time. It is 60 minutes by default.

### Default

- It is 60 minutes by default.

### Example

```text
Configure the daylight saving time from 2:00am, the first Sunday of May to 2:00am, the last Sunday of Oct and the offset is 45 minutes:
Switch(config)# system-time dst recurring first Sun May 02:00 last Sun Oct 02:00 45
```

### Notes
- Privilege requirement: Only Admin and Operator level users have access to these commands.

## hostname

### Purpose

The hostname command is used to configure the system name. To clear the system name information, please use no hostname command.

### Command Mode

Global Configuration Mode

### Syntax

```text
hostname [ hostname ]
no hostname
```

### Parameters

- hostname
- System Name. The length of the name ranges from 1 to 32 characters. By default, it is the device name, for example
- SG6654XHP

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Configure the system name as TP-Link
Switch(config)# hostname TP-Link
```

### Notes
- Privilege requirement: Only Admin and Operator level users have access to these commands.

## location

### Purpose

The location command is used to configure the system location. To clear the system location information, please use no location command.

### Command Mode

Global Configuration Mode

### Syntax

```text
location [ location ]
no location
```

### Parameters

- location
- Device Location. It consists of 32 characters at most.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Configure the system location as Hong Kong:
Switch(config)# location Hong Kong
```

### Notes
- Privilege requirement: Only Admin and Operator level users have access to these commands.

## contact-info

### Purpose

The contact-info command is used to configure the system contact information. To clear the system contact information, please use no contact-info command.

### Command Mode

Global Configuration Mode

### Syntax

```text
contact-info [ contact_info ]
no contact-info
```

### Parameters

- contact_info
- Contact Information. It consists of 32 characters at most. It is
- www.omadanetworks.com
- by default.

### Default

- `contact_info` is `www.omadanetworks.com` by default.

### Example

```text
Configure the system contact information as www.tp-link.com:
Switch(config)# contact-info
www.tp-link.com
```

### Notes
- Privilege requirement: Only Admin and Operator level users have access to these commands.

## led

### Purpose

The led command is used to control the LEDs.

### Command Mode

Global Configuration Mode

### Syntax

```text
led {on | off}
```

### Parameters

- on | off
- The LEDs are configured as on or off. By default, they are on.

### Default

- By default, they are on.

### Example

```text
Configure the LED as off:
Switch(config)# led off
```

### Notes
- Privilege requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip management-vlan

### Purpose

The ip management-vlan command is used to switch the management VLAN in standalone mode (non-Controller adoption mode). By default, the management VLAN is VLAN 1. After switching the management VLAN, the Controller retains the device-side configurations related to this VLAN, and subsequent communication between the device and the Controller also uses this VLAN (requires Controller version support). Before switching the management VLAN, ensure proper configuration of the VLAN, ports, VLAN interface (VLAN IF), etc., to guarantee normal Controller adoption and management of the device. To restore the management VLAN to the default, please use the no ip management-vlan command.

### Command Mode

Global Configuration Mode

### Syntax

```text
ip management-vlan vlan-id
no ip management-vlan
```

### Parameters

- vlan-id
- The VLAN ID of the management VLAN, ranging from 1 to 4090 (since the Controller only supports VLAN IDs 1
- 4090).

### Default

- By default, the management VLAN is VLAN 1.

### Example

```text
Configure the switch
s management VLAN as VLAN 100 via CLI commands.
(1) Create VLAN 100:
switch(config)# vlan 100
switch(config-vlan)# name mgmt-vlan
switch(config-vlan)# exit
(2) Add the port to the management VLAN:
switch(config)# interface gigabitEthernet 1/0/1
switch(config-if)# switchport general allowed vlan 100 untagged
switch(config-if)# switchport pvid 100
switch(config-if)# exit
(3) Configure the VLAN 100 interface:
switch(config)# interface vlan 100
# Configure a static IP:
switch(config-if)# ip address 192.168.0.1 255.255.255.0
# Or obtain an IP address via DHCP:
switch(config-if)# ip address-alloc dhcp
switch(config-if)# exit
(4) Switch the management VLAN to VLAN 100:
switch(config)# ip management-vlan 100
(5) Verify the configuration using show running-config.
```

### Notes
- Privilege requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip address

### Purpose

The ip address command is used to configure the IP address and IP subnet mask for the specified interface manually. The interface type includes: routed port, port-channel interface, loopback interface and VLAN interface.

### Command Mode

Interface Configuration Mode

### Syntax

```text
ip address { ip-addr } { mask } [ secondary ]
no ip address [ ip-addr ] [ mask ]
```

### Parameters

- ip-addr
- The IP address of the Layer 3 interface.
- mask
- The subnet mask of the Layer 3 interface.
- secondary
- Specify the interface
- s secondary IP address. If this parameter is omitted here, the configured IP address is the interface
- s primary address.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Create the VLAN interface 2 with the primary IP address as 192.168.1.1/24 and secondary IP address as 192.168.2.1/24:
Switch (config)# interface vlan 2
Switch (config-if)# ip address 192.168.1.1 255.255.255.0
Switch (config-if)# ip address 192.168.2.1 255.255.255.0 secondary
```

### Notes
- Privilege requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip address-alloc

### Purpose

The IP address-alloc command is used to enable the DHCP Client function or the BOOTP Protocol. When this function is enabled, the specified interface will obtain IP from DHCP Server or BOOTP server. To disable the IP obtaining function on the specified interface, please use the no ip address command. This command applies to the routed port, the port-channel interface and the VLAN interface.

### Command Mode

Interface Configuration Mode

### Syntax

```text
ip address-alloc { dhcp | bootp }
no ip address
```

### Parameters

- dhcp
- Specify the Layer 3 interface to obtain IP address from the DHCP Server.
- bootp
- Specify the Layer 3 interface to obtain IP address from the BOOTP Server.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Enable the DHCP Client function on the Lay 3 routed port 1/0/1:
Switch (config)# interface gigabitEthernet 1/0/1
Switch (config-if)# no switchport
Switch (config-if)# ip address-alloc dhcp
Disable the IP address obtaining function on the VLAN interface 2:
Switch (config)# interface vlan 2
Switch (config-if)# no ip address
```

### Notes
- Privilege requirement: Only Admin, Operator and Power User level users have access to these commands.

## controller cloud-based

### Purpose

The controller cloud-based command is used to enable Cloud-Based Controller managment. When this feature is enabled, you can further add your devices to your Omada Cloud-Based Controller. To disable the feature, use the no controller cloud-based command.

### Command Mode

Global Configuration Mode

### Syntax

```text
controller cloud-based
no controller cloud-based
```

### Parameters

Official documentation does not explicitly specify parameters.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

Official documentation does not provide an example.

### Notes
- Only available on certain devices, according to the official document.
- Privilege requirement: Only Admin, Operator and Power User level users have access to these commands.

## controller inform-url

### Purpose

If your switch and Omada SDN Controller are not located on the same subnet, the controller inform-url command is used to inform the switch of the controller s URL/IP address. To disable the feature, use the no controller inform-url command.

### Command Mode

Gloabal Configuration Mode

### Syntax

```text
controller inform-url { controller-url | controller-ip }
no controller inform-url
```

### Parameters

- controller-url
- Specify the URL of Omada SDN Controller.
- controller-ip
- Specify the IP address of Omada SDN Controller.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Inform the switch of the controller whose IP address is 192.168.1.1:
Switch (config)# controller inform-url 192.168.1.1
```

### Notes
- Only available on certain devices, according to the official document.
- Privilege requirement: Only Admin, Operator and Power User level users have access to these commands.

## controller discover

### Purpose

The controller discover command is used to control whether the device sends out controller discovery broadcast packets. By default, the device sends controller discovery broadcast packets. When the switch is turned off, the device will no longer periodically send broadcast discovery packets, and controllers will be unable to discover the device. However, this setting does not affect the sending of unicast discovery packets. If a controller's address is explicitly specified, that controller can still discover the device. To remove this configuration, please use the no controller discover command.

### Command Mode

Gloabal Configuration Mode

### Syntax

```text
controller discover
no controller discover
```

### Parameters

- None.

### Default

- By default, the device sends controller discovery broadcast packets.

### Example

```text
Disable the device from sending broadcast discovery packets to controllers:
Switch (config)# no controller discover
```

### Notes
- Only available on certain devices, according to the official document.
- Privilege requirement: Only Admin, Operator and Power User level users have access to these commands.

## controller dns-adoption

### Purpose

The controller dns-adoption command is used to enable the DNS-ADOPTION function. The DNS-ADOPTION function serves as a supplementary method for users to connect to the controller: Users configure the domain name on the DNS server to point to the IP address of the corresponding Omada controller, allowing users to establish a connection to the controller by accessing this domain name. After enabling the DNS-ADOPTION function, the device periodically sends DNS requests for the domain name "omada". If disabled, it will no longer send such DNS requests. This function is enabled by default. To disable this function, please use the no controller dns-adoption command.

### Command Mode

Gloabal Configuration Mode

### Syntax

```text
no controller dns-adoption
no no controller dns-adoption
```

### Parameters

- None.

### Default

- This function is enabled by default.

### Example

```text
Enable the DNS-ADOPTION function:
Switch (config)# controller dns-adoption
```

### Notes
- Only available on certain devices, according to the official document.
- Privilege requirement: Only Admin, Operator and Power User level users have access to these commands.

## reset

### Purpose

The reset command is used to reset the switch s software. After resetting, all configuration of the switch will restore to the factory defaults and your current settings will be lost.

### Command Mode

Privileged EXEC Mode

### Syntax

```text
reset [ except-ip ]
```

### Parameters

- except-ip
- Maintain the IP address when resetting the switch.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Reset all settings of the switch except its IP address:
Switch # reset except-ip
```

### Notes
- Privilege requirement: Only Admin level users have access to these commands.

## service reset-disable

### Purpose

The service reset-disable command is used to disable the reset function of the console port or reset button. To enable the reset function, use no service reset-disable command. By default, the reset function is enabled.

### Command Mode

Global Configuration Mode

### Syntax

```text
service reset-disable
no service reset-disable
```

### Parameters

Official documentation does not explicitly specify parameters.

### Default

- By default, the reset function is enabled.

### Example

```text
Disable the reset function of console port or reset button:
Switch (config)# service reset-disable
```

### Notes
- Privilege requirement: Only Admin level users have access to these commands.

## reboot

### Purpose

The reboot command is used to reboot the Switch. To avoid damage, please don t turn off the device while rebooting.

### Command Mode

Privileged EXEC Mode

### Syntax

```text
reboot
```

### Parameters

Official documentation does not explicitly specify parameters.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Reboot the switch:
Switch # reboot
```

### Notes
- Privilege requirement: Only Admin level users have access to these commands.

## reboot-schedule

### Purpose

This reboot-schedule command is used to configure the switch to reboot at a certain time point. To delete the reboot schedule settings, please use the reboot-schedule cancel command.

### Command Mode

Global Configuration Mode

### Syntax

```text
reboot-schedule at time [ date ] [ save_before_reboot ]
reboot-schedule in interval [ save_before_reboot ]
reboot-schedule cancel
```

### Parameters

- time
- Specify the time point for the switch to reboot, in the format of hh:mm.
- date
- Specify the date for the switch to reboot, in the format of DD:MM:YYYY. The date should be within 30 days.
- save_before_reboot
- Save the configuration file before the switch reboots.
- interval
- Specify a time period after which the switch reboots. It ranges from 1 to 43200 minutes.
- cancel
- Delete the reboot schedule settings.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Specify the switch to save the configuration files and reboot in 200 minutes:
Switch (config)# reboot-schedule in 200 save_before_reboot
```

### Notes
- Privilege requirement: Only Admin level users have access to these commands.
- In the command reboot-schedule at time [ date ] [ save_before_reboot ], if no date is specified and the time you set here is later than the time that this command is executed, the switch will reboot later that day; otherwise the switch will reboot at the time point the next day.

## copy running-config startup-config

### Purpose

The copy running-config startup-config command is used to save the current settings.

### Command Mode

Privileged EXEC Mode

### Syntax

```text
copy running-config startup-config
```

### Parameters

Official documentation does not explicitly specify parameters.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Save current settings:
Switch # copy running-config startup-config
```

### Notes
- Privilege requirement: Only Admin and Operator level users have access to these commands.

## copy startup-config tftp

### Purpose

The copy startup-config tftp command is used to backup the configuration file to TFTP server.

### Command Mode

Privileged EXEC Mode

### Syntax

```text
copy startup-config tftp ip-address ip-addr filename name [vrf vrf-name]
```

### Parameters

- ip-addr
- IP Address of the TFTP server. Both IPv4 and IPv6 addresses are supported, for example 192.168.0.1 or fe80::1234.
- name
- Specify the name for the configuration file which would be backup.
- vrf-name
- VRF instance name (1
- 15 characters).

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Backup the configuration files to TFTP server with the IP 192.168.0.148, name this file config.cfg and specify the VRF instance named vrf1:
Switch # copy startup-config tftp ip-address 192.168.0.148 filename config vrf vrf1
Backup the configuration files to TFTP server with the IP fe80::1234 and name this file config.cfg:
Switch # copy startup-config tftp ip-address fe80::1234 filename config
```

### Notes
- Privilege requirement: Only Admin and Operator level users have access to these commands.

## copy tftp startup-config

### Purpose

The copy tftp startup-config command is used to download the configuration file to the switch from TFTP server.

### Command Mode

Privileged EXEC Mode

### Syntax

```text
copy tftp startup-config ip-address ip-addr filename name [vrf vrf-name]
```

### Parameters

- ip-addr
- IP Address of the TFTP server. Both IPv4 and IPv6 addresses are supported, for example 192.168.0.1 or fe80::1234.
- name
- Specify the name for the configuration file which would be downloaded.
- vrf-name
- VRF instance name (1
- 15 characters).

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Download the configuration file named as config.cfg to the switch from TFTP server with the IP 192.168.0.148 and specify the VRF instance named vrf1:
Switch # copy tftp startup-config ip-address 192.168.0.148 filename config vrf vrf1
Download the configuration file named as config.cfg to the switch from TFTP server with the IP fe80::1234
Switch # copy tftp startup-config ip-address fe80::1234 filename config
```

### Notes
- Privilege requirement: Only Admin level users have access to these commands.

## copy backup-config tftp

### Purpose

The copy backup-config tftp command is used to export the backup configuration file of the switch to TFTP server.

### Command Mode

Privileged EXEC Mode

### Syntax

```text
copy backup-config tftp ip-address ip-addr filename name [vrf vrf-name]
```

### Parameters

- ip-addr
- IP Address of the TFTP server. Both IPv4 and IPv6 addresses are supported, for example 192.168.0.1 or fe80::1234.
- name
- Specify the name for the configuration file which would be exported.
- vrf-name
- VRF instance name (1
- 15 characters).

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Export the backup configuration file of the switch to the TFTP server with the IP 192.168.0.148, name the file config.cfg, and specify the VRF instance named vrf1:
Switch # copy backup-config tftp ip-address 192.168.0.148 filename config vrf vrf1
```

### Notes
- Privilege requirement: Only Admin level users have access to these commands.

## copy backup-config startup-config

### Purpose

The copy backup-config startup-config command is used to replace the startup configuration file using the backup configuration file.

### Command Mode

Privileged EXEC Mode

### Syntax

```text
copy backup-config startup-config
```

### Parameters

Official documentation does not explicitly specify parameters.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Replace the startup configuration file using the backup configuration file.:
Switch # copy backup-config startup-config
```

### Notes
- Privilege requirement: Only Admin level users have access to these commands.

## copy running-config backup-config

### Purpose

The copy running-config backup-config tftp command is used to save the current running configuration as the backup configuration file.

### Command Mode

Privileged EXEC Mode

### Syntax

```text
copy running-config backup-config
```

### Parameters

Official documentation does not explicitly specify parameters.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Save the current running configuration as the backup configuration file.
Switch # copy running-config backup-config
```

### Notes
- Privilege requirement: Only Admin level users have access to these commands.

## copy tftp backup-config

### Purpose

The copy tftp backup-config command is used to download the backup configuration file from a TFTP server.

### Command Mode

Privileged EXEC Mode

### Syntax

```text
Copy tftp backup-config ip-address ip-addr filename name [vrf vrf-name]
```

### Parameters

- ip-addr
- IP Address of the TFTP server. Both IPv4 and IPv6 addresses are supported, for example 192.168.0.1 or fe80::1234.
- name
- Specify the name for the configuration file which would be downloaded.
- vrf-name
- VRF instance name (1
- 15 characters).

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Download the configuration file named config.cfg from the TFTP server with the IP 192.168.0.148 and specify the VRF instance named vrf1:
Switch # copy tftp backup-config ip-address 192.168.0.148 filename config vrf vrf1
```

### Notes
- Privilege requirement: Only Admin level users have access to these commands.

## ftp open

### Purpose

The ftp open command is used to connect to an FTP server.

### Command Mode

Privileged EXEC Mode and Any Configuration Mode

### Syntax

```text
ftp open ip-addr [vrf vrf-name]
ftp open ipv6 ip-addr [vrf vrf-name]
```

### Parameters

- ip-addr
- IPv4 or IPv6 address.
- vrf-name
- VRF instance name (1-15 characters).

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Connect to an FTP server at IP 192.168.0.2 with VRF instance vrf1:
Switch (config)# ftp open 192.168.0.2 vrf vrf1
```

### Notes
- Privilege requirement: Only Admin, Operator and Power User level users have access to these commands.

## scp get

### Purpose

The scp get command is used to download a file to the device via SCP.

### Command Mode

Privileged EXEC Mode and Any Configuration Mode

### Syntax

```text
scp get username ip-addr source-filename dest-filename [vrf vrf-name]
scp ipv6 get username ipv6-addr source-filename dest-filename [vrf vrf-name]
```

### Parameters

- username
- SCP login username.
- ip-addr
- IPv4 address.
- source-filename
- Source filename (allowed characters: alphanumeric, -_@:/.[]()).
- dest-filename
- Destination filename (allowed characters: same as above).
- vrf-name
- VRF instance name (1-15 characters).

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Download test from server 192.168.0.2 (user admin) to local file test with VRF vrf1:
Switch (config)# scp get admin 192.168.0.2 test test vrf vrf1
```

### Notes
- Privilege requirement: Only Admin, Operator and Power User level users have access to these commands.

## scp put

### Purpose

The scp put command is used to upload a file from the device to a server via SCP.

### Command Mode

Privileged EXEC Mode and Any Configuration Mode

### Syntax

```text
scp put username ip-addr source-filename dest-filename [vrf vrf-name]
scp ipv6 put username ipv6-addr source-filename dest-filename [vrf vrf-name]
```

### Parameters

- username
- SCP login username.
- ip-addr
- IPv4 address.
- source-filename
- Source filename (allowed characters: alphanumeric, -_@:/.[]()).
- dest-filename
- Destination filename (allowed characters: same as above).
- vrf-name
- VRF instance name (1-15 characters).

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Upload local file test to server 192.168.0.2 (user admin) as test with VRF vrf1:
Switch (config)# scp put admin 192.168.0.2 test test vrf vrf1
```

### Notes
- Privilege requirement: Only Admin, Operator and Power User level users have access to these commands.

## sftp open

### Purpose

The sftp open command is used to connect to an SFTP server.

### Command Mode

Privileged EXEC Mode and Any Configuration Mode

### Syntax

```text
sftp open ip-addr username [vrf vrf-name]
sftp open ipv6 ipv6-addr username [vrf vrf-name]
```

### Parameters

- ip-addr
- IPv4 address.
- ipv6-addr
- IPv6 address.
- username
- SFTP login username.
- vrf-name
- VRF instance name (1-15 characters).

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Connect to SFTP server 192.168.0.2 (user admin) with VRF vrf1:
Switch (config)# sftp open admin 192.168.0.2 vrf vrf1
```

### Notes
- Privilege requirement: Only Admin, Operator and Power User level users have access to these commands.

## copy logging

### Purpose

The copy logging command command is used to export system log information to the user file system.

### Command Mode

Privileged EXEC Mode

### Syntax

```text
copy logging { flash | usbflash1 | usbflash2 } filename
```

### Parameters

- flash | usbflash1 | usbflash2
- The location of the exported file.
- filename
- The name of the exported log file.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Export the log information to flash and name it syslog.log:
Switch # copy logging flash syslog.log
```

### Notes
- Privilege requirement: Only Admin level users have access to these commands.

## copy logging tftp

### Purpose

The copy logging tftp command command is used to export system log information to a remote end.

### Command Mode

Privileged EXEC Mode

### Syntax

```text
copy logging tftp ip-address filename
```

### Parameters

- ip-address
- The destination IP address of the exported file.
- filename
- The name of the exported log file.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Export the log information to 192.168.1.255 and name it syslog.log:
Switch # copy logging tftp 192.168.1.255 syslog.log.
```

### Notes
- Privilege requirement: Only Admin level users have access to these commands.

## boot application

### Purpose

The boot application command is used to configure the image file as startup image or backup image.

### Command Mode

Global Configuration Mode

### Syntax

```text
boot application filename { image1 | image 2 } { startup | backup }
no boot application
```

### Parameters

- image1 | image2
- Specify the image file to be configured. By default, the image1.bin is the startup image and the image2.bin is the backup image.
- startup | backup
- Specify the property of the image, either startup image or backup image.

### Default

- By default, the image1.

### Example

```text
Configure the image2.bin as the startup image:
Switch (config)# boot application filename image2 startup
```

### Notes
- Privilege requirement: Only Admin level users have access to these commands.

## boot config

### Purpose

The boot config command is used to configure the configuration file as startup configuration or backup configuration.

### Command Mode

Global Configuration Mode

### Syntax

```text
boot config filename { config1 | config 2 } { startup | backup }
no boot config
```

### Parameters

- config1 | config2
- Specify the configuration file to be configured. By default, the config1.cfg is the startup image and the config2.cfg is the backup image.
- startup | backup
- Specify the property of the configuration.

### Default

- By default, the config1.

### Example

```text
Configure the config2.cfg as the startup image:
Switch (config)# boot config filename config2 startup
```

### Notes
- Privilege requirement: Only Admin level users have access to these commands.

## remove backup-image

### Purpose

The remove backup-image command is used to delete the backup-image.

### Command Mode

Privileged EXEC Mode

### Syntax

```text
remove backup-image
```

### Parameters

Official documentation does not explicitly specify parameters.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Delete the backup image file:
Switch # remove backup-image
```

### Notes
- Privilege requirement: Only Admin level users have access to these commands.

## firmware upgrade

### Purpose

The firmware upgrade command is used to upgrade the switch s backup image file via the TFTP server. The uploaded firmware file will take place of the Backup Image, and user can choose whether to reboot the switch with the Backup Image.

### Command Mode

Privileged EXEC Mode

### Syntax

```text
firmware upgrade tftp ip-address ip-addr filename name [vrf vrf-name]
```

### Parameters

- ip-addr
- IP Address of the TFTP server. Both IPv4 and IPv6 addresses are supported, for example 192.168.0.1 or fe80::1234.
- name
- Specify the name of the desired firmware file.
- vrf-name
- VRF instance name (1-15 characters).

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Upgrade the switch
s backup image file with the file firmware.bin in the TFTP server with the IP address 192.168.0.148, and reboot the switch with this firmware:
Switch # firmware upgrade tftp ip-address 192.168.0.148 filename firmware.bin
It will only upgrade the backup image. Continue? (Y/N):y
Operation OK!
Reboot with the backup image? (Y/N): y
Upgrade the switch
s backup image file with the file firmware.bin in the TFTP server with the IP address fe80::1234, but do not reboot the switch:
Switch # firmware upgrade tftp ip-address fe80::1234 filename firmware.bin
It will only upgrade the backup image. Continue? (Y/N):y
Operation OK!
Reboot with the backup image? (Y/N): n
```

### Notes
- Privilege requirement: Only Admin level users have access to these commands.

## patch load

### Purpose

This command is used to load a patch file from a TFTP server into the patch area of the system. The patch is in the deactivated state and has not taken effect.

### Command Mode

Privileged EXEC Mode and Any Configuration Mode

### Syntax

```text
patch load ip-address ip-addr filename filename [vrf vrf-name]
```

### Parameters

- ipaddr: IP address of the TFTP server.
- filename: Name of the patch file.
- vrf-name: VRF instance name (1-15 characters).

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Download the patch file named patch.bin from the TFTP server address with IP address 192.168.0.2 and specify the VRF instance named vrf1:
Switch# patch load ip-address 192.168.0.146 filename patch.bin vrf vrf1
```

### Notes
- Only available on certain devices, according to the official document.
- Privilege requirement: None

## patch active

### Purpose

This command is used to temporarily run a deactivated patch loaded into the system patch area. When a deactivated patch is temporarily run, the patch is activated and takes effect. When the device is restarted, the patch that was activated before the restart will be deactivated. Users can perform the following three operations on the activated patch.

### Command Mode

Privileged EXEC Mode and Any Configuration Mode

### Syntax

```text
patch active
```

### Parameters

- patch run: Change the patch status to running.
- patch deactive: Change the patch status to deactivated.
- patch delete: Invalidate the patch and delete it from the patch area.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Activate all deactivated patches loaded into the system patch area:
Switch# patch active
```

### Notes
- Only available on certain devices, according to the official document.
- Privilege requirement: None

## patch run

### Purpose

This command is used to permanently run an activated patch. When an activated patch is permanently run, the patch is in the running state. When the device is restarted, the patch that was in the running state before the restart will remain in the running state and take effect. Users can perform the following two operations on the running patch:

### Command Mode

Privileged EXEC Mode and Any Configuration Mode

### Syntax

```text
patch run
```

### Parameters

- patch uninstall: Return the patch from the running state to the activated state.
- patch delete: Invalidate the patch and delete it from the patch area.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Permanently run an activated patch:
Switch# patch run
```

### Notes
- Only available on certain devices, according to the official document.
- Privilege requirement: None

## patch deactive

### Purpose

This command is used to deactivate an activated patch:

### Command Mode

Privileged EXEC Mode and Any Configuration Mode

### Syntax

```text
patch deactive
```

### Parameters

- patch uninstall: Return the patch from the running state to the activated state.
- patch delete: Invalidate the patch and delete it from the patch area.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Deactivate an activated patch:
Switch# patch deactive
```

### Notes
- Only available on certain devices, according to the official document.
- Privilege requirement: None

## patch uninstall

### Purpose

This command is used to uninstall a running patch and activate it:

### Command Mode

Privileged EXEC Mode and Any Configuration Mode

### Syntax

```text
patch uninstall
```

### Parameters

- None

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Uninstall a running patch and activate it:
Switch# patch uninstall
```

### Notes
- Only available on certain devices, according to the official document.
- Privilege requirement: None

## patch delete

### Purpose

This command is used to delete a patch in the deactivated, activated, or running state, invalidating the patch and deleting the patch file from the system patch area:

### Command Mode

Privileged EXEC Mode and Any Configuration Mode

### Syntax

```text
patch delete
```

### Parameters

- None

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Delete a patch:
Switch# patch delete
```

### Notes
- Only available on certain devices, according to the official document.
- Privilege requirement: None

## show patch information

### Purpose

This command is used to view the patch information of the current system:

### Command Mode

Privileged EXEC Mode and Any Configuration Mode

### Syntax

```text
show patch information
```

### Parameters

- None

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
View the patch information of the current system:
Switch# show patch information
```

### Notes
- Only available on certain devices, according to the official document.
- Privilege requirement: None

## mcu-firmware unit upgrade

### Purpose

The mcu-firmware unit upgrade command is used to upgrade the switch s MCU-firmware online.

### Command Mode

None

### Syntax

```text
mcu-firmware unit {unit id} type {mcu-type} upgrade
```

### Parameters

- unit id
- Stack unit ID, ranging from 1 to 4.
- mcu-type
- MCU device type, which can be pse, crps, fan, monitor.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Display the switch MCU firmware version:
Switch#mcu-firmware type pse version
```

### Notes
- Only available on certain devices, according to the official document.
- Privilege requirement: Only Admin, Operator and Power User level users have access to these commands.

## mcu-firmware type

### Purpose

The mcu-firmware type command is used to display the MCU version information.

### Command Mode

None

### Syntax

```text
mcu-firmware type {mcu-type} version
```

### Parameters

- mcu-type
- MCU device type, which can be pse, crps, fan, monitor.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Upgrade the switch
s MCU-firmware online:
Switch#mcu-firmware unit 1 type pse upgrade
```

### Notes
- Only available on certain devices, according to the official document.
- Privilege requirement: Only Admin, Operator and Power User level users have access to these commands.

## checkpoint file

### Purpose

The checkpoint file command is used to create a checkpoint file. When creating a checkpoint file, it snapshots the current configuration. When deleting a checkpoint file, specify the filename for deletion. Note that after performing a device reset operation, all checkpoint files will be cleared. To delete a checkpoint file, please use the no checkpoint file command.

### Command Mode

Privileged EXEC Mode

### Syntax

```text
checkpoint file filename
no checkpoint file fileName
```

### Parameters

- fileName: Checkpoint file name, in the format of letters, numbers, underscores, hyphens and dots, and the length is limited to 1 to 32 characters. For example: hello_2024-01.cfg

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Create a checkpoint file named
hello2024
for the current configuration:
Switch#checkpoint file hello2024
```

### Notes
- Only available on certain devices, according to the official document.
- Privilege requirement: Privileged EXEC Mode and Any Configuration Mode

## show checkpoint

### Purpose

The show checkpoint command is used to view the names of all existing checkpoint files, or view all configuration information in a specific checkpoint file.

### Command Mode

Privileged EXEC Mode

### Syntax

```text
show checkpoint
show checkpoint file fileName
```

### Parameters

- fileName: Checkpoint file name, in the format of letters, numbers, underscores, hyphens and dots, and the length is limited to 1 to 32 characters. fileName must be the name of an existing file in the show checkpoint command execution result.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
View the configuration information in the checkpoint file named
hello2024
Switch#show checkpoint file hello2024
```

### Notes
- Only available on certain devices, according to the official document.
- Privilege requirement: Privileged EXEC Mode and Any Configuration Mode

## rollback running-config file

### Purpose

The rollback running-config file command is used to roll back the configuration of the switch to the configuration in an existing checkpoint file.

### Command Mode

Privileged EXEC Mode

### Syntax

```text
rollback running-config file fileName
```

### Parameters

- fileName: Checkpoint file name, in the format of letters, numbers, underscores, hyphens and dots, and the length is limited to 1 to 32 characters. fileName must be the name of an existing file in the show checkpoint command execution result.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Roll back the configuration of the switch to the configuration in the checkpoint file named
hello2024
Switch# rollback running-config file hello2024
```

### Notes
- Only available on certain devices, according to the official document.
- Privilege requirement: Privileged EXEC Mode and Any Configuration Mode

## boot autoinstall start

### Purpose

The boot autoinstall start command is used to start Auto Install function. To stop the Auto Install function, use no boot autoinstall start.

### Command Mode

Global Configuration Mode

### Syntax

```text
boot autoinstall start
no boot autoinstall start
```

### Parameters

Official documentation does not explicitly specify parameters.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Start Auto Install function:
Switch(config)# boot autoinstall start
```

### Notes
- Privilege requirement: Only Admin level users have access to these commands.

## boot autoinstall persistent-mode

### Purpose

The boot autoinstall persistent-mode command is used to start Auto Install function to next reboot cycle. To disable persistent mode, use no boot autoinstall persistent-mode.

### Command Mode

Global Configuration Mode

### Syntax

```text
boot autoinstall persistent-mode
no boot autoinstall persistent-mode
```

### Parameters

Official documentation does not explicitly specify parameters.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Start Auto Install function:
Switch(config)# boot autoinstall persistent-mode
```

### Notes
- Privilege requirement: Only Admin level users have access to these commands.

## boot autoinstall auto-save

### Purpose

The boot autoinstall auto-save command is used to automatically save the new configuration file that was downloaded by Auto Install function to start-up configuration file Auto Install. To disable auto-save configuration feature use no boot autoinstall auto-save.

### Command Mode

Global Configuration Mode

### Syntax

```text
boot autoinstall auto-save
no boot autoinstall auto-save
```

### Parameters

Official documentation does not explicitly specify parameters.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Configure Auto Install function to auto-save new configuration file to start-up configuration file:
Switch(config)# boot autoinstall auto-save
```

### Notes
- Privilege requirement: Only Admin level users have access to these commands.

## boot autoinstall auto-reboot

### Purpose

The boot autoinstall auto-reboot command is used to automatically reboot the switch after Auto Install function is completed successfully. To disable auto-reboot feature use no boot autoinstall auto-reboot.

### Command Mode

Global Configuration Mode

### Syntax

```text
boot autoinstall auto-reboot
no boot autoinstall auto-reboot
```

### Parameters

Official documentation does not explicitly specify parameters.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Configure the switch to auto reboot after Auto Install function completed successfully:
Switch(config)# boot autoinstall auto-reboot
```

### Notes
- Privilege requirement: Only Admin level users have access to these commands.

## boot autoinstall retry-count

### Purpose

The boot autoinstall retry-count command is used to configure retry count when Auto Install function uses TFTP to download configuration files in a cycle of Auto Install process. To set retry count to default value use no boot autoinstall retry-count.

### Command Mode

Global Configuration Mode

### Syntax

```text
boot autoinstall retry-count count
no boot autoinstall retry-count
```

### Parameters

- count
- The count of retrying auto install. The value ranges from 1 to 3.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Configure TFTP retry 2 times when download files failed:
Switch(config)# boot autoinstall retry-count 2
```

### Notes
- Privilege requirement: Only Admin level users have access to these commands.

## show boot autoinstall

### Purpose

The show boot autoinstall command is used to display the configuration of Auto Install function.

### Command Mode

Privileged EXEC Mode and Any Configuration Mode

### Syntax

```text
show boot autoinstall
```

### Parameters

Official documentation does not explicitly specify parameters.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Display the configuration of Auto Install function:
Switch# show boot autoinstall
```

### Notes
- Privilege requirement: None.

## show boot autoinstall downloaded-config

### Purpose

The show boot autoinstall downloaded-config command is used to display the configuration file which downloaded by Auto Install.

### Command Mode

Privileged EXEC Mode and Any Configuration Mode

### Syntax

```text
show boot autoinstall downloaded-config
```

### Parameters

Official documentation does not explicitly specify parameters.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Display the configuration file which downloaded by Auto Install:
Switch# show boot autoinstall downloaded-config
```

### Notes
- Privilege requirement: None.

## ping

### Purpose

The ping command is used to test the connectivity between the switch and one node of the network.

### Command Mode

Privileged EXEC Mode

### Syntax

```text
ping [ ip | ipv6 ] { ip_addr } [ -n count ] [ -l size ] [ -i interval] [-vrf vrf-name]
```

### Parameters

- The type of the IP address for ping test should be IPv4.
- ipv6
- The type of the IP address for ping test should be IPv6.
- ip_addr
- The IP address of the destination node for ping test. If the parameter ip/ipv6 is not selected, both IPv4 and IPv6 addresses are supported, for example 192.168.0.100 or fe80::1234.
- -n count
- The amount of times to send test data during Ping testing. It ranges from 1 to 10. By default, this value is 4.
- -l size
- The size of the sending data during ping testing. It ranges from 1 to 1500 bytes. By default, this value is 64.
- -i interval
- The interval to send ICMP request packets. It ranges from 100 to 1000 milliseconds. By default, this value is 1000.
- vrf-name
- VRF instance name (1-15 characters).

### Default

- By default, this value is 4.
- By default, this value is 64.
- By default, this value is 1000.

### Example

```text
To test the connectivity between the switch and the network device with the IP 192.168.0.131, please specify the count (-l) as 512 bytes and count (-i) as 1000 milliseconds. If there is not any response after 8 times
Ping test, the connection between the switch and the network device is failed to establish:
Switch # ping 192.168.0.131
n 8
l 512
To test the connectivity between the switch and the network device with the IP fe80::1234, please specify the count (-l) as 512 bytes and count (-i) as 1000 milliseconds. If there is not any response after 8 times
Ping test, the connection between the switch and the network device is failed to establish:
Switch # ping fe80::1234
n 8
l 512
```

### Notes
- Privilege requirement: None.

## tracert

### Purpose

The tracert command is used to test the connectivity of the gateways during its journey from the source to destination of the test data.

### Command Mode

Privileged EXEC Mode

### Syntax

```text
tracert [ ip | ipv6 ] ip_addr [ maxHops ] [-vrf vrf-name]
```

### Parameters

- The type of the IP address for tracert test should be IPv4.
- ipv6
- The type of the IP address for tracert test should be IPv6.
- ip_addr
- The IP address of the destination device. If the parameter ip/ipv6 is not selected, both IPv4 and IPv6 addresses are supported, for example 192.168.0.100 or fe80::1234.
- maxHops
- The maximum number of the route hops the test data can pass though. It ranges from 1 to 30. By default, this value is 4.
- vrf-name
- VRF instance name (1-15 characters).

### Default

- By default, this value is 4.

### Example

```text
Test the connectivity between the switch and the network device with the IP 192.168.0.131. If the destination device has not been found after 20 maxHops, the connection between the switch and the destination device is failed to establish:
Switch # tracert 192.168.0.131 20
Test the connectivity between the switch and the network device with the IP fe80::1234. If the destination device has not been found after 20 maxHops, the connection between the switch and the destination device is failed to establish:
Switch # tracert fe80::1234 20
```

### Notes
- Privilege requirement: Only Admin, Operator and Power User level users have access to these commands.

## show system-info

### Purpose

The show system-info command is used to display System Description, Device Name, Device Location, System Contact, Hardware Version, Firmware Version, System Time, Run Time and so on.

### Command Mode

Privileged EXEC Mode and Any Configuration Mode

### Syntax

```text
show system-info
```

### Parameters

Official documentation does not explicitly specify parameters.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Display the system information:
Switch # show system-info
```

### Notes
- Privilege requirement: None.

## show image-info

### Purpose

The show image-info command is used to display the information of image files in the system.

### Command Mode

Privileged EXEC Mode and Any Configuration Mode

### Syntax

```text
show image-info
```

### Parameters

Official documentation does not explicitly specify parameters.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Display the system image files
information:
Switch# show image-info
```

### Notes
- Privilege requirement: Only Admin level users have access to these commands.

## show boot

### Purpose

The show boot command is used to display the boot configuration of the system.

### Command Mode

Privileged EXEC Mode and Any Configuration Mode

### Syntax

```text
show boot
```

### Parameters

Official documentation does not explicitly specify parameters.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Display the system boot configuration information:
Switch# show boot
```

### Notes
- Privilege requirement: Only Admin level users have access to these commands.

## show running-config

### Purpose

The show running-config command is used to display the current operating configurations of the whole system, a specified unit, or a specified port.

### Command Mode

Privileged EXEC Mode and Any Configuration Mode

### Syntax

```text
show running-config [unit {all | | [exclude keyword ] [include keyword ] | interface {fastEthernet |gigabitEthernet | ten-gigabitEthernet} port} ]
show running-config [all | | [exclude keyword] [include keyword ] | interface {fastEthernet |gigabitEthernet | ten-gigabitEthernet} port ]
```

### Parameters

- unit
- Specify the unit number of a switch to show the unit
- s operating configurations. By default, it is 1.
- Display all the operating configurations of the whole system or a specified unit.
- Enable filter to filtrate the configurations. You can use exclude and include to set the filter rule.
- keyword
- The filter conditions, such as interface, vlan, and user.
- port
- Specify the number of the port to show the port
- s operating configurations.

### Default

- By default, it is 1.

### Example

```text
Display the current operating configurations only related to the user:
Switch# show running-config | include user
```

### Notes
- Privilege requirement: Only Admin level users have access to these commands.

## show startup-config

### Purpose

The show startup-config command is used to display the current configuration saved in the switch. These configuration settings will not be lost the next time you reboot the switch.

### Command Mode

Privileged EXEC Mode and Any Configuration Mode

### Syntax

```text
show startup-config
```

### Parameters

Official documentation does not explicitly specify parameters.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Display the saved configuration:
Switch# show startup-config
```

### Notes
- Privilege requirement: Only Admin level users have access to these commands.

## show system-time

### Purpose

The show system-time command is used to display the time information of the switch.

### Command Mode

Privileged EXEC Mode and Any Configuration Mode

### Syntax

```text
show system-time
```

### Parameters

Official documentation does not explicitly specify parameters.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Display the time information of the switch
Switch# show system-time
```

### Notes
- Privilege requirement: None.

## show system-time dst

### Purpose

The show system-time dst command is used to display the DST information of the switch.

### Command Mode

Privileged EXEC Mode and Any Configuration Mode

### Syntax

```text
show system-time dst
```

### Parameters

Official documentation does not explicitly specify parameters.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Display the DST information of the switch
Switch# show system-time dst
```

### Notes
- Privilege requirement: None.

## show system-time ntp

### Purpose

The show system-time ntp command is used to display the NTP mode configuration information.

### Command Mode

Privileged EXEC Mode and Any Configuration Mode

### Syntax

```text
show system-time ntp
```

### Parameters

Official documentation does not explicitly specify parameters.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Display the NTP mode configuration information of the switch:
Switch# show system-time ntp
```

### Notes
- Privilege requirement: None.

## show cable-diagnostics interface

### Purpose

The show cable-diagnostics interface command is used to display the cable diagnostics of the connected Ethernet Port., which facilitates you to check the connection status of the cable connected to the switch, locate and diagnose the trouble spot of the network.

### Command Mode

Privileged EXEC Mode and Any Configuration Mode

### Syntax

```text
show cable-diagnostics interface { fastEthernet port | gigabitEthernet port  | ten-gigabitEthernet port }
```

### Parameters

- port
- The number of the port which is selected for Cable test.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Show the cable-diagnostics of port 3:
Switch# show cable-diagnostics interface gigabitEthernet 1/0/3
```

### Notes
- Privilege requirement: None.

## show cpu-utilization

### Purpose

The show cpu-utilization command is used to display the system s CPU utilization in the last 5 seconds/1minute/5minutes.

### Command Mode

Privileged EXEC Mode and Any Configuration Mode

### Syntax

```text
show cpu-utilization
```

### Parameters

Official documentation does not explicitly specify parameters.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Display the CPU utilization information of the switch:
Switch# show cpu-utilization
```

### Notes
- Privilege requirement: None.

## show memory-utilization

### Purpose

The show memory-utilization command is used to display the current system s memory utilization in the last 5 seconds/1minute/5minutes.

### Command Mode

Privileged EXEC Mode and Any Configuration Mode

### Syntax

```text
show memory-utilization
```

### Parameters

Official documentation does not explicitly specify parameters.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Display the memory utilization information of the switch:
Switch# show memory-utilization
```

### Notes
- Privilege requirement: None.

## show controller

### Purpose

The show controller command is used to display the current controller settings and status.

### Command Mode

Privileged EXEC Mode and Any Configuration Mode

### Syntax

```text
show controller
```

### Parameters

Official documentation does not explicitly specify parameters.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Display the current controller settings and status:
Switch# show controller
```

### Notes
- Privilege requirement: None.

## show temperature

### Purpose

The show temperature command is used to display the temperature of switch.

### Command Mode

Privileged EXEC Mode and Any Configuration Mode

### Syntax

```text
show temperature
```

### Parameters

Official documentation does not explicitly specify parameters.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Display the temperature information of the switch:
Switch-DC# show temperature
```

### Notes
- Privilege requirement: None.

## show voltage

### Purpose

The show voltage command is used to display the voltage of DC power board.

### Command Mode

Privileged EXEC Mode and Any Configuration Mode

### Syntax

```text
show voltage
```

### Parameters

Official documentation does not explicitly specify parameters.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Display the voltage information of the switch:
Switch # show voltage
```

### Notes
- Privilege requirement: None.

## clear config interface

### Purpose

The clear config interface command is used to clear all configurations of a specified port.

### Command Mode

Privileged EXEC Mode and Any Configuration Mode

### Syntax

```text
clear config interface [fastEthernet | gigabitEthernet | two-gigabitEthernet | ten-gigabitEthernet |  port-channel ] port
```

### Parameters

- port
- The port number.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Clear all configurations of gigabitEthernet port 1/0/3:
Switch(config)# clear config interface gigabitEthernet 1/0/3
```

### Notes
- Privilege requirement: Only Admin level users have access to these commands.

## power backup unit

### Purpose

The power backup unit command is used to configure the power backup mode.

### Command Mode

Global Configuration Mode

### Syntax

```text
power backup unit {unit id} {power} mode {mode}
```

### Parameters

- unit id
- Stack unit ID, ranging from 1-4.
- power
- power supply module number.
- mode
- Power backup mode

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Configure the power backup mode of stack unit 1:
Switch(config)#power backup unit 1 pwr1 mode enable
```

### Notes
- Only available on certain devices, according to the official document.
- Privilege requirement: Only Admin and Operator level users have access to these commands.

## show power

### Purpose

The show power command is used to display the power details.

### Command Mode

Privileged EXEC Mode and Any Configuration Mode

### Syntax

```text
show power [detail]
```

### Parameters

Official documentation does not explicitly specify parameters.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Display the power details:
Switch#show power
```

### Notes
- Only available on certain devices, according to the official document.
- Privilege requirement: None.
