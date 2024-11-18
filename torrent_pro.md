# VPN and DNS Configuration


1. **Ensure OpenVPN is Running:**
   ```sh
   sudo systemctl status openvpn@your_protonvpn_config_file
   ```
   - Ensure it shows active (running). If not, troubleshoot the OpenVPN connection.

2. **Route DNS Traffic through VPN:**
   - Add these lines to your OpenVPN configuration file:
     ```sh
     push "dhcp-option DNS 1.1.1.1"
     push "dhcp-option DNS 1.0.0.1"
     ```
   - Restart OpenVPN to apply changes:
     ```sh
     systemctl restart openvpn@your_protonvpn_config_file
     ```

### Testing and Debugging

1. **Ping Indexer:**
   ```sh
   ping <indexer_domain>
   ```

2. **Test DNS Resolution:**
   ```sh
   dig <indexer_domain>
   nslookup <indexer_domain>
   ```

3. **Check Prowlarr Logs:**
   ```sh
   tail -f /opt/Prowlarr/config/logs/rolling.log
   ```

By following these steps, you should be able to diagnose and fix the DNS and SSL issues preventing Prowlarr from connecting to indexers. This ensures that Prowlarr can resolve domain names and establish secure connections.

---

# Radarr Connection Issue Resolution

1. **Check if Radarr is Running:**
   ```sh
   sudo systemctl status radarr
   ```
   - If Radarr is not running, start the service:
     ```sh
     sudo systemctl start radarr
     sudo systemctl enable radarr
     ```

2. **Verify Radarr Configuration:**
   - Check the Radarr configuration file (usually located at `/etc/radarr/config.xml` or `/home/USERNAME/.config/Radarr/config.xml`):
     ```xml
     <Config>
       ...
       <Port>7878</Port>
       <BindAddress>0.0.0.0</BindAddress>
       ...
     </Config>
     ```
   - Make sure `BindAddress` is set to `0.0.0.0` to listen on all network interfaces, or to the specific IP address if needed.

3. **Check Network and Firewall Settings:**
   - Ensure that the port 7878 is open and not blocked by any firewall.
     ```sh
     sudo ufw allow 7878
     sudo ufw status
     ```

4. **Check for Port Conflicts:**
   ```sh
   sudo lsof -i :7878
   ```

5. **Check Radarr Logs:**
   - Logs are typically located in `/home/USERNAME/.config/Radarr/logs/` or `/var/log/radarr/`.
     ```sh
     cat /home/USERNAME/.config/Radarr/logs/radarr.log
     ```

6. **Reinstall Radarr (if needed):**
   ```sh
   sudo apt-get remove radarr
   sudo apt-get install radarr
   ```

### Example of Diagnosing and Resolving Issues

1. **Check Radarr Status:**
   ```sh
   sudo systemctl status radarr
   ```
   Example output:
   ```plaintext
   ● radarr.service - Radarr Daemon
      Loaded: loaded (/etc/systemd/system/radarr.service; enabled; vendor preset: enabled)
      Active: active (running) since Mon 2024-06-02 13:00:00 UTC; 1h 30min ago
   ```

2. **Check Radarr Configuration:**
   ```sh
   nano /home/USERNAME/.config/Radarr/config.xml
   ```
   Ensure it has:
   ```xml
   <Config>
     ...
     <Port>7878</Port>
     <BindAddress>0.0.0.0</BindAddress>
     ...
   </Config>
   ```

3. **Open Firewall Port:**
   ```sh
   sudo ufw allow 7878
   sudo ufw status
   ```

4. **Check for Port Conflicts:**
   ```sh
   sudo lsof -i :7878
   ```

5. **Review Radarr Logs:**
   ```sh
   cat /home/USERNAME/.config/Radarr/logs/radarr.log
   ```

### Reinstallation Steps

1. **Remove Radarr:**
   ```sh
   sudo apt-get remove radarr
   ```

2. **Install Radarr:**
   ```sh
   sudo apt-get install radarr
   ```

### Example Radarr Service File

Ensure your Radarr service file (`/etc/systemd/system/radarr.service`) is correctly configured:
```ini
[Unit]
Description=Radarr Daemon
After=syslog.target network.target

[Service]
User=radarr
Group=radarr
Type=simple
ExecStart=/usr/bin/mono /opt/Radarr/Radarr.exe -nobrowser -data=/var/lib/radarr

[Install]
WantedBy=multi-user.target
```

After editing the service file, reload the systemd daemon and restart Radarr:
```sh
sudo systemctl daemon-reload
sudo systemctl restart radarr
```

Following these steps should help you diagnose and resolve the connection issue with Radarr. If you continue to face problems, providing specific error logs will help in giving more precise guidance.

---

### Radarr Service Failing to Start with Status Code 2

1. **Check Radarr Logs:**
   ```sh
   sudo journalctl -u radarr.service -b
   ```

   - Additionally, check the Radarr log files typically located in `/var/lib/radarr/` or `/opt/Radarr/`.

2. **Verify Mono Installation:**
   ```sh
   mono --version
   ```
   - If Mono is not installed or is an incorrect version, you can install/update it:
     ```sh
     sudo apt update
     sudo apt install mono-devel
     ```

3. **Check Radarr Configuration:**
   - Ensure that the Radarr configuration file and directories have the correct permissions:
     ```sh
     sudo chown -R radarr:radarr /opt/Radarr
     sudo chown -R radarr:radarr /var/lib/radarr
     ```

4. **Review the Systemd Service File:**
   - Open the service file for editing:
     ```sh
     sudo nano /etc/systemd/system/radarr.service
     ```
   - The content should look something like this:
     ```ini
     [Unit]
     Description=Radarr Daemon
     After=syslog.target network.target

     [Service]
     User=radarr
     Group=radarr
     Type=simple
     ExecStart=/usr/bin/mono /opt/Radarr/Radarr -nobrowser -data=/var/lib/radarr
     TimeoutStopSec=20
     KillMode=process
     Restart=on-failure

     [Install]
     WantedBy=multi-user.target
     ```

5. **Reload Systemd and Restart Radarr:**
   ```sh
   sudo systemctl daemon-reload
   sudo systemctl start radarr
   ```

6. **Check for Missing Dependencies:**
   - Ensure that all dependencies required by Radarr are installed:
     ```sh
     sudo apt update
     sudo apt install libmono-cil-dev curl
     ```

7. **Reinstall Radarr:**
   - Stop and disable the Radarr service:
     ```sh
     sudo systemctl stop radarr
     sudo systemctl disable radarr
     ```

   - Remove the existing installation:
     ```sh
     sudo rm -rf /opt/Radarr
     sudo rm -rf /var/lib/radarr
     ```

   - Download and install the latest version of Radarr:
     ```sh
     sudo mkdir -p /opt/Radarr
     sudo chown -R radarr:radarr /opt/Radarr
     cd /opt/Radarr
     sudo curl -L -O https://github.com/Radarr/Radarr/releases/download/v3.2.2.5080/Radarr.develop.3.2.2.5080.linux.tar.gz
     sudo tar -xzvf Radarr.develop.3.2.2.5080.linux.tar.gz
     ```

---

### Lidarr Setup

Lidarr is a music collection manager for Usenet and BitTorrent users. It can monitor multiple RSS feeds for new tracks from your favorite artists and will grab, sort and rename them. It can also be configured to automatically upgrade the quality of files already downloaded when a better quality format becomes available.

1. **Create and Configure the Lidarr User:**
   - The user `lidarr` is created and is part of the group `media`.
   - Your download clients and media server run as and are part of the group `media`.
   - Your paths used by your download clients and media server are accessible (read/write) to the group `media`.
   - Create the directory `/var/lib/lidarr` and ensure the user `lidarr` has read/write permissions for it:
     ```sh
     sudo mkdir -p /var/lib/lidarr
     sudo chown -R lidarr:media /var/lib/lidarr
     ```

2. **Download and Install Lidarr:**
   ```sh
   wget --content-disposition 'http://lidarr.servarr.com/v1/update/master/updatefile?os=linux&runtime=netcore&arch=x64'
   tar -

xzvf Lidarr*.linux.tar.gz -C /opt
   sudo chown -R lidarr:media /opt/Lidarr
   ```

3. **Create a Systemd Service File:**
   ```ini
   [Unit]
   Description=Lidarr Daemon
   After=syslog.target network.target

   [Service]
   User=lidarr
   Group=media
   Type=simple
   ExecStart=/opt/Lidarr/Lidarr -nobrowser -data=/var/lib/lidarr
   TimeoutStopSec=20
   KillMode=process
   Restart=on-failure

   [Install]
   WantedBy=multi-user.target
   ```

   - Save the file as `/etc/systemd/system/lidarr.service`.

4. **Start Lidarr:**
   ```sh
   sudo systemctl enable lidarr
   sudo systemctl start lidarr
   sudo systemctl status lidarr
   ```

You should now be able to access Lidarr at `http://localhost:8686`. If you need to access it from a different machine, make sure the port is open and accessible through your firewall.

---

### Lidarr Setup Example

**Install Prerequisites:**
```sh
sudo apt update
sudo apt install -y libmediainfo0v5 libchromaprint-tools
```

**Create Lidarr User:**
```sh
sudo adduser --system --group --home /var/lib/lidarr lidarr
```

**Download and Extract Lidarr:**
```sh
wget --content-disposition 'http://lidarr.servarr.com/v1/update/master/updatefile?os=linux&runtime=netcore&arch=x64'
tar -xzvf Lidarr*.linux.tar.gz -C /opt
sudo chown -R lidarr:lidarr /opt/Lidarr
```

**Create Service File:**
```ini
[Unit]
Description=Lidarr Daemon
After=syslog.target network.target

[Service]
User=lidarr
Group=lidarr
Type=simple
ExecStart=/opt/Lidarr/Lidarr -nobrowser -data=/var/lib/lidarr
TimeoutStopSec=20
KillMode=process
Restart=on-failure

[Install]
WantedBy=multi-user.target
```

**Enable and Start Service:**
```sh
sudo systemctl enable lidarr
sudo systemctl start lidarr
sudo systemctl status lidarr
```

You can access Lidarr by navigating to `http://localhost:8686` in your web browser. If you encounter any issues, checking the logs located in `/var/lib/lidarr/logs` can provide more insight.

---
# Verifying DNS Configuration on Linux with `dig`

**Install `dnsutils`:**
```sh
sudo apt-get install dnsutils
```

**Basic `dig` Commands:**

1. **Check A Record for a Domain:**
   ```sh
   dig example.com
   ```

2. **Check Specific DNS Server:**
   ```sh
   dig @8.8.8.8 example.com
   ```

3. **Check MX Records:**
   ```sh
   dig example.com MX
   ```

4. **Check NS Records:**
   ```sh
   dig example.com NS
   ```

5. **Check ALL Records:**
   ```sh
   dig example.com ANY
   ```

**Common `dig` Options:**

- `+short`: Display simplified output.
  ```sh
  dig example.com +short
  ```

- `+trace`: Trace the path to resolve the query.
  ```sh
  dig example.com +trace
  ```

- `+noall +answer`: Display only the answer section.
  ```sh
  dig example.com +noall +answer
  ```

### `dig` Examples

1. **Check A Record for Google:**
   ```sh
   dig google.com
   ```

   **Output:**
   ```plaintext
   ; <<>> DiG 9.11.3-1ubuntu1.11-Ubuntu <<>> google.com
   ;; global options: +cmd
   ;; Got answer:
   ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 12345
   ;; flags: qr rd ra; QUERY: 1, ANSWER: 5, AUTHORITY: 0, ADDITIONAL: 0
   ;; ANSWER SECTION:
   google.com.  299  IN  A  142.250.72.206
   google.com.  299  IN  A  142.250.72.238
   google.com.  299  IN  A  142.250.72.206
   ```

2. **Check MX Records for Gmail:**
   ```sh
   dig gmail.com MX
   ```

   **Output:**
   ```plaintext
   ; <<>> DiG 9.11.3-1ubuntu1.11-Ubuntu <<>> gmail.com MX
   ;; global options: +cmd
   ;; Got answer:
   ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 67890
   ;; flags: qr rd ra; QUERY: 1, ANSWER: 5, AUTHORITY: 0, ADDITIONAL: 0
   ;; ANSWER SECTION:
   gmail.com.  299  IN  MX  20 alt1.gmail-smtp-in.l.google.com.
   gmail.com.  299  IN  MX  30 alt2.gmail-smtp-in.l.google.com.
   gmail.com.  299  IN  MX  40 alt3.gmail-smtp-in.l.google.com.
   ```

3. **Trace DNS Resolution Path:**
   ```sh
   dig google.com +trace
   ```

**Common Issues and Fixes:**

- **Timeouts:** If `dig` times out, ensure your DNS server is reachable and responsive.
- **No Answers:** If no answers are returned, verify the domain and check for typos.

Using `dig` can help troubleshoot DNS issues by providing detailed information about the DNS resolution process and identifying potential problems.

### Alternative DNS Testing Tools

- **nslookup:**
  ```sh
  nslookup example.com
  ```

- **host:**
  ```sh
  host example.com
  ```

- **DNSCheck:**
  ```sh
  dnscheck example.com
  ```

### Additional Commands and Options for `dig`

**Query Specific DNS Records:**
- AAAA (IPv6 address): `dig example.com AAAA`
- CNAME (Canonical name): `dig example.com CNAME`
- TXT (Text record): `dig example.com TXT`
- SOA (Start of Authority): `dig example.com SOA`
- PTR (Pointer record): `dig -x 192.0.2.1`

**Using `dig` with +noall +answer:**
- Simplify output to show only the answer section:
  ```sh
  dig example.com +noall +answer
  ```

**Trace DNS Resolution Path:**
- `+trace` shows the path the query takes to resolve the domain:
  ```sh
  dig example.com +trace
  ```

**Check Reverse DNS (PTR record):**
- Perform a reverse DNS lookup:
  ```sh
  dig -x 8.8.8.8
  ```

### Example `dig` Commands

1. **Check CNAME Record:**
   ```sh
   dig www.example.com CNAME
   ```

   **Output:**
   ```plaintext
   ;; ANSWER SECTION:
   www.example.com.  3600  IN  CNAME  example.com.
   ```

2. **Check AAAA Record (IPv6):**
   ```sh
   dig example.com AAAA
   ```

   **Output:**
   ```plaintext
   ;; ANSWER SECTION:
   example.com.  3600  IN  AAAA  2001:db8::1
   ```

3. **Check TXT Record:**
   ```sh
   dig example.com TXT
   ```

   **Output:**
   ```plaintext
   ;; ANSWER SECTION:
   example.com.  3600  IN  TXT  "v=spf1 include:_spf.example.com ~all"
   ```

Using these tools and techniques will help you effectively diagnose and resolve DNS-related issues, ensuring reliable network and application performance.