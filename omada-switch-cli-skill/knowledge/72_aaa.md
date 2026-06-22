# AAA Commands

Source document: CLI Reference Guide, Managed Switches, 1900002754 REV1.1.0, April 2026

Source chapter: Chapter 71 AAA Commands

Location: extracted Word text lines 27098-27917

## Chapter Notes

Official documentation states: AAA stands for authentication, authorization and accounting. This feature is used to authenticate users trying to log in to the switch or trying to access the administrative level privilege. Applicable Access Application The authentication can be applied on the following access applications: Telnet, SSH and HTTP. Authentication Method List A method list describes the authentication methods and their sequence to authenticate a user. The switch supports Login List for users to gain access to the switch, and Enable List for normal users to gain administrative privileges. RADIUS/TACACS+ Server User can configure the RADIUS/TACACS+ servers for the connection between the switch and the server. Server Group User can define the authentication server group with up to several servers running the same secure protocols, either RADIUS or TACACS+. Users can set these servers in a preferable order, which is called the server group list. When a user tries to access the switch, the switch will ask the first server in the server group list for authentication. If no response is received, the second server will be queried, and so on.

- Use these commands only when the requested feature and target interface/VLAN/ring/session details are clear.

## tacacs-server host

### Purpose
The tacacs-server host command is used to configure a new TACACS+ server. To delete the specified TACACS+ server, please use no tacacs-server host command. When the command includes a VRF name, it indicates that the server address belongs to that specific VRF instance.

### Command Mode
Global Configuration Mode

### Syntax
```text
tacacs-server host ip-address [ port port-id ] [ timeout time ] [ vrfName vrf-name ] [ key { [ 0 ] string | 7 encryped-string } ]
no tacacs-server host ip-address
```

### Parameters
```text
ip-address
Specify the IP address of the TACACS+ server.
port-id
Specify the server
s port number for AAA. By default it is 49.
time
Specify the time in seconds the switch waits for the server
s response before it times out. The time ranges from 1 to 9 seconds. The default is 5 seconds.
vrf-name
Specify the vrf name of the TACACS server. By the default it is default.
[ 0 ] string | 7 encrypted-string
0 and 7 are the encryption type. 0 indicates that an unencrypted key will follow. 7 indicates that a symmetric encrypted key with a fixed length will follow. By default, the encryption type is 0.
string
is the shared key for the switch and the authentication servers to exchange messages.
encrypted-string
is a symmetric encrypted key with a fixed length, which you can copy from another switch
s configuration file. The key or encrypted-key you configured here will be displayed in the encrypted form. Always configure the key as the last item of this command.
```

### Default
By default it is 49. By default, the encryption type is 0.

### Example
```text
Configure a TACACS+ server with the IP address as 1.1.1.1, TCP port as 1500, timeout as 6 seconds, VRF instance asv1, and the unencrypted key string as 12345.
Switch(config)# tacacs-server host 1.1.1.1 port 1500 timeout 6 vrfName v1 key 12345
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- User guidelines: The TACACS+ servers you configured are added in the server group tacacs by default.

## show tacacs-server

### Purpose
This show tacacs-server command is used to display the summary information of the TACACS+ servers.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show tacacs-server
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the information of all the TACACS+ servers:
Switch(config)# show tacacs-server
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## radius-server host

### Purpose
The radius-server host command is used to configure a new RADIUS server. To delete the specified RADIUS server, please use no radius-server host command. When the command includes a VRF name, it indicates that the server address belongs to that specific VRF instance.

### Command Mode
Global Configuration Mode

### Syntax
```text
radius-server host ip-address [ auth-port port-id ] [ acct-port port-id ] [ timeout time ] [ retransmit number ] [ nas-id nas-id ] [ vrfName vrf-name ] [radsec-enable radsec-enable] [verify-enable verify-enable] [tls-port port] [tls-idletimeout idletimeout][tls-connectiontimeout connectiontimeout] [tls-retrys retrys] [certificate certificate ] [client-profile-id client-profile-id] [ key { [ 0 ] string | 7 encrypted-string } ]
no radius-server host ip-address
```

### Parameters
```text
ip-address
Specify the IP address of the RADIUS server.
auth-port port-id
Specify the UDP destination port for authentication requests. By default it is 1812.
acct-port port-id
Specify the UDP destination port for accouting requests. By deault it is 1813.
time
Specify the time in seconds the switch waits for the server
s response before it times out. The time ranges from 1 to 9 seconds. The default is 5 seconds.
number
Specify the number of times a RADIUS request is resent to a server if the server is not responding in time. By default it is 2 times.
nas-id
Specify the name of the NAS (Network Access Server) to be contained in RADIUS packets for identification. It ranges from 1 to 31 characters. The default value is the MAC address of the switch. Generally, the NAS indicates the switch itself.
vrf-name
Specify the vrf name of the RADIUS server. By the default it is default.
radsec-enable: RADSEC state (enabled/disabled).
verify-enable: State of validating RADIUS server certificate
(enabled/disabled).
port: RADIUS server listening port, ranging from 1 to 65535.
idletimeout: TLS tunnel idle timeout, ranging from 10 to 60.
connectiontimeout: TLS connection timeout, ranging from 1 to 9.
retrys: Number of send attempts, ranging from 1 to 5.
certificate: Certificate template name.
client-profile-id: Client template name and client key
[ 0 ] string | 7 encrypted-string
0 and 7 are the encryption type. 0 indicates that an unencrypted key will follow. 7 indicates that a symmetric encrypted key with a fixed length will follow. By default, the encryption type is 0.
string
is the shared key for the switch and the authentication servers to exchange messages.
encrypted-string
is a symmetric encrypted key with a fixed length, which you can copy from another switch
s configuration file. The key or encrypted-key you configured here will be displayed in the encrypted form. Always configure the key as the last item of this command.
```

### Default
By default it is 1812. By default it is 2 times. By default, the encryption type is 0.

### Example
```text
Configure a RADIUS server with an IP address of 1.1.1.1, an auth-port of 1200, a timeout of 6, a retransmit of 3, a VRF instance of v1, and a key of 12345.
Switch(config)# radius-server host 1.1.1.1 auth-port 1200 timeout 6 retransmit 3 vrfName v1 key 12345
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- User guidelines: The RADIUS servers you configured are added in the server group radius by default.

## radius-server radsec-profile

### Purpose
The radius-server radsec-profile command is used to create a RADSEC template with a specified name and enter its configuration mode. To delete the RADSEC template with the corresponding name, please use the no radius-server radsec-profile command.

### Command Mode
Global Configuration Mode

### Syntax
```text
radius-server radsec-profile name
no radius-server radsec-profile name
```

### Parameters
```text
name: The name of the radsec-profile.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Create a RADSEC template named test:
Switch(config)#radius-server radsec-profile test
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## download ca-certificate

### Purpose
The download ca-certificate command is used to download the CA certificate.

### Command Mode
Global Configuration Mode

### Syntax
```text
download ca-certificate filename ip ipaddress
```

### Parameters
```text
filename: The name of the certificate file to be imported, which should be a PEM file.
ipaddress: TFTP server IP address.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Import the certificate file named clntcert.pem as the CA certificate, with the TFTP server address as 192.168.0.146:
Switch(config)#radius-server radsec-profile test
Switch(radsec-certificate)#download ca-certificate clntcert.pem ip 192.168.0.146
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## download client-certificate

### Purpose
The download client-certificate command is used to download the client certificate provided by the user.

### Command Mode
Global Configuration Mode

### Syntax
```text
download client-certificate filename ip ipaddress
```

### Parameters
```text
filename: The name of the certificate file to be imported, which should be a PEM file.
ipaddress: TFTP server IP address.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Import the certificate file named clntcert.pem as the client certificate, with the TFTP server address set to 192.168.0.146:
Switch(config)#radius-server radsec-profile test
Switch(radsec-certificate)#download client-certificate clntcert.pem ip 192.168.0.146
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## download client-key

### Purpose
The download client-key command is used to download the private key file provided by the user.

### Command Mode
Global Configuration Mode

### Syntax
```text
download client-certificate filename ip ipaddress password password
```

### Parameters
```text
filename: The name of the certificate file to be imported, which should be a PEM file.
ipaddress: TFTP server IP address.
password: Private key file password.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Import the file named clntkey.pem as the private key, the TFTP server address is 192.168.0.146, and the private key file password is key123:
Switch(config)#radius-server radsec-profile test
Switch(radsec-certificate)#download client-certificate clntcert.pem ip 192.168.0.146 password key123
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## show radius-server

### Purpose
This show radius-server command is used to display the summary information of the RADIUS servers.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show radius-server
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the information of all the RADIUS servers:
Switch(config)# show radius-server
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## show radius-server certificate

### Purpose
This show radius-server certificate command is used to display the certificate directory and the corresponding certificate names.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show radius-server certificate
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the certificate directory and corresponding certificate names:
Switch(config)# show radius-server certificate
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## radius-server load-balance algorithm

### Purpose
The radius-server load-balance algorithm command is used to configure the load-balancing algorithm.

### Command Mode
Global Configuration Mode

### Syntax
```text
radius-server load-balance algorithm method
```

### Parameters
```text
method: RADIUS server load balancing algorithm (message-based/user-based).
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the load balancing algorithm of the RADIUS server group to message-based:
Switch(config)#radius-server load-balance algorithm message-based
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## radius-server load-balance least-outstading

### Purpose
The radius-server load-balance least-outstading command is used to configure the load balancing batch of the RADIUS server.

### Command Mode
Global Configuration Mode

### Syntax
```text
radius-server load-balance least-outstading Batch_size
```

### Parameters
```text
Batch_size: RADIUS server batch, ranging from 1 to 100, and the default value is 30.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the RADIUS server load balancing batch size to 50:
Switch(config)#radius-server load-balance least-outstading 50
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## radius-server dead-count

### Purpose
The radius-server dead-count command is used to configure the maximum number of consecutive non-responses during the RADIUS server status detection process.

### Command Mode
Global Configuration Mode

### Syntax
```text
radius-server dead-count dead-count
```

### Parameters
```text
dead-count: Maximum number of consecutive non-responses during the RADIUS server status detection process, ranging from 1 to 6, and the default value is 2.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the maximum number of consecutive non-responses during the RADIUS server status detection process to 3:
Switch(config)#radius-server dead-count 3
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## radius-server dead-cycle

### Purpose
The radius-server dead-cycle command is used to configure the number of cycles in the detection period during the RADIUS server status detection process.

### Command Mode
Global Configuration Mode

### Syntax
```text
radius-server dead-cycle dead-cycle
```

### Parameters
```text
dead-cycle: Maximum number of consecutive non-responses during the RADIUS server status detection process, ranging from 1 to 6, and the default value is 2.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the number of cycles in the detection period during the RADIUS server status detection process to 3:
Switch(config)#radius-server dead-cycle 3
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## radius-server dead-interval

### Purpose
The radius-server dead-interval command is used to configure the detection period of the RADIUS server status detection process.

### Command Mode
Global Configuration Mode

### Syntax
```text
radius-server dead-interval dead-interval
```

### Parameters
```text
dead-interval: Maximum number of consecutive non-responses during the RADIUS server status detection process, ranging from 1 to 15s, and the default value is 5.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the detection period of the RADIUS server status detection process to 10s:
Switch(config)#radius-server dead-interval 10
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## radius-server dead-time

### Purpose
The radius-server dead-time command is used to configure the duration that the RADIUS server remains in the down state.

### Command Mode
Global Configuration Mode

### Syntax
```text
radius-server dead-time dead-time
```

### Parameters
```text
dead-time: After the device marks the RADIUS server status as Down, it will set the server status to Force-up within the set dead-time. The range is 1~900s, and the default value is 300.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the duration for the RADIUS server in the down state to 600s:
Switch(config)#radius-server dead-time 600
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## radius-server max-unresponsiveinterval

### Purpose
The radius-server max-unresponsiveinterval command is used to configure the maximum unresponsive interval of the RADIUS server.

### Command Mode
Global Configuration Mode

### Syntax
```text
radius-server max-unresponsiveinterval interval
```

### Parameters
```text
interval: The maximum unresponsive interval of the RADIUS server. The range is 1~900s, and the default value is 300.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the maximum unresponsive interval of the RADIUS server to 600s:
Switch(config)#radius-server max-unresponsiveinterval 600
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## radius-server testuser

### Purpose
The radius-server testuser command is used to configure the user name and password used by the automatic detection function.

### Command Mode
Global Configuration Mode

### Syntax
```text
radius-server testuser username password
```

### Parameters
```text
username: Username used by the automatic detection function, 64 characters/numbers at most.
password: Password used by the automatic detection function, 64 characters/numbers at most.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Set the user name used for the automatic detection function to test and the password to key123:
Switch(config)#radius-server testuser test key123
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## radius-server detect-server

### Purpose
The radius-server detect-server command is used to configure the interval and timeout used by the automatic detection function. To disable this feature, please use the no radius-server detect-server command.

### Command Mode
Global Configuration Mode

### Syntax
```text
radius-server detect-server { interval interval | timeout timeout }
```

### Parameters
```text
interval: The automatic detection interval of the RADIUS server in the down state, ranging from 1-200s, and the default value is 60.
timeout: The automatic detection timeout, ranging from 1-9s, the default value is 3.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the interval and timeout used by the automatic detection function to 6s:
Switch(config)# radius-server detect-server timeout 6
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## aaa group

### Purpose
This aaa group command is used to create AAA server groups to group existing TACACS+/RADIUS servers for authentication. This command puts the switch in the server group subconfiguration mode. To delete the corresponding AAA group, please use the no aaa group command.

### Command Mode
Global Configuration Mode

### Syntax
```text
aaa group { radius | tacacs } group-name
no aaa group { radius | tacacs } group-name
```

### Parameters
```text
radius | tacacs
Specify the server group type as RADIUS or TACACS+.
group-name
Specify the server group name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Create a RADIUS server group with the name radius1:
Switch(config)# aaa group radius radius1
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## server

### Purpose
This server command is used to add the existing server in the defined server group. To remove the specified server from the server group, please use the no server command. When the command includes a VRF name, it indicates that the server address belongs to that specific VRF instance.

### Command Mode
Server Group Configuration Mode

### Syntax
```text
server ip-address [ vrfName vrf-name ]
no server ip-address [ vrfName vrf-name ]
```

### Parameters
```text
ip-address
Specify the server
s IP address.
vrf-name
Specify the vrf name of the server. By the default it is default.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Create the RADIUS server 1.1.1.1 and VRF address v1 to RADIUS server group
rad copy startup-config tftp command is used to backup the configuration file to TFTP server ius1
Switch(config)# aaa group radius radius1
Switch(aaa-group)# server 1.1.1.1 vrfName v1
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## show aaa group

### Purpose
This show aaa group command is used to display the summary information of the AAA groups. All the servers in this group will be listed if you specify the group name.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show aaa group [ group-name ]
```

### Parameters
```text
group-name
Specify the server group name.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the information of all the server groups:
Switch(config)# show aaa group
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## aaa authentication login

### Purpose
This aaa authentication login command is used to configure a login authentication method list. A method list describes the authentication methods and their sequence to authenticate a user. To delete the specified authentication method list, please use the no aaa authentication login command.

### Command Mode
Global Configuration Mode

### Syntax
```text
aaa authentication login { method-list } { method1 } [ method2 ] [ method3 ] [ method4 ]
no authentication login method-list
```

### Parameters
```text
method-list
Specify the method list name.
method1, method2, method3, method4
Specify the authentication methods in order. The next authentication method is tried only if the previous method does not respond, not if it fails.
The preset methods include radius, tacacs, local and none.
radius
means the RADIUS server group
radius
tacacs
means the RACACS+ server group
tacacs
local
means local username database are used;
none
means no authentication is used for login.
Users can aslo define new method with the
aaa group
command.
```

### Default
By default the login authentication method list is default with local as method1.

### Example
```text
Configure a login authentication method list
list1
with the priority1 method as radius and priority2 method as local:
Switch(config)# aaa authenticaiton login list1 radius local
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- User guidelines: By default the login authentication method list is default with local as method1.

## aaa authentication enable

### Purpose
This aaa authentication enable command is used to configure a privilege authentication method list. A method list describes the authentication methods and their sequence to elevate a user s privilege. To delete the specified authentication method list, please use the no aaa authentication enable command.

### Command Mode
Global Configuration Mode

### Syntax
```text
aaa authentication enable { method-list } { method1 } [ method2 ] [ method3 ] [ method4 ]
no authentication enable method-list
```

### Parameters
```text
method-list
Specify the method list name.
method1, method2, method3, method4
Specify the authentication methods in order. The next authentication method is tried only if the previous method does not respond, not if it fails.
The preset methods include radius, tacacs, local and none.
radius
means the RADIUS server group
radius
tacacs
means the RACACS+ server group
tacacs
local
means local username database are used;
none
means no authentication is used for privilege elevation.
Users can aslo define new method with the
aaa group
command.
```

### Default
By default the enable authentication method is default with none as method1.

### Example
```text
Configure a privilege authentication method list
list2
with the priority1 method as radius and priority2 method as local:
Switch(config)# aaa authenticaiton enable list2 radius local
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- User guidelines: By default the enable authentication method is default with none as method1.

## aaa authentication dot1x default

### Purpose
This aaa authentication dot1x default command is used to configure an 802.1x authentication method list. A method list describes the authentication methods for users login in 802.1x. To delete the default authentication method list, please use the no aaa authentication dot1x default command.

### Command Mode
Global Configuration Mode

### Syntax
```text
aaa authentication dot1x default { method }
no aaa authentication dot1x default
```

### Parameters
```text
method
Specify the method name. Only RADIUS server group is supported, and the default method is server group
radius
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the default 802.1x authentication method as
radius1
Switch(config)# aaa authentication dot1x default radius1
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## aaa accounting dot1x default

### Purpose
This aaa accounting dot1x default command is used to configure an 802.1x accounting method list. To delete the default accounting method list, please use the no aaa accounting dot1x default command.

### Command Mode
Global Configuration Mode

### Syntax
```text
aaa accounting dot1x default { method }
no aaa accounting dot1x default
```

### Parameters
```text
method
Sp+ecify the method name. Only RADIUS server group is supported, and the default method is server group
radius
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the default 802.1x accounting method as
radius1
Switch(config)# aaa accounting dot1x default radius1
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## show aaa authentication

### Purpose
This show aaa authentication command is used to display the summary information of the authentication login, enable and dot1x metheod list.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show aaa authentication [ login | enable | dot1x ]
```

### Parameters
```text
login | enable | dot1x
Specify the method list type.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the information of all the authentication method lists:
Switch(config)# show aaa authentication
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## show aaa accounting

### Purpose
This show aaa accounting command is used to display the summary information of the accounting metheod list.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show aaa accounting [ dot1x ]
```

### Parameters
```text
dot1x
Specify the method list type.
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the information of the default 802.1x accounting method list:
Switch(config)# show aaa accounting
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## line telnet

### Purpose
The line telnet command is used to enter the Line Configuration Mode to configure the telnet terminal line to which you want to apply the authentication list.

### Command Mode
Global Configuration Mode

### Syntax
```text
line telnet
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enter the telnet terminal line configuration mode:
Switch(config)#line telnet
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## login authentication (telnet)

### Purpose
The login authentication command is used to apply the login authentication method list to the telnet terminal line. To restore to the default authentication method list, please use the no login authentication command.

### Command Mode
Line Configuration Mode

### Syntax
```text
login authentication { method-list }
no login authentication
```

### Parameters
```text
method-list
Specify the login method list on the telnet terminal line. It is
default
by default, which contains the method
local
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the login authentication method list on the telnet terminal line as
list1
Switch(config)#line telnet
Switch(config-line)# login authentication list1
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## line ssh

### Purpose
The line ssh command is used to enter the Line Configuration Mode to configure the ssh terminal line to which you want to apply the authentication list.

### Command Mode
Global Configuration Mode

### Syntax
```text
line ssh
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enter the ssh terminal line configuration mode:
Switch(config)#line ssh
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## login authentication (ssh)

### Purpose
The login authentication command is used to apply the login authentication method list to the ssh terminal line. To restore to the default authentication method list, please use the no login authentication command.

### Command Mode
Line Configuration Mode

### Syntax
```text
login authentication { method-list }
no login authentication
```

### Parameters
```text
method-list
Specify the login method list on the ssh terminal line. It is
default
by default, which contains the method
local
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the login authentication method list on the ssh terminal line as
list1
Switch(config)# line ssh
Switch(config-line)# login authentication list1
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## line console

### Purpose
The line console command is used to enter the Line Configuration Mode to configure the console terminal line to which you want to apply the authentication list.

### Command Mode
Global Configuration Mode

### Syntax
```text
line console line-number
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Enter the console 0 terminal line configuration mode:
Switch(config)#line console 0
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- Official note: This command is only available on certain devices.

## login authentication (console)

### Purpose
The login authentication command is used to apply the login authentication method list to the console terminal line. To restore to the default authentication method list, please use the no login authentication command.

### Command Mode
Line Configuration Mode

### Syntax
```text
login authentication { method-list }
no login authentication
```

### Parameters
```text
method-list
Specify the login method list on the console terminal line. It is
default
by default, which contains the method
local
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the login authentication method list on the console 0 terminal line as
list1
Switch(config)# line console 0
Switch(config-line)# login authentication list1
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- Official note: This command is only available on certain devices.

## enable authentication (telnet)

### Purpose
The enable authentication command is used to apply the privilege authentication method list to the telnet terminal line. To restore to the default authentication method list, please use the no enable authentication command.

### Command Mode
Line Configuration Mode

### Syntax
```text
enable authentication { method-list }
no enable authentication
```

### Parameters
```text
method-list
Specify the enable method list on the telnet terminal line. It is
default
by default, which contains the method
none
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the enable authentication method list on the telnet terminal line as
list2
Switch(config)#line telnet
Switch(config-line)# enable authentication list2
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## enable authentication (ssh)

### Purpose
The enable authentication command is used to apply the privilege authentication method list to the ssh terminal line. To restore to the default authentication method list, please use the no enable authentication command.

### Command Mode
Line Configuration Mode

### Syntax
```text
enable authentication { method-list }
no enable authentication
```

### Parameters
```text
method-list
Specify the enable method list on the ssh terminal line. It is
default
by default, which contains the method
none
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the enable authentication method list on the ssh terminal line as
list2
Switch(config)# line ssh
Switch(config-line)# enable authentication list2
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## enable authentication (console)

### Purpose
The enable authentication command is used to apply the privilege authentication method list to the console terminal line. To restore to the default authentication method list, please use the no enable authentication command.

### Command Mode
Line Configuration Mode

### Syntax
```text
enable authentication { method-list }
no enable authentication
```

### Parameters
```text
method-list
Specify the enable method list on the console terminal line. It is
default
by default, which contains the method
none
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the enable authentication method list on the console 0 terminal line as
list2
Switch(config)# line console 0
Switch(config-line)# enable authentication list2
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- Official note: This command is only available on certain devices.

## ip http login authentication

### Purpose
The ip http login authentication command is used to apply the login authentication method list to users accessing through HTTP. To restore to the default authentication method list, please use the no ip http login authentication command.

### Command Mode
Global Configuration Mode

### Syntax
```text
ip http login authentication { method-list }
no ip http login authentication
```

### Parameters
```text
method-list
Specify the login method list on the HTTP access. It is
default
by default, which contains the method
local
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the login authentication method list on the HTTP access as
list1
Switch(config)# ip http login authentication list1
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## ip http enable authentication

### Purpose
The ip http enable authentication command is used to apply the privilege authentication method list to users accessing through HTTP. To restore to the default authentication method list, please use the no ip http enable authentication command.

### Command Mode
Line Configuration Mode

### Syntax
```text
ip http enable authentication { method-list }
no ip http enable authentication
```

### Parameters
```text
method-list
Specify the enable method list on the HTTP access. It is
default
by default, which contains the method
none
```

### Default
Not explicitly specified in the official documentation.

### Example
```text
Configure the enable authentication method list on the HTTP access as
list2
Switch(config)# ip http enable authentication list2
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## show aaa global

### Purpose
This show aaa global command is used to display global status of AAA function and the login/enable method lists of different application modules: telnet, ssh and HTTP.

### Command Mode
Privileged EXEC Mode and Any Configuration Mode

### Syntax
```text
show aaa global
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Display the AAA function
s global status and each application
s method list:
Switch(config)# show aaa global
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.

## enable admin password

### Purpose
The enable admin password command is used to set or change the Enable password for users to change the access level to admin. To remove the Enable password, please use no enable admin command. This command uses the symmetric encryption.

### Command Mode
Global Configuration Mode

### Syntax
```text
enable admin password { [ 0 ] password | 7 encrypted-password }
no enable admin
```

### Parameters
```text
Specify the encryption type. 0 indicates that an unencrypted password will follow. By default, the encryption type is 0.
password
Enable password, a string with 31 characters at most, which can contain only English letters (case-sensitive), digits and 17 kinds of special characters. The special characters are !$%
()*,-./[]_{|}. By default, it is empty. By default, it is empty.
Indicates a symmetric encrypted password with fixed length will follow.
encrypted-password
A symmetric encrypted password with fixed length, which you can copy from another switch
s configuration file. After the encrypted password is configured, you should use the corresponding unencrypted password if you re-enter this mode.
```

### Default
By default, the encryption type is 0. By default, it is empty. By default, it is empty.

### Example
```text
Set the Enable password as
abc123
and unencrypted for users to change the access level to admin:
Switch(config)#enable admin password 0 abc123
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- User guidelines: If the password you configured here is unencrypted and the global encryption function is enabled in service password-encryption , the password in the configuration file will be displayed in the symmetric encrypted form. If both the enable admin password and enable admin secret are defined, only the latest configured password will take effect.

## enable admin secret

### Purpose
The enable admin secret command is used to set or change the Enable password for users to change the access level to admin. To remove the Enable password, please use no enable admin command. This command uses the MD5 encryption.

### Command Mode
Global Configuration Mode

### Syntax
```text
enable admin secret { [ 0 ] password | 5 encrypted-password | 8 encrypted-password | 9 encrypted-password }
no enable admin
```

### Parameters
```text
Specify the encryption type. 0 indicates that an unencrypted password will follow. the password will be encrypted by MD5. By default, the encryption type is 0.
password
A string with 31 characters at most, which can contain only English letters (case-sensitive), digits and 17 kinds of special characters. The special characters are !$%
()*,-./[]_{|}. By default, it is empty.
Indicates an MD5 encrypted password with fixed length will follow.
Indicates an PBKDF2 encrypted password with fixed length will follow.
Indicates a SCRYPT encrypted password with fixed length will follow.
encrypted-password
An/A MD5/SCRYPT/PBKDF2 encrypted password with fixed length, which you can copy from another switch
s configuration file. After the encrypted password is configured, you should use the corresponding unencrypted password if you re-enter this mode.
```

### Default
By default, the encryption type is 0. By default, it is empty.

### Example
```text
Set the Enable password as
abc123
and unencrypted for users to change the access level to admin. The password will be displayed in the encrypted form.
Switch(config)#enable admin secret 0 abc123
```

### Notes
- Permission requirement: Only Admin level users have access to these commands.
- User guidelines: If both the enable admin password and enable admin secret are defined, only the latest configured password will take effect.

## enable-admin

### Purpose
The enable-admin command is used to get the administrative privelges by a non-admin user.

### Command Mode
Privileged EXEC Mode

### Syntax
```text
enable-admin
```

### Parameters
No parameters.

### Default
Not explicitly specified in the official documentation.

### Example
```text
Get the administrative privelges (the Enable password is
123456
Switch# enable-admin
Password: 123456
```

### Notes
- Permission requirement: Only User, Power User and Operator level users have access to these commands.
