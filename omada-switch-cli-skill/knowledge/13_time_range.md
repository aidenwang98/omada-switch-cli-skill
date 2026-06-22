# Time Range Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 11 Time Range Commands

Location: Word document text export, Chapter 11, after Chapter 10 SDM Template Commands and before Chapter 12 Interface Configuration Commands.

## Chapter Notes

Time Range Commands configure time ranges that can be bound to a PoE port or an ACL rule. This file covers only the time-range and holiday objects themselves; it does not authorize generating PoE or ACL binding commands from chapters that have not been added yet.

## time-range

### Purpose

Create a time-range entry for the switch and enter Time-Range Create Configuration Mode. After a time-range entry is created, specify the date and time. A time range can implement multiple time ranges simultaneously as long as they do not conflict. Use `no time-range` to delete the corresponding time-range configuration.

### Command Mode

Global Configuration Mode

### Syntax

```text
time-range name
no time-range name
```

### Parameters

- `name`: Time-range name, ranging from 1 to 16 characters.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Switch(config)# time-range tRange1
```

### Notes

- Privilege requirement: Only Admin, Operator and Power User level users have access to these commands.

## absolute

### Purpose

Create an absolute time range for the switch time range. Use `no absolute` to delete the corresponding absolute time-range configuration.

### Command Mode

Time-Range Create Configuration Mode

### Syntax

```text
absolute from start-date to end-date
no absolute [index ]
```

### Parameters

- `start-date`: Start date in Absoluteness Mode, in `MM/DD/YYYY` format.
- `end-date`: End date in Absoluteness Mode, in `MM/DD/YYYY` format.
- `index`: Official documentation does not explicitly describe this parameter beyond the no-form syntax.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Switch(config)#time-range tRange1
Switch(config-time-range)#absolute from 05/05/2017 to 10/05/2017
```

### Notes

- Privilege requirement: Only Admin, Operator and Power User level users have access to these commands.

## periodic

### Purpose

Create a periodic mode time range for the switch time range. Use `no periodic` to delete the corresponding periodic mode time-range configuration.

### Command Mode

Time-Range Create Configuration Mode

### Syntax

```text
periodic start start-time end end-time day-of-the-week week-day
no periodic [ index ]
```

### Parameters

- `start-time`: Start time in `HH:MM` format.
- `end-time`: End time in `HH:MM` format.
- `week-day`: In the format of `1-3, 6`, `daily`, `off-day`, or `working-day`. For example, `1-3,6` represents Monday, Tuesday, Wednesday and Saturday; `daily` represents every day; `off-day` represents the weekends; `working-day` represents the working days.
- `index`: Official documentation does not explicitly describe this parameter beyond the no-form syntax.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Switch(config)#time-range tSeg1
Switch(config -time-range)#periodic start 08:30 end 12:00 day-of-the-week 6-7
```

### Notes

- Privilege requirement: Only Admin, Operator and Power User level users have access to these commands.
- The official example prompt contains a space in `Switch(config -time-range)#`; this file preserves the official example formatting.

## holiday (time-range mode)

### Purpose

Create holiday mode behavior for the time range. When the excluded holiday occurs, the time range will not take effect; when included, the time range will take effect on holidays.

### Command Mode

Time-Range Create Configuration Mode

### Syntax

```text
holiday { exclude | include }
```

### Parameters

- `exclude`: The time range will not take effect on holiday.
- `include`: The time range will take effect on holiday.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Switch(config)#time-range tRange3
Switch(config-time-range)#holiday exclude
```

### Notes

- Privilege requirement: Only Admin, Operator and Power User level users have access to these commands.

## holiday

### Purpose

Create a holiday for the switch. Use `no holiday` to delete the corresponding holiday configuration.

### Command Mode

Global Configuration Mode

### Syntax

```text
holiday name start-date start-date end-date end-date
no holiday name
```

### Parameters

- `name`: Holiday name, ranging from 1 to 16 characters.
- `start-date`: Start date of the holiday, in `MM/DD` format, for instance `05/01`.
- `end-date`: End date of the holiday, in `MM/DD` format, for instance `05/01`.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Switch(config)# holiday holiday1 start-date 10/01 end-date 10/03
```

### Notes

- Privilege requirement: Only Admin, Operator and Power User level users have access to these commands.

## show holiday

### Purpose

Display the defined holiday.

### Command Mode

Privileged EXEC Mode and Any Configuration Mode

### Syntax

```text
show holiday
```

### Parameters

Official documentation does not explicitly specify parameters.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Switch# show holiday
```

### Notes

- Privilege requirement: None.

## show time-range

### Purpose

Display the defined time range.

### Command Mode

Privileged EXEC Mode and Any Configuration Mode

### Syntax

```text
show time-range [ time-range-name ]
```

### Parameters

- `time-range-name`: Specify the time range name with 1 to 16 characters.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Switch# show time-range
```

### Notes

- Privilege requirement: None.
