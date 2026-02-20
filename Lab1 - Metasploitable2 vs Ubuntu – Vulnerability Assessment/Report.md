# Lab 1 - Metasploitable2 vs Ubuntu – Vulnerability Assessment Lab



### Overview

This lab compares a deliberately vulnerable system (Metasploitable2) with a securely configured system (Ubuntu Linux) to demonstrate how exposed services, outdated software, and misconfigurations increase attack surface and risk.



#### Objectives

* Discover hosts within an isolated network
* Enumerate open ports and running services
* Identify known vulnerabilities and associated CVEs
* Compare attack surface between secure and insecure systems
* Propose basic hardening and mitigation measures



#### Lab Environment

Attacker - Kali Linux, Vulnerable Target - Metasploitable2, Secure Target - Ubuntu Linux



#### Skills Demonstrated

Network and asset discovery

Service enumeration

Vulnerability awareness

CVE interpretation



#### Network Configuration:

Host-only adapter (isolated lab environment)



#### Tools Used

* Nmap – Host discovery, service enumeration, vulnerability scripts
* arp-scan – Layer 2 host discovery
* Linux networking utilities



#### Methodology

##### Host Discovery

###### *ARP Scan*

sudo arp-scan -l



Result: 3 live hosts detected



###### *Nmap Ping Scan*

nmap -sn 192.168.92.0/24

Result: 4 live hosts detected (including Kali)



IP Address	System

\- 192.168.92.13	Kali Linux

\- 192.168.92.14	Ubuntu

\- 192.168.92.15	Metasploitable2

\- 192.168.92.2	Default Gateway



System identities were confirmed using: ip a



### Enumeration

Full TCP port scan with service version detection

Nmap Scan Command

nmap -sV -p- 192.168.92.x

-sV: Service and version detection

-p-: Scan all TCP ports



#### Metasploitable2 Results

Metasploitable2 exposed numerous services across multiple ports, including:



\* FTP (21)

\* SSH (22)

\* Telnet (23)

\* SMTP (25)

\* HTTP (80)

\* SMB (139/445)

\* IRC (6667)



Many services were outdated, misconfigured, or intentionally vulnerable, resulting in a large attack surface.



#### Ubuntu Results

\- No open TCP ports detected

\- No network-accessible services running



This reflects Ubuntu’s secure-by-default configuration, where services are not exposed unless explicitly enabled.



### Vulnerability Identification

Scan Method

nmap --script vuln 192.168.92.x



This scan was used to identify known vulnerabilities and associated CVEs.



##### Metasploitable2 Vulnerabilities

\- Multiple high- and medium-risk vulnerabilities identified

\- Numerous CVEs associated with exposed services

\- Weak encryption, outdated protocols, and insecure configurations observed



##### Ubuntu Vulnerabilities

\- No vulnerabilities detected

\- No exposed services

\- Minimal attack surface



### Key Findings

###### Metasploitable2

* Numerous open ports and exposed services
* Outdated and intentionally vulnerable software
* Multiple high- and medium-risk CVEs identified
* Large attack surface



Service	Port	Risk				Risk Level  Reason
FTP	21	Anonymous access		High	    Unauthorised access
SSH	22	Brute-force attacks	        High	    Credential compromise

Telnet	23	Unencrypted traffic	        High	    Eavesdropping

HTTP	80	Information disclosure		Medium	    Reconnaissance



###### Ubuntu

* No open ports detected
* No externally accessible services running
* Secure-by-default configuration
* Minimal attack surface



#### CVE Mapping Examples



High Risk – SMTP (OpenSSL / SSL 3.0)

Service: SMTP

Port: 25

CVE: CVE-2014-3566 (POODLE)

Type: Information Disclosure



###### Description:

The SSL 3.0 protocol uses weak CBC padding, enabling man-in-the-middle attackers to recover plaintext data via padding-oracle attacks. This compromises confidentiality and secure communications.



Medium Risk – UnrealIRCd 3.2.8.1

Service: IRC

Port: 6667

CVE: CVE-2010-2075

Type: Backdoored Software



###### Description:

This version of UnrealIRCd contained malicious code that allowed unauthorised remote actions. A compromised service at this level undermines all other security controls on the system.



#### Suggested Defensive Countermeasures

Excessive services - Apply service minimisation

Legacy software - Patch and update software regularly

Decommission e.g. outdated SMB

Hide service banners to reduce information disclosure



#### Conclusion

This lab highlights the importance of secure configuration and service minimisation. Metasploitable2 exposes numerous outdated and vulnerable services, creating a large attack surface and multiple high-risk vulnerabilities. Ubuntu, by contrast, demonstrates a secure-by-default approach with minimal exposure. This exercise reinforces that reducing attack surface, maintaining patching programmes, and prioritising vulnerabilities are among the most effective defensive strategies

