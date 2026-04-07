
## Network Reconnaissance & Host Discovery (Metasploitable2)
### Objective
Identify live hosts and enumerate exposed services on a vulnerable target (Metasploitable2) within an isolated virtual lab environment.

### Environment
- **Kali Linux (Attacker):** 192.168.56.30  
- **Metasploitable2 (Target):** 192.168.56.50  
- **Windows 11 (Additional Target for later labs):** 192.168.56.11  
**Network Setup:** VirtualBox Internal Network  Subnet: 192.168.56.0/24

### Repository Structure
```text
/Network-Reconnaisance & Host Discovery/
│
├── README.md
└── /screenshots/
      ├── 1-verify-IP-addresses.png
      ├── 2-ping-Kali-to-Metasploitable2.png
      ├── 3-nmap-live-host-discovery.png
      └── 4-nmap-scan-results-Metasploitable2.png
```
      
### Steps taken
- Verified connectivity with command:  `ping 192.168.56.50`  and confirmed ICMP replies → Layer 3 connectivity.
##### Screenshot verified IP addresses:  
![verifyconnectivity](./screenshots/1-verify-IP-addresses.pngpng)
##### Screenshot ping Kali to Metasploitable2 result:  
./screenshots/2-ping-Kali-to-Metasploitable2.pn

- Host Discovery with command:  nmap -sn 192.168.56.0/24 Detected: - Detected Kali, Metasploitable2, and Windows 11 (no port scanning performed (ping sweep only))
#### Screenshot live host discovery:  
./screenshots/3-nmap-live-host-discovery.png

- Port Scanning & Service Enumeration with command:  nmap -sS -sV -A 192.168.56.50

##### Nmap options used:
- -sS → SYN scan  
- `-sV` → Service version detection  
- `-A` → Aggressive scan (OS detection, scripts)
##### Identified:
- 20+ open ports, outdated services (FTP, Telnet, SSH, SMB, MySQL, etc.) and high attack surface exposure  
Screenshot of nmap port and service scanning:  
./screenshots/4-nmap-scan-results-Metasploitable2.png

### MITRE ATT&CK Mapping
- **TA0043 – Reconnaissance**  
- **T1595 – Active Scanning**  
- **T1595.002 – Vulnerability Scanning**

### Analysis 
- The lab identified live hosts, open ports,  service versions  and identified outdated and vulnerable services on Metasploitable2  

### Recommendations
- Restrict unnecessary services  
- Disable insecure protocols e.g FTP, Telnet
- Apply segmentation to limit exposure  
- Implement host‑based firewalls  



