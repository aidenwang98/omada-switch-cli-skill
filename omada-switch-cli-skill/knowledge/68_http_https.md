# HTTP and HTTPS Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 67 HTTP and HTTPS Commands

Location: extracted Word text lines 26639-26878

## Chapter Notes

Official documentation states: With the help of HTTP (HyperText Transfer Protocol) or HTTPS (Hyper Text Transfer Protocol over Secure Socket Layer), you can manage the switch through a standard browser. HTTP is the protocol to exchange or transfer hypertext. SSL (Secure Sockets Layer), a security protocol, is to provide a secure connection for the application layer protocol (e.g. HTTP) based on TCP. Adopting asymmetrical encryption technology, SSL uses key pair to encrypt/decrypt information. A key pair refers to a public key (contained in the certificate) and its corresponding private key. By default the switch has a certificate (self-signed certificate) and a corresponding private key. The Certificate/Key Download function enables the user to replace the default key pair.

- Use these commands only when the requested feature and target interface/VLAN/ring/session details are clear.

## ip http server

### Purpose
The ip http server command is used to enable the HTTP server within the switch. To disable the HTTP function, please use no ip http server command. This function is enabled by default. The HTTP and HTTPS server function can be disabled at the same time.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip http server
no ip http server
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Disable the HTTP function:
Switch(config)# no ip http server
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## ip http port

### Purpose
The ip http port command is used to configure the port number of the HTTP server within the switch. To set the number to the default value, please use no ip http port command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip http port port-num
no ip http port
```

### Parameters
```text
port-num
Enter the port number. This value ranges from 1 to 65535.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set the port number of HTTP server as 1800:
Switch(config)# ip http port 1800
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## ip http max-users

### Purpose
The ip http max-users command is used to configure the maximum number of users that are allowed to connect to the HTTP server. To cancel this limitation, please use no ip http max-users command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip http max-users admin-num operator-num poweruser-num user-num
no ip http max-users
```

### Parameters
```text
admin-num
The maximum number of the users logging on to the HTTP server as Admin, ranging from 1 to 16. The total number of users should be no more than 16.
operator-num
The maximum number of the users logging on to the HTTP server as operator, ranging from 0 to 15. The total number of users should be no more than 16.
poweruser-num
The maximum number of the users logging on to the HTTP server as Power User, ranging from 0 to 15. The total number of users should be no more than 16.
user-num
The maximum number of the users logging on to the HTTP server as User, ranging from 0 to 15. The total number of users should be no more than 16.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the maximum number of the Admin, Operator, Power User and User as 5, 1, 1, 1 for HTTP:
Switch(config)# ip http max-users 5 1 1 1
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## ip http session timeout

### Purpose
The ip http session timeout command is used to configure the connection timeout of the HTTP server. To restore to the default timeout time, please use no ip http session timeout command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip http session timeout time
no ip http session timeout
```

### Parameters
```text
time
The timeout time, ranging from 5 to 30 in minutes. By default, the value is 10.
```

### Default
By default, the value is 10.

### Example
```text
Configure the timeout time of the HTTP connection as 15 minutes:
Switch(config)# ip http session timeout 15
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## ip http secure-server

### Purpose
The ip http secure-server command is used to enable the HTTPS server within the switch. To disable the HTTPS function, please use no ip http secure-server command. This function is enabled by default. The HTTP and HTTPS server function can be disabled at the same time.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip http secure-server
no ip http secure-server
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Disable the HTTP function:
Switch(config)# no ip http secure-server
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip http secure-port

### Purpose
The ip http secure-port command is used to configure the port number of the HTTPS server within the switch. To set the number to the default value, please use no ip http secure-port command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip http secure-port port-num
no ip http secure-port
```

### Parameters
```text
port-num
Enter the port number. This value ranges from 1 to 65535.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set the port number of HTTPS server as 2800:
Switch(config)# ip http secure-port 2800
```

### Notes
- Permission requirement: Only Admin and Operator level users have access to these commands.

## ip http secure-protocol

### Purpose
The ip http secure-protocol command is used to configure the SSL protocol version. To restore to the default SSL version, please use no ip http secure-protocol command. By default, the switch supports all the protocol versions, including SSL 3.0, TLS 1.0, TLS 1.1 and TLS 1.2.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip http secure-protocol { ssl3 | tls1 | tls11 | tls12 | all }
no ip http secure-protocol
```

### Parameters
```text
ssl3
Select SSL Version 3.0 as the protocol for HTTPS.
tls1
Select TLS Version 1.0 as the protocol for HTTPS.
tls11
Select TLS Version 1.1 as the protocol for HTTPS.
tls12
Select TLS Version 1.2 as the protocol for HTTPS.
all
Enable all the above protocols for HTTPS. The HTTPS server and client will negotiate the protocol each time.
```

### Default
By default, the switch supports all the protocol versions, including SSL 3.

### Example
```text
Configure the protocol of SSL connection as SSL 3.0:
Switch(config)# ip http secure-protocol ssl3
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip http secure-ciphersuite

### Purpose
The ip http secure-ciphersuite command is used to configure the cipherSuites over the SSL connection supported by the switch. To restore to the default ciphersuite types, please use no ip http secure-ciphersuite command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip http secure-ciphersuite { [ rc4-128-md5 ] [ rc4-128-sha ] [ des-cbc-sha ] [ 3des-ede-cbc-sha ] [ ecdhe-a128-g-s256 ] [ ecdhe-a256-g-s384 ] }
no ip http secure-ciphersuite
```

### Parameters
```text
[ rc4-128-md5 ] [ rc4-128-sha ] [ des-cbc-sha ] [ 3des-ede-cbc-sha ] [ ecdhe-a128-g-s256 ] [ ecdhe-a256-g-s384 ]
Specify the encryption algorithm and the digest algorithm to use on an SSL connection. By default, the switch supports all these ciphersuites.
```

### Default
By default, the switch supports all these ciphersuites.

### Example
```text
Configure the ciphersuite to be used for encryption over the SSL connection as 3des-ede-cbc-sha:
Switch(config)# ip http secure-ciphersuite 3des-ede-cbc-sha
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip http secure-max-users

### Purpose
The ip http secure-max-users command is used to configure the maximum number of users that are allowed to connect to the HTTPs server. To cancel this limitation, please use no ip http secure-max-users command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip http secure-max-users admin-num operator-num poweruser-num user-num
no ip secure-max-users
```

### Parameters
```text
admin-num
The maximum number of the users logging on to the HTTPs server as Admin, ranging from 1 to 16. The total number of users should be less than 16.
Operator-num
The maximum number of the users logging on to the HTTPs server as operator, ranging from 0 to 15. The total number of users should be less than 16.
poweruser-num
The maximum number of the users logging on to the HTTP server as Power User, ranging from 0 to 15. The total number of users should be less than 16.
user-num
The maximum number of the users logging on to the HTTP server as User, ranging from 0 to 15. The total number of users should be less than 16.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the maximum number of the Admin, Operator, Power User and User as 5, 1, 1, 1 for HTTPs:
Switch(config)# ip http secure-max-users 5 1 1 1
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip http secure-session timeout

### Purpose
The ip http secure-session timeout command is used to configure the connection timeout of the HTTPS server. To restore to the default timeout time, please use no ip http secure-session timeout command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip http secure-session timeout time
no ip http secure-session timeout
```

### Parameters
```text
time
The timeout time, ranging from 5 to 30 in minutes. By default, the value is 10.
```

### Default
By default, the value is 10.

### Example
```text
Configure the timeout time of the HTTPs connection as 15 minutes:
Switch(config)# ip http secure-session timeout 15
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip http secure-server download certificate

### Purpose
The ip http secure-server download certificate command is used to download a certificate to the switch from TFTP server.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip http secure-server download certificate ssl-cert ip-address ip-addr
```

### Parameters
```text
ssl-cert
The name of the SSL certificate which is selected to download to the switch. The length of the name ranges from 1 to 25 characters. The Certificate must be BASE64 encoded.
ip-addr
The IP address of the TFTP server. Both IPv4 and IPv6 addresses are supported, for example 192.168.0.1 or fe80::1234.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Download an SSL Certificate named ssl-cert from TFTP server with the IP address of 192.168.0.146:
Switch(config)# ip http secure-server download certificate ssl-cert ip-address 192.168.0.146
Download an SSL Certificate named ssl-cert from TFTP server with the IP address of fe80::1234
Switch(config)# ip http secure-server download certificate ssl-cert ip-address fe80::1234
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## ip http secure-server download key

### Purpose
The ip http secure-server download key command is used to download an SSL key to the switch from TFTP server.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip http secure-server download key ssl-key ip-address ip-addr
```

### Parameters
```text
ssl-key
The name of the SSL key which is selected to download to the switch. The length of the name ranges from 1 to 25 characters. The Key must be BASE64 encoded.
ip-addr
The IP address of the TFTP server. Both IPv4 and IPv6 addresses are supported, for example 192.168.0.1 or fe80::1234.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Download an SSL key named ssl-key from TFTP server with the IP address of 192.168.0.146:
Switch(config)# ip http secure-server download key ssl-key ip-address 192.168.0.146
Download an SSL key named ssl-key from TFTP server with the IP address of fe80::1234
Switch(config)# ip http secure-server download key ssl-key ip-address fe80::1234
```

### Notes
- Permission requirement: Only Admin, Operator and Power User level users have access to these commands.

## show ip http configuration

### Purpose
The show ip http configuration command is used to display the configuration information of the HTTP server, including status, session timeout, access-control, max-user number and the idle-timeout, etc.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip http configuration
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the configuration information of the HTTP server:
Switch(config)# show ip http configuration
```

### Notes
- Permission requirement: None.

## show ip http secure-server

### Purpose
The show ip http secure-server command is used to display the global configuration of SSL.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show ip http secure-server
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the global configuration of SSL:
Switch(config)# show ip http secure-server
```

### Notes
- Permission requirement: None.
