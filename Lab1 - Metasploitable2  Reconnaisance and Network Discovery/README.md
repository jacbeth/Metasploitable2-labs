
# Lab 1 – Network Reconnaissance & Host Discovery (Metasploitable2)

---

## 📝 Objective
Identify live hosts and enumerate exposed services on a vulnerable target (Metasploitable2) within an isolated virtual lab environment.

---

## 🧪 Environment

**Virtual Machines Used**
- **Kali Linux (Attacker):** 192.168.56.30  
- **Metasploitable2 (Target):** 192.168.56.50  
- **Windows 11 (Additional Target for later labs):** 192.168.56.11  

**Network Setup**
- VirtualBox Internal Network  
- Subnet: `192.168.56.0/24`

---

## 🔍 Initial Observation
The goal of this lab was to perform reconnaissance without exploitation.  
Tasks included verifying connectivity, discovering hosts, and enumerating services.

---

## 🧬 Analysis Summary
- Verified connectivity between Kali and Metasploitable2  
- Identified all live hosts on the subnet  
- Enumerated open ports and service versions  
- Identified outdated and vulnerable services on Metasploitable2  
- Documented findings for use in later exploitation labs  

---

## 🧩 MITRE ATT&CK Mapping
- **TA0043 – Reconnaissance**  
- **T1595 – Active Scanning**  
- **T1595.002 – Vulnerability Scanning**

---

## 📁 Repository Structure
```text
/Lab01-Network-Recon/
│
├── README.md
├── Notes.md
└── /screenshots/
      ├── 1-verify-IP-addresses.png
      ├── 2-ping-Kali-to-Metasploitable2.png
      ├── 3-nmap-live-host-discovery.png
      └── 4-nmap-scan-results-Metasploitable2.png
