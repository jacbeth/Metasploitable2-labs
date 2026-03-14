
## 📓 **Lab 1: Network Reconnaissance & Host Discovery**

## 1. Objective
Perform structured reconnaissance to identify live hosts and enumerate exposed services on Metasploitable2.  
This information will support later exploitation and defensive analysis.

---

## 2. Setup & Configuration

### Virtual Machines
- Kali Linux – 192.168.56.30  
- Metasploitable2 – 192.168.56.50  
- Windows 11 – 192.168.56.11  

### Network
- VirtualBox Internal Network  
- Subnet: `192.168.56.0/24`

### Verification
Used `ip a` on each VM to confirm correct addressing.

Screenshot:  
`./screenshots/1-verify-IP-addresses.png`

---

## 3. Event Detection / Recon Steps

### Step 1 – Verify Connectivity
Command:  
`ping 192.168.56.50`  
Confirmed ICMP replies → Layer 3 connectivity.

Screenshot:  
`./screenshots/2-ping-Kali-to-Metasploitable2.png`

---

### Step 2 – Host Discovery
Command:  
`nmap -sn 192.168.56.0/24`  

Findings:
- Detected Kali, Metasploitable2, and Windows 11  
- No port scanning performed (ping sweep only)

Screenshot:  
`./screenshots/3-nmap-live-host-discovery.png`

---

### Step 3 – Port Scanning & Service Enumeration
Command:  
`nmap -sS -sV -A 192.168.56.50`

Options:
- `-sS` → SYN scan  
- `-sV` → Service version detection  
- `-A` → Aggressive scan (OS detection, scripts)

Findings:
- 20+ open ports  
- Outdated services (FTP, Telnet, SSH, SMB, MySQL, etc.)  
- High attack surface exposure  

Screenshot:  
`./screenshots/4-nmap-scan-results-Metasploitable2.png`

---

## 4. MITRE ATT&CK Mapping
- **TA0043 – Reconnaissance**  
- **T1595 – Active Scanning**  
- **T1595.002 – Vulnerability Scanning**

---

## 5. Recommendations
- Restrict unnecessary services  
- Disable insecure protocols (FTP, Telnet)  
- Apply segmentation to limit exposure  
- Implement host‑based firewalls  
- Monitor for repeated scanning behaviour  

---

## 6. Conclusion
The reconnaissance phase successfully identified live hosts and exposed services.  
Metasploitable2 presents a large attack surface, making it ideal for future exploitation labs.

---

## 7. Additional Notes / Lessons Learned
- Internal networks often expose more services than external ones  
- Nmap’s `-A` flag provides rapid insight but is noisy  
- Reconnaissance is essential for both attackers and defenders  
