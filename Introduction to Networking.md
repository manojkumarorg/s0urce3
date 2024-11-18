Topologies:

Point-to-Point:
one to one connection shares
#### Point-To-Point Topology

![image](https://academy.hackthebox.com/storage/modules/34/redesigned/topo_p2p.png)
Bus: One can share other can receive

![image](https://academy.hackthebox.com/storage/modules/34/redesigned/topo_bus.png)
Star: Acts like a router where a source sends a packet to the router it forwards to the destination
#### Star Topology

![image](https://academy.hackthebox.com/storage/modules/34/redesigned/topo_star.png)
Ring:
Each host/node has two connection cables one for incoming and other for outgoing.
 A token is a bit pattern that continually passes through a ring network in one direction, which works according to the `claim token process`.
 #### Ring Topology

![image](https://academy.hackthebox.com/storage/modules/34/redesigned/topo_ring.png)
Mesh:
Each node has its each router if one network fails other can communicate without any error.
#### Mesh Topology

![image](https://academy.hackthebox.com/storage/modules/34/redesigned/topo_mesh.png)
Tree:Extended star topolgy or LAN connection.
#### Tree Topology

![image](https://academy.hackthebox.com/storage/modules/34/redesigned/topo_tree.png)
Hybrid:When two basic network toplogies are interconnected
![image](https://academy.hackthebox.com/storage/modules/34/redesigned/topo_hybrid.png)
	Daisy Chain: multiple hosts are connected by placing a cable from one node to another.
![[Pasted image 20240611222830.png]]
PROXY:(mediator)
A device sits in the middle of the connection inspect the contents of the traffic.
Without the ability to be a `mediator`, the device is technically a `gateway`, not a proxy.
Operate in Layer7

#### Forward Proxy

![image](https://academy.hackthebox.com/storage/modules/34/redesigned/forward_proxy.png)
example is  Forward Proxy is Burp Suite, as most people utilize it to forward HTTP Requests.

---

## Reverse Proxy

As you may have guessed, a `reverse proxy`, is the reverse of a `Forward Proxy`. Instead of being designed to filter outgoing requests, it filters incoming ones. The most common goal with a `Reverse Proxy`, is to listen on an address and forward it to a closed-off network.

![[Pasted image 20240611225622.png]]
Example:
Web Application Firewalls inspect web requests for malicious content and block the request if it is malicious.

OSI LAYER:
![[Pasted image 20240611230020.png]]
Packet transfer:
![[Pasted image 20240611230520.png]]
OSI follows vertical approach
TCP/IP follows horizontal approach

PROTOCOLS:
- `IPv4` / `IPv6`
- `IPsec`
- `ICMP`
- `IGMP`
- `RIP`
- `OSP`

IP ADDRESSING :
The `IPv4` format allows 4,294,967,296 unique addresses. The IP address is divided into a `host part` and a `network part`. The `router` assigns the `host part` of the IP address  `network administrator` assigns the `network part`. On the Internet, this is `IANA`, which allocates and manages the unique IPs.


| **`Class`** | **Network Address** | **First Address** | **Last Address** | **Subnetmask** | **CIDR**  | **Subnets** | **IPs**        |
| ----------- | ------------------- | ----------------- | ---------------- | -------------- | --------- | ----------- | -------------- |
| `A`         | 1.0.0.0             | 1.0.0.1           | 127.255.255.255  | 255.0.0.0      | /8        | 127         | 16,777,214 + 2 |
| `B`         | 128.0.0.0           | 128.0.0.1         | 191.255.255.255  | 255.255.0.0    | /16       | 16,384      | 65,534 + 2     |
| `C`         | 192.0.0.0           | 192.0.0.1         | 223.255.255.255  | 255.255.255.0  | /24       | 2,097,152   | 254 + 2        |
| `E`         | 240.0.0.0           | 240.0.0.1         | 255.255.255.255  | reserved       | reserved  | reserved    | reserved       |
| `D`         | 224.0.0.0           | 224.0.0.1         | 239.255.255.255  | Multicast      | Multicast | Multicast   | Multicast      |

SUBNETTING:

With the help of subnet mask the CIDR number has been known

dividing a larger networks into small ones
path:
- `Network address`
- `Broadcast address`
- `First host`
- `Last host`
- `Number of hosts`

 Imagine If I have an IP address of 192.168.0.1 how many host can I split the ip address in this network? Is there formula for host 2^h-2 is this right?
The IP address 192.168.0.1 is typically part of the private IP range 192.168.0.0/24, which means it has a default subnet mask of 255.255.255.0. This gives us:

- Network bits: 24 (from the subnet mask 255.255.255.0)
- Host bits: 32 - 24 = 8

Using the formula \(2^h - 2\):

\[2^8 - 2 = 256 - 2 = 254\]

So, you can have 254 usable host addresses in the 192.168.0.0/24 network. The subtraction of 2 accounts for the network address (192.168.0.0) and the broadcast address (192.168.0.255), which cannot be assigned to hosts.

Example:
Let us take the following IPv4 address and subnet mask as an example:

- IPv4 Address: `192.168.12.160`
- Subnet Mask: `255.255.255.192`
- CIDR: `192.168.12.160/26`
#### Network Part

|**Details of**|**1st Octet**|**2nd Octet**|**3rd Octet**|**4th Octet**|**Decimal**|
|---|---|---|---|---|---|
|IPv4|`1100 0000`|`1010 1000`|`0000 1100`|`10`10 0000|192.168.12.160`/26`|
|Subnet mask|`1111 1111`|`1111 1111`|`1111 1111`|`11`00 0000|`255.255.255.192`|
|Bits|/8|/16|/24|/32|
#### Host Part

| **Details of** | **1st Octet** | **2nd Octet** | **3rd Octet** | **4th Octet** | **Decimal**       |
| -------------- | ------------- | ------------- | ------------- | ------------- | ----------------- |
| IPv4           | 1100 0000     | 1010 1000     | 0000 1100     | 10`10 0000`   | 192.168.12.160/26 |
| Subnet mask    | 1111 1111     | 1111 1111     | 1111 1111     | 11`00 0000`   | 255.255.255.192   |
| Bits           | /8            | /16           | /24           | /32           |                   |

The bits in the `host part` can be changed to the `first` and `last` address. The first address is the `network address`, and the last address is the `broadcast address` for the respective subnet.
#### Network Address

So if we now set all bits to `0` in the `host part` of the IPv4 address, we get the respective subnet's `network address`.

|**Details of**|**1st Octet**|**2nd Octet**|**3rd Octet**|**4th Octet**|**Decimal**|
|---|---|---|---|---|---|
|IPv4|1100 0000|1010 1000|0000 1100|10`\|00 0000`|`192.168.12.128`/26|
|Subnet mask|`1111 1111`|`1111 1111`|`1111 1111`|`11\|`00 0000|255.255.255.192|
|Bits|/8|/16|/24|/32|
 If we make host part is zero means we can get the first usable network address(Network address)
 If we make host part is one means we can get the first usable network address(Broadcast address)


| **Hosts**         | **IPv4**         |
| ----------------- | ---------------- |
| Network Address   | `192.168.12.128` |
| First Host        | `192.168.12.129` |
| Other Hosts       | `...`            |
| Last Host         | `192.168.12.190` |
| Broadcast Address | `192.168.12.191` |

Subnetting into smaller networks:

| **Exponent** | **Value** |
| ------------ | --------- |
| 2`^0`        | = 1       |
| 2`^1`        | = 2       |
| 2`^2`        | = 4       |
| 2`^3`        | = 8       |
| 2`^4`        | = 16      |
| 2`^5`        | = 32      |
| 2`^6`        | = 64      |
| 2`^7`        | = 128     |
| 2`^8`        | = 256     |
Imagine if we have an ip address of 192.168.12.128  our task is to assign a 4 additional subnets so use this formula =2^n
n-subnet number
Now we increase/expand our subnet mask by `2 bits` from `/26` to `/28`, and it looks like this:

| **Details of** | **1st Octet** | **2nd Octet** | **3rd Octet** | **4th Octet** | **Decimal**         |
| -------------- | ------------- | ------------- | ------------- | ------------- | ------------------- |
| IPv4           | 1100 0000     | 1010 1000     | 0000 1100     | 1000`\|` 0000 | 192.168.12.128`/28` |
| Subnet mask    | `1111 1111`   | `1111 1111`   | `1111 1111`   | `1111\|` 0000 | `255.255.255.240`   |
| Bits           | /8            | /16           | /24           | /32           |                     |
Next, we can divide the `64` IPv4 addresses that are available to us into `4 parts`:

|**Hosts**|**Math**|**Subnets**|**Host range for each subnet**|
|---|---|---|---|
|64|/|4|= `16`|

So we know how big each subnet will be. From now on, we start from the network address given to us (192.168.12.128) and add the `16` hosts `4` times:

|**Subnet No.**|**Network Address**|**First Host**|**Last Host**|**Broadcast Address**|**CIDR**|
|---|---|---|---|---|---|
|1|`192.168.12.128`|192.168.12.129|192.168.12.142|`192.168.12.143`|192.168.12.128/28|
|2|`192.168.12.144`|192.168.12.145|192.168.12.158|`192.168.12.159`|192.168.12.144/28|
|3|`192.168.12.160`|192.168.12.161|192.168.12.174|`192.168.12.175`|192.168.12.160/28|
|4|`192.168.12.176`|192.168.12.177|192.168.12.190|`192.168.12.191`|192.168.12.176/28|

## Mental Subnetting
Network Address: `192.168.1.1/25`, it is immediately apparent that 192.168.2.4 would not be in the same network because the `/25` subnet means only the fourth octet may change


Subnet mask calculation:
To calculate the subnet mask for the IP address **10.200.20.0/27**, follow these steps:

1. **Find the Subnet Number**:
    
    - Subtract the prefix number from 32: (32 - 27 = 5).
2. **Calculate the Subnet Mask**:
    
    - Since we have 8 bits in each octet, turn on the first 5 bits (network bits):
        - Subnet Mask: **255.255.255.248**
Qn:
Split the network 10.200.20.0/27 into 4 subnets and submit the network address of the 3rd subnet as the answer.

Use formula 2^n
n=4(subnets)
 then it will become 10.200.20.0/29

Subnet mask`1111 1111`|`1111 1111`|`1111 1111`|`1111\|` 1000|`255.255.255.248|
here 2 usable 


# MAC Addresses
---

Each host in a network has its own `48`-bit (`6 octets`) `Media Access Control` (`MAC`) 

The MAC address consists of a total of `6 bytes`. The first half (`3 bytes` / `24 bit`) is the so-called `Organization Unique Identifier` (`OUI`)

| **Local Range**     |
| ------------------- |
| 0`2`:00:00:00:00:00 |
| 0`6`:00:00:00:00:00 |
| 0`A`:00:00:00:00:00 |
| 0`E`:00:00:00:00:00 |

The last bit can have two states, 0 and 1, as we already know. The last bit identifies the MAC address as `Unicast` (`0`) or `Multicast` (`1`)

#### MAC Broadcast

|**Representation**|**1st Octet**|**2nd Octet**|**3rd Octet**|**4th Octet**|**5th Octet**|**6th Octet**|
|---|---|---|---|---|---|---|
|Binary|`1111 1111`|`1111 1111`|`1111 1111`|`1111 1111`|`1111 1111`|`1111 1111`|
|Hex|`FF`|`FF`|`FF`|`FF`|`FF`|`FF`|

The second last bit in the first octet identifies whether it is a `global OUI`, defined by the IEEE, or a `locally administrated` MAC address.
#### Global OUI

|**Representation**|**1st Octet**|**2nd Octet**|**3rd Octet**|**4th Octet**|**5th Octet**|**6th Octet**|
|---|---|---|---|---|---|---|
|Binary|1101 11`0`0|1010 1101|1011 1110|1110 1111|0001 0011|0011 0111|
|Hex|D`C`|AD|BE|EF|13|37|
MAC-It maps a host's IP address to its corresponding MAC address to facilitate communication between devices on a  (`LAN`).

Two kind of request:
arp request
arp replay

#### Tshark Capture of ARP Requests

  MAC Addresses

```shell-session
1   0.000000 10.129.12.100 -> 10.129.12.255 ARP 60  Who has 10.129.12.101?  Tell 10.129.12.100
2   0.000015 10.129.12.101 -> 10.129.12.100 ARP 60  10.129.12.101 is at AA:AA:AA:AA:AA:AA

3   0.000030 10.129.12.102 -> 10.129.12.255 ARP 60  Who has 10.129.12.103?  Tell 10.129.12.102
4   0.000045 10.129.12.103 -> 10.129.12.102 ARP 60  10.129.12.103 is at BB:BB:BB:BB:BB:BB
```

# IPv6 Addresses

---

`IPv6` is the successor of IPv4. In contrast to IPv4, the `IPv6` address is `128` bit long. The `prefix` identifies the host and network parts

IPv6 consistently follows the `end-to-end` principle and provides publicly accessible IP addresses for any end devices without the need for NAT.

Stateless Address Autoconfiguration (SLAAC) is a key feature of IPv6 that enables devices to automatically configure their own unique IPv6 addresses without the need for manual configuration.

Omit leading zeros:

Specify IPv6 addresses by omitting leading zeros. For example, IPv6 address `1050:0000:0000:0000:0005:0600:300c:326b` can be written as `1050:0:0:0:5:600:300c:326b`.

Double colon:

Specify IPv6 addresses by using double colons (`::`) in place of a series of zeros. For example, IPv6 address `ff06:0:0:0:0:0:0:c3` can be written as `ff06::c3`. Double colons can be used only once in an IP address

In RFC 5952, the aforementioned IPv6 address notation was defined:

- All alphabetical characters are always written in lower case.
- All leading zeros of a block are always omitted.
- One or more consecutive blocks of `4 zeros` (hex) are shortened by two colons (`::`).
- The shortening to two colons (`::`) may only be performed `once` starting from the left.

Protocols:

| **Protocol**                                      | **Acronym** | **Description**                                                                                                                                                                                                                                                                                |
| ------------------------------------------------- | ----------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Wired Equivalent Privacy                          | `WEP`       | WEP is a type of security protocol that was commonly used to secure wireless networks.                                                                                                                                                                                                         |
| Secure Shell                                      | `SSH`       | A secure network protocol used to log into and execute commands on a remote system                                                                                                                                                                                                             |
| File Transfer Protocol                            | `FTP`       | A network protocol used to transfer files from one system to another                                                                                                                                                                                                                           |
| Simple Mail Transfer Protocol                     | `SMTP`      | A protocol used to send and receive emails                                                                                                                                                                                                                                                     |
| Hypertext Transfer Protocol                       | `HTTP`      | A client-server protocol used to send and receive data over the internet                                                                                                                                                                                                                       |
| Server Message Block                              | `SMB`       | A protocol used to share files, printers, and other resources in a network                                                                                                                                                                                                                     |
| Network File System                               | `NFS`       | A protocol used to access files over a network                                                                                                                                                                                                                                                 |
| Simple Network Management Protocol                | `SNMP`      | A protocol used to manage network devices                                                                                                                                                                                                                                                      |
| Wi-Fi Protected Access                            | `WPA`       | WPA is a wireless security protocol that uses a password to protect wireless networks from unauthorized access.                                                                                                                                                                                |
| Temporal Key Integrity Protocol                   | `TKIP`      | TKIP is also a security protocol used in wireless networks but less secure.                                                                                                                                                                                                                    |
| Network Time Protocol                             | `NTP`       | It is used to synchronize the timing of computers on a network.                                                                                                                                                                                                                                |
| Virtual Local Area Network                        | `VLAN`      | It is a way to segment a network into multiple logical networks.                                                                                                                                                                                                                               |
| VLAN Trunking Protocol                            | `VTP`       | VTP is a Layer 2 protocol that is used to establish and maintain a virtual LAN (VLAN) spanning multiple switches.                                                                                                                                                                              |
| Routing Information Protocol                      | `RIP`       | RIP is a distance-vector routing protocol used in local area networks (LANs) and wide area networks (WANs).                                                                                                                                                                                    |
| Open Shortest Path First                          | `OSPF`      | It is an interior gateway protocol (IGP) for routing traffic within a single Autonomous System (AS) in an Internet Protocol (IP) network.                                                                                                                                                      |
| Interior Gateway Routing Protocol                 | `IGRP`      | IGRP is a Cisco proprietary interior gateway protocol designed for routing within autonomous systems.                                                                                                                                                                                          |
| Enhanced Interior Gateway Routing Protocol        | `EIGRP`     | It is an advanced distance-vector routing protocol that is used to route IP traffic within a network.                                                                                                                                                                                          |
| Pretty Good Privacy                               | `PGP`       | PGP is an encryption program that is used to secure emails, files, and other types of data.                                                                                                                                                                                                    |
| Network News Transfer Protocol                    | `NNTP`      | NNTP is a protocol used for distributing and retrieving messages in newsgroups across the internet.                                                                                                                                                                                            |
| Cisco Discovery Protocol                          | `CDP`       | It is a proprietary protocol developed by Cisco Systems that allows network administrators to discover and manage Cisco devices connected to the network.                                                                                                                                      |
| Hot Standby Router Protocol                       | `HSRP`      | HSRP is a protocol used in Cisco routers to provide redundancy in the event of a router or other network device failure.                                                                                                                                                                       |
| Virtual Router Redundancy Protocol                | `VRRP`      | It is a protocol used to provide automatic assignment of available Internet Protocol (IP) routers to participating hosts.                                                                                                                                                                      |
| Spanning Tree Protocol                            | `STP`       | STP is a network protocol used to ensure a loop-free topology in Layer 2 Ethernet networks.                                                                                                                                                                                                    |
| Terminal Access Controller Access-Control System  | `TACACS`    | TACACS is a protocol that provides centralized authentication, authorization, and accounting for network access.                                                                                                                                                                               |
| Session Initiation Protocol                       | `SIP`       | It is a signaling protocol used for establishing and terminating real-time voice, video and multimedia sessions over an IP network.                                                                                                                                                            |
| Voice Over IP                                     | `VOIP`      | VOIP is a technology that allows for telephone calls to be made over the internet.                                                                                                                                                                                                             |
| Extensible Authentication Protocol                | `EAP`       | EAP is a framework for authentication that supports multiple authentication methods, such as passwords, digital certificates, one-time passwords, and public-key authentication.                                                                                                               |
| Lightweight Extensible Authentication Protocol    | `LEAP`      | LEAP is a proprietary wireless authentication protocol developed by Cisco Systems. It is based on the Extensible Authentication Protocol (EAP) used in the Point-to-Point Protocol (PPP).                                                                                                      |
| Protected Extensible Authentication Protocol      | `PEAP`      | PEAP is a security protocol that provides an encrypted tunnel for wireless networks and other types of networks.                                                                                                                                                                               |
| Systems Management Server                         | `SMS`       | SMS is a systems management solution that helps organizations manage their networks, systems, and mobile devices.                                                                                                                                                                              |
| Microsoft Baseline Security Analyzer              | `MBSA`      | It is a free security tool from Microsoft that is used to detect potential security vulnerabilities in Windows computers, networks, and systems.                                                                                                                                               |
| Supervisory Control and Data Acquisition          | `SCADA`     | It is a type of industrial control system that is used to monitor and control industrial processes, such as those in manufacturing, power generation, and water and waste treatment.                                                                                                           |
| Virtual Private Network                           | `VPN`       | VPN is a technology that allows users to create a secure, encrypted connection to another network over the internet.                                                                                                                                                                           |
| Internet Protocol Security                        | `IPsec`     | IPsec is a protocol used to provide secure, encrypted communication over a network. It is commonly used in VPNs, or Virtual Private Networks, to create a secure tunnel between two devices.                                                                                                   |
| Point-to-Point Tunneling Protocol                 | `PPTP`      | It is a protocol used to create a secure, encrypted tunnel for remote access.                                                                                                                                                                                                                  |
| Network Address Translation                       | `NAT`       | NAT is a technology that allows multiple devices on a private network to connect to the internet using a single public IP address. NAT works by translating the private IP addresses of devices on the network into a single public IP address, which is then used to connect to the internet. |
| Carriage Return Line Feed                         | `CRLF`      | Combines two control characters to indicate the end of a line and a start of a new one for certain text file formats.                                                                                                                                                                          |
| Asynchronous JavaScript and XML                   | `AJAX`      | Web development technique that allows creating dynamic web pages using JavaScript and XML/JSON.                                                                                                                                                                                                |
| Internet Server Application Programming Interface | `ISAPI`     | Allows to create performance-oriented web extensions for web servers using a set of APIs.                                                                                                                                                                                                      |
| Uniform Resource Identifier                       | `URI`       | It is a syntax used to identify a resource on the Internet.                                                                                                                                                                                                                                    |
| Uniform Resource Locator                          | `URL`       | Subset of URI that identifies a web page or another resource on the Internet, including the protocol and the domain name.                                                                                                                                                                      |
| Internet Key Exchange                             | `IKE`       | IKE is a protocol used to set up a secure connection between two computers. It is used in virtual private networks (VPNs) to provide authentication and encryption for data transmission, protecting the data from outside eavesdropping and tampering.                                        |
| Generic Routing Encapsulation                     | `GRE`       | This protocol is used to encapsulate the data being transmitted within the VPN tunnel.                                                                                                                                                                                                         |
| Remote Shell                                      | `RSH`       | It is a program under Unix that allows executing commands and programs on a remote computer.                                                                                                                                                                                                   |
Difference between smb and ftp: Does the same function
SMB-A protocol used to share files within a network
FTP -A protocol/service it can be accessed or share any files within a network 
use bridge for accessing the private network 


STP(spanning tree protocol):
![[Pasted image 20240613213208.png]]
 trunking:
 Trunking provides a way of **overcoming the bandwidth limitations of a single physical link** and is used in both switch-to-switch and switch-to-server connections to relieve traffic congestion


| **Protocol**                                              | **Acronym**  | **Port**         | **Description**                                                                                                                                                                    |
| --------------------------------------------------------- | ------------ | ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Telnet                                                    | `Telnet`     | `23`             | Remote login service                                                                                                                                                               |
| Secure Shell                                              | `SSH`        | `22`             | Secure remote login service                                                                                                                                                        |
| Simple Network Management Protocol                        | `SNMP`       | `161-162`        | Manage network devices                                                                                                                                                             |
| Hyper Text Transfer Protocol                              | `HTTP`       | `80`             | Used to transfer webpages                                                                                                                                                          |
| Hyper Text Transfer Protocol Secure                       | `HTTPS`      | `443`            | Used to transfer secure webpages                                                                                                                                                   |
| Domain Name System                                        | `DNS`        | `53`             | Lookup domain names                                                                                                                                                                |
| File Transfer Protocol                                    | `FTP`        | `20-21`          | Used to transfer files                                                                                                                                                             |
| Trivial File Transfer Protocol                            | `TFTP`       | `69`             | Used to transfer files                                                                                                                                                             |
| Network Time Protocol                                     | `NTP`        | `123`            | Synchronize computer clocks                                                                                                                                                        |
| Simple Mail Transfer Protocol                             | `SMTP`       | `25`             | Used for email transfer                                                                                                                                                            |
| Post Office Protocol                                      | `POP3`       | `110`            | Used to retrieve emails                                                                                                                                                            |
| Internet Message Access Protocol                          | `IMAP`       | `143`            | Used to access emails                                                                                                                                                              |
| Server Message Block                                      | `SMB`        | `445`            | Used to transfer files                                                                                                                                                             |
| Network File System                                       | `NFS`        | `111`, `2049`    | Used to mount remote systems                                                                                                                                                       |
| Bootstrap Protocol                                        | `BOOTP`      | `67`, `68`       | Used to bootstrap computers                                                                                                                                                        |
| Kerberos                                                  | `Kerberos`   | `88`             | Used for authentication and authorization                                                                                                                                          |
| Lightweight Directory Access Protocol                     | `LDAP`       | `389`            | Used for directory services                                                                                                                                                        |
| Remote Authentication Dial-In User Service                | `RADIUS`     | `1812`, `1813`   | Used for authentication and authorization                                                                                                                                          |
| Dynamic Host Configuration Protocol                       | `DHCP`       | `67`, `68`       | Used to configure IP addresses                                                                                                                                                     |
| Remote Desktop Protocol                                   | `RDP`        | `3389`           | Used for remote desktop access                                                                                                                                                     |
| Network News Transfer Protocol                            | `NNTP`       | `119`            | Used to access newsgroups                                                                                                                                                          |
| Remote Procedure Call                                     | `RPC`        | `135`, `137-139` | Used to call remote procedures                                                                                                                                                     |
| Identification Protocol                                   | `Ident`      | `113`            | Used to identify user processes                                                                                                                                                    |
| Internet Control Message Protocol                         | `ICMP`       | `0-255`          | Used to troubleshoot network issues                                                                                                                                                |
| Internet Group Management Protocol                        | `IGMP`       | `0-255`          | Used for multicasting                                                                                                                                                              |
| Oracle DB (Default/Alternative) Listener                  | `oracle-tns` | `1521`/`1526`    | The Oracle database default/alternative listener is a service that runs on the database host and receives requests from Oracle clients.                                            |
| Ingres Lock                                               | `ingreslock` | `1524`           | Ingres database is commonly used for large commercial applications and as a backdoor that can execute commands remotely via RPC.                                                   |
| Squid Web Proxy                                           | `http-proxy` | `3128`           | Squid web proxy is a caching and forwarding HTTP web proxy used to speed up a web server by caching repeated requests.                                                             |
| Secure Copy Protocol                                      | `SCP`        | `22`             | Securely copy files between systems                                                                                                                                                |
| Session Initiation Protocol                               | `SIP`        | `5060`           | Used for VoIP sessions                                                                                                                                                             |
| Simple Object Access Protocol                             | `SOAP`       | `80`, `443`      | Used for web services                                                                                                                                                              |
| Secure Socket Layer                                       | `SSL`        | `443`            | Securely transfer files                                                                                                                                                            |
| TCP Wrappers                                              | `TCPW`       | `113`            | Used for access control                                                                                                                                                            |
| Internet Security Association and Key Management Protocol | `ISAKMP`     | `500`            | Used for VPN connections                                                                                                                                                           |
| Microsoft SQL Server                                      | `ms-sql-s`   | `1433`           | Used for client connections to the Microsoft SQL Server.                                                                                                                           |
| Kerberized Internet Negotiation of Keys                   | `KINK`       | `892`            | Used for authentication and authorization                                                                                                                                          |
| Open Shortest Path First                                  | `OSPF`       | `89`             | Used for routing                                                                                                                                                                   |
| Point-to-Point Tunneling Protocol                         | `PPTP`       | `1723`           | Is used to create VPNs                                                                                                                                                             |
| Remote Execution                                          | `REXEC`      | `512`            | This protocol is used to execute commands on remote computers and send the output of commands back to the local computer.                                                          |
| Remote Login                                              | `RLOGIN`     | `513`            | This protocol starts an interactive shell session on a remote computer.                                                                                                            |
| X Window System                                           | `X11`        | `6000`           | It is a computer software system and network protocol that provides a graphical user interface (GUI) for networked computers.                                                      |
| Relational Database Management System                     | `DB2`        | `50000`          | RDBMS is designed to store, retrieve and manage data in a structured format for enterprise applications such as financial systems, customer relationship management (CRM) systems. |

 [Time-To-Live](https://en.wikipedia.org/wiki/Time_to_live) (`TTL`) field in the ICMP packet header that limits the packet's lifetime as it travels through the network. It prevents packets from circulating indefinitely on the network in the event of routing loops. Each time a packet passes through a router, the router decrements the `TTL value by 1`. When the TTL value reaches `0`, the router discards the packet and sends an ICMP `Time Exceeded` message back to the sender.


[Voice over Internet Protocol](https://www.fcc.gov/general/voice-over-internet-protocol-voip) (`VoIP`) is a method of transmitting voice and multimedia communications. For example, it allows us to make phone calls using a broadband internet connection instead of a traditional phone line, like Skype, Whatsapp, Google Hangouts, Slack, Zoom, and others.(TCP5060/5061)


WAP:
Communication between devices occurs over RF in the `2.4 GHz` or `5 GHz` bands in a WiFi network. When a device, like a laptop, wants to send data over the network, it first communicates with the [Wireless Access Point](https://en.wikipedia.org/wiki/Wireless_access_point) (`WAP`) to request permission to transmit. The WAP is a central device, like a router, that connects the wireless network to a wired network and controls access to the network. Once the WAP grants permission, the transmitting device sends the data as RF signals, which are received by the wireless adapters of other devices on the network. The data is then converted back into a usable form and passed on to the appropriate application or system.

Must Know while using wireless:

|   |   |
|---|---|
|`MAC address`|A unique identifier for the device's wireless adapter.|
|`SSID`|The network name, also known as the `Service Set Identifier` of the WiFi network.|
|`Supported data rates`|A list of the data rates the device can communicate.|
|`Supported channels`|A list of the `channels` (frequencies) on which the device can communicate.|
|`Supported security protocols`|A list of the security protocols that the device is capable of using, such as `WPA2`/`WPA3`.|

Nevertheless, some packets can get lost, so the so-called `CRC` checksum has been integrated. [Cyclic Redundancy Check](https://en.wikipedia.org/wiki/Cyclic_redundancy_check) (`CRC`) is an error-detection mechanism used in the WEP protocol to protect against data corruption in wireless communications. A CRC value is calculated for each packet transmitted over the wireless network based on the packet's data. It is used to verify the integrity of the data. When the destination device receives the packet, the CRC value is recalculated and compared to the original value. If the values match, the data has been transmitted successfully without any errors. However, if the values do not match, the data has been corrupted and needs to be retransmitted.

So we are using WPA ,`WEP` uses a `40-bit` or `104-bit` key to encrypt data, while `WPA using AES` uses a `128-bit` key.

Conjugation of WEP/WPA is PEAP/LEAP

LEAP uses same key (shared key )for authentication and encryption while peap doesnt use this method

In a wireless network, when a wireless access point (WAP) sends an authentication request to a [Terminal Access Controller Access-Control System Plus](https://www.ciscopress.com/articles/article.asp?p=422947&seqNum=4) (`TACACS+`) server, it is likely that the `entire request packet` will be encrypted to protect the confidentiality and integrity of the request.

 wireless networks' security:
 - Disabling broadcasting
- WiFi Protected Access
- MAC filtering
- Deploying EAP-TLS
Beacon frames is one of the management frames used in 802.11x standard

VPN:
The VPN client and server use these ports to establish and maintain the VPN connection. At the TCP/IP layer, a VPN connection typically uses the [Encapsulating Security Payload](https://www.ibm.com/docs/en/i/7.4?topic=protocols-encapsulating-security-payload) (`ESP`) protocol to encrypt and authenticate the VPN traffic. This allows the VPN client and server to exchange data over the public internet securely.

ACCESS & TRUNK PORTS:
Any port on a `VLAN`-enabled switch must be either an `access port` or a `trunk port`. `Access ports` belong to and can carry the traffic of only one `VLAN` (or in some cases two, with the second being for `voice traffic`); any traffic arriving on an `access port` is assumed to belong to the `VLAN` the port was assigned. On the other hand, `trunk ports` can carry multiple `VLANs` at the same time; `trunk links` connect two `trunk ports` on two switches (or a switch and router) to allow information from multiple `VLANs` to be carried out across switches.


Crytpogaphy key exchange mechanism:
[Elliptic curve Diffie-Hellman](https://medium.com/swlh/understanding-ec-diffie-hellman-9c07be338d4a) (`ECDH`) is a variant of Diffie-Hellman key exchange that uses elliptic curve cryptography to generate the shared secret key.

 `Pre-Shared Key` (`PSK`) is a secret value shared between the two parties involved in the key exchange. This key is used to authenticate the parties and establish a shared secret that encrypts subsequent communication

TCP packets, also known as `segments`, are divided into several sections called headers and payloads.

UDP transfers `datagrams` (small data packets) between two hosts. It is a connectionless protocol, meaning it does `not` need to establish a connection between the sender and the receiver before sending data. Instead, the data is sent directly to the target host without any prior connection.

# Cryptography

#### Symmetric Encryption

Symmetric encryption, also known as secret key encryption, is a method that uses the same key to encrypt and decrypt the data.

Ex:AES,DES

Asymmetric encryption, also known as `public-key encryption`, is a method of encryption that uses two different keys:

- a `public key`
- a `private key`

Ex:RSA,PGP,ECC