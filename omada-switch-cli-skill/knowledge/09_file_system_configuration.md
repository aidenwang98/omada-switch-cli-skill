# File System Configuration Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 7 File System Configuration Commands

Location: Word document text export, Chapter 7, after Chapter 6 PTP Configuration Commands and before Chapter 8 Management Port Configuration Commands.

## Chapter Notes

File System Commands configure local file-system navigation, file copy/rename/delete operations, and FTP view operations. The official chapter title says these commands are only available on certain devices; treat all commands in this file as device-model dependent.

## copy

### Purpose

The copy command is used to copy the specified file.

### Command Mode

Privileged EXEC Mode and Any Configuration Mode

### Syntax

```text
copy {flash|usbflash1|usbflash2} {filename} {destination}
```

### Parameters

- flash|usbflash1|usbflash2
- The flash type of the source file.
- filename
- File name.
- destination
- Copied file path.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Copy the specified file:
Switch#copy flash test.txt usbflash1
```

### Notes
- Privilege requirement: Only Admin, Operator and Power User level users have access to these commands.

## cd

### Purpose

The cd command is used to change the current file path.

### Command Mode

Privileged EXEC Mode and Any Configuration Mode

### Syntax

```text
cd {filename|flash|usbflash1|usbflash2} [filename]
```

### Parameters

- filename|flash|usbflash1|usbflash2
- The path that needs to be switched. If you enter filename, the file will be found in the current path by default.
- filename
- Specify the file in the corresponding flash.

### Default

- If you enter filename, the file will be found in the current path by default.

### Example

```text
Change the current file path:
Switch# cd usbflash1 test
```

### Notes
- Privilege requirement: Only Admin, Operator and Power User level users have access to these commands.

## dir

### Purpose

The dir command is used to list files and subdirectories contained in the specified working directory.

### Command Mode

Privileged EXEC Mode and Any Configuration Mode

### Syntax

```text
dir [flash|usbflash1|usbflash2] [filename]
```

### Parameters

- flash|usbflash1|usbflash2
- Specify path.
- filename
- Specify the file in the corresponding flash.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
List files and subdirectories contained in the specified working directory:
Switch#dir flash
```

### Notes
- Privilege requirement: Only Admin, Operator and Power User level users have access to these commands.

## pwd

### Purpose

The pwd command is used to display the absolute path name of the current working directory.

### Command Mode

Privileged EXEC Mode and Any Configuration Mode

### Syntax

```text
pwd
```

### Parameters

Official documentation does not explicitly specify parameters.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Display the absolute path name of the current working directory:
Switch#pwd
```

### Notes
- Privilege requirement: Only Admin, Operator and Power User level users have access to these commands.

## rename

### Purpose

The rename command is used to rename a file.

### Command Mode

Privileged EXEC Mode and Any Configuration Mode

### Syntax

```text
rename {srcFilename} {dstFilename}
```

### Parameters

- srcFilename
- Source file name.
- dstFilename
- Renamed file name.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Rename a file:
Switch#rename test1 test2
```

### Notes
- Privilege requirement: Only Admin, Operator and Power User level users have access to these commands.

## delete

### Purpose

The delete command is used to delete a file.

### Command Mode

Privileged EXEC Mode and Any Configuration Mode

### Syntax

```text
delete {filename|flash|usbflash1|usbflash2} [filename]
```

### Parameters

- filename|flash|usbflash1|usbflash2
- The file that needs to be deleted. If you enter filename, the file will be found in the current working path by default.
- filename
- Specify the file in the corresponding flash.

### Default

- If you enter filename, the file will be found in the current working path by default.

### Example

```text
Delete a file:
Switch# delete text.txt
```

### Notes
- Privilege requirement: Only Admin, Operator and Power User level users have access to these commands.

## ftp

### Purpose

The ftp command is used to enter the FTP (File Transfer Protocol) view.

### Command Mode

Privileged EXEC Mode and Any Configuration Mode

### Syntax

```text
ftp
```

### Parameters

Official documentation does not explicitly specify parameters.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Enter the FTP view:
Switch#ftp
```

### Notes
- Privilege requirement: Only Admin, Operator and Power User level users have access to these commands.

## open

### Purpose

The open command is used to connect to FTP server.

### Command Mode

FTP Configuration Mode

### Syntax

```text
open [ipv6] {hostIp}
```

### Parameters

- ipv6
- Specify the FTP server type as IPv6.
- hostIp
- FTP server IP.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Connect to FTP server:
Switch(ftp)#open 192.168.0.146
```

### Notes
- Privilege requirement: Only Admin, Operator and Power User level users have access to these commands.

## put

### Purpose

The put command is used to upload files to FTP server.

### Command Mode

FTP Configuration Mode

### Syntax

```text
put {srcFilename} {dstFilename}
```

### Parameters

- srcFilename
- Source file name.
- dstFilename
- Destination file name.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Upload files to FTP server:
Switch(ftp)#put src.c dst.c
```

### Notes
- Privilege requirement: Only Admin, Operator and Power User level users have access to these commands.

## get

### Purpose

The get command is used to download files from FTP server.

### Command Mode

FTP Configuration Mode

### Syntax

```text
get {srcFilename} {dstFilename}
```

### Parameters

- srcFilename
- Source file name.
- dstFilename
- Destination file name.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Download files from FTP server:
Switch(ftp)#get src.c dst.c
```

### Notes
- Privilege requirement: Only Admin, Operator and Power User level users have access to these commands.

## close

### Purpose

The close command is used to close current FTP connection.

### Command Mode

Privileged EXEC Mode and Any Configuration Mode

### Syntax

```text
close
```

### Parameters

Official documentation does not explicitly specify parameters.

### Default

Official documentation does not explicitly specify a standalone default value.

### Example

```text
Close current FTP connection:
Switch#close
```

### Notes
- Privilege requirement: Only Admin, Operator and Power User level users have access to these commands.
