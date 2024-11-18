### **Simple Network Configuration**  
#### **Devices**:  
- **1 Router**  
- **2 Switches**  
- **4 PCs**  
- **1 PT-Server**

---

### **Steps for Configuration**:  
#### **1. Device Interconnection**:  
Use copper Ethernet cables (UTP) to connect devices as follows:  
- **Router to Switch 1**:  
  - **Router (TX Pins 1,2)** to **Switch (RX Pins 1,2)**.  
- **Switch 1 to Switch 2**:  
  - Connect using a straight-through cable.  
- **Switches to PCs**:  
  - **Switch (TX Pins 3,6)** to **PC (RX Pins 3,6)**.

---

#### **2. Configure IP Addresses**:  
Assign IPs to each device in the same network/subnet. Example:  
- **Router Interface**: 192.168.1.1/24  
- **PC1**: 192.168.1.2/24  
- **PC2**: 192.168.1.3/24  
- **PC3**: 192.168.1.4/24  
- **PC4**: 192.168.1.5/24  
- **PT-Server**: 192.168.1.10/24  

---

#### **3. Configure the Router**:  
1. **Assign IP to Interface**:  
   ```bash
   Router(config)# interface <interface_name>
   Router(config-if)# ip address 192.168.1.1 255.255.255.0
   Router(config-if)# no shutdown
   ```
2. **Enable SSH for Remote Access**:  
   - **Step 1**: Verify SSH Support:  
     ```bash
     Router# show ip ssh
     ```
   - **Step 2**: Configure Domain:  
     ```bash
     Router(config)# ip domain-name example.com
     ```
   - **Step 3**: Generate RSA Keys:  
     ```bash
     Router(config)# crypto key generate rsa
     ```
   - **Step 4**: Add a User:  
     ```bash
     Router(config)# username admin secret password123
     ```
   - **Step 5**: Configure VTY Lines:  
     ```bash
     Router(config)# line vty 0 4
     Router(config-line)# login local
     Router(config-line)# transport input ssh
     ```
   - **Step 6**: Enable SSH Version 2:  
     ```bash
     Router(config)# ip ssh version 2
     ```

---

#### **4. Test Connectivity**:  
- Use the `ping` command from each PC to verify connectivity.  
- Example:  
  ```bash
  ping 192.168.1.1
  ping 192.168.1.10
  ```

---

### **Installing Cloudflare WARP on a Server**  
1. Add the Cloudflare WARP key:  
   ```bash
   curl https://pkg.cloudflareclient.com/pubkey.gpg | sudo gpg --yes --dearmor --output /usr/share/keyrings/cloudflare-warp-archive-keyring.gpg
   ```
2. Add the repository:  
   ```bash
   echo "deb [arch=amd64 signed-by=/usr/share/keyrings/cloudflare-warp-archive-keyring.gpg] https://pkg.cloudflareclient.com/ $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/cloudflare-client.list
   ```
3. Update and install:  
   ```bash
   sudo apt-get update && sudo apt-get install cloudflare-warp
   ```

---

### **Ethernet Cable Information**  
#### **Copper Ethernet Cables**:  
- **UTP (Unshielded Twisted Pair)**:  
  - No metallic shield, vulnerable to interference.  

#### **Pin Assignments**:  
- **10BASE-T/100BASE-T**: 2 pairs (4 wires).  
- **1000BASE-T/10GBASE-T**: 4 pairs (8 wires).  

| Device A          | Device B          | TX Pins | RX Pins |  
|--------------------|-------------------|---------|---------|  
| **Router**         | **Switch**        | 1,2     | 1,2     |  
| **Switch**         | **PC**            | 3,6     | 3,6     |  

---

### **Verification Commands**  
- **Ping Connectivity**:  
  ```bash
  ping <destination_IP>
  ```
- **Check Routing**:  
  ```bash
  netstat -r
  ```
- **SSH Test**:  
  Use any SSH client (e.g., `ssh admin@192.168.1.1`).
