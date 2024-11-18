

---

### NETWORK:
A digital telecommunication network for sharing resources between nodes, which are computing devices that use common telecommunication technology. Data transmission between nodes is supported over data links consisting of physical cable media such as twisted pair or fiber optic cables or through Wi-Fi.
- **Note:** Resources can be shared through multiple clients, e.g., file sharing.
- **Early days:** Used floppy disks for sharing 1.44 megabytes.

### CABLES:
- Thicknet
- Thinnet
- Co-axial
- Serial
- Optical
- RJ-45

### DEVICES:
**Wireless Access Point and Hubs:** Do the same process.

#### HUB:
- When a signal is received in one port in a hub, it amplifies to all the ports in the device. (Layer 1)

#### SWITCH:
- When a signal is received in one port in a switch, it sees the MAC-address tables and forwards to that particular port. (Layer 2)

#### BRIDGE:
- Intermediate device between switch and hub. (Layer 2)

#### FIREWALL:
- Restricts or denies traffic using firewall rules.
  - **Note:** In many cases, the firewall is behind the router; in some cases, it is near the ISP.

#### WIRELESS LAN CONTROLLER:
- Manages access points.
  - **Note:** Autonomous systems don't need WLAN controllers; they are preferred only for lightweight access points.

#### NEXT-GEN FIREWALL:
- **IDS:** Protects you by sniffing and warning, and you have to block. (Small dog will bark)
- **IPS:** Blocks malicious traffic from gaining access to your computer. (Large dog will bite)

---

### TCP/IP & OSI:

#### OSI LAYER:
- APPLICATION (Layers 5-7)
- PRESENTATION
- SESSION
- TRANSPORT (Segments)
- NETWORK (Packets)
- DATA LINK (Frames)
- PHYSICAL (Bits)

#### TCP/IP:
- APPLICATION
- TRANSPORT (Segments)
- NETWORK (Packets)
- DATA LINK (Frames)
- PHYSICAL (Bits)

**Ephemeral Port Number:**
- Private Ports: 49152 to 65535
- Linux Kernel Uses: 32768 to 61000
- OS: 1025 to 5000

**Contiguous Network Mask:**
- Only contiguous ones and zeros subnet masks are supported.

---

### SUBNETTING:
![[Pasted image 20240721125637.png]]

![[Pasted image 20240721125715.png]]

**Example:**
- PC: 192.168.10.18/24
- Binary: 11000000.10101000.0001010.00010010/24
- Subnet Mask: 11111111.11111111.1111111.00000000/24

| Address Type     | Binary                                                 |
|------------------|--------------------------------------------------------|
| First IP Address | 11000000.10101000.0001010.00000001                     |
| Last IP Address  | 11000000.10101000.0001010.11111110                     |
| Network Address  | 11000000.10101000.0001010.00000000                     |
| Broadcast Address| 11000000.10101000.0001010.11111111                     |

**Method:**
- 128, 64, 32, 16, 8, 4, 2, 1
- Subtract the value from the first row:
  - 256-128=128
  - 256-64=192

**Example 1:**
- 172.16.35.123 255.255.240.0
- 256-240=16, so the network will be incremented by 16
  - 172.16.35.16
  - 172.16.35.32
  - 172.16.35.48

**Step-by-Step Subnetting:**
1. Convert the IP address and subnet mask to binary.
2. Determine the subnet increment.
3. Calculate the first, last, network, and broadcast addresses for each subnet.

**Reserved Ranges:**
- RFC 1918: 10.0.0.0 to 10.255.255.255
- Localhost: 127.0.0.0 to 127.255.255.255
- RFC 1918: 172.16.0.0 to 172.31.255.255
- RFC 1918: 192.168.0.0 to 192.168.255.255

**Verification:**
- Example: PC-1: 10.1.248.1/20, PC-2: 10.1.192.2/20
- Convert to binary and compare network portions.

**Lab 1 (Subnetting):**
- IP: 192.168.1.64/26
- Host Calculation: 2^n - 2
- Subnet incremented by 16 values.

**Wildcard Mask Calculation:**
- Subnet mask - 1

**Subnet Creation Example:**
- Given IP: 192.168.1.64/26
- Subnet mask: 255.255.255.192

| Subnet    | First IP        | Last IP         | Network Address | Broadcast Address |
|-----------|------------------|-----------------|-----------------|-------------------|
| Subnet 1  | 192.168.1.1      | 192.168.1.62    | 192.168.1.0     | 192.168.1.63      |
| Subnet 2  | 192.168.1.65     | 192.168.1.126   | 192.168.1.64    | 192.168.1.127     |
| Subnet 3  | 192.168.1.129    | 192.168.1.190   | 192.168.1.128   | 192.168.1.191     |
| Subnet 4  | 192.168.1.193    | 192.168.1.254   | 192.168.1.192   | 192.168.1.255     |

---

### COMMUNICATION TYPES:

**Unicast:** One to one  
**Broadcast:** One to many  
**Multicast:** Many to one if the device accepts/subscribed  

- In IPv4, Broadcast is supported whereas in IPv6, it is not supported, providing a more scalable and robust environment.

---

### ETHERNET:

- **Born:** 1970s
- **Types:**
  - 10BASE5 (Thicknet, 500 meters)
  - 10BASE2 (Thinnet, 100 meters)

**Ethernet uses baseband signals, Co-axial cable uses broadband signals.**

**MAC-address:**
- 48 bits
  - 24 bits for Organizational identifier
  - 24 bits for Station address (vendor assigned station address)

#### CSMA/CD:
- Hubs operate in this manner.
- **CS:** It senses any signal is receiving.
- **MA:** Multiple access.
- **CD:** Carrier sense multiple access collision domain. It checks whether a device is communicating or not.

**Types of Cables:**
- **LAN uses Copper Straight Through Cable:**
  - PC to Switch
  - PC to Hub
  - PC to Bridge

**Cross Over Cable:**
- Used for PC to PC (same device).

**Copper Cross Over Cable:**
- Can be used for copper/fiber cabling transceiver (15 meters).

**Roll-over Cables:**
- Used for connecting console ports.

**Switches:**
- Hubs replaced by bridges, and bridges replaced by switches due to modern devices being more advanced and fast.
- **Switches use ASIC** (Application Specific Integrated Circuit) for high throughput and quick table updates, processing in hardware whereas bridges use software to process.
- **Bridges:** Limited ports.
- **Switches:** No limit.
- **Switches using full duplex:** Collision will be disabled; it uses CSMA/CD.

**Router:**
- Throughput is the rate of message over a communication channel.
- **Auto-Negotiation:** Feature allowing two different speed networks to communicate by adjusting to a suitable speed.
- **Late Collision:** Occurs when a large amount of traffic is sent through the half-duplex mode; use auto for duplex and speed.

**Loopback Interface:**
- Virtual interface in a device.
- Can create more but IP and subnet will be like this: /32 mask.
- **Advantage:** Interface doesn’t go down unless manually shut down, avoiding wasting IP addresses. If idle, interface goes down; telnet loopback interface to access the terminal, but routing protocol must be configured.

---

### TCP DETAILS:

**Flags in TCP:**
- **Congestion Window Reduced Flag**
- **Echo Congestion Notification**
- **Urgent Flag:** Set to be urgent if processed, ACK will be used for ACK of data.
- **Push:** Sender sends to receiver immediately to the application socket.
- **Reset:** To reset the connection.
- **SYN:** Synchronize the sequence number.
- **Windowing:** Method for controlling sending data packets between two network devices where dependable and sequential delivery of data packets is needed.

---

### VLANs & TRUNKING:

- **Trunking:** Allows multiple VLANs to traverse a single link.
- **802.1Q:** Used as encapsulation in trunking mode between switches.
  - **Voice VLAN (Tagged Frames):** IP phones.
  - **Native VLAN (Untagged Frames):** Frames in the native VLAN do not carry VLAN tags.

**

Access Ports:**
- Port configured for a specific VLAN and carries traffic for only that VLAN.

**Trunk Ports:**
- Port used to carry traffic for multiple VLANs, connecting switches to each other or to other network devices.

**Dynamic Trunking Protocol (DTP):**
- Protocol that negotiates trunking on a link between two devices.

**802.1X:**
- Network access control protocol for secure authentication.

---

### BPDU GUARD:
BPDU-Bridge protocol Data Unit

- **BPDU Guard:** Protects the switch ports from receiving any bridge protocol data units (BPDUs) from connected devices.
- **When to Use:** When connecting end devices to the switch ports to prevent them from participating in STP (Spanning Tree Protocol).

---

### SWITCHPORT CONFIGURATION:

**Steps:**
1. Configure the port mode:
   ```shell
   switchport mode access
   ```
2. Assign the VLAN:
   ```shell
   switchport access vlan <VLAN_ID>
   ```
3. Enable BPDU Guard:
   ```shell
   spanning-tree bpduguard enable
   ```

**Example Configuration:**
- **Interface GigabitEthernet0/1:**
  ```shell
  interface GigabitEthernet0/1
    switchport mode access
    switchport access vlan 10
    spanning-tree bpduguard enable
  ```

**Trunk Port Configuration:**
1. Set the port mode:
   ```shell
   switchport mode trunk
   ```
2. Specify allowed VLANs:
   ```shell
   switchport trunk allowed vlan <VLAN_IDs>
   ```

**Example Configuration:**
- **Interface GigabitEthernet0/2:**
  ```shell
  interface GigabitEthernet0/2
    switchport mode trunk
    switchport trunk allowed vlan 10, 20, 30
  ```

---

# TROUBLESHOOTING SCENARIO:
![[Pasted image 20240726235841.png]]

If the encapsulation is wrong on one side of the port the packet will get failed we should use same encapsulation. After doing if doesn't came make it force shutdown and no shutdown 

use :
```
R1#debug ip icmp ##note the changes
```
 check while pinging it has been using the default gateway 
HDLC is the default encapsulation for Cisco serial interfaces 

cdp and lldp to discover the neighbouring devices in the network
```
S1#conf t
S1#cdp run
s1#lldp run
```
for Multivendor environment we're using lldp

If the port is blocking or in the orange color set it to priority:
```
R1#conf t
R1#spanning-tree <which vlan> priority 0  ## this will make port forwarding
```

priority can be determined by the actually priority + vlan number so it can be act as a root

![[Pasted image 20240727122100.png]]

While viewing the spanning tree if any of the port has been blocking  make it etherchannel
![[Pasted image 20240727131501.png]]

|Aspect|Physical Interface|Logical Port Channel|
|---|---|---|
|Nature|Hardware-based, tangible|Virtual, combines multiple physical interfaces|
|Example|GigabitEthernet0/1|Port-channel1|
|Functionality|Single connection point|Aggregates bandwidth, increases redundancy|
|Use Case|Direct device connections|Link aggregation, load balancing|
while configuring etherchannel we should know about the Link aggregation protocol and port aggregation protocol
![[Pasted image 20240727132135.png]]
# Routing protocol

Distance vector routing protocol -RIP
Link state routing protocol-OSPF

Routed Protocol : 
- IPv4,IPv6
- Carry user information
- Choose the decision independently in determining the path
Routing Protocols:
- EIGRP(Best path- Bandwidth and delay)
- OSPF(Best path-Bandwidth)
- RIP(Best path-Hop count)
- ISIS
- BGP
- Communication information about the networks
- Determine best route between networks

Static Routes:
- RIP (updates every 30 sec) we can set administrately


dhcp helper command used to forward the request to the router 
	where to use the helper address if the router or switch is not forwarding the traffic we may set the ip helper address which service we are accessing

option 125 check for RFC

DNS:
note: RFC 1918 It is a private IP address and non routable on the internet 
client uses a random port number/familiar port number

VLSM

CIDR or Classless Inter-Domain Routing was introduced in 1993
to replace the prior addressing architecture of classful networks.
classful networks were not scalable
classful networking introduce 3 classes of addresses
for allocation of IP addresses to hosts and networking devices

summarization in variable length subnet mask:
![[Pasted image 20240731214808.png]]
 172.16.64.0/24     10101100.00010000.01000000.00000000

 172.16.127.0/24 - 10101100.00010000.01111111.00000000
  so the summary of above two ip is 172.16.64.0/28
![[Pasted image 20240731215803.png]]
if I am breaking the network using subnet.
after calculating you subnet  is in the range of 4 to 7 means you should consider it as 4
![[Pasted image 20240731220355.png]]
mask should be considered based on the for example if it is in the range of 10.8.0.0/24 and 10.16.0.0/24

00001010.00010000.00000000.00000000
00001010.00010000.00000000.00000000

EIGRP has a administrative distance of 90 
OSPF has an administative distance of 110
RIP has an administrative distance of 120
BGP has an administrative distance of 200
IBGP has an administrative distance of 20

EIGRP is more reliable and lower the adminsitrative distance is routable 

HSRP: # Hot Standby Router Protocol (HSRP)
if we configure this protocol in router if one of our default gateway gone down we re able to access the virtual gateway 


```
Enter configuration commands, one per line. End with CNTL/Z.

Core1(config)#int vlan 10
Core1(config-if)#st
Core1(config-if)#standby 1 ?
ip Enable HSRP and set the virtual IP address
ipv6 Enable HSRP IPv6
preempt Overthrow lower priority Active routers
priority Priority level
timers Hello and hold timers
track Priority Tracking

Core1(config-if)#standby 1 ip ?

A.B.C.D Virtual IP address

<cr>
Core1(config-if)#standby 1 ip 10.1.10.254
Core1(config-if)#st
Core1(config-if)#standby h
Core1(config-if)#standby ?
<0-4095> group number
ip Enable HSRP and set the virtual IP address
ipv6 Enable HSRP IPv6
preempt Overthrow lower priority Active routers
priority Priority level
timers Hello and hold timers
track Priority Tracking
version HSRP versio
Core1(config-if)#
%HSRP-6-STATECHANGE: Vlan10 Grp 1 state Speak -> Standby
%HSRP-6-STATECHANGE: Vlan10 Grp 1 state Standby -> Active
Core1(config-if)#
```

the higher the priority will make the HSRP more reliable
```
Core1(config-if)#standby 1 priority 200
Core1(config-if)#standby 1 preempt ## allow the switch force to become the hsrp

```
do the same side if you have 2 core switches

SNMP:
QUERY BASED AND NETWORK BASED PROTOCOL

Query based:
relaible
takes 5 min


event based:
 it shows immediatly when a network or interface goes down
 Not relaible 

Affect network reachability:
ACL
FIREWALL RULE/POLICIES
SNMP/ICMP

Network management protocols are the key product of solar winds product
performance monitoring:
ICMP/PING
SNMP
WMI


CIRCUIT SWITCHED NETWORK & PACKET SWITCHED NETWORK:

Circuit switched:
It creates a physical way to establish a connection like continous connection made through lanline
Dail up internet connection via dail up

Packet switched:
Breaks the packet and reaches the destination path correctly and it is connection less network
voip,lan,wan,internet 


MIB & OID 
Complete tool for monitoring SNMP enabled device and servers
object identifier-included with MIB and used for polling a specific interface

RFC-Request for comments:

The RFC series has two subseries,:
STDs and BCPs.
STDs are 'Internet Standard' RFCs, 
BCPs are RFCs that describe 'Best Current Practices' for the Internet, some of which are administrative processes for the IETF.

Internet Engineering Task Force:
The Internet Engineering Task Force (IETF) is a [standards organization](https://www.bing.com/search?q=Standards%20organization%20wikipedia&form=WIKIRE) for the [Internet](https://www.bing.com/search?q=Internet%20standard%20wikipedia&form=WIKIRE) and is responsible for the [technical standards](https://www.bing.com/search?q=Technical%20standard%20wikipedia&form=WIKIRE) that make up the [Internet protocol suite](https://www.bing.com/search?q=Internet%20protocol%20suite%20wikipedia&form=WIKIRE) (TCP/IP). It has no formal membership roster or requirements and all its participants are volunteers


# subnetting
![[Pasted image 20240721125637.png]]
![[Pasted image 20240721125715.png]]
![[Pasted image 20240721131525.png]]![[Pasted image 20240721131525.png]]
![[Pasted image 20240721201549.png]]
