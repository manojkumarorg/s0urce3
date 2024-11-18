### **BOOTING PROCESS**
#### **BIOS**:
- **POST (Power-On Self-Test)**: Checks all devices for communication. Ends when the disk is discovered.  
- **MBR (Master Boot Record)**: Small program responsible for locating and loading the OS. BIOS executes this code to start the OS.  

#### **UEFI**:
- Stores boot code in firmware, enabling secure boot into protected mode.  
- **BCD (Boot Configuration Database)**: Contains additional startup code.  
- If booting from a cold start, **Winload.exe** is loaded.  
  - **Winload.exe**: Creates a hardware configuration record in the registry.  

#### **Registry Keys**:
- **HKEY_CURRENT_USER**: Stores settings specific to the logged-in user.  
- **HKEY_LOCAL_MACHINE**: Stores global Windows configurations.  

---

### **OSI vs. TCP/IP Model**

| **OSI Layer Model**                                                                                       | **TCP/IP Layer Model**                             |
|----------------------------------------------------------------------------------------------------------|---------------------------------------------------|
| **Application** {Data, ALL} - Handles user interaction                                                   | **Application**                                   |
| **Presentation** {Data Format, Encryption, PEOPLE} - Ensures readable data                               |                                                   |
| **Session** {SEEM} - Manages sessions between applications                                               |                                                   |
| **Transport** {Segments, L4 Header, DATA, TO} - Handles data transfer reliability                        | **Transport**                                     |
| **Network** {Packets, L3 Header, NEED} - Routes packets across networks                                  | **Network**                                       |
| **Data Link** {Frames, L2 Trailer, L2 Header, DATA} - Manages data transfer between nodes                | **Datalink**                                      |
| **Physical** {Bits, PROCESSING} - Handles transmission over physical medium                             | **Physical**                                      |

#### **Real-Time Example**:
![[Pasted image 20240506192019.png]]  

---

### **Windows Architecture**
#### **HAL (Hardware Abstraction Layer)**:
- Provides an abstraction layer between hardware and the operating system.  
- Bridges hardware and firmware interfaces.  

#### **Execution Modes**:
1. **User Mode**:  
   - Installed applications and system processes run here.  
   - **Components**:  
     - **Win32 Subsystem**: Implements core Windows APIs.  
     - **Service Process**: Background services support various functions.  
     - **System Process**: Manages essential system operations.  
     - **Usermode APIs**: Allow applications to request OS services.  

2. **Kernel Mode**:  
   - Provides low-level access to hardware resources.  
   - **Components**:  
     - **Execution Services**: Manages memory, process scheduling, and I/O.  
     - **Kernel Mode Drivers**:  
       - **Device Drivers**: For hardware like NICs and GPUs.  
       - **File System Drivers**: Enable file system operations (e.g., FAT32, NTFS).  
       - **Network Drivers**: Facilitate communication.  
     - **Microkernel**: Handles basic OS functions and hardware interactions.  

---

### **Useful PowerShell and Command-Line Commands**

1. **List subdirectories and files**:  
   ```bash
   Get-Alias dir
   ```

2. **Check routing tables**:  
   ```bash
   netstat -r
   ```

3. **Check active TCP connections and associated processes**:  
   ```bash
   netstat -abno
   ```

4. **Clear Recycle Bin**:  
   ```bash
   Clear-RecycleBin
   ```

5. **Test DNS**:  
   ```bash
   nslookup cisco.com
   ```

6. **List active network connections**:  
   ```bash
   netstat
   ```

---

### **Network Troubleshooting: Cables**
- **MMF (Multimode Fiber)**:  
  - Suitable for LANs with low-cost LEDs.  
  - Bandwidth: Up to 10 Gbps over 550 meters.  

- **SMF (Singlemode Fiber)**:  
  - Ideal for long-distance communication (e.g., telephony, cable TV).  

![[Pasted image 20240523181802.png]]

