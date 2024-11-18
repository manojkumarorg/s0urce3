# NETWORK

Network is a conduit it connects two or more computers or other devices
![[Pasted image 20240808000753.png]]

# COMMUNICATION BETWEEN DEVICES

![[Pasted image 20240808001213.png]]

# PROTOCOLS
![[Pasted image 20240808001323.png]]
At each layer protocols will add each layer Header and trialer and pass the data to reciever

Department of defence and the engineering
OSI doesn't provide much more information about the protocols whereas TCP/IP do 
![[Pasted image 20240808001718.png]]

# 5 LAYER MODEL
![[Pasted image 20240808002008.png]]


# 5 LAYER PROTOCOL
![[Pasted image 20240808182740.png]]

# BUILDING ETHERNET LANs

`Checksum is an error detection mechanism that is widely used in computer networks to ensure the integrity of data transmitted over a network.`
![[Pasted image 20240808184307.png]]
Ethernet operates on layer 1 and 2
An Ethernet [frame](https://www.bing.com/search?q=Frame%20(networking)%20wikipedia&form=WIKIRE) is preceded by a [preamble](https://www.bing.com/search?q=Preamble%20(communication)%20wikipedia&form=WIKIRE) and start frame delimiter (SFD)

ETHERNET COMPONENTS:
- NIC
- CSMA/CD(as its MAC protocol)(either do transmit or receive)
- Half-duplex
![[Pasted image 20240808185753.png]]

whereas 802.11 is a standard for wireless same as ethernet frame 2 it includes Logical Link Controller
![[Pasted image 20240808190539.png]]
Last three address will the device unique id
![[Pasted image 20240808190857.png]]

Repeater:
It is a physical layer device it connects the physical wire cables together
![[Pasted image 20240808191224.png]]

5-4-3 RULE
5-segements
4-repeaters
3-populated segments
2-link segments
1-collision domain

Bridges segment the larger network into small collision domain

![[20240808-1349-48.9514234.mp4]]

L1 -- HUBS, REPEATERS
L2 -- BRIDGE,SWITCH

# SWITCHES

To Prevent network loops switches uses STP
![[Pasted image 20240808203045.png]]

Network bandwith: bit rate (bits/s)
![[Pasted image 20240808203439.png]]Converting Mbps to bits per second:
Mbps/8=Bytes/s
Devices are in the different vlan even must be in the same  switch need to be communicate router must be used

why router?
Switches can't connect the geographically dispersed networks 

WIRELESS LAN:
- Autonomous Architecture -- ap(fat ap-802.11)
- Centralized Architecture --(ap controller)
- Distributed Architecture 
![[Pasted image 20240808214320.png]]
Collision domains contain end user device and ethernet switch(L2)
L2 - COLLSION DOMAIN
L3-BROADCAST DOMAIN
![[Pasted image 20240808224436.png]]

FDDI-fibre optic communication (200km)
router will never change the layer 3 address

![[Pasted image 20240809191320.png]]

# IP ADDRESSING

HOW IP CAMES?
ARPA WAS CREATED TO ESTABLISH A CONNECTION BETWEEN IN THE WAN

CIDR :
![[Pasted image 20240809202950.png]]
HOST BITS:
![[Pasted image 20240809203422.png]]
IP SUBNETTING:
STEP:1
![[Pasted image 20240809203611.png]]
STEP:2
![[Pasted image 20240809203727.png]]
STEP:3
![[Pasted image 20240809204233.png]]
STEP:4
![[Pasted image 20240809204542.png]]
STEP:5
![[Pasted image 20240809204720.png]]
STEP:6
NOTE:
YOU CAN CHECK HERE WHETHER THE THESE TWO DEVICES NEEDS ROUTER TO COMMUNICATE BETWEEN THE THE DEVICE BY PERFOMRING AND OPERATION SEE HERE THESE TWO ARE IN THE DIFFERENT SUBNET SO IT NEEDS ROUTER TO COMMUNICATE
![[Pasted image 20240809204935.png]]

# VARIABLE LENGTH SUBNET MASKING
IF YOU CALCULATE THE NUMBER OF HOST WE CAN JUMP BY ADDING WITH THAT NUMBER FOR EXAMPLE:
IN THIS CASE WE HAVE 2^5-2 =30 JUMP WITH 30 
NETWORK NUMBER :192.168.3.0
IP RANGES:192.168.3.1-192.168.3.30
BROADCAST ADDRESS :192.168.3.31

NXTT JUMP INTO NEXT SUBNET:
STEP:7
![[Pasted image 20240809205356.png]]
STEP:8
![[Pasted image 20240809205654.png]]
EXAMPLE:
STEP:1
![[Pasted image 20240809205811.png]]STEP:2
![[Pasted image 20240809205903.png]]
STEP:3
![[Pasted image 20240809210146.png]]

# EVOLOVE OF IP
![[Pasted image 20240809210359.png]]

![[Pasted image 20240809210522.png]]
 LOOPBACK INTERFACE IS JUST A INTERFACE TO SEND A MESSAGE TO ITSELF IF THE NETWORK FAILS OR DOING TROUBLESHOOTING
 
IP MULTICASTING:
![[Pasted image 20240809210735.png]]

DIRECT ROUTING HAPPENS WHEN DEVICES ARE IN THE SAME NETWORK ![[Pasted image 20240809211153.png]]

LONG MATCH ROUTING:
![[Pasted image 20240809213227.png]]

MTU:
THE FIXED UPPER LIMIT ON THE SIZE OF THE PACKET THAT CAN BE SENT IN A SINGLE FRAME
IF THE MTU IS LARGE IT WILL DO FRAGMENTATION
AND THEN RESAMBLED TO THE DESTINATION ADDRESS

# IPv4 versus IPv6
![[Pasted image 20240809213817.png]]
 HEADER 
 ![[Pasted image 20240809214656.png]]
 EXTENSION USED BETWEEN HEADER AND THE DATA :
 ![[Pasted image 20240809214959.png]]

IPv6 SHORTEND:
![[Pasted image 20240809215617.png]]
 ![[Pasted image 20240809215650.png]]
# rules
![[Pasted image 20240809220043.png]]
![[Pasted image 20240809223417.png]]

SUBNETTING IPv6:
![[Pasted image 20240809223822.png]]


RFC 4291:
::/128 UNSPECIFIED
::1/128 LOOPBACK
FF00::/8 MUTLICAST
FF80::/10 LOCAL LINK

EXAMPLE:
![[Pasted image 20240809224059.png]]


# WAN TECHNOLOGIES

LAN'S ARE OWNED BY INDIVIDUAL ORGANIZATION WHEREAS WAN'S ARE USED THIRD PARTY SERVICE PROVIDER

TRADITIONALLY WAN OPERATES IN L2,L1
 MPLS-WAN SERVICE (L2.5)

L1:

 LOCAL LOOP :
 ![[Pasted image 20240809225755.png]]
DIGITAL LINES:
![[Pasted image 20240809225903.png]]

WHAT SPECIFIC TECHNOLOGIES UED BY WAN IN LAYER1?
ANALOG TELEPHONE LINES
DIGITAL TELEPHONE LINES
FIBRE OPTIC CONNECTION


T1 AND T3 LINES FOR ANALOG LINES

T-CARRIER SYSTEM ORGINALLY DEVELOPED AS A WAY TO REDUCE THE NO OF CABLES USED IN LARGE CITIES

24 DIGITAL SIGNAL 0 -- 1 DS1

![[Pasted image 20240809231139.png]]
SURVEY 
![[Pasted image 20240809231626.png]]
![[Pasted image 20240809232403.png]]

SONET AND SDH USES TIME DIVISION MULTIPLEXING
OTN USES WAVELENGTH DIVIVION MULTIPLEXING

OTN CAN BE USED NOWADAYS IT CAN TRANSMIT OVER 40-80 CHANNELS SIMULTANEOUSLY

**L2:**
WHAT SPECIFIC TECHNOLOGIES UED BY WAN IN LAYER2?
- PPP
- FRAME DELYA
- ATM
- CARRIER ETHERNET

WAN USES SIMILAR LIKE LAN PROTOCOL IT USES PPP PROTOCOL SO IF WE ARE TWO WAN WITH THE INTERMEDIATE ROUTER AND THE ROUTER NEEDS TO BE CONFIGURED PPP ON BOTH SIDES

![[Pasted image 20240809233522.png]]

STEP:1
ACK
STEP:2
AUTH
STEP:3
ESTABLISHING PPP
NOTE:
NCP is responsible for establishing, configuring, and terminating network layer protocols over a PPP connection. [It allows PPP to support multiple network layer protocols, such as IPv4, IPv6, AppleTalk, and others](https://www.ciscopress.com/articles/article.asp?p=2202412&seqNum=5
A leased line, sometimes called a dedicated line, is a dedicated **point-to-point link and fixed-bandwidth data connection**

FRAME RELAY IS AN EXAMPLE OF VPN
COST EFFIECIENT 
NOT MAKE FASTER

![[Pasted image 20240810140834.png]]
ATM:
TRANSPORT VOICE  VIDEO AND DATA IN THE SAME NETWORK WITH QUALITY OF SERVICE 
NOT FASTER THAN VPN
COMPLICATED
VPN


CARRIER ETHERNET :
NO LONGER NEED FRAME RELAY OR ATM WAN TO RUN
CAN OFFER MULTIPLE SERVICES USING SINGLE INTERFACE TO CUSTOMER
EX:
METRO ETHERNET FORUM
IEEE
ITU
![[Pasted image 20240810141655.png]]

MPLS:
![[Pasted image 20240810142025.png]]LAYER(2.5) PROTOCOL
IT USES LABEL SWITCHED PATH AND CONNECTS THE LINK BETWEEN THE DEVICES
UNIDDIRECTIONAL

LER:
LABEL EDGE ROUTER THE ROUTER WHICH FOLLOWS THE LABELED SWITCH PATH AND EACH LSR HAS LER 

FEC:
GROUP OF PACKETS FORWARDED IN THE SAME WAY TO MPLS PROVIDERS DOMAIN

![[Pasted image 20240810143514.png]]


# TRANSPORT LAYER PROTOCOL


SOFTWARE PORT NUMBERS

PORT 0   RESERVED
PORT 1-1023 WELL KNOWN PORTS
PORY 1024-49151   REGISTERED PORTS
PORT 49152-65535  DYNAMIC OR PRIVATE PORTS


![[Pasted image 20240810151338.png]]
\
UDP :
CONNECTIONLESS SERVICE
DATAGRAM NOT SEGMENST

UDP PROTOCOLS:
![[Pasted image 20240810151458.png]]

IF THE SENDING COMPUTER DOESNT RECEIVE THE DNS REPLY EITHER IT GETS DROPPED OR SENT ACROSS THE DIFFERENT DNS SERVER

UDP:
DNS
TFTP
SNMP
(MULIPLEXING DATA)
![[Pasted image 20240810152239.png]]

TCP:
HTTP
SMTP
FTP
(MULIPLEXING DATA)

![[Pasted image 20240810152932.png]]![[Pasted image 20240810153032.png]]



10.10.1.8
00001010.00001010.00000001.00001000
11111111.11111111.11111111.11110000

00001010.00000010.00000001.00000000

10.10.1.50
00001010.00001010.00000001.00110010
11111111.11111111.11111111.11110000
00001010.00001010.00000001.00110000



QUIZ:
![[20240810-1019-46.3804238.mp4]]

# SOFTWARE ARCHITECTURE



Unix based freeBSD
Deamons are service or process that runs on the device
common daemons:
- rpd
- mgf
- dcd

CONTROL AND FORWARDING PLANES:
CONTROL PLANE:
Routing engine (rpd)
Manages the routing table
It Derives the forwarding table

FORWARDING PLANE:
Made up of a PACKET FORWARDING ENGINE

TRAFFIC PROCESSING:
TRANSIST TRAFFIC:
Handles by PFE

 - FORWARDING TABLES IS STORED IN THE ROUTING ENGINE AND PACKET FORWARDING ENGINE
- MGD IS RESPONSIBLE FOR CONFIGURING THE ROUTER AND ALL USER COMMANDS 
- JUNOS OS PROVIDES SEPARATION  BETWEEN CONTROL AND FORWARDING PLANES


# BSD SHELL AND CLI MODES

When logging in as a root we have certain commands like top, mkdir ,mount ,cat accessible
No routing and switching happens here
Interacting with underlying Unix OS and filesystem
Format for Unix BSD Shell
```
root@:~#
```
monitor and troubleshoot format :(operational mode)
```
root>
```
configuration mode format:(aka edit mode)
```
root#
```
commands:
```
root@:~# vi text.txt ##opening a text editor
```

```
root@:~# show chassis firmware
```

Navigating configuration:
so if we want to edit the specific set of heiracrhy ew can use this 
```
router# edit routing-instances
router# edit customer1
router# set instance-type vrf
```
 configuring inet for a devices:
 ```
 router:~#cli
 router>edit ## entering configuration mode
 router#edit ?
 router#edit <int>
 router#edit unit<number>
 router#edit family inet ## for ipv4 addressing
 router#up ## setting the interface up 
 router#edit family mpls
 router#up
 router#edit family inet
 router#set address <ip_address>
 router#up
 router#show
```

If we want to delete an address in that family:
```
router#edit unit<number> family inet
router#delete address <ip_address>
router#show
```

configuration:
- active -- currently running
- Candidate  -- not committed

Candidate configuration will not active until the device has not committed
 ```
 router#commit
```
User logging and permission:

```
router# show configuration system login ## if there no login
router# edit system login
router# set user <name>
router# set user <name> class ?
read-only    permission(view)
super-user    permission(all)
unauthorized  permissin(none)

router# edit user <name>
router# set authentication plain-text password ## after declaring we have to set the commit message
router# commit
router# show | compare
router# exit
router# exit
```
after configuring user we can able to start the shell
```
user> start shell
%ls
```
# WORKING WITH CONFIGS

LOADING AND ROLLBACK

ROLLBACK--It stores upto 50 previously committed configuration
it will load the  previously committed configuration as the candidate

LOAD -- it load the previously saved configuration to candidate from the file
for example if we have config file that were stored somewhere we can make them as candidate by entering the load 
















# JUNOS OS FUNDAMENTALS


![[Pasted image 20240810162044.png]]


IT IS REPRESNETED BY M.NZB.S
21.1
Z-RELEASE TYPE
B- BUILD NUMBER
S- SPIN NUMBER

![[Pasted image 20240810162611.png]]

QUIZ:1
![[Pasted image 20240810163056.png]]
![[20240810-1101-41.6053040.mp4]]

# INTERACTING WITH JUNOS
![[Pasted image 20240811212351.png]]

TROUBLESHOOTING AND MONITORING COMMANDS:
![[Pasted image 20240811212751.png]]
COMMON COMMANDS :
![[Pasted image 20240811212809.png]]

# CLI MODE


![[Pasted image 20240812221258.png]]
TO EASILY RECOVER PREVIOUS COMMANDS:
```
router#rollback 0
```

```
router# configure 
```

To allow only single user to edit the configuration
```
router# configure exclusive
```

In contrast uncommitted changes will retain back to the candidate configuration

```
router#configure private
```

![[Pasted image 20240812222241.png]]
If two committing messages were received second one will be warned

```
router# configure batch
```

where commit operations are executed in batches. When one batch is complete next set of batches will be in the queue

All commits are created independently and sequentially
```
router#configure dynamic
```
 time taken is much low for commiting
 ![[Pasted image 20240812223133.png]]


Configuration file uses curly braces and indendation

to move the more level to the hierarchy:
```
router# up (number)
```
symbol used in configuration file:
```
{}
```

# CUSTOMIZE THE CONFIG

Using set to add the configuration statements
```
router#set we-management http
```
removing configuration
```
router# delete web-management
```

```
router# wildcard delete int ge-*
```
activate configuration into effect:
```
router# activate we-management
```

![[Pasted image 20240812225122.png]]

Committing configuration :
```
router#commit
```

commit synchronize --- will commit on both routing engines
![[Pasted image 20240812230007.png]]

the commit confirmed(the software support the ranges of  1 to 65535 min within 10 min being default)

we can schedule the commit operation 
```
router# commit at <time>
router# show system commit #status of committing
router# commit comment "<text>" ## it will add these text in the commit file last
```

![[Pasted image 20240812230657.png]]

JUNOS it can store 0 to  49 rollback configuration

To return back to the rescue configuration 
```
router# rollback rescue
```

QUIZ:

![[20240812-1746-54.4253938.mp4]]


COMMON CONFIGURATION COMMANDS:

Saving a candidate configuration:
```
router# save <file_name>
```
if path not specified it will be saved in the user's
![[Pasted image 20240812231927.png]]


To load a configuration file:
```
router# load ?
```
![[Pasted image 20240812232113.png]]

HELP COMMANDS:
![[Pasted image 20240812232830.png]]![[Pasted image 20240812233022.png]]


RUN command:
```
router#set unit 0 family inet address 192.168.1.1
router# run ping 192.168.1.1 count 1
```
 run command will execute operational mode commands while in configuration mode 

# FACTORY DEFAULT CONFIG

Ex series are designs to operate as layer 2 switch

Overwriting the candidate config mode:
```
router#load factory-default
```
Root password:
```
router#set system root-authentication plain-text-password
```
Perform save operation:
```
router#commit
```

CONFIGURATION TASKS:
 To perform shutdown:
 ```
 router#request system halt ?
```
Power off:
```
router#request system poweroff
```

By halting it will stop all the CPU functions in the hardware but the system will be powered on state

By starting the cli
```
router@%cli
router>
```

Initial config:
```
router# edit system
router# set host-name router
```


INTERFACE TYPES AND CONFIGURATION
fxp0,mc0 are management network
fxp1,em1 connects and control forwarding
ge,xe,et provide network connectivity like fa0 or gig

![[Pasted image 20240813213057.png]]
Interface naming:
![[Pasted image 20240813224736.png]]
to quickly verify the interface state:
```
router> show interfaces ge-0/2/2 terse
```

![[Pasted image 20240821214207.png]]
![[Pasted image 20240821214343.png]]
# ACTIVITY
![[20240821-1635-42.2722578.mp4]]


# USER AUTH
 ![[Pasted image 20240821222209.png]]
  to validate users radius and tacacs+ used
  ![[Pasted image 20240821222345.png]]
  auth setting:
```
user@router# show system authentication-order
```
![[Pasted image 20240821222603.png]]
it sees the local database:
![[Pasted image 20240821222749.png]]components of auth:
![[Pasted image 20240821222915.png]]
predefined commands:
![[Pasted image 20240821222949.png]]![[Pasted image 20240821223001.png]]
![[Pasted image 20240821223039.png]]
![[Pasted image 20240821223049.png]]
![[Pasted image 20240821223237.png]]
QUIZ:
![[Pasted image 20240821223422.png]]

Archiving config file if data loss:
![[Pasted image 20240821223552.png]]Monitoring :
![[Pasted image 20240821223739.png]]

 LAB:(AUTH)
 
 ![[20240821-1708-36.1916148.mp4]]
 AUTHENTICATION :
 
![[20240821-1734-09.0827159.mp4]]
 ARCHIVAL CONFIG:
 ![[20240821-1805-31.5689503.mp4]]
 SYSTEM LOGGING AND TRACING:
 - Uses unix syslog-style config syntax
 - primary syslog files is /var/log/messages
ex:
![[Pasted image 20240821234536.png]]
the general syslog configuration options inlcude:
![[Pasted image 20240822000927.png]]

 ![[Pasted image 20240822001316.png]]
 tracing a specific protocol:
 ![[Pasted image 20240822001425.png]]

```
user@router# edit protocols <protocol_name>
```
when trace file has reached maximum in size it will rename it as tracefile.zero and again it reaches the maximux size means it will rename as tracefile.one and so far

To avoid timestamps on each line use 
```
user@router# no-stamp tracefile.zero
```

![[Pasted image 20240822002147.png]]
By default JUNOS os stores log and trace files in /var/log/
use "show log <file_name>" to display the contents
![[Pasted image 20240822002335.png]]

we can monitor serveral log file at one time using this command:
```
user@router# monitor start <file_name>
```
to filter the file :
```
user@router# monitor start messages | match fail
```
use esc+q to halt or resume real time output

Log and Trace file manipulation:
```
user@router# clear log <file_name>
user@router# file delete <file_name>
```
file operations:
- Delete
- compare
- copy
- list
- rename

**To enable remote logging set a syslog server at the "edit system tracing" hierarchy level**

configuring NTP:
![[Pasted image 20240822003313.png]]
 if there is lag between client and the server it will synchronizely vary between 1 thousand sec
*     * - it denotes the peer will be selected for synchronization
*  space - discarded because of high stratum value or fails sanity check
*  x - designated filesticker by the intersection algorithm
* . - called from candidate end of the list
*  - discarded by the clustering algorithm
* +  included in the final selection set
* #- selected for synchronization but the system exceeds the maximum

Configuring SNMP:
![[Pasted image 20240822004517.png]]
Versions are 1,2c,3
ex:

![[Pasted image 20240822004804.png]]
quiz:
![[Pasted image 20240822004927.png]]![[Pasted image 20240822005002.png]]
 LAB:
 ![[20240821-1920-32.1731056.mp4]]

# OPERATIONAL MONITORING AND MANITENANCE

For system level operations
```
lab@vsrx-1> show system <argument>
```
![[Pasted image 20240823155446.png]]

CHASSIS:
**A hardware device that is designed for expansion and accepts a variety of plug-in modules of different type**

To monito chassis:
```
user@router> show chasssis
```

Interfaces:
```
user@router> show interfaces <name>
```

To quickly verify the state of all physical and logical interfaces:
```
user@router> show interfaces terse
```

Monitor traffic:
```
user@router> monitor traffic ## It will directly access to the tcp dump utility
```

Monitoring interface :
```
user@router> monitor interface traffic
```

Quiz:

![[20240823-1032-26.1340022.mp4]]
 Packet capture example:
 ![[Pasted image 20240823160715.png]]

QUIZ:
![[Pasted image 20240823160951.png]]
![[Pasted image 20240823161036.png]]


Password recovery process:
```
user@router# edit system ports
user@router# console insecure
```
 
 QUIZ:
 ![[20240823-1043-25.6824237.mp4]]
 LAB:
 ![[20240823-1049-13.2368675.mp4]]
# Upgrading the JUNOS-OS
```
user@router> show system storage
```

Frees storage on the device and list the files for deletion:
```
user@router> request system storage cleanup
```
List files for deletion but not actually delete
```
user@router> request system storage cleanup dry-run
```

Remove all the configuration information:
```
user@router> request system zerioze
```
removed information recoverable:
```
user@router> request system zerioze media
```
Upgrade/Downgrade:
```
user@router> request system software add <path/image_name>
```
to activate the system perform reboot

Performing a Unified ISSU:
![[Pasted image 20240827005153.png]]

STEPS:
![[Pasted image 20240827215808.png]]

```
request system software add /var/tmp/junos-install-vsrx3-x86-64-21.1R1.11.tgz reboot
```

```
load override /var/home/lab/ijos/lab6-start.config
```
LAB:(Upgrading OS)

![[20240827-1705-41.4763404.mp4]]

# Interface configuration examples

Physical interface properties:
![[Pasted image 20240827225637.png]]
![[Pasted image 20240827225749.png]]

Vlans are configure using the command:
```
user@router> edit system herirarchy
```
![[Pasted image 20240827230257.png]]


Link aggregation  enables you to group ethernet interfaces to form a singgle aggregated ethernet interfaces-LAG

Note:
Top command in JUNOS is aka The command is equivalent to the Junos CLI command “show system processes extensive”.

If LACP is used atleast one side must be configure as a Active mode
![[Pasted image 20240827231520.png]]

QUIZ:
![[Pasted image 20240827231736.png]]
![[Pasted image 20240827231811.png]]

Configuratin Groups:
![[Pasted image 20240827231931.png]]


![[Pasted image 20240827232403.png]]

Quiz:
![[Pasted image 20240827232525.png]]

![[Pasted image 20240827232731.png]]


# ROUTING FUNDAMENTALS

Routing Table

inet.0 --ipv4 unicast routes
inet.1 --multicast forwarding
inet.2 -- multicast BGP routes to provide the reverse path and the forwarding path
inet.3 -- MPLS path information
inet.4 MSDP route entries
inet.6 -- ipv6 unicast routes
mpls.0 --MPLS for next hop


![[Pasted image 20240827233822.png]]

```
user@router> show route forwarding-table
```
![[Pasted image 20240827234502.png]]


QUIZ:
![[Pasted image 20240827234836.png]]
![[Pasted image 20240827235830.png]]


Routing with instances:
```
user@router> show router table new-distance.inet.0
```

LOAD BASED LINE CONFIFURATION:

Configuring and monitoring an IPv4 interfaces:
```
lab@vSRX-1# show route all
lab@vSRX-1# configure
lab@vSRX-1# edit interfaces
lab@vSRX-1# set ge-0/0/4 u


nit 0 family inet address <ipv4 or ipv6>## common method to set this address 
lab@vSRX-1# show interface terse ## current state of the recently configured devices
lab@vSRX-1> ping 172.18.1.1 rapid count 2 ## send only 2 counts
```
Configuring and monitoring 
an IPv6 interfaces:
```
lab@vSRX-1# show security
lab@vSRX-1# edit security
lab@vSRX-1#set forwarding-options family inet6 mode packet-based## if ping fails 
```

- Static routes: **5**
- OSPF internal routes: **10**
- OSPF external routes (Type 1): **150**
- OSPF external routes (Type 2): **150**
- RIP: **100**
- Directly connected routes: **0**

# ACTIVITY2

![[20240909-1428-17.9226129.mp4]]

# static and dynamic routing

```
lab@vSRX-1> edit routing-options
lab@vSRX-1> show route protocol static
```
![[Pasted image 20240910175439.png]]

Configuring:
![[Pasted image 20240910175710.png]]

Use resolve cli option to enable resolution indirectly connected to the next hops

Qualified next hops:
![[Pasted image 20240910182046.png]]

# QUIZ
![[Pasted image 20240910182314.png]]

DYNAMIC ROUTING:![[Pasted image 20240910182511.png]]
EGP is used by independent network entities(BGP)


# QUIZ
![[Pasted image 20240910182837.png]]


# ospf
shortest path follow(dijikstra algorithm)

![[Pasted image 20240910190709.png]]

```
lab@vSRX-1> show ospf neighbor detail
```
By default in OSPF  it priority value is set to 128

```
lab@vSRX-1> edit interface ge0/0/1 unit 0
lab@vSRX-1>set family inet6 address <ipv6>
lab@vSRX-1>set family inet6 address <ipv6> eui-64 ## eui defines the router automatically generate the interface id based on the mac-address
```
/127 for point to point links
/128 for loopback interfaces
![[Pasted image 20240910204650.png]]

# QUIZ
![[Pasted image 20240910204946.png]]

LOAD BASED CONFIGURATION(DESKTOP):
```
[lab@desktop ~]$ python3 labs.py lab8-start
```
```
lab@vSRX-1# edit routing-options
lab@vSRX-1# set static route 0/0 next-hop 172.18.1.1
lab@vSRX-1# set static route 192.168.1.2/32 next-hop 172.20.101.10 ## next hop

```

set static route 192.168.2.1/32 qualified-next-hop 172.20.77.2 preference 6 

# ROUTING POLICY

![[Pasted image 20240921122009.png]]

Default routing policy:
RIP![[Pasted image 20240921122500.png]]

```
users@Router# edit routing-policy
```
![[Pasted image 20240921122737.png]]
# QUIZ
![[Pasted image 20240921122830.png]]
![[Pasted image 20240921122917.png]]

BUILDING BLOCK OF ROUTING POLICY:
![[Pasted image 20240921123150.png]]

Prefix list contains a list of prefixes:
```
user@router# edit policy-options
```
![[Pasted image 20240921125114.png]]
Route filters:
![[Pasted image 20240921125251.png]]

- `172.16.0.0/12 orlonger`: This matches the `172.16.0.0/12` network itself and any network that is more specific (has a longer subnet mask), such as `172.16.0.0/13`, `172.16.0.0/16`, etc.
- This is useful when you want to match an entire range of IP addresses that fall under a larger prefix.
### **`from`**:

- **Purpose**: This keyword defines the **criteria or condition** that the router will check. In simpler terms, it tells the router what routes to look for.
- **How it works**: In the example, `from` is followed by a list of **route filters** (like specific IP addresses or subnets) that the policy is interested in.
```from {     route-filter 172.16.0.0/12 orlonger;     route-filter 192.168.0.0/16 orlonger;     route-filter 10.0.0.0/8 orlonger; }
        
    - This tells the router: "If you see any routes that match these network ranges (`172.16.0.0/12`, `192.168.0.0/16`, `10.0.0.0/8`) **or** any routes that are longer (like `172.16.1.0/24`), take the action defined in `then`."

2. then

- **Purpose**: This defines **what action** the router should take **when it finds a match** based on the `from` condition.
- **How it works**: In this case, the action is `reject`.
    - Example:
        
        Copy code
        
        `then reject;`
        
    - This tells the router: "If the routes match what is defined in the `from` section, then discard or reject those routes."
```
Longer match:
```

`172.16.0.0/12 longer` would match:

- Routes like `172.16.1.0/24`, `172.16.2.0/16`, `172.16.128.0/17`
- It **does not match** `172.16.0.0/12` itself, because it is looking for more specific subnets.
```
![[Pasted image 20240921141632.png]]

# Firewall filters

![[Pasted image 20241014191010.png]]

building blocks for firewall :
![[Pasted image 20241016204709.png]]


![[Pasted image 20241017183058.png]]
```
user@router# edit firewall family inet
```

![[Pasted image 20241017184157.png]]

# Designing the output filter traffic

![[Pasted image 20241017184736.png]]

# Designing the input filter
![[Pasted image 20241017185038.png]]

# Applying ff
![[Pasted image 20241017185301.png]]

we can reset counter statistics 
```
user@router> clear firewall filter
```
understanding the log
```
user@router> show firewall log
```
showing input firewall filter
```
user@router>show firewall counter filter input-ff inbound-discarded
```
showing input firewall filter
```
user@router> show firewall counter filter output-ff inbound-accepted
```

Policing
![[Pasted image 20241017195102.png]]


Format for writing the ff-policy:
```
policy {
    from {
        source-address 192.168.1.0/24;
        destination-address 10.0.0.0/8;
    }
    then {
        permit;  // or deny, log, etc.
    }
}
```

Configuration example:
![[Pasted image 20241017200302.png]]

# Unicast RPF

![[Pasted image 20241018233233.png]]

Configuration:
![[Pasted image 20241018233725.png]]

If Unicast RPF is not enabled the uRPF flag is not displayed

# LAB (firewall filters)
![[Pasted image 20241018234220.png]]

Configuring and monitoring firewall filters:
```
user@router# edit family inet filter protect-host
```
protect-host is the firewall filter name
```
user@router# set term limit-icmp from protocol icmp
user@router# set term limit-icmp from source-address <ip_address>
user@router# set term limit-icmp then accept
```
like wise if you use for other protocol do the same procedure

inputing the firewall filter:
```
user#router# set unit 0 fmaily inet filter input 
```

# Class of service

![[Pasted image 20241028234626.png]]

QUIZ:
![[Pasted image 20241028235212.png]]
![[Pasted image 20241028235314.png]]
 How multifield classifier is configured same as firewall filters in then value:
 ![[Pasted image 20241028235921.png]]


# JTAC PROCEDURES

```
user@router> show chassis hardware
```

sne tool website 

kb-knowledge base
