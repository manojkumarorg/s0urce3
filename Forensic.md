### Steganography Tools and Techniques

#### **1. Steghide**
Steghide is a steganography tool used to embed and extract data from image and audio files.  
**Supported File Formats**: `JPEG`, `BMP`, `WAV`, `AU`.  

- **Installation**:  
  - Install via `apt`:  
    ```bash
    sudo apt install steghide
    ```  
  - [GitHub Source](https://github.com/StefanoDeVuono/steghide).  

- **Commands**:  
  - Check for embedded data:  
    ```bash
    steghide info <file>
    ```  
  - Extract embedded data:  
    ```bash
    steghide extract -sf <file>
    ```  

#### **2. Foremost**
Foremost recovers files based on headers, footers, and data structures. Useful for retrieving `png` images.  

- **Installation**:  
  - Install via `apt`:  
    ```bash
    sudo apt install foremost
    ```  
  - [GitHub Source](https://github.com/korczis/foremost).  

- **Command**:  
  ```bash
  foremost -i <file>
  ```  

#### **3. Stegsolve**
Stegsolve applies various color filters to images, helping to reveal hidden messages.  

- **Download**: [Stegsolve Tool](https://0xrick.github.io/lists/stego/#stegsolve).  

---

### Supporting Tools

#### **4. Strings**
Displays printable strings from files.  
**Command**:  
```bash
strings <file>
```

#### **5. Exiftool**
Reads metadata from images and other files.  

- **Command**:  
  ```bash
  exiftool <file>
  ```

#### **6. Binwalk**
Analyzes binary files to detect and extract embedded data.  

- **Installation**:  
  ```bash
  sudo apt install binwalk
  ```  
  - [GitHub Source](https://github.com/ReFirmLabs/binwalk).  

- **Commands**:  
  - Display embedded data:  
    ```bash
    binwalk <file>
    ```  
  - Extract data:  
    ```bash
    binwalk -e <file>
    ```

#### **7. zsteg**
Detects hidden data in `PNG` and `BMP` files.  

- **Installation**:  
  ```bash
  gem install zsteg
  ```  
  - [GitHub Source](https://github.com/zed-0xff/zsteg).  

- **Commands**:  
  - Analyze all methods:  
    ```bash
    zsteg -a <file>
    ```  
  - Extract specific data:  
    ```bash
    zsteg -E <payload> <file>
    ```  

#### **8. WavSteg**
A Python tool for hiding and extracting data in WAV files.  

- **Download**: [GitHub Source](https://github.com/ragibson/Steganography#WavSteg).  

- **Command**:  
  ```bash
  python3 WavSteg.py -r -s <soundfile> -o <outputfile>
  ```  

#### **9. Sonic Visualizer**
Analyzes audio files to reveal hidden shapes and patterns.  

- **Download**: [Official Website](https://www.sonicvisualiser.org).  

---

### Additional Tools and Techniques
1. **StegCracker**: Brute-forces passwords for `steghide`.  
   - [GitHub Source](https://github.com/Paradoxis/StegCracker).  

2. **Hex Editors**: Examine file headers and verify magic numbers.  
   - Use `hexedit` to inspect headers of `PNG` files (`IHDR`, `IDAT`).  

3. **Magic Headers**: Identify file types from header bytes.  
   - [List of File Signatures](https://en.wikipedia.org/wiki/List_of_file_signatures).  

4. **Wireshark and PCAP Analysis**: Analyze network packets to find hidden data.  
   - Export data from PCAP files:  
     ```bash
     tshark -r <file>.pcapng -T fields -e usb.capdata > out
     ```  

5. **TCPDump**: Capture network traffic to analyze hidden data.  
   ```bash
   tcpdump -i eth0 -w dump.pcap
   ```  

6. **Filters for Specific Protocols**:
   - Example for FTP:  
     ```bash
     ip.src == <IP> and ip.dst == <IP>
     ```  

---

### Common Techniques Summary
- **String Extraction**: Use `strings` to find hidden text.  
- **Metadata Analysis**: Use `exiftool` to reveal metadata clues.  
- **Binary Inspection**: Use `binwalk` and `zsteg` for embedded data.  
- **Image Manipulation**: Tools like `Stegsolve` apply filters for visual clues.  
- **Audio Analysis**: Use tools like `Sonic Visualizer` for spectrogram analysis.  

--- 

### Example Workflow
1. **Check Metadata**:  
   ```bash
   exiftool <image>.png
   ```  
2. **Look for Base64 Content**:  
   ```bash
   strings <file>
   ```  
3. **Extract Hidden Data**:  
   ```bash
   steghide extract -sf <image>.png
   ```  

--- 


Metadata Extraction
File Carving
Hexadecimal and binary analysis

For example (ctf_game ):
Memory dumps are created when the host device crashes

 setting up the volatility3 tool from github
**_.vmem files are VMWare memory dumps, this is not always the file extension dumps will use. Most times it will be a .dmp file._**
execute the tool :
```
volatility -f OtterCTF.vmem imageinfo
```
LSADump.
Since this is a Windows 7 file, the password may be stored in the machine’s LSA secrets (where passwords to PCs are stored locally sometimes).
```
volatility -f OtterCTF.vmem --profile=Win7SP1x64 lsadump
```

```
volatility -f OtterCTF.vmem --profile=Win7SP1x64 hivelist
volatility -f OtterCTF.vmem --profile=Win7SP1x64 printkey -o <Insert SYSTEM hive address here> -K 'ControlSet001\Control\ComputerName\ComputerName'
```

This will allow us to find the computer name. Remember that we use the -K command to specify where in that registry hive we wanted to go. First did ‘ControlSet001’ and followed the menu from there.
To find any local address:
```
volatility -f OtterCTF.vmem --profile=Win7SP1x64 netscan
```
setup the profile you can see this by executing the first command:

```
volatility -f OtterCTF.vmem --profile=Win7SP1x64 netscan
```

PSList lists all of the processes that were running when the memory dump was formed. Dumped the memory of the process called LunarMS.exe, grepped for Lunar-3. The \ character is to escape the ‘-‘ from being read as a command. -C 1 gives one line of context above and below each entry that meets our grep requirements.
```
volatility -f OtterCTF.vmem --profile=Win7SP1x64 pslist
volatility -f OtterCTF.vmem --profile=Win7SP1x64 memdump -p <LunarMS process ID> -d <directory path you want to dump to>
strings <LunarMS PID>.dmp | grep -a Lunar\-3 -C 1
```
 pasting the password into the clipboard


#filerecovery
## File Headers[](https://ctf.support/forensics/file-recovery/#file-headers "Anchor to: File Headers")

To fix corrupted and invalid file headers, a hex editor like [010 Editor](https://www.sweetscape.com/010editor/) can be used.

To analyze various office files, [oletools](https://github.com/decalage2/oletools) can be used.

## VBA[](https://ctf.support/forensics/office-files/#vba "Anchor to: VBA")

To extract VBA from office documents, `olevba` and `olevba3` from [oletools](https://github.com/decalage2/oletools) can be used.
