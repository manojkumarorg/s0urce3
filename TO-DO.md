Use cases:
**Primary ones** 
separate vlans:
*PC,LAP -10.1.72.0
*IOT - 10.1.73.0
*GUEST devices - 10.1.74.0 (Based on the no of systems if necessary )
*subnets based on users (policy for managing Ip & Ip addressing plan - dhcp)
*restrict access  between vlans -Inter-vlan routing if needed(Restrictions-traffic, resources)
*Topology - star or mesh
*Access level - Privileged/Non-privileged/outside environment ppl
vpn service in router (or) vm

base level restriction would be institution policy
2 vlan in one AP(LAP,mobiles/tablets):
1 vlan - all access
second vlan - restriction based on users level

Data Limits on VLAN Assignment(Qos)- L3

~~vm ware for authentication server(may be radius or some else)~~

~~**VPN Server on a Dedicated Device**: Set up a dedicated server or VM to handle VPN traffic, with RADIUS and LDAP integration.~~


![[Pasted image 20241113202008.png]]
tlsx3016F 
