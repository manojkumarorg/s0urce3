# FTP
To begin an FTP session, control connection requests are sent to the server using destination TCP port 21. 
When the session is opened, the server uses TCP port 20 to transfer the data files.

SMB protocol is used  for accessing files on a remote host

Universal Naming Convention (UNC) format is used to connect to resources

```
∖∖servername∖sharename∖file
```
servername- server that is hosting the resource
sharename-root of the folder in the filesystem

 Each disk volume has an administrative share, represented by the volume letter and the $ 
 such as C$ 
 points :
- In FTP, passive mode (PASV) is a data connection mode used during file transfers.
- When a client initiates a passive connection, it sends the `PASV` command to the server, requesting a port number to connect to.
- The server responds with a port, and the client establishes a second connection to that port for data transfer.



# HTTP/HTTPS


- **Protocol/scheme** - HTTPS or other protocols such as FTP, SFTP, mailto, and NNTP
- **Hostname** - w​ww.example.com
- **Path and file name** - /author/book.html
- **Fragment** 155
![[Pasted image 20240510200908.png]]

# OSPF 

It follows the path which is know as shortest path
OSPF is a link-state routing protocol that uses the ==Dijkstra algorithm== to calculate the shortest path first (SPF).

- **Open Shortest Path First (OSPF)** is a classless routing protocol that supports VLSMs.

VLSM:
**Variable Length Subnet Mask (VLSM)** is a technique used in IP networking to allocate IP addresses more efficiently.

in most of the cases while connecting two router have a serial port if not there we have to manually add  WIC-2T(Wan interface card) port so that it can connect two devices.


Use copper cross over to connect router and pc if your are connecting directly.

wildcard mask is the mask in which path is available for examination.
It indicates the size of the network.

![[Pasted image 20240603184237.png]]  

Configuring router int:

For ethernet:

```
Router1> enable
Router1# configure terminal
Router1(config)# interface GigabitEthernet0/0
Router1(config-if)# ip address 192.168.1.1 255.255.255.0
Router1(config-if)# no shutdown
Router1(config-if)# exit
Router1(config)# exit
```


```
# For Router2
Router2> enable
Router2# configure terminal
Router2(config)# interface GigabitEthernet0/0
Router2(config-if)# ip address 192.168.1.2 255.255.255.0
Router2(config-if)# no shutdown
Router2(config-if)# exit
Router2(config)# exit
```

For Serial:

```
# For Router1
Router1> enable
Router1# configure terminal
Router1(config)# interface Serial0/0
Router1(config-if)# ip address 10.0.0.1 255.255.255.252
Router1(config-if)# clock rate 64000  # Only needed on the DCE side
Router1(config-if)# no shutdown
Router1(config-if)# exit
Router1(config)# exit
```

```
# For Router2
Router2> enable
Router2# configure terminal
Router2(config)# interface Serial0/0
Router2(config-if)# ip address 10.0.0.2 255.255.255.252
Router2(config-if)# no shutdown
Router2(config-if)# exit
Router2(config)# exit

```

Configuring OSPF :

For Router 1:
```
Router1> enable
Router1# configure terminal
Router1(config)# router ospf 1
Router1(config-router)# router-id 1.1.1.1
Router1(config-router)# network 192.168.1.0 0.0.0.255 area 0
Router1(config-router)# network 10.0.0.0 0.0.0.3 area 0
Router1(config-router)# exit
Router1(config)# exit

```

For Router 2:
```
Router2> enable
Router2# configure terminal
Router2(config)# router ospf 1
Router2(config-router)# router-id 2.2.2.2
Router2(config-router)# network 192.168.1.0 0.0.0.255 area 0
Router2(config-router)# network 10.0.0.0 0.0.0.3 area 0
Router2(config-router)# exit
Router2(config)# exit

```

You can verify by adding a simple PDU to the network it will show the status of the network sucessfull or failed.




# BGP(Broaded Gateway protocol):

![[Pasted image 20240605183527.png]]


1. **Enable BGP**:
     [Execute the command `router bgp <AS_number>` to enter BGP configuration mode and specify the Autonomous System (AS) number](https://www.packettracernetwork.com/tutorials/bgp.html)[1](https://www.packettracernetwork.com/tutorials/bgp.html)[2](https://ccnatutorials.in/packet-tracer/bgp-implementation-in-packet-tracer/).
configuring in CLI:

Router R1:
```
Router(config-if)#
Router(config-if)#exit
Router(config)#interface Serial0/0
Router(config-if)#clock rate 64000
Router(config-if)#ip address 192.168.2.1 255.255.255.0
Router(config-if)#
Router(config-if)#exit
Router(config)#router bgp 100
Router(config-router)#network 192.168.1.0
Router(config-router)#network 192.168.2.0
Router(config-router)#neighbor 192.168.2.2 remote 200
Router(config-router)#neighbor 192.168.2.2 remote-as 200
Router(config-router)#neighbor 192.168.3.2 remote-as 200
Router(config-router)#exit
Router(config)#
```

Router R2:
```
Router(config-if)#exit
Router(config)#router bgp 200
Router(config-router)#network 192.168.2.0
Router(config-router)#network 192.168.3.0
Router(config-router)#neighbor 192.168.2.1 remote-as 100
Router(config-router)#%BGP-5-ADJCHANGE: neighbor 192.168.2.1 Up
neighbor 192.168.2.1 remote-as 100
Router(config-router)#neighbor 192.168.2.4 remote-as 100
Router(config-router)#exit
```

By connecting the end devices use a simple PDU :
![[Pasted image 20240605184253.png]]


# SMTP / IMAP
 
 SMTP is a protocol designed to transfer electronic mail reliably and efficiently.

SMTP is a push protocol and is used to send the email, whereas POP and IMAP are used to retrieve emails on the end user's side. SMTP transfers emails between systems, and notifies on incoming emails. 

Using SMTP, a client can transfer an email to another client on the same network or another network through a relay or gateway access available to both networks.

# SNMP

Monitoring  router performance with SNMP:

 SNMP on a router in Packet Tracer and use SNMP management software to monitor router performance metrics such as CPU utilization, memory usage, and interface status.
 
# TCP/IP (4,6)


Certainly! I'll present the information in a tabular format for clarity and neatness.

---

## Network Communication

| Communication Type | Source IP       | Destination IP       | Description             |
|--------------------|-----------------|----------------------|-------------------------|
| TCP                | <my-ipaddress>  | <youtube-ipaddress>  | Sends the video         |
| UDP                | <my-ipaddress>  | <youtube-ipaddress>  | Sends an HTML file      |

---

## Network Address Translation (NAT)

| Function                          |
|-----------------------------------|
| Translates private IP addresses into public IP addresses for routing traffic. |

---

## IP Address Ranges

| Type                | Range                                    |
|---------------------|------------------------------------------|
| Private IP          | 10.0.0.0 - 10.255.255.255                |
|                     | 172.16.0.0 - 172.31.255.255              |
|                     | 192.168.0.0 - 192.168.255.255            |
| Link-Local Addresses| 169.254.0.0 /16 or 169.254.0.1 to 169.254.255.254 (APIPA addresses) |
| IPv4 Unicast Host   | 1.1.1.1 to 223.255.255.255               |

---

## IP Address Classes

| Class    | Range                        | Number of Host Addresses |
|----------|------------------------------|--------------------------|
| Class A  | 0.0.0.0/8 to 127.0.0.0/8     | 16 million               |
| Class B  | 128.0.0.0 /16 - 191.255.0.0 /16 | 65,000                |
| Class C  | 192.0.0.0 /24 - 223.255.255.0 /24 | 245                |

---

## IPv6 Address Simplification Rules

| Rule                                        | Description                                              |
|---------------------------------------------|----------------------------------------------------------|
| Omit Leading Zeros                          | e.g., 01AB -> 1AB                                        |
| Double Colon (::)                           | Can replace any single, contiguous string of one or more 16-bit hextets consisting of all zeros |

---

## TCP and UDP Protocols

| Protocol | Characteristics                                                | Common Applications               |
|----------|-----------------------------------------------------------------|-----------------------------------|
| TCP      | Acknowledges receipt of packets                                 | FTP, HTTP, SMTP, DNS, SSH         |
| UDP      | No acknowledgement, no sequence number                          | DNS, TFTP                         |

### Common Port Numbers

| Port Number | Transport | Application Protocol |
|-------------|-----------|----------------------|
| 20          | TCP       | FTP (data)           |
| 21          | TCP       | FTP (control)        |
| 22          | TCP       | SSH                  |
| 23          | TCP       | TELNET               |
| 25          | TCP       | SMTP                 |
| 53          | UDP/TCP   | DNS                  |
| 67          | UDP       | DHCP (SERVER)        |
| 68          | UDP       | DHCP (CLIENT)        |
| 69          | UDP       | TFTP                 |
| 80          | TCP       | HTTP                 |
| 110         | TCP       | POP3                 |
| 143         | TCP       | IMAP                 |
| 161         | UDP       | SNMP                 |
| 443         | TCP       | HTTPS                |

### Port Range Categories

| Range          | Description                          |
|----------------|--------------------------------------|
| 1-1023         | Well-known ports (often destination) |
| 1024-49151     | Registered ports (source/destination)|
| 49152-65535    | Private ports (often source)         |

---

## Network Address Calculation

| Calculation Type         | Description                                            | Value                                 |
|--------------------------|--------------------------------------------------------|---------------------------------------|
| Network Address          | 192.168.2.38/24 (255.255.255.0)                        | 192.168.2.0/24                        |
| Broadcast Address        | Replace host portion with 1s                           | 192.168.2.255                         |
| First Usable Address     | First host in binary, with 1 at end of host portion    | 192.168.2.1                           |
| Last Usable Address      | Last host in binary, with 1 at end of host portion     | 192.168.2.254                         |

### Binary Calculations

| Step                | Value                                                      |
|---------------------|------------------------------------------------------------|
| IP Address (Binary) | 11000000.10101000.00000010.00100110                        |
| Subnet Mask (Binary)| 11111111.11111111.11111111.00000000                        |
| Network Address     | 11000000.10101000.00000010.00000000 (192.168.2.0/24)       |
| Broadcast Address   | 11000000.10101000.00000010.11111111 (192.168.2.255)        |
| First Usable Host   | 11000000.10101000.00000010.00000001 (192.168.2.1)          |
| Last Usable Host    | 11000000.10101000.00000010.11111110 (192.168.2.254)        |

---

## Hosts Calculation Formula

| Description                  | Calculation                      |
|------------------------------|----------------------------------|
| Number of Usable Hosts       | \(2^h - 2\)                      |
| Example (192.168.0.1 /24)    | Network bits: 24                 |
|                              | Host bits: 32 - 24 = 8           |
|                              | \(2^8 - 2 = 256 - 2 = 254\)      |
|                              | Usable Hosts: 254                |

---

# TELNET
Telnet is an application layer protocol that enables a user to communicate with a remote device. A Telnet client is installed on the user's machine, which accesses the command line interface of another remote machine that runs a Telnet server program
