### **Ethernet Switching Overview**

Each Ethernet Network Interface Card (NIC) has a unique address permanently embedded, known as the **MAC address** (Media Access Control address). This address ensures that each device on the network can be uniquely identified.

---

### **MAC Table and Timeout**

- **5-minute Timeout**: The **MAC table** in a switch maps MAC addresses to specific ports. If a device is inactive for 5 minutes, its entry is removed from the table to keep it updated and prevent stale data.

---

### **How Switches Operate**

When a node communicates with another using the **`ping`** command via a switch:
- The switch sends the packet only to the specific destination node, using its MAC address.
- If the destination MAC address is not in the switch’s MAC address table, it will **flood the frame** to all ports except the incoming port.

---

### **Multilayer Switches (Layer 2/Layer 3)**

- **Multilayer Switch (L2/L3)**: 
   - Connects multiple switches and a single router.
   - If one switch fails, others continue to forward frames, maintaining network connectivity.
   - Typically used for efficient communication within larger networks.

- **Data Centers**:  
   - Nexus switches are commonly used in **core** and **distribution layers**.
   - **Spine-Leaf Architecture**: Spine nodes are connected to leaf nodes, typically used in large MNCs for high scalability and redundancy.

---

### **Ethernet Frame Structure**

The size of an Ethernet frame ranges from **64 bytes (minimum)** to **1518 bytes (maximum)**. Here's the breakdown of a typical Ethernet frame:

| Field                      | Size          |
|----------------------------|---------------|
| Preamble/SFD                | 8 bytes       |
| Destination MAC Address     | 6 bytes       |
| Source MAC Address          | 6 bytes       |
| Type/Length                 | 2 bytes       |
| Data                        | 45-1500 bytes |
| FCS (Frame Check Sequence)  | 4 bytes       |

- **0x0800** - IPv4 Protocol
- **0x0806** - ARP (Address Resolution Protocol)

---

### **Ethernet Standards**

For example, **802.3 100BASE-T**:
- **100** - Speed in Mbps
- **BASE** - Baseband transmission (all signals share a single channel)
- **T** - Twisted-pair cable
- **Data Link Layer (LLC)** - 802.2
- **Physical Layer (MAC)** - 802.3

---

### **Security Configuration Example (Cisco Switch CLI)**

```bash
Switch> en
Switch# conf t
Switch(config)# hostname Office-SW2
Switch(config)# line con 0
Switch(config-line)# password Cisco123
Switch(config-line)# login
Switch(config-line)# end
SwitchOffice-SW2#
```

---

### **Network Controller Configuration**

- **Adding a Switch**:  
   When adding a new switch to the network using a laptop, you configure it to allow the network controller to monitor and manage the network effectively.
   
- **Adding Student Profile**:  
   The controller adds a student profile, allowing for network monitoring and management based on that user's access.

---

### **Common Commands and Use Cases**

1. **What is the use case of adding new discovery in the network controller?**  
   The discovery process ensures that new devices joining the network are found and recognized, like sending out a search party to locate new devices.

2. **What is the use case of the command "interface vlan 20"?**  
   This command is used to configure settings for **VLAN 20** on the switch, allowing you to apply settings to a specific segment of the network.

3. **What is the use case of "username student privilege 1 password StudentPass"?**  
   This command creates a user account with **limited privileges** (privilege 1) and a password for access. The user can perform only basic actions based on the configured privileges.

---

### **MAC Address Table Operations**

- **If the destination MAC address is in the MAC table**:  
  The switch forwards the frame through the specific port.

- **If the destination MAC address is not in the MAC table**:  
  The switch will **flood** the frame to all ports except the incoming port.

- **For broadcast or multicast traffic**:  
  The switch floods the frame out all ports, except the incoming port.

---

### **Spanning Tree Protocol (STP)**

- **STP** (Spanning Tree Protocol) is used in Layer 2 networks to prevent loops by dynamically blocking redundant paths.
- It ensures a loop-free topology by selecting a **root bridge** and then determining the best path to each switch.

---

### **Firewall Configuration**

- **Internal Firewall Interface**: Connects to the **switch**.
- **External Firewall Interface**: Connects to the **router**.  
This setup ensures secure separation between the internal network and external resources, controlling traffic flow between them.

---

### **Console Port and Configuration**

- To configure a Cisco device, you typically connect via the **console port** using a **rollover cable**.
- **1 Stop Bit**: For each 8-bit data packet, a stop bit is used for synchronization during transmission.