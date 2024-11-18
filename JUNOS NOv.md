
~~***NETWORKING IS A MARATHON - NOT A SPRINT***~~

# JUNOS OS HARDWARE AND ITS POWER

![[Pasted image 20241107125634.png]]

It saves upto 49 previous configuration

# QUIZ
![[20241107-0737-22.7135725.mp4]]

# ADVANTAGES OF JUNOS OS
![[Pasted image 20241107132600.png]]

![[Pasted image 20241107132833.png]]

# QUIZ
![[20241107-0758-55.3110082.mp4]]

# FIXED PORT ,MODULAR CHASIS & ROUTING ENGINE

FIXED PORT CHASIS
![[Pasted image 20241107133252.png]]

SFP-SMALL FORM FACTOR PLUGGABLE
QSPF-Run upto 100 Gbps
SFP- Run upto 10 Gbps
![[Pasted image 20241107133722.png]]

ROUTING ENGINE:
![[Pasted image 20241107140700.png]]

# QUIZ
![[20241107-0838-04.4869132.mp4]]
MX -SERIES ROUTER
![[Pasted image 20241107141255.png]]
PTX-SERIES ROUTER
![[Pasted image 20241107141610.png]]
ACX-SERIES ROUTER
![[Pasted image 20241107142011.png]]
SRX-FIREWALL
![[Pasted image 20241107142442.png]]
![[Pasted image 20241107142824.png]]

# QUIZ
![[20241107-0907-28.5526452.mp4]]

# SSH & OPERATIONAL MODE

one cable per subnet
# QUIZ

![[20241108-1014-03.5726594.mp4]]

![[Pasted image 20241108154642.png]]

![[Pasted image 20241108155123.png]]
# QUIZ
![[20241108-1026-54.3370625.mp4]]

After getting enter into the ssh we have only two modes:
*operational mode sign indication - >
*configurational mode sign indication - #
![[Pasted image 20241108160138.png]]
most commonly used commands:
![[Pasted image 20241108160240.png]]
![[Pasted image 20241108160336.png]]

# QUIZ

![[20241108-1035-17.5754213.mp4]]

![[Pasted image 20241108161348.png]]
# QUIZ
![[20241108-1045-33.1761038.mp4]]

LLDP PROTOCOL 
![[Pasted image 20241108161850.png]]

# QUIZ
![[20241108-1050-16.8195959.mp4]]
CLI
![[Pasted image 20241108171233.png]]

# QUIZ
![[20241108-1145-23.4373996.mp4]]

# IPv6 addressing

# QUIZ
![[20241109-1833-12.4865645.mp4]]

# QUIZ
![[20241109-1839-12.9607618.mp4]]
SHRINKING IPV6
![[Pasted image 20241110001153.png]]
SUBNETTING
![[Pasted image 20241110001411.png]]

# interface naming and logical units
![[Pasted image 20241110002435.png]]

![[Pasted image 20241110003201.png]]

# QUIZ
![[20241109-1904-40.6558947.mp4]]

![[Pasted image 20241110003725.png]]
![[Pasted image 20241110003938.png]]
# QUIZ
![[20241109-1910-19.0523914.mp4]]

![[Pasted image 20241110004417.png]]

# QUIZ
![[20241109-1915-18.4703748.mp4]]


# # Network Interfaces, Part 2 - Revealing and Filtering Detailed Interface Output

![[Pasted image 20241110135558.png]]

```
router>show interfaces extensive <interface_number>
```

# QUIZ

![[20241110-0837-03.7186657.mp4]]

FILTERING OPTION MADE EASSY 
![[Pasted image 20241110140808.png]]

COUNTING ![[Pasted image 20241110141004.png]]

# QUIZ
![[20241110-0843-21.6280196.mp4]]

# Reading a JUNOS OS configuration
# QUIZ
![[20241110-0908-20.8957922.mp4]]

![[Pasted image 20241110144137.png]]

Top level hierarchical
![[Pasted image 20241110144412.png]]

![[Pasted image 20241110144501.png]]

# QUIZ
![[20241110-0915-25.4661620.mp4]]

Specific viewing ![[Pasted image 20241110145358.png]]

Management services are enabled on the services sub-hierarchy
![[Pasted image 20241110150323.png]]
# QUIZ
![[20241110-0936-24.0723067.mp4]]

![[Pasted image 20241110150858.png]]
Similarly for guest LAN
![[Pasted image 20241110151422.png]]

# QUIZ
![[20241110-0945-08.4128614.mp4]]
RED color are top level hierarchy
BLUE color are sub level hierarchy
![[Pasted image 20241110151731.png]]

# QUIZ 
![[20241110-0950-42.3470622.mp4]]

# ACTIVITY 01
![[20241110-1001-25.7720927.mp4]]
![[20241110-1017-06.4673436.mp4]]


# JUNOS CONFIG (THE BASICS)

changing the host name 
```
router>configure
router# set system host-name router_1
```

![[Pasted image 20241111230109.png]]
Scraping all my proposed configuration
```
router# rollback 1
```
 here rollback will overwrite the candidate configuration by the user giving the active configuration
# Quiz
![[20241111-1734-45.2419544.mp4]]
command to see whatever the user made changes
```
router# show system commit
```

THIS  IS HOW JUNOS CORRECTION WORKS IF WE DO COMMIT 
![[Pasted image 20241111231504.png]]
USE COMMIT CHECK TO VERIFY THE CONIFGURATION IS VALID BUT NOT SAVES 
```
router# commit check
```

# QUIZ
![[20241111-1746-57.6515531.mp4]]

CONFIGURING NEW INTERFACES
 To add a new ip in the interfaces
 ```
 router# set interfaces xe1/1/0 unit 0 family inet6 address <ip_address>
```
![[Pasted image 20241111232511.png]]

# QUIZ
![[20241111-1756-58.9339927.mp4]]

EDITING AND DELETING CONFIGURATION
![[Pasted image 20241111232929.png]]
USING DELETE COMMAND WILL DELETE THE EXISTING/OLD  IP IN THE INTERFACES
```
router# delete interfaces xe1/1/0 unit 0 family inet address <ip_address>
```

hierarchy method deleting the configuration 
![[Pasted image 20241111234249.png]]

# QUIZ
![[20241111-1816-33.5416504.mp4]]

COMMIT CONFIRMED
 AUTOMATICALLY ROLL BACK IN 2  MINUTES UNLESS COMMIT CONFIRMED
 ![[Pasted image 20241111235139.png]]

![[Pasted image 20241111235523.png]]

# QUIZ
![[20241111-1826-18.3308770.mp4]]

# JUNOS OS (POWER USER)

Two user entering into the configuration mode 
![[Pasted image 20241112105359.png]]

Lock the candidate configuration 
```
employee@router# configure exclusive
```
if the user wants needs a private configuration tab to config
```
router> configure private (creates multiple candidate configuration)
```

In this case if two user are using the same private config mode at the same time 
```
router> config private
router# set system host-name <name>
router# commit and-quit
```
Commit at certain time
```
router# commit at "yyyy-mm-dd" "hrs-m-s"
```

# QUIZ
![[20241112-0537-44.6411443.mp4]]

DEACTIVATING AND DISABLING DIFFERENT TYPE OF PEICES OF CONFIGURATION

```
router# set interfaces xe-1/1/0 disable
```
To undisable the interface 
```
router# delete set interfaces xe-1/1/0 disable
```

Deactivating the physical interface
```
router# deactivate interface xe-1/1/0
```
 reactivate the interface
 ```
 router# activate interfcace xe-1/1/0
```

# QUIZ
![[20241112-0555-02.6920784.mp4]]

DEPLOYING CONFIGURATION WITHIN A HIERARCHY
 SHORTER COMMADS
 ```
 router#set family inet address <ip_address>
```

# QUIZ 
![[20241112-0605-42.5602010.mp4]]

![[Pasted image 20241112143223.png]]
 RESULT 
 ![[Pasted image 20241112143423.png]]

renaming the interfaces
```
router# rename interfaces xe-1/1/0 to xe-1/1/1
```

# QUIZ
![[20241112-0937-11.2173154.mp4]]
keyboard shortcuts:
ctrl+w - delete one word at a time
ctrl+A -Begin at the cmd
ctrl+e moves to the end
esc+b - moves backward
esc+f - moves forward
ctrl+k -deletes after that cursor

# QUIZ
![[20241112-0942-45.3900513.mp4]]

![[Pasted image 20241112154850.png]]

STATIC ROUTES:
Configured by the system administarator
DYNAMIC ROUTES:
LEARN
ADVERTISE
RE-ADVERTISE

# QUIZ
![[20241112-1345-53.9756043.mp4]]

# QUIZ
![[20241112-1742-38.8080264.mp4]]
# SUBNETTING
![[Pasted image 20241112231527.png]]
 BASED ON THE PREFIX IT WILL BE CHOOSEN 
 ![[Pasted image 20241112232325.png]]

NOTE:
```
- **Static routes** have an administrative distance of **1** (or a custom value if configured otherwise, such as `5` in this example).
- **OSPF (Open Shortest Path First)** has an administrative distance of **110**.
```

# QUIZ
![[20241112-1803-58.9408390.mp4]]

TO VIEW THE ROUTING TABLE IN THE JUNOS DEVICES
```
router> show route table inet.0
or 
router> show route <ip_address>
```

# QUIZ
![[20241112-1812-08.4195059.mp4]]

# STATIC ROUTES
# QUIZ
![[20241112-1827-37.8491981.mp4]]

CONFIGURING STATIC ROUTES:
```
router# set routing-options static route <ip_address> next hop <ip_address>
```
you can verify by using this command:
```
router# show | compare
```
![[Pasted image 20241113000626.png]]
when using with ipv_6
use routing information base
```
router# set routing -options rib inet6.0 static route <ip_address(6)> next hop <ip_address(6)>
```
# QUIZ
![[20241112-1840-02.1691868.mp4]]
VIEW ROUTING FOR A SPECIFIC PREFIX
```
router# show route 0/0 exact
```
check whether you specific ip address matches with the default route
```
router# show route <ip_address>
```
# QUIZ
![[20241112-1846-58.4665167.mp4]]


# DYNAMIC ROUTING
# QUIZ
![[20241112-1904-42.8978608.mp4]]
TYPES
![[Pasted image 20241113003554.png]]

distance vector protocol
RIP(rareley used)

![[20241112-1908-09.5659927.mp4]]
link state protocol
OSPF
IS-IS

# QUIZ
![[20241112-1916-41.7738249.mp4]]
# CONFIGURING OSPF

```
router# set protocols ospf area 0 interface xe-1/1/0
```
verify the connection using
```
router# show ospf neighbour
```
![[Pasted image 20241113005658.png]]

# QUIZ
![[20241112-1928-58.3734192.mp4]]

# QUIZ
![[20241112-1933-27.3353365.mp4]]

![[Pasted image 20241113010604.png]]

# QUIZ
![[20241112-1937-38.8758969.mp4]]
Creating OSPFv2 neighbor adjaceny
```
router> configure
router# delete routing-options static route
router# delete routing-options rib inet6.0 static route <ip address(6)>
router# show | compare
router# commit
router# set protocols ospf area 0 interface
router# show | compare
router# commit and-quit
router#show ospf neighbor
router# show  route protocol ospf
```

# passive modes

```
router> show interfaces description
router> configure
router# set protocols ospf area 0 interface ge-0/0/1.0 passive
```

# OSPF_3 NEIGHBOR ADJANCY
```
router>configure
router# set protocol ospf3 area 0 interface ge-0/0/0.5
router# show route <ip_address(6)>
```

# ACTIVITY 2

![[20241112-1951-33.0577943.mp4]]
# # Junos OS Switches, Part 1 - VLANs, MAC Tables, and Access Ports
two ranges of series ex and qfx 
![[Pasted image 20241113021718.png]]
![[Pasted image 20241113021804.png]]

# QUIZ
![[20241112-2048-42.7682939.mp4]]
ADDING A VLAN IN A SWITHC
```
switch# set vlans Guest vlan-id 20
switch# show | compare
switch# commit and-quit
```

# QUIZ
![[20241112-2102-01.3360451.mp4]]

CONFIGURING ACCESS PORTS and VERIFYING MAC-TABLES
![[Pasted image 20241113024656.png]]

HERE THE ASTERISK SYMBOL SHOWS THAT THE INTERFACE IS UP 
![[Pasted image 20241113024732.png]]
VERIFYING THE MAC TABLE
```
switch# show ethernet-switching table <specific_vlan>
```
# QUIZ
![[20241112-2119-44.4558600.mp4]]

# TRUNK PORTS ON JUNOS OS SWITCHES
REPLACING 3 PORTS BY 1 PORT 
![[Pasted image 20241113135838.png]]

```
router# edit interfaces xe-0/1/0
router# set description "Trunk ports in router"
router# set unit 0 family ethernet switching interface-mode trunk

By allowing the vlan in that interfaces

router# set unit 0 family ethernet switchin vlan members [ multiple vlan names]
router# set vlan memebers all
```
By default lldp is enabled default on all interfaces in the switches

# QUIZ
![[20241113-0944-30.4937254.mp4]]
![[Pasted image 20241113151954.png]]

# quiz
![[20241113-0957-22.1318548.mp4]]

These 5 commands will replace the 9 lines of configuration 

```
router# delete protocols lldp
router# set protocols lldp interface xe-1/1/0
router# replace pattern xe-1/1/1.0. with xe-1/1/10.0
router# replace pattern xe-1/1/2.0 with xe-1/1/20.0
router# replace pattern xe-1/1/3.0 with xe-1/1/30.0
router# commit and-quit
```


# QUIZ
![[20241113-1006-43.1748251.mp4]]

![[Pasted image 20241113154051.png]]

# QUIZ
![[20241113-1016-39.1774408.mp4]]
VERIFYING TH EXISTING CONFIGURATION
```
router# show configuration interface xe-1/0/0 | display set
```

Configuring the new interface with multiple units

```
router> configure
router# deactivate interface xe-1/0/0
router# show | compare
router# commit
router# run show interface terse xe-1/0/0
router# set interface ge-0/0/0 vlan tagging
router# set interface ge-0/0/0 description " Trunk interface for mutliple vlans"
router# set interface ge-0/0/0 unit 10 description "corporate Vlan"
router# set interface gr-0/0/0 unit 10 vlan-id 10
router# set interface unit 10 family inet address <ip_address>
router# set interface unit 10 family inet6 address <ip_address(6)>
router# show | compare
router# commit
router# run show interface ge-0/0/0 terse
router# run show interfaces ge-0/0/0.10 detail | match vlan
```

Fixing the protocol configuration on the devices
```
router# delete interfaces ge-0/0/1
router# show | compare
router# show configuration | display set | match ge-0/0/[1-3]
router# commit
router> configure
router# delete protocols lldp
router# set protocols lldp interface ge-0/0/0
router# show | compare
router# commit
router# replace pattern ge-0/0/1.0 with ge-0/0/10.0
router# show | compare
router# commit
router> configure
router# show lldp neighbors
router# show route protocol ospf
```

# OUT OF BAND MANAGEMENT INTERFACES

# QUIZ
![[20241113-1048-19.8179547.mp4]]
![[Pasted image 20241113162024.png]]
MANUALLY SETTING THE TIME IN JUNOS
```
router# set system time-zone US/Eastern( in config mode)
router> set date <yyyymmddhhmm>
router> show system uptime
router# set system ntp server <ip_address>
```
 To see the status of each server
 ```
 router# show ntp associations
```

# QUIZ
![[20241113-1057-29.8865988.mp4]]

# DNS RESOLUTION IN ROUTER

Configuring the dns server
```
router# set system name-server <ip_address of the dns server>
router# commit and-quit
```
# QUIZ
![[20241113-1101-23.0050460.mp4]]
USER ACCOUNT CONFIGURATION
```
router# show configuration system login user employee | display set
```
changing the password for existing users
```
router# set system login user employee authentication plain-text-password
router# commit and-quit
```

# QUIZ
![[20241113-1108-10.9252896.mp4]]
FOUR DEFAULT USERS IN THE JUNOS:
```
Super-user
unauthorized
operator
read-only
```
permission flags
![[Pasted image 20241113164057.png]]


# QUIZ
![[20241113-1207-56.0820332.mp4]]

CONFIGURING J-WEB ACCESS:
![[Pasted image 20241113200449.png]]

# QUIZ

![[20241113-1436-33.5357050.mp4]]

# Setting up a brand new JUNOS device out of the box

# QUIZ
![[20241113-1455-33.9433677.mp4]]

Using the console port making configuration:

RJ45/8P8C connector
console connecting cables:
DB9 connector
USB connector

![[Pasted image 20241113202846.png]]

amnesiac means the device doesnt have a host name
![[Pasted image 20241113203238.png]]
ON a new device by doing all commits will reject until you set a admin pwd
```
router# set system root-authentication plain-text-password
```

# QUIZ
![[20241113-1504-57.9828524.mp4]]

SETTING FOR A NEW DEVICE:
![[Pasted image 20241113203718.png]]
SETTING SYSTEM MESSAGE ON LOGIN SCREEN
```
router# set system login message "<message>"
```
USING ANNOUNCEMENT WE CAN SAY 
```
router# set system login announcement "<line_1>\n<line_2>\n"
```
# QUIZ
![[20241113-1512-23.5010969.mp4]]
# CONTROL PLANE AND DATA PLANE
![[Pasted image 20241116181709.png]]

# QUIZ
![[20241116-1249-49.7608048.mp4]]

![[Pasted image 20241116182230.png]]

![[Pasted image 20241116183814.png]]

# QUIZ
![[20241116-1313-08.5967341.mp4]]
![[Pasted image 20241116184747.png]]

# QUIZ
![[20241116-1323-38.7192548.mp4]]

KERNAL & SHELL
![[Pasted image 20241116185742.png]]

# QUIZ
![[20241116-1329-40.4697375.mp4]]

Daemons:
Routing protocols
Management
device control -sending physical interface into the ports
chassisid - alarms,electric supply fans

![[Pasted image 20241116191452.png]]

# QUIZ
![[20241116-1346-27.5786894.mp4]]

![[Pasted image 20241116192026.png]]

# QUIZ
![[20241116-1351-02.5968948.mp4]]

# Logging troubleshooting & monitoring

```
router> show log messages
```
Logs will be displayed under the system syslog hierarchy
```
router> show configuration system
```
syslog severity levels:
![[Pasted image 20241117110902.png]]

Configuring a new log file
```
router# set system syslog file <filename.txt> deamon info
router# set system syslog file <filename.txt> files 3 size 1M world-readable
router# show | compare
router# commit and-quit
```
Viewing log entries in a real time:
```
router> monitor start messages
```
if u cant identify the services code you can decode by using help:
```
router> help syslog <message>
```
setting syslog into the external server
```
router# set system syslog host <ip_address_of_external_server/domain_name> any notice
```
# QUIZ
![[20241117-0546-56.0580618.mp4]]

![[Pasted image 20241117112650.png]]

this is the default mtu for layer 3 interface


tracroute:
 3 packet of ttl(ipv4) and sends 1 hop limit(ipv6)
 when the next hop reaches it sets the ttl to zeros and generates an icmp ttl exceeded and each round increase the ttl/hop limit by 1
![[Pasted image 20241117113354.png]]

# QUIZ
![[20241117-0644-08.1389266.mp4]]

Viewing live statistics and exception traffic
```
router> monitor interface traffic
```
![[Pasted image 20241117122141.png]]
this number matches enable us to verify the neighborship is to be successful
# QUIZ
![[20241117-0653-03.3038675.mp4]]

```
router> help reference <services>
```
It will gives you the entire configuration from how to do 
# QUIZ
![[20241117-0659-04.1197668 1.mp4]]
```
router> show log interactive-commands
```
It will displays the log files and their contents
```
router> show log interactive-commands | match user
```
filter based on user
```
router> show log interactive-commands | match user | last 15
```
it shows the 15 most log entries
```
router> show log messaged | last 30
```
timestamps
```
router> show log messages | match "down|error"
```

# Activity 3

![[20241117-0721-44.9140525.mp4]]

# JUNOS OS FIREWALL FILTER

Statefull security and stateless firewall policy

- **Stateless Filtering**: Does not track connection states. Each packet is filtered based on predefined rules.(firewall hirerachy)
- **Stateful Filtering**: Tracks the state of connections and ensures that only packets belonging to an established session are allowed.(security hierarchy)

# QUIZ
![[20241117-0803-01.6157373.mp4]]

Firewall filters:
![[Pasted image 20241117134142.png]]
Non-terminating actions of firewall :
![[Pasted image 20241117134655.png]]

# QUIZ
![[20241117-0817-11.4732962.mp4]]

Processing terms in firewall filters
![[Pasted image 20241117135350.png]]

Every firewall filter has default term of implicit term

# QUIZ
![[20241117-0825-01.2176280.mp4]]
All stateless filters are configured under the firewall hierarchy :
format for configuring a firewall in JUNOS OS device
```
router# set firewall family inet  filter <filter_name> term <term_name> from MATCH CONDITIONS
router# set firewall family inet  filter <filter_name> term <term_name> from ACTIONS
```

# QUIZ
![[20241117-0915-26.0163650.mp4]]
Firewall filter counter verification
```
router> show firewall counter <name_of_vlan> filter LAN TO WAN
```
# QUIZ
![[20241117-0929-55.5559689.mp4]]

Reject -It drops and send the icmp packet to the destination
Discards- Completely drops the packet 

# QUIZ
![[20241117-0939-17.1420496.mp4]]

CREATING A SIMPLE FIREWALL FILTER:
```
router> configure
router# edit firewall family inet filter <FILTER FROM ROUTER_2>
router# set term BLOCK_FROM_PING_FROM_40-1 from source-address <ip_address>
router# set term BLOCK_FROM_PING_FROM_40-1 from icmp-type echo-request
router# set term BLOCK_FROM_PING_FROM_40-1 from icmp-type echo-reply
router# set term BLOCK_FROM_PING_FROM_40-1 then discard
router# top
router# set interfaces <interface_name> unit 0 family inet filter input <FILTER FROM ROUTER_2>
router# show | compare
router# commit and-quit


lab@desktop:~$ ssh <username>@<ip_>
### packet loss ###
```

FIXING A BROKEN FIREWALL FILTER:
```
router# edit firewall family inet filter <FILTER FROM ROUTER_2> 
```
Creating a new term:
```
router# set term ACCPET-ALL_FROM_ROUTER_2 from source-address <ip>
do this if we you need to want to send traffic from different vlan/device
router# set term ACCPET-ALL_FROM_ROUTER_2 then accept
router# top
router# show | compare
router# commit and-quit
```
INSERTIN A NEW TERM INTO A FIREWALL FILTER
```
router> show ospf neighbor
router> configure
router# edit firewall family inet filter <FILTER FROM ROUTER_2>
router# set term <BLOCK_FROM_ROUTER_2_ROUTER_1> from source-address <ip>
router# set term <BLOCK_FROM_ROUTER_2_ROUTER_1> then discard
router# show | compare
router# commit
router# insert term <BLOCK_FROM_ROUTER_2_ROUTER_1> before term ACCPET-ALL_FROM_ROUTER_2
router> show ospf neighbor
### If it doesnt shows seems to be broken ###
router>configure
router# edit firewall family inet filter <FILTER FROM ROUTER_2>
router# set term <BLOCK_FROM_ROUTER_1_TO_ROUTER_2> from destination-address <ip>
router# set term <BLOCK_FROM_ROUTER_1_TO_ROUTER_2> from protocol tcp
router# set term <BLOCK_FROM_ROUTER_1_TO_ROUTER_2> from destination-port ssh
router# show | compare
router# commit
router# run show configuration firewall
### All will work fine ###
```


On router_1
```
router# set term <ACCEPT_ALL_FROM_ROUTER_2> then count COUNT_FINAL_TERM
router# show | compare
router# top
router# commit
router> show firewall filter from COUNT_FINAL_TERM filter <ACCEPT_ALL_FROM_ROUTER_2>
### You can verify by executing this command ###
router> ping <d_ip> source <ip> count 99 rapid size 1472
```

# Interfaces deeper dive

Configuration of Loopback interfaces to access via ssh

```
router# interfaces lo0 unit 0 family inet address <ipv4orv6>
#### setting ospf in a loopback ###
router# set protocols ospf area 0  interface lo0.0
router# set protocols ospf3 area 0  interface lo0.0
```
 IRB interface configuration:
 
```
router# set interfaces irb unit <id> family inet address
### VLAN configuration ###
switch# set vlan <vlan_name> 13 interface irb.10
```

# QUIZ
![[20241117-1040-08.4359220.mp4]]

Primary and prefered ip  address
![[Pasted image 20241117161724.png]]

# QUIZ
![[20241117-1047-59.8361880.mp4]]

LINK AGGREGATION GROUP:
# QUIZ

![[20241117-1256-15.5029005.mp4]]

# LAG
A LAG is a method of combining multiple physical network interfaces into a single logical interface to improve bandwidth, redundancy, and reliability
 
 
 STEPS TO CREATE A LINK AGGREGATION GROUPS:
 
 1.Configure the quantity of interfaces you need
 2.configure with ae itself 
 3.add your link into the bundle

Configuring JUNOS to enable the interface:
```
router# set chassis aggregated-devices ethernet  device-count 1
```
the device-count 1 -- interface ae0.

```
router# set interface aggregated ae0 unit 0 family inet address <ip>
router# set interface aggregated ae0 aggregated-ether-option lacp active
```
LACP -link aggregation control protocol

It checks this link is part of lag bundle
```
router# set interface <interface_name> gigether-options 802.3ad ae0
```
![[Pasted image 20241117184115.png]]

```
router# show | compare
router# commit
router> show interfaces terse | match ae0
```
# QUIZ
![[20241117-1315-45.3446051.mp4]]

ANNOTATE,LOCK AND REDACT BE SHRUNK DOWN:
```
router> show configuration | no-more
```
No-more -- will show the entire hierarchical view not by tapping the spacrbar

Hidding the filter in the JUNOS :
```
router# firewally family inet filter <filter_name> apply-flags omit
```
Protecting the config hierarchy :
```
router# protect protocols lldp
router# show | compare
router# commit and-quit
```
Leaving comments on the config:
```
router# annotate system  "message"
router# edit system
router# annotate hostname " message"
router# commit and-quit
```

# QUIZ
![[20241117-1340-23.8065820.mp4]]

Viewing JUNOS file using list:
```
router> file list
router> show <filename>  ### view the content of the file###
```
Saving CLI output as text file using save:
```
router> show interfaces terse | save <file_name>.txt
router> file list
```
comparing your configuration to any local file
```
router> show configuration | compare <file_name>.txt
```
Comparing the difference between two text files:
```
router> file compare files <file_name>.txt <file_name>.txt
```

Line numbers:
a-addition
c-changes
d-deletion

FTP AND SCP :
```
router> file copy scp://<user_name>@<ip>/lab/configs/<file_name>.txt  /var/tmp
router> file copy /var/tmp/<file_name>.txt scp://<user_name>@<ip>/lab/configs
```

# QUIZ
![[20241117-1351-30.8912082.mp4]]

Complete replace of existing config with new candidate config:
```
router# load override <file_name>
```

Load merge terminal is same as the set command we used so far

# QUIZ
![[20241117-1412-27.9027165.mp4]]

Automating aspects of JUNOS OS configs
![[Pasted image 20241117194859.png]]
Using apply-groups for automated ,consistent configs

```
router# set groups MTU_9192_GROUP interfaces <xe-*> mtu 9192
router# commit and-quit
```
Viewing the results of apply-configs:
```
router> show configuration interfaces <interface_name> | display inheritance
```


![[Pasted image 20241117200614.png]]

# QUIZ
![[20241117-1436-56.1076346.mp4]]

# XML API's

```
router> show system information | display xml
```

![[Pasted image 20241117233337.png]]

![[Pasted image 20241117233808.png]]

# QUIZ
![[20241117-1808-36.3825691.mp4]]

# ACTIVITY 4





# Backup static routes ,routing instances, OSPF areas and BGP

Viewing the current static routes on the router
```
router> show configuratioin routing-options | display set
```
![[Pasted image 20241118095052.png]]


A numerically higher preference indicates lower priority.

![[Pasted image 20241118095640.png]]

This configuration is commonly used for **redundancy** in networks. If the primary route goes down (e.g., due to a link or device failure), the backup route ensures continuous network connectivity.


Hierarchical configuration :
```
router> show configuration routing-options static
```

When a static route is configured with a next-hop IP that is **not directly reachable** via a connected interface, the `resolve` option allows the router to find a route to the next-hop IP using another existing route in the routing table

![[Pasted image 20241118101046.png]]

- The configuration brings dynamic-like behavior to static routes by letting the network determine the best route to reach the specified next-hop address, as seen in Junos OS.
- This is useful when there are multiple paths to the same destination, like the LAN `172.16.99.0/24` in this diagram.

```
router# set routing-options static route 192.168.200.0/24 next-hop 172.16.10.5 no-readvertise

```

When static routes are configured in a network, they can be advertised into dynamic routing protocols like OSPF, BGP, etc., making them known to other routers in the network. However, not all static routes are intended to be shared.

![[Pasted image 20241118102503.png]]
![[Pasted image 20241118102749.png]]

![[Pasted image 20241118103149.png]]

OSPF:
![[Pasted image 20241118103549.png]]

EGP tends to slow because of this:
![[Pasted image 20241118104022.png]]
BGP USES THE AUTONOMOUS SYSTEM HOP COUNT INSTEAD OF USING THE ROUTER HOP COUNT
![[Pasted image 20241118104517.png]]

# FIREWALL -DEEPER DIVE
![[Pasted image 20241118105228.png]]

![[Pasted image 20241118105307.png]]

AUTOMATIC PREFIX LIST:
```
router# set policy-options prefix-list DIRECT_IP apply-path "interface<*> unit<*> family inet address <*>" 
```
apply-path says find all subnets configured on all interfaces within the interface hierarchy
```
router# router# set policy-options prefix-list DIRECT_IP | display inheritance
```
To see the automated prefix-lists
![[Pasted image 20241118105922.png]]
![[Pasted image 20241118110239.png]]

![[Pasted image 20241118110402.png]]

![[Pasted image 20241118110440.png]]
Logging traffic:
```
router> show firewall log
```
Clear the logs using :
```
router> clear firewall log
```
![[Pasted image 20241118110829.png]]
Tracking all logs using syslog:
![[Pasted image 20241118110904.png]]

![[Pasted image 20241118111300.png]]

firewall filter :
![[Pasted image 20241118111420.png]]

![[Pasted image 20241118111457.png]]
Things to consider while setting  a firewall filter :
![[Pasted image 20241118111559.png]]
With Routing instances:
![[Pasted image 20241118111634.png]]
Class of service :
It prioritize the important traffic
It can rate limit certain traffic to avoid oversaturation(policing)

```
router> show class-of-service forwarding-class
```

![[Pasted image 20241118112257.png]]
 Configuring policier
 ![[Pasted image 20241118112457.png]]
![[Pasted image 20241118112523.png]]
![[Pasted image 20241118112617.png]]
![[Pasted image 20241118112732.png]]
![[Pasted image 20241118113319.png]]

![[Pasted image 20241118113416.png]]
![[Pasted image 20241118113454.png]]

# Logging & Troubleshooting & Monitoring

![[Pasted image 20241118113851.png]]

Configuration part of SNMP:
![[Pasted image 20241118114037.png]]

![[Pasted image 20241118114051.png]]

![[Pasted image 20241118114107.png]]

After doing this :
```
router# show | compare  
router# commit and-quit
```
NMS cannot communicate with layer 2 devices
If you put your NMP on the same LAN subnet as the management interfaces on the devices you NMS has full connectivity to all the devices

![[Pasted image 20241118114408.png]]
![[Pasted image 20241118114440.png]]

![[Pasted image 20241118114509.png]]

![[Pasted image 20241118114537.png]]

![[Pasted image 20241118114558.png]]
![[Pasted image 20241118114656.png]]

Keywords for traceoptions:
![[Pasted image 20241118114723.png]]


![[Pasted image 20241118114843.png]]

![[Pasted image 20241118115200.png]]

![[Pasted image 20241118115458.png]]
Describing the error information that are available in the show interfaces extensive command

7 sections:
![[Pasted image 20241118115609.png]]

![[Pasted image 20241118120051.png]]
Check CPU,temperature, memory:
```
router> show chassis routing-engine
```

![[Pasted image 20241118120202.png]]
Check who is logged:
```
router> show system users
```
You can kick of the user:
```
router> request system logout <user_name>
```

![[Pasted image 20241118120332.png]]

# JUNOS OS DEVICE ADMINSTRATIONS

![[Pasted image 20241118120851.png]]

![[Pasted image 20241118120915.png]]

![[Pasted image 20241118120926.png]]

CONFIGURING AUTHENTICATION:
![[Pasted image 20241118120947.png]]

![[Pasted image 20241118121042.png]]
![[Pasted image 20241118121100.png]]

![[Pasted image 20241118121115.png]]

![[Pasted image 20241118121128.png]]

![[Pasted image 20241118121212.png]]

![[Pasted image 20241118121237.png]]
![[Pasted image 20241118121308.png]]
 ORDER IN WHICH IT IS BEING PROCESSED :
 ![[Pasted image 20241118121340.png]]
![[Pasted image 20241118121501.png]]

![[Pasted image 20241118121519.png]]

![[Pasted image 20241118121834.png]]

![[Pasted image 20241118121908.png]]

# ROUTING POLICY 
![[Pasted image 20241118122306.png]]
![[Pasted image 20241118122339.png]]

![[Pasted image 20241118122405.png]]

![[Pasted image 20241118122459.png]]





![[Pasted image 20241118122711.png]]

![[Pasted image 20241118122754.png]]

![[Pasted image 20241118123021.png]]

![[Pasted image 20241118123125.png]]

![[Pasted image 20241118123247.png]]

![[Pasted image 20241118123307.png]]

![[Pasted image 20241118123330.png]]

![[Pasted image 20241118123414.png]]
![[Pasted image 20241118123611.png]]
![[Pasted image 20241118123659.png]]
# Upgrading JUNOS -OS
![[Pasted image 20241118124626.png]]
![[Pasted image 20241118124749.png]]


![[Pasted image 20241118124841.png]]

![[Pasted image 20241118124936.png]]

![[Pasted image 20241118125009.png]]
![[Pasted image 20241118125032.png]]


```
switch> file list /var/tmp
```

![[Pasted image 20241118125158.png]]
after upgrading reboot the device:
```
switch> request system reboot
```
![[Pasted image 20241118125254.png]]
![[Pasted image 20241118125344.png]]

![[Pasted image 20241118125400.png]]

![[Pasted image 20241118125436.png]]
# J-WEB
![[Pasted image 20241118125730.png]]

# CABLES & ETHERNET
![[Pasted image 20241118131030.png]]

![[Pasted image 20241118131344.png]]

![[Pasted image 20241118131406.png]]

![[Pasted image 20241118131451.png]]

![[Pasted image 20241118131549.png]]

![[Pasted image 20241118131627.png]]

![[Pasted image 20241118131724.png]]

![[Pasted image 20241118131837.png]]

![[Pasted image 20241118132022.png]]


![[Pasted image 20241118132059.png]]

![[Pasted image 20241118132117.png]]


![[Pasted image 20241118132130.png]]

![[Pasted image 20241118133012.png]]


# IPv4 & SUBNETTING
![[Pasted image 20241118132327.png]]
![[Pasted image 20241118132412.png]]

![[Pasted image 20241118132508.png]]

![[Pasted image 20241118132553.png]]
![[Pasted image 20241118132634.png]]
![[Pasted image 20241118132705.png]]
![[Pasted image 20241118132728.png]]

![[Pasted image 20241118132806.png]]

![[Pasted image 20241118132835.png]]

![[Pasted image 20241118132855.png]]

![[Pasted image 20241118132913.png]]

![[Pasted image 20241118132939.png]]


# Refresher - Switches, MAC Learning, Broadcast Domains, and VLANs

![[Pasted image 20241118133324.png]]

![[Pasted image 20241118133347.png]]

![[Pasted image 20241118133409.png]]
![[Pasted image 20241118133440.png]]
![[Pasted image 20241118133522.png]]

![[Pasted image 20241118133539.png]]

![[Pasted image 20241118133556.png]]

![[Pasted image 20241118133612.png]]

![[Pasted image 20241118133627.png]]

![[Pasted image 20241118133645.png]]

![[Pasted image 20241118133658.png]]

![[Pasted image 20241118133717.png]]

![[Pasted image 20241118133802.png]]

![[Pasted image 20241118133817.png]]

![[Pasted image 20241118133832.png]]

# Refresher - TCP and UDP
![[Pasted image 20241118144855.png]]

![[Pasted image 20241118145229.png]]


TCP 
**![[Pasted image 20241118145301.png]]**

![[Pasted image 20241118145600.png]]


![[Pasted image 20241118145645.png]]

![[Pasted image 20241118145952.png]]

![[Pasted image 20241118150046.png]]

![[Pasted image 20241118150111.png]]
