2-PC's and 2 SWITCH (3650-24PS)(L3)



LABS:
![[Pasted image 20240615233217.png]]

user privileged mode

```
enable
```

Global configuration mode:

```
Configure terminal
```

```
show ip int brief
```

Configuring VLAN in multilayer switch:
 ```
 int vlan1
 no shutdown
 ip address <ip> <subnetmask> 
 end
```

![[Pasted image 20240615233147.png]]


On a layer 2 switch if you configure a SVI -Allows you to configure the switch

If we change the mac-address the switch will auto-update the table and ping succeed

Why we need default gateway :Loopback interface
Loopback interface is a used to create a imaginary network for each subnet.
Router(config)#interface ?

Dialer Dialer interface
Dot11Radio Dot11 interface
Ethernet IEEE 802.3
FastEthernet FastEthernet IEEE 802.3
GigabitEthernet GigabitEthernet IEEE 802.3z
==Loopback Loopback interface==
Port-channel Ethernet Channel of interfaces
Serial Serial
Tunnel Tunnel interface
Virtual-Template Virtual Template interface
Vlan Catalyst Vlans
range interface range command
Router(config)#interface interface loopback

For example :
we can set a virtual interface in my router using this command
```
int loop 1
ip address 192.168.100.254 255.255.255.0
```
![[Pasted image 20240616003838.png]]
by configuring the switch for the default gateway it can ping over the loopback interface
the ping succeed.


VIRTUAL CONFIGURING IN SWITCH(TELNET) USING COSOLE:
```
line vty 0 4 # upto 5 users can get connect(vty is virtual terminal of switch)
password cisco
login
```
After entering this you will be accessed only the user execution mode ,if you want to set the password for previliged exact mode do this.....
```
enable password cisco
```

![[Pasted image 20240616011720.png]]
same do this for router to access the same methodology

if i want to put password for my console port for my Router:
```
en
conf t
line console 0
login
password cisco
exit
copy running-config startup-config
```
\
LIFE OF A PACKET:

While pinging two packets are generated ARP,ICMP 
the reason behind arp packet is one pc subnet  is communicating with other subnet and other device to the local pc.
The switch does not change the mac-address it does switching the process

![[Pasted image 20240622004139.png]]

HDLC-High level data link control(some of the encapsulation is used in serial link)
In this concept it does'nt use the source and mac-address but it only have source and destination IP address.

ETHERNET 2  is most common encapsulation used.

When PC1 pings to PC2 the destination mac address will be the router address(bia)

What encapsulation is used in this process is "ETHERNET 2 Header"
 In serial link what will be the destination mac-address?
 ans: No mac-address
 
Q/A:
PC1 pings PC2. Answer the following questions based on the echo request message sent from PC1 to PC2.
1) What is the destination MAC address in the frame at A in the network?
a) PC1's MAC address
b) PC2's MAC address
c) Switch1's G1/0/1 MAC address
d) Switch2's G1/0/2 MAC address
e) Router1's G0/0/0 MAC address
f) Router1's Se0/1/0 MAC address
g) Router2's G0/0/0 MAC address
h) Router2's Se0/1/0 MAC address
i) Switch2's G1/0/1 MAC address
j) Switch 2's G0/0/0 MAC address
k) There is no MAC address
  
Your Answer: Router1's G0/0/0 MAC address

2) What is the destination MAC address at A in the network?
Your Answer: 0010.aaaa.aaaa
3) What encapsulation is used at A in the network?
Your Answer: Ethernet header 2

4) What is the destination MAC address in the frame at B in the network?
a) PC1's MAC address
b) PC2's MAC address
c) Switch1's G1/0/1 MAC address
d) Switch2's G1/0/2 MAC address
e) Router1's G0/0/0 MAC address
f) Router1's Se0/1/0 MAC address
g) Router2's G0/0/0 MAC address
h) Router2's Se0/1/0 MAC address
i) Switch2's G1/0/1 MAC address
j) Switch 2's G0/0/0 MAC address
k) There is no MAC address

Your Answer: Router1's G0/0/0 MAC address

5) What is the destination MAC address at B in the network?
Your Answer: 0010.aaaa.aaaa

6) What is the destination MAC address in the frame at C in the network?
a) PC1's MAC address
b) PC2's MAC address
c) Switch1's G1/0/1 MAC address
d) Switch2's G1/0/2 MAC address
e) Router1's G0/0/0 MAC address
f) Router1's Se0/1/0 MAC address
g) Router2's G0/0/0 MAC address
h) Router2's Se0/1/0 MAC addres
i) Switch2's G1/0/1 MAC address
j) Switch 2's G0/0/0 MAC address
k) There is no MAC address

7) What encapsulation is used at C in the network?
Your Answer: There is no MAC address

8) What is the destination MAC address in the frame at D in the network?
a) PC1's MAC address
b) PC2's MAC address
c) Switch1's G1/0/1 MAC address
d) Switch2's G1/0/2 MAC address
e) Router1's G0/0/0 MAC address
f) Router1's Se0/1/0 MAC address
g) Router2's G0/0/0 MAC address
h) Router2's Se0/1/0 MAC address
i) Switch2's G1/0/1 MAC address
j) Switch 2's G0/0/0 MAC address
k) There is no MAC address

Your Answer: PC2's MAC address

9) What is the destination MAC address at D in the network?
Your Answer: 0010.2222.2222

10) What encapsulation is used at D in the network?
Your Answer: Ethernet header 2

11) What is the destination MAC address in the frame at E in the network?
a) PC1's MAC address
b) PC2's MAC address
c) Switch1's G1/0/1 MAC address
d) Switch2's G1/0/2 MAC address
e) Router1's G0/0/0 MAC address
f) Router1's Se0/1/0 MAC address
g) Router2's G0/0/0 MAC address
h) Router2's Se0/1/0 MAC address
i) Switch2's G1/0/1 MAC address
j) Switch 2's G0/0/0 MAC address
k) There is no MAC address

Your Answer: PC2's MAC address

12) What is the destination MAC address at E in the network?
Your Answer: 0010.2222.2222

13) What encapsulation is used at E in the network?
Your Answer: Ethernet header 2

SUBNETTING:

Dividing the larger network into small subnetwork

For example we have an IP address of 192.168.1.0/24
For network portion we have the formula 2^n
For host 2^n-2
for host why we are using -2(i.e one for network and one for broadcast)
We are host for 2 networks so we use the formula 2^n
Task:1 subnet the IP address into two networks 192.168.1.0/24

Subentting for one network

![[Pasted image 20240629225558.png]]
For next network we should add one to it we can get the other subnet:
![[Pasted image 20240629230543.png]]

for OSPF we should give me ip address for dhcp pool we should give the network ip
if we are setting dhcp pool with an excluded range of ip address we would allocate  a lease time so that he can access ![[Pasted image 20240731003843.png]]
![[Pasted image 20240731003919.png]]

LAB2:
Routing protocol is created to communicate between one router to other router.
![[Pasted image 20240630232331.png]]

subnet this network into 3 networks
192.168.1.0/24
N.N.N.H
breaking the host portion into binaries :
192.168.1.00000000
if we need to steal network we have to go from left to right from the binary 
if we need to steal host we have to go from right to left from the binary
formula:2^n
so we have to subnet for 3 so use 2^2=4 it gives one additional subnet so we are going to break the additional subnet by by taking 2 host from the binary side.
 ==N|S|H==
192.168.1.|00|000000=192.168.1.0/26 (1st subnet)
192.168.1.|01|000000=192.168.1.64/26(2nd subnet)
192.168.1.|10|000000=192.168.1.128/26(3rd subnet)
192.168.1.|11|000000=192.168.1.192/26(optional if they ask 4 you can use this)
![[Pasted image 20240630232900.png]]
Vlan1-is the layer three interface to configure the switch
multilayer switch ip address will be one less than the router ip
(i.e) If my network is 192.168.1.0/26 
subnet : 192.168.1.192
First ip :192.168.1.1/26
last ip:192.168.1.62/26
broadcast :192.168.1.63/26
default gateway :192.168.1.63 is configured on PC,Layer3 switch to cross communicate

configuring between two routers:
![[Pasted image 20240630235131.png]]
2nd router:
![[Pasted image 20240630235041.png]]


for router 2 we have use the 2nd ip address of the subnet mask 
![[Pasted image 20240701002723.png]]
 after configuring OSPF between the router i can ping each other across the subnet
 For router 2:
 ![[Pasted image 20240701230017.png]]
 ```
Router2> enable
Router2# configure terminal
Router2(config)# router ospf 1
Router2(config-router)# network 192.168.1.64 0.0.0.63 area 0
Router2(config-router)# network 192.168.1.128 0.0.0.63 area 0
Router2(config-router)# exit
Router2(config)# exit
Router2#
```
 
 
 
 For router 1:
 ![[Pasted image 20240701230116.png]]
 ```
Router1> enable
Router1# configure terminal
Router1(config)# router ospf 1
Router1(config-router)# network 192.168.1.0 0.0.0.63 area 0
Router1(config-router)# network 192.168.1.64 0.0.0.63 area 0
Router1(config-router)# exit
Router1(config)# exit
Router1#
```
 Tracert router explained:
![[Pasted image 20240701230601.png]]
From PC2(192.168.1.129) To PC1(192.168.1.1)
It shows the hops(i.e across how many router are connected across these networks)

In different subnet are the router can able to ping each other you can use the command
```
debug ip packet
```
To turn off the debugging we can use 
```
un all
```
NOTE: Don't use in the real time because it will down all the network traffic which are going 
across the network.
In order to troubleshoot we can change subnet on both the side
for example:
R1=10.1.1.1/24
R2=10.1.2.2/24

we can change the subnet by making it as /16 so that they are in same subnet can ping each other

LAB3: 
Configuring DHCP in router
1.Excluded address range 10.1.1.1 to 10.1.1.100
2.pool name PC
3.Network 10.1.1.0/24
4.Default-gateway =router1
5.DNS server= router1
6.Test the pc can ping loopback of router 1
![[Pasted image 20240702000711.png]]
same setup configuration for router and multilayer switch and PC
```
R1#sh run | include dhcp
```
Output the running DHCP in the network
![[Pasted image 20240702001407.png]]
by using this command i have created a loopback in my router which is one virtual interface in my router 
```
int loop 1
ip address 1.1.1.1 255.255.255.0
```

Loopback ping succeeded
![[Pasted image 20240702001646.png]]

![[Pasted image 20240702004956.png]]

![[Pasted image 20240702005041.png]]
while debugging is on 
![[Pasted image 20240702005328.png]]

LAB 3 continuing with more complex:

Creating vlan 10 and 20 to turn these up 
![[Pasted image 20240702144812.png]]
To configure routing protocol or use static routes to allocate the ip address for PC's

static routes in router:
![[Pasted image 20240702161317.png]]

enabling cdp in layer 3 switch :
![[Pasted image 20240702161353.png]]


static routes configured so that the router can ping each other from anyside of the interface
![[Pasted image 20240702233147.png]]


LAB 4: Router on a stick or Inter vlan routing
VLAN1=10.1.1.0/24 ,VLAN10=10.1.10.0/24 ,VLAN20=10.1.20.0/24
Router=last ip address in the subnet
Switch=10.1.1.253/24 only
configure vlan on switch (PC1 in VLAN10 and PC2 in VLAN20)
configure between the router and switch
make sure pc1 ping pc2(PC1=10.1.10.1 AND PC2=10.1.20.1)


Solution:
router can do the intervlan routing neither a switch cannot do
making one as native and other not native 
![[Pasted image 20240703150357.png]]


status of intervlan assigning:
![[Pasted image 20240703145423.png]]
```
sh cdp neighbour
```
this command will show whether all these things are configures correctly.

making trunk port between the router int and switch int
![[Pasted image 20240703152330.png]]

result for vlan10 pc
![[Pasted image 20240703152652.png]]
On PC2:
![[Pasted image 20240703152933.png]]
we can't ping the switch because it is layer 2 we should set the default gateway on the switch to ping
![[Pasted image 20240703153154.png]]

In multilayer switch when routing is enabled the default gateway will be ignored by the switch while pinging
![[Pasted image 20240703153429.png]]

enabling no routing in switch:
![[Pasted image 20240703153552.png]]
```
### 1. Create VLANs and Assign Names

plaintext
Switch> enable
Switch# configure terminal

# Create VLAN 10 and name it
Switch(config)# vlan 10
Switch(config-vlan)# name Sales
Switch(config-vlan)# exit

# Create VLAN 20 and name it
Switch(config)# vlan 20
Switch(config-vlan)# name Marketing
Switch(config-vlan)# exit

#### 2. Assign IP Addresses to VLAN Interfaces

plaintext
# Configure VLAN 10 interface
Switch(config)# interface vlan 10
Switch(config-if)# ip address 101.10.1.1 255.255.255.0
Switch(config-if)# no shutdown
Switch(config-if)# exit

# Configure VLAN 20 interface
Switch(config)# interface vlan 20
Switch(config-if)# ip address 10.1.20.1 255.255.255.0
Switch(config-if)# no shutdown
Switch(config-if)# exit

## 3. Assign Physical Interfaces to VLANs and Ensure They Are Up

plaintext
# Assign interface GigabitEthernet1/0/1 to VLAN 10
Switch(config)# interface GigabitEthernet1/0/1
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 10
Switch(config-if)# no shutdown
Switch(config-if)# exit

# Assign interface GigabitEthernet1/0/2 to VLAN 20
Switch(config)# interface GigabitEthernet1/0/2
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 20
Switch(config-if)# no shutdown
Switch(config-if)# exit

```

Difference between the layer3 switch and hub:
![[20240703-1343-47.7444945.mp4]]Collision domain and broadcast domain:(HUB)
![[Screen Recording 2024-07-03 194219.mp4]]
Collision Domain and broadcast domain(LAYER 3 switch):
![[20240703-1437-02.4268732.mp4]]
Here no collision occurs but the device buffers to send it later.
In exam pov there is 4 collision domain because if we set pc to use half-duplex after setting this we have collsion so it drops the frame.
![[20240703-1448-24.8180658.mp4]]

LAB 4:
BASIC CAMPUS NETWORK
ip routing is enabled in layer 3 switch to route between one vlan to other vlan
in layer 3 switch if many vlans are there means we should make it as trunk port and the one vlan which we can make it as access port

MAC address are automatically allocated in the layer 3 switch

![[Pasted image 20240708131130.png]]
- access port – a port that can be assigned to a single VLAN. The frames that arrive on an access port are assumed to be part of the access VLAN.
- trunk port – a port that is connected to another switch. This port type can carry traffic of multiple VLANs, thus allowing you to extend VLANs across your entire network.
If a switch is connected to the other port of the switch while configuring vlan it should be a trunk port .Encapsulation used is dot1q we need not to specify while enabling trunk port in switches.
![[Pasted image 20240710184719.png]]

Assigning IP address to vlan:
![[Pasted image 20240710185540.png]]
 No.of existing vlan is 5 but its operating mode is server we should make it as a client to access vtp in switch
 ![[Pasted image 20240710191837.png]]
 While setting up a vtp core switch should be a server and the access switch should be a client
 when we are adding trunk we should add trh encapsulation dot1Q
```
Switch(config)#do sh vtp st
VTP Version capable : 1 to 2
VTP version running : 1
VTP Domain Name : ccna
VTP Pruning Mode : Disabled
VTP Traps Generation : Disabled
Device ID : 0002.4A72.C900
Configuration last modified by 0.0.0.0 at 3-1-93 00:34:49
Feature VLAN :
--------------
VTP Operating Mode : Client
Maximum VLANs supported locally : 255
Number of existing VLANs : 9
Configuration Revision : 4
MD5 digest : 0xA2 0x1F 0x01 0x52 0x89 0xA8 0x04 0x8B
0x21 0x66 0x25 0x63 0x8B 0x79 0xA9 0xA2
Switch(config)#int f0/1
Switch(config-if)#swi
Switch(config-if)#switchport mode ac
Switch(config-if)#switchport mode access
Switch(config-if)#swit
Switch(config-if)#switchport acc
Switch(config-if)#switchport access vlan 10
Switch(config-if)#
```

Configuring access layer switch with ip address :
![[Pasted image 20240710192616.png]]
other 2 switch :
![[Pasted image 20240710193111.png]]
  Configuration  between the switch and PC :
  ```
S2(config)#int f0/1
S2(config-if)#switchport mode access
S2(config-if)#switchport access vlan 20
S2(config-if)#end
```
result:
![[Pasted image 20240710195401.png]]

Configure VTP:
3 switches
1) Users should be able to add VLANS on S1 and S2 but not S3
2) S2 should not synchronize its vlan database with the other switches
3) VTP domain name CCNA
![[Pasted image 20240710211409.png]]
 from server side i have created a vlan2 but it not visible to other two switches we can make it by
 executing this command
 1)Access the int like which you are able to see int g1/0/1
 ```
 S#conf t
 S#int g1/0/1
 S#switchport mode trunk
 S#end
```
Disabling spanning tree:
![[20240710-1641-14.7844657.mp4]]
Getting MAC-address with the help of IP address using arp protocol
After getting disabled of spanning tree protocol switches broadcast and it make a looping(BROADCAST STORM (2loops)) and repeats and multiplies the same packet in a network(Don't get disable the spanning tree).
![[20240710-1655-36.8468160.mp4]]
cons:
Instability in MAC table
Broadcast strom (network melts)
Big mess.

Why is Spanning tree port fast important?
![[Pasted image 20240710224155.png]]
DHCP server doesn't provide an IP address for PC's so it provides like this 
![[Pasted image 20240710224346.png]]
This is called as link local address Link-local addresses are not guaranteed to be unique beyond their network segment. Therefore, [routers](https://en.wikipedia.org/wiki/Router_(computing) "Router (computing)") do not forward [packets](https://en.wikipedia.org/wiki/Data_packet "Data packet") with link-local source or destination addresses.

[IPv4](https://en.wikipedia.org/wiki/IPv4 "IPv4") link-local unicast addresses are assigned from address block _**169.254**.0.0/16_ (_169.254.0.0_ through _169.254.255.255_).
In [computer networking](https://en.wikipedia.org/wiki/Computer_network "Computer network"), a **link-local address** is a network address that is valid only for communications on a _local [link](https://en.wikipedia.org/wiki/Link_layer "Link layer")_, i.e. within a [subnetwork](https://en.wikipedia.org/wiki/Subnetwork "Subnetwork") that a host is connected to. Link-local addresses are most often [unicast network addresses](https://en.wikipedia.org/wiki/Unicast_network_address "Unicast network address") assigned automatically through a process known as **stateless address autoconfiguration** (**SLAAC**) or **link-local address autoconfiguration**,[[1]](https://en.wikipedia.org/wiki/Link-local_address#cite_note-rfc3927-1) also known as **automatic private IP addressing** (**APIPA**) or **auto-IP**

Spanning tree takes 30s to bootup the network topology so we can make it fast by using spanning tree port fast:
```
S1#conf t
S1#int range g1/0/1 -3
S1#spanning tree port fast
S1#end
```
Caution:
Wants to connect pc and services don't connect with other switches.

LAB5:
Access control list setup:
It is a fundamental way to permit and deny traffic in a network.
Configure ACLs as follows:
  
1) Restrict traffic internally using Router1 as follows:
- Use access list number 100
- Inside PC1 can only access the HTTP server 1 using HTTP on subnet 10.1.1.0/24
- Inside PC2 can only access the HTTP server 2 using HTTPS on subnet 10.1.1.0/24
- No other PCs or servers on subnet 10.1.2.0/24 can access subnet 10.1.1.0/24 (Explicitly add this line. This is normally done to log the traffic with the word log, but PT does not support logging)
- Hosts on subnet 10.1.2.0/24 can access any other network
- Bind access list in the most efficient place on Router
2) Verification:
- Verify that Inside PC1 can access the internal HTTP server 1 using HTTP, but not ping HTTP server 2
- Verify that Inside PC2 can access the internal HTTP server 2 using HTTPS, but not ping HTTP server 1
- Verify that both inside PC1 and PC2 can browse to cisco.com and facebook.com
![[Pasted image 20240711184945.png]]
here we are going to permit the http it does't list it out and it lies above the tcp layer in osi model so we'r going to choose tcp
```
Router1(config)#access-list 100 permit tcp host 10.1.2.101 host 10.1.1.100 eq 80
```
this is the command for permitting to access only http from the server not to going to other network.
```
R1#conf t
R1#access-lists 100 permit tcp host <host_ip> host <destination_ip> eq <port_number> 
R1#exit
R1#sh access-lists
Router1#sh access-lists
Extended IP access list 100
10 permit tcp host 10.1.2.101 host 10.1.1.100 eq www
20 permit tcp host 10.1.2.102 host 10.1.1.101 eq 443
```
 TO deny the service using ACL :
 ``
 ```
 Router1(config)#access-list 100 deny ip 10.1.2.0 0.0.0.255 10.1.1.0 0.0.0.255
```
here we should use the wildcard mask not to use the default-network mask
we have done onething we have given the packet to go anywhere as there the packet doesnt know where to go so it goes anywhere on the internet.

![[Pasted image 20240711191952.png]]
if wanna remove one from the access list we should specify it:
```
R#conf t
R#ip access-list extended 100
R# no 15 ## access list number displayed while viewing
R#end
```
Now were going to bind the address in the router.
```
R#conf t
R#int g0/0/0
R#ip access-group inbound 100
R#end
```
after binding you can see matches in ur router.
![[Pasted image 20240711214251.png]]

hw:
![[Pasted image 20240711223813.png]]

To match the 2 host ip addresses we need a inverse mask:
PC1 =10.1.1.100 bin:0110 0100
PC2 =10.1.1.101 bin:0110 0101
last digit is different we use inverse mask of 0000 0001


![[Screenshot 2024-07-12 181756.png]]
response and return traffic to access the cisco.com from the inside PC:

![[Pasted image 20240712183108.png]]
Here established looks like the acknowledgement traffic in tcp 3 way handshake
![[Pasted image 20240712185952.png]]

results:
![[Pasted image 20240712190234.png]]
```
Router1(config)#access-list 101 permit tcp any 10.1.1.0 0.0.0.255 eq 80
Router1(config)#access-list 101 permit tcp any 10.1.1.0 0.0.0.255 eq 443
```
after doing this outside of my pc can access the internal server http and https

LAB 7:
NAT-Network address translation it translates a private ip address into public ip address
PAT-Port address translation it translates multiple ip address into single ip address.
![[Pasted image 20240712193311.png]]
here we are getting an ip address from the isp to allocate ip address for my router :
```
R1#conf t
R1#ip address dhcp
R1#no shutdown
```

![[Pasted image 20240712193255.png]]
here we have to set an ip address for g0/0/1 int to allocate ip address for clients:
![[Pasted image 20240712193846.png]]
we haven't configured NAT so we cant ping the dns server:
![[Pasted image 20240712194403.png]]
Configuring router on NAT so that the PC can access the internet
```
R1# conf t
R1#int g0/0/0 ##if it is outside
R1#ip nat out
R1#exit
R1#int g0/0/1 ##if it inside
R1#ip nat in
R1#exit
R1#conf t
R1# ip nat inside source list 1 int <outside int> overload ## overload for multiple port forwarding
R1#access-list 1 permit any ## setting these clients can be natted whereas other cant'b
```
after getting this we can ping ,you can verify by ensuring typing this command
```
R1#sh ip nat translation
```
![[Pasted image 20240712212857.png]]
In NAT only the ip address of the clients can be changed whereas the destination remains same
when mulitple port numbers are mapped it shows ![[Pasted image 20240712214105.png]]
LAB 7 part-2:
configuring static NAT:
![[Pasted image 20240712214440.png]]
```
R1#conf t
R1#int g0/0/0 
R1#ip address 10.1.1.254 255.255.255.0
R1#no shutdown
R1#int g0/0/1
R1#ip address 8.8.8.100 255.255.255.0
R1#no shutdown
R1#ip route 0.0.0.0 0.0.0.0 8.8.8.8 ## the default-gateway is going to be isp in your router but in this we are considering google.com
R1#int g0/0/0
R1#ip nat out
R1#int g0/0/1
R1#ip nat in
R1#exit
R1(config)#ip nat inside source static tcp <inside_server_ip> <port_no> <global_ip_address> <port_no>
R1#
```

There is no global and local address since we have created the static nat:
```
R1#sh ip nat tra
R1#sh ip nat translations 
Pro  Inside global     Inside local       Outside local      Outside global
tcp 8.8.8.200:80       10.1.1.100:80      ---                ---
```
![[Pasted image 20240712220818.png]]

rather than specifying a port number we can assign the global address and local address :
```
R1(config)#ip nat inside source static <ftp_server_ip> <ftp_dns>
```

![[Pasted image 20240712231511.png]]

If ur going to set the internal dns server you can use the ip address of the internal dns-server in ur network and access it by using domain name after setting up the dns service.
LAB:8
Dynamic NAT:
```
R1# conf t
R1#int g0/0/0 ##if it is outside
R1#ip nat out
R1#exit
R1#int g0/0/1 ##if it inside
R1#ip nat in
R1#exit
R1#conf t
R1# ip nat inside source list 1 int <outside int> overload ## overload for multiple port forwarding
R1#access-list 1 permit any ## setting these clients can be natted whereas other cant'b
R1#ip route 0.0.0.0 0.0.0.0 <isp>
R1#end
```

LAB 9 :
Configure register:
![[Pasted image 20240713100359.png]]
 But in my router it shows me 0*2142 configuration register:
 ![[Pasted image 20240713100505.png]]
 so we can set by default using this command:
 ```
R1#conf t
R1#config-register 0*2102
R1#end
```
we have config-register it says in it ignores router startup-config
- Ignores the contents of Non-Volatile RAM (NVRAM) (ignores configuration) so we have replace it by 2102 
- rommon mode can be solved by setting the :
```
rommon 1>confreg 2102
rommon 2>boot
R2#
```
this is for boot flash test.bin we have to remove that:

![[Pasted image 20240713104926.png]]
```
R3#conf t
R3#int g0/0/0
R3#no shutdown
```
after doing this we still have the flash boot test.bin we can remove by using:
```
R3#conf t
R3#no boot flash <file_name>
```

LAB10:
RECOVERY INITIAL PASSWORD:
![[Pasted image 20240713111723.png]]
here i have exported the startup-config file in my laptop so i can view the password of global config mode. and setting default password to cisco

```
R1#conf t
R1# ?
R1# enable password cisco
```
bypassing password in cisco router :
after turning off and on the power supply get back to the cli and press ctrl+C:
```
rommon 1> confreg 2142 ## it bypassing the startup-config
rommon 2> boot
R2>en
R2#conf t
R2#enable password cisco ## it will shows as a simple text
R2#service password-encryption
```
after doing this re-back to the original one or other it will be bypassed.

```
R1# conf t
R1# configure-register 2102 ##It is one which my router has defualt
```
resetting password in cisco switch:
```
Switch: ##press the mode for 3 sec it will get into this
Switch: dir flash:
switch: rename flash:config.text flash:config.text.old ##rename the config file
switch: boot
S1>  ## erase the nvram
S1#  ##we have jumped into the previleged mode but we dont wanna jump
S1# reload
S1>en
S1#copy flash:config.text system:running-config

```
![[Pasted image 20240713153854.png]]

LAB 10: RESTORE ISO IMAGE FROM THE ROUTER:
![[Pasted image 20240713155046.png]]

```
rommon 1>tptfpdnld
rommon 2>      ## set the variables ip,subnet,gateway,server_ip,file_name
rommon 3>set
rommon 4>tftpdnld
rommon 5>y
rommon 6>
```
![[Screenshot 2024-07-13 160459.png]]

LAB12:
BACKUP AND RESTORING IOS:

![[Pasted image 20240713161438.png]]

```
>en
R1#copy st
R1#copy startup-config tftp
Address or name of remote host []? 10.1.1.100
Destination filename [R1-confg]? R1-start-config
Writing startup-config....!!
[OK - 694 bytes]
694 bytes copied in 3.004 secs (231 bytes/sec)
R1#copy run
R1#copy running-config
% Incomplete command.
R1#copy running-config tftp
Address or name of remote host []? 10.1.1.100
Destination filename [R1-confg]? R1-run-config
R1#sh fla
R1#sh flash:
5 33591768 c2900-universalk9-mz.SPA.151-4.M4.bin
[33591768 bytes used, 222152232 available, 255744000 total]
249856K bytes of processor board System flash (Read/Write)
R1#copy flash: tftp
Source filename []? c2900-universalk9-mz.SPA.151-4.M4.bin
Address or name of remote host []? 10.1.1.100
Destination filename [c2900-universalk9-mz.SPA.151-4.M4.bin]? op=router

  Writing c2900-universalk9-mz.SPA.151-4.M4.bin...!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

[OK - 33591768 bytes]

  

33591768 bytes copied in 1.105 secs (3191852 bytes/sec)

R1#conf t

Enter configuration commands, one per line. End with CNTL/Z.

R1(config)#int loo

R1(config)#int loopback 0

  

R1(config-if)#

%LINK-5-CHANGED: Interface Loopback0, changed state to up

  

%LINEPROTO-5-UPDOWN: Line protocol on Interface Loopback0, changed state to up

  

R1(config-if)#ip ad

R1(config-if)#ip address 1.1.1.1 255.255.255.255

R1(config-if)#exit

R1(config)#exit

R1#

%SYS-5-CONFIG_I: Configured from console by console

  

R1#wr

Building configuration...

[OK]

R1#copy run

R1#copy running-config st

R1#copy running-config startup-config

Destination filename [startup-config]?

Building configuration...

[OK]

R1#copy st
R1#copy tftp st
R1#copy tftp startup-config
Address or name of remote host []? 10.1.1.100
Source filename []? R1-startup
Destination filename [startup-config]?
Accessing tftp://10.1.1.100/R1-startup...
R1#copy tftp startup-config
Address or name of remote host []? 10.1.1.100
Source filename []? R1-start-config
Destination filename [startup-config]?
Accessing tftp://10.1.1.100/R1-start-config...
Loading R1-start-config from 10.1.1.100: !
[OK - 694 bytes]
694 bytes copied in 0 secs
R1#
```

upgrading the router ios:
```
R1#copy tftp flash
R1# it will ask the remote ip 10.1.1.100
R1#destinatnation file c2900-universalk9-mz.SPA.155-3.M4a.bin
R1(config)#boot system flash c2900-universalk9-mz.SPA.155-3.M4a.bin 
R1#reload
```

LAB 12:
NTP & SYSLOG:
![[Pasted image 20240713182251.png]]

On router:
```
R1#conf t
R1#logging host <syslog_server_ip>
R1#end
```
do the same in switch !!
we need to configure the time in both the devices time is wrong
```
R1#conf t
R1#service timestamps log datetime msec
```
do the same in switch
we need to configure the NTP server:
```
R1#conf t
R1# ntp server <server_ip>
```
do the same in switch
LAB12:
![[Pasted image 20240714101846.png]]

SNMP:
```
R1#conf t
R1#snmp-server community private rw
R1#snmp-server community public ro
```
do the same in router 2
then go to PC MIB browser set the ip address of the device which you wanna do 
advanced set the v3
![[Pasted image 20240714102046.png]]

LAB 13:
PORT SECURITY:
![[Pasted image 20240714103149.png]]

Port security is a feature in network switches that **blocks unknown wired devices from gaining access to a network**
It also limits the MAC-address
configuring port security on Switch:
first we have to choose the interface...
```
Switch(config)#int g1/0/1
Switch(config-if)#switchport mode access
Switch(config-if)#switchport port-security
Switch#sh port-security interface g1/0/1

```
by enabling port security by default only 1 mac-address are permitted then the interface cames down cuz of violation take place 
![[Pasted image 20240714110316.png]]
for re-enabling the port we should shutdown and no-shutdown
we are only limiting the number of mac-address tables not limiting the mac-address
 securesticky mac-address we are going to put in the running configuration
 ```
 Switch(config)#int g1/0/3
 Switch(config-if)#switchport mode access
 Switch(config-if)#switchport port-security
 Switch(config-if)#switchport port-security mac-address sticky
```
after getting ann ip address for the 2nd pc we get violation and address has been changed:

![[Pasted image 20240714130536.png]]
using sticky it will automatically save the mac-address in the running-config
HERE manually configuring the mac-address for port security
LAB14:
DHCP SNOOPING:
![[Pasted image 20240715221705.png]]

**DHCP Snooping** is a security feature implemented on Layer 2 network switches. Its purpose is to prevent unauthorized rogue DHCP servers from accessing your network
By enabling dhcp server in switch so that switch will prevent unauthorized network:

if two dhcp servers are there in a network we need to trust the server here is the commnad to enable dhcp snooping:
```
S1#conf t
S1(config)#ip dhcp snooping
S1(config)#ip dhcp snooping vlan 1 ## all the interface are configured on vlan 1
S1(config)#int g0/2  ## which int the real server is there in the network
S1(config-if)#ip dhcp snooping trust
S1#term mon
S1# ip debug dhcp snooping packet
```
LAB 15:
AAA,TACAS,RADIUS:
It's a protocol used for authentication, authorization, and accounting (**AAA**) services in network security. TACACS+ offers enhanced security features and flexibility compared to its predecessor, TACACS. RADIUS, which stands for Remote Authentication Dial-In User Service, is another AAA protocol used for managing network access. ![[Pasted image 20240715222324.png]]
By enabling AAA server on the router,switch:
```
R2#conf t
R2#aaa new-model
R2(config)#aaa authentication login default group tacacs+ local## group considered as all ports.
R2(config)#aaa authentication enable default group tacacs+ local
R2(config)#tacacs-server host 10.1.1.250 key cisco
```
same for radius server
![[Pasted image 20240716223017.png]]

LAB 15:
STATIC ROUTES:
![[Pasted image 20240717001511.png]]
```
R1#conf t
R1(config)#ip route 192.168.3.0(next network) 255.255.255.0 192.168.1.2(next hop)
```
do the same as in all device while viewing sh ip route it should have all the network so that it can be able to ping.
LAB 15:
OSPF single area:
![[Pasted image 20240717004814.png]]
IN OSPF if we have more than one area we have to use area 0:
router ID can be selected by highest ip address any physical/loopback interface:

```
R1#conf t
R1(config)#router ospf 1
R1(config-router)#network 10.1.1.1 0.0.0.0(inverse mask)

```
if there is a different interface like we have 3 but if there is 2 we can use this command:
```
R1#conf t
R3(config)#int g0/0(which interface)
```

LAB 16:
 OSPF MULTI-AREA:
 ![[Pasted image 20240717013603.png]]
 Exact match in the ip address means:
 ```
 R1#conf t
 R1(config-router)#network 10.1.1.1 0.0.0.0 area 1
 R1(config-router)#network 1.1.1.1 255.255.255.255 area 1
```
enabling ospf using the interfaces:
```
R3#CONF T
R3(config)#router ospf 1
R3(config)#exit
R3(config)#int loop 0
R3(config)#ip ospf 1 area 0
R3(config)#int g0/1
R3(config)#ip ospf 1 areo 0
R3(config)#int g0/0
R3(config)#ip ospf 1 area 2
```
enabling ospf using single command in all interfaces:
```
R4#conf t
R4#router ospf 1
R4#network 0.0.0.0 255.255.255.255 area 2
R4(config-router)#network 4.4.4.4 255.255.255.255 area 2
```

WIFI DEMO:
Wireless LAN controller:
Light weight access point requires wlan to work:


WLC have a default ip of 192.168.1.1 if we want to control the controller we have to be in the same subnet.![[Pasted image 20240717213444.png]]
After configuring with these we can access the web interface of wlc after using it we have to access it by https!....

![[WhatsApp Image 2024-07-18 at 18.21.19_f3e131fa.jpg]]

we configure manually configure access point or we can use DHCP server.
![[Pasted image 20240718184217.png]]


When AP’s do not require WLC to work their magic, they are referred to as **autonomous access points**.

If they require WLC to configure & manage, it is called **lightweight access points**

configuring ipv6:(uses usincast routing)

same as ipv4:
![[Pasted image 20240719194651.png]]
GRE TUNNEL:
Generic routing protocol it encapsulates and routes different network protocols over an ip network.
the ISP dont have more than 10 networks in the routing table inorder to route we need to tunnel.
tunnel can be used two ip network it is a point to point link.
```
C1#conf t
C1(config)#interface tunnel 10
C1(config)# <ip address> <subnet mask>
C1(config-if)#tunnel source GigabitEthernet 0/0/1
C1(config-if)#tunnel destination <isp_ip address>


```
do the same side of other side of the tunnel
in the real world we'r gonna setup a 30 bit so we dont need to set 24 bit
![[Pasted image 20240719225806.png]]
one rsc 18 address into other address..

```
C1(config)#router osp
C1(config)#router ospf 1
C1(config-router)#net
C1(config-router)#network 10.1.3.1 0.0.0.0 a
C1(config-router)#network 10.1.3.1 0.0.0.0 area 0
```

LAB16:
Quality of service: Mechanism to control traffic and perform task with limited network capacity
[Pasted image 20240719230905.png]]
![[Pasted image 20240719230905.png]]

```
R1(config)#class-map match-all
R1(config-cmap)#match protocol rtp

```
we need to enable policy here,
```
R1(config)#policy-map mark
R1(config-pmap)#?
class policy criteria
exit Exit from policy-map configuration mode
no Negate or set default values of a command
R1(config-pmap)#cla
R1(config-pmap)#class voice
R1(config-pmap-c)#set ip dscp af31
R1(config-pmap-c)#priority 25 ##bandwidth

```

LAB 18:
VOIP :
![[Pasted image 20240719234829.png]]

for intervlan routing we have to specify the dot1q
The purpose of a tagged or "trunked" port is to pass traffic for multiple VLANs, whereas an untagged or "access" port **accepts traffic for only a single VLAN**.

```
Router(config)#int f0/0.1
Router(config-subif)#encapsulation dot1Q 1 native
Router(config-subif)#ip address 10.1.1.254 255.255.255.0
Router(config)cdp run

```
power usage:
```
Switch#sh power inline
```
![[Pasted image 20240720002835.png]]
![[Pasted image 20240720003310.png]]

configuring telephone service:
```
Router(config)#telephony-service
Router(config-telephony)#ip source-address 10.1.101.254 port 2000 ?
Router(config)#ephone-dn 1 ## do this for no of e-phones
Router(config)#ephone-dn 1
Router(config)#number 1000
Router(config)#ephone 1
Router(config)#type 7960

```

to specify the vlan we need to configure the dot1q
configuring cdp to specify which vlan want to configure
configuring physical ephones:

after restarting we get this :
![[Pasted image 20240720113058.png]]

```

R1#sh ip dh
R1#sh ip dhcp bin
R1#sh ip dhcp binding 
IP address       Client-ID/              Lease expiration        Type
                 Hardware address
10.1.100.3       0004.9AD4.268B           --                     Automatic
10.1.100.1       0006.2AC5.DEB6           --                     Automatic
10.1.100.2       0002.4A26.B27D           --                     Automatic
10.1.101.3       00D0.BA6A.B528           --                     Automatic
10.1.101.2       0090.0CB1.438E           --                     Automatic
10.1.101.1       0004.9A05.0DC7           --                     Automatic
```
after setting buttons on :
```
Router(config-ephone)# button 1:1
```
ephones will regsitered.
![[Pasted image 20240720114612.png]]


![[Pasted image 20240720114823.png]]
 call connected
