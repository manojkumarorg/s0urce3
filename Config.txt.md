### Basic Commands and Configuration

**Secure all passwords in the config file:**
- `service password-encryption`

**MOTD Banner:**
```plaintext
# banner motd # Unauthorized access is strictly prohibited! #
```

**Show Commands:**
- `show running-config` : Display the current configuration of the router.
- `show ip route` : Display the routing configuration of the router.
- `show protocols`
- `show version`

**Routing Information Protocol (RIP):**
- RIP stands for Routing Information Protocol.

### Building a Small Cisco Network

#### Basic Switch Configuration

**Part 1:**

1. **Enable and configure terminal:**
    ```plaintext
    Switch> enable
    Switch# configure terminal
    Switch(config)# hostname S1
    S1(config)#
    ```

2. **Configure S1 with an IP address:**
    - An IP address is required to connect to a switch remotely, managed through VLAN1 by default.
    ```plaintext
    S1(config)# interface vlan 1
    S1(config-if)# ip address 192.168.1.253 255.255.255.0
    S1(config-if)# no shutdown
    %LINEPROTO-5-UPDOWN: Line protocol on Interface Vlan1, changed state to up
    S1(config-if)# end
    S1#
    S1# copy running-config startup-config
    Destination filename [startup-config]?
    Building configuration...
    [OK]
    S1# show ip interface brief
    ```

3. **Configure S2 with a hostname and IP address:**
    - Repeat the same steps as for S1.
    ```plaintext
    S2# show ip interface brief
    <output omitted>
    Vlan1 192.168.1.254 YES manual up up
    ```

**Part 2: Configure the PCs**

1. **Configure both PCs with IP addresses:**
    - **PC1:** IP address 192.168.1.1, Subnet mask 255.255.255.0
    - **PC2:** IP address 192.168.1.2, Subnet mask 255.255.255.0

2. **Test connectivity from the PCs:**
    - From PC1, ping S1:
    ```plaintext
    PC> ping 192.168.1.253
    ```
    - Repeat the pings to S1, S2, and PC1 from PC2.

3. **Verify network connectivity from the switches:**
    - From S1, ping PC1:
    ```plaintext
    S1> ping 192.168.1.1
    Sending 5, 100-byte ICMP Echos to 192.168.1.1, timeout is 2 seconds:
    Success rate is 100 percent (5/5), round-trip min/avg/max = 0/0/1 ms
    ```
    - From S2, ping PC1:
    ```plaintext
    S2> ping 192.168.1.1
    Sending 5, 100-byte ICMP Echos to 192.168.1.1, timeout is 2 seconds:
    Success rate is 100 percent (5/5), round-trip min/avg/max = 0/0/1 ms
    ```

### Basic Router Configuration

**Part 1: Verify the Default Router Configuration**

1. **Establish a console connection to R1:**
    - Connect the console cable to the router.
    - Open the terminal on PCA and select RS 232.
    - Click on R1 and choose Console.
    - In the PCA terminal, click OK and press ENTER to establish the console connection.

2. **Enter privileged mode and examine the current configuration:**
    - Enter privileged EXEC mode:
    ```plaintext
    Router> enable
    ```
    - Check the running configuration:
    ```plaintext
    Router# show running-config
    ```
    - Display the current contents of NVRAM:
    ```plaintext
    Router# show startup-config
    ```

**Part 2: Configure and Verify the Initial Router Settings**

1. **Configure the initial settings on R1:**
    - Set the hostname:
    ```plaintext
    Router(config)# hostname R1
    ```
    - Configure the MOTD banner:
    ```plaintext
    Router(config)# banner motd# Unauthorized access is strictly prohibited.#
    ```
    - Encrypt plain text passwords:
    ```plaintext
    Router(config)# service password-encryption
    ```
    - Set passwords:
    ```plaintext
    Router(config)# enable secret itsasecret
    Router(config)# line console 0
    Router(config-line)# password letmein
    Router(config-line)# login
    ```

2. **Verify the initial settings on R1:**
    - View the configuration for R1:
    ```plaintext
    Router# show running-config
    ```
    - Exit the current console session until you see "R1 con0 is now available."
    - Press ENTER; you should see the MOTD banner and be prompted for a password.

**Part 3: Save the Running Configuration File**

1. **Save the configuration file to NVRAM:**
    - Use the following command:
    ```plaintext
    Router# copy running-config startup-config
    ```
    - The shortest version of this command:
    ```plaintext
    Router# write
    ```
    - To display the contents of NVRAM:
    ```plaintext
    Router# show startup-config
    ```

2. **Optional: Save the startup configuration file to flash:**
    - Examine the contents of flash:
    ```plaintext
    Router# show flash
    ```
    - Save the startup configuration file to flash:
    ```plaintext
    Router# copy startup-config flash
    ```

### Securing Devices

**SSH Configuration:**
1. **Verify SSH support:**
    ```plaintext
    show ip ssh
    ```
2. **Configure the IP domain:**
    ```plaintext
    ip domain-name domain-name
    ```
3. **Generate RSA key pairs:**
    ```plaintext
    crypto key generate rsa
    ```
4. **Configure user authentication:**
    ```plaintext
    username username secret password
    ```
5. **Configure the vty lines:**
    ```plaintext
    line vty 0 15
    login local
    transport input ssh
    ```
6. **Enable SSH version 2:**
    ```plaintext
    ip ssh version 2
    ```

**ICMP and IPv6 Configuration:**
- ICMP Echo Message can be used to test the reachability of a host on an IP network.
- **RA messages** in IPv6 provide addressing information to hosts.
- **Duplicate Address Detection (DAD)** ensures the uniqueness of IPv6 addresses.

### Subnetting Example

- IP address: 172.21.42.0/24
- Subnets:
  - Guest: 10 hosts
  - Robots: 57 hosts
  - Server: 26 hosts
  - Workers: 117 hosts

### Additional Information

- **Physical layer standards** are governed by ISO, IEEE.
- **TCP/IP layer** standards are governed by IETF.
- Terms used to measure the quality of bandwidth include latency, throughput, and goodput.

**Clock in Router:**
- When connecting two routers using a serial line, one acts as the **Data Communications Equipment (DCE)**, and the other as the **Data Terminal Equipment (DTE)**. The DCE side typically sets the clock rate.

### Example of Signal Interference:
1. A pure digital signal is transmitted.
2. On the medium, there is an interference signal.
3. The digital signal is corrupted by the interference signal.
4. The receiving computer reads a changed signal. 

---

Let me know if there's anything more you need!