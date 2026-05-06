# 🎯 CRITICAL CYBERSECURITY TOPICS (Essential Core)

## **PHASE 1: ABSOLUTE FOUNDATIONS**

### **Linux Fundamentals**
- File system hierarchy (`/etc`, `/var`, `/proc`)
- User/group management, permissions (`chmod`, `chown`)
- Process management (`ps`, `top`, `kill`, `systemctl`)
- Bash scripting (variables, loops, conditionals)
- Log analysis

### **Windows Fundamentals**
- Windows Registry
- Active Directory basics (domains, GPOs)
- PowerShell fundamentals
- Windows Event Logs

### **Networking (CRITICAL)**
- **OSI Model** (all 7 layers)
- **TCP/IP Model**
- **IP addressing, subnetting, CIDR**
- **TCP vs UDP** (3-way handshake, flags)
- **DNS** (resolution process, record types)
- **HTTP/HTTPS** (methods, status codes, headers)
- **TLS/SSL handshake**
- Firewalls (stateful vs stateless)
- VPN basics

### **Core Security Concepts**
- **CIA Triad** (Confidentiality, Integrity, Availability)
- Authentication, Authorization, Accounting (AAA)
- Defense in Depth
- Principle of Least Privilege

### **Cryptography Essentials**
- **Symmetric encryption** (AES)
- **Asymmetric encryption** (RSA)
- **Hashing** (SHA-256, bcrypt)
- **Digital signatures & certificates**
- **PKI basics**

### **Python Programming**
- Variables, data types, control flow
- Functions, modules
- Libraries: `os`, `socket`, `requests`
- Writing basic security automation

### **SQL Basics**
- SELECT, INSERT, UPDATE, DELETE
- WHERE, JOIN clauses

---

## **PHASE 2: CORE OFFENSIVE SKILLS**

### **Reconnaissance**
- **Nmap** (port scanning, service detection, NSE scripts)
- DNS enumeration
- Subdomain enumeration
- Directory brute-forcing (`ffuf`, `Gobuster`)

### **Web Application Security (CRITICAL)**
- **OWASP Top 10:**
  1. **SQL Injection** (Union, Blind, Time-based)
  2. **Cross-Site Scripting (XSS)** (Reflected, Stored, DOM)
  3. **Broken Access Control** (IDOR, privilege escalation)
  4. **Authentication failures**
  5. **Security misconfiguration**
  6. **Injection attacks** (Command injection)
  7. **CSRF**
  8. **SSRF**
- **Burp Suite** (Proxy, Repeater, Intruder)
- API security basics

### **System Exploitation Fundamentals**
- **Metasploit Framework** (`msfconsole`, `msfvenom`, Meterpreter)
- Password attacks (brute force, dictionary)
- **Privilege Escalation:**
  - **Linux**: SUID binaries, sudo misconfigurations, cron jobs
  - **Windows**: Token impersonation, unquoted service paths
- **Lateral movement basics** (Pass-the-Hash)

### **Active Directory Attacks (CRITICAL)**
- **AD enumeration** (BloodHound)
- **Kerberoasting**
- **Pass-the-Hash / Pass-the-Ticket**
- **DCSync attack**
- **Golden Ticket attack**

---

## **PHASE 2: CORE DEFENSIVE SKILLS**

### **SIEM (CRITICAL)**
- **Splunk** or **Elastic Stack (ELK)**
- Writing queries/searches
- Creating alerts and correlation rules
- Log source integration
- **Windows Event Log analysis** (Event IDs 4624, 4625, 4672, 4688, 7045)
- **Linux log analysis** (`/var/log/auth.log`, syslog)

### **Threat Intelligence**
- **IOCs** (Indicators of Compromise)
- **MITRE ATT&CK Framework** (understanding TTPs)
- Threat intel feeds

### **Incident Response Process**
- **SANS 6-step process:**
  1. Preparation
  2. Identification
  3. Containment
  4. Eradication
  5. Recovery
  6. Lessons Learned
- Chain of custody

### **Digital Forensics Essentials**
- **Disk imaging** (FTK Imager, `dd`)
- **Windows artifacts:**
  - Registry forensics
  - Prefetch files
  - Event Logs
  - $MFT (Master File Table)
- **Memory forensics basics** (Volatility)
- Timeline analysis

### **Malware Analysis Basics**
- **Static analysis** (strings, file hash, PE structure)
- **Dynamic analysis** (sandboxing, process monitoring)
- Behavioral indicators

---

## **PHASE 3: ADVANCED CRITICAL SKILLS**

### **Advanced Active Directory**
- Forest and domain trust attacks
- **Azure AD / Entra ID enumeration**
- Hybrid identity exploitation

### **Cloud Security (CRITICAL)**
- **AWS IAM** misconfigurations
- **S3 bucket** enumeration/exploitation
- **EC2 metadata service** (IMDSv1 attacks)
- **Azure AD** enumeration
- **Managed identity** exploitation
- **Kubernetes RBAC** abuse
- Container escape techniques

### **Advanced Detection Engineering**
- **Sigma rules** (writing and converting)
- Detection-as-Code
- Alert tuning (reducing false positives)
- **ATT&CK-aligned detection**

### **Threat Hunting**
- Hypothesis-driven hunting
- **TTP-based hunting** (using ATT&CK)
- Hunting for:
  - Lateral movement
  - Persistence mechanisms
  - Data exfiltration

### **Security Architecture**
- **Zero Trust Architecture** (NIST 800-207)
- Network segmentation
- Threat modeling (**STRIDE**)

### **DevSecOps Essentials**
- **CI/CD pipeline security**
- **SAST** (Static Application Security Testing)
- **DAST** (Dynamic Application Security Testing)
- **SCA** (Software Composition Analysis)
- Container security basics
- **Secret management** (HashiCorp Vault)

---

## **CRITICAL CERTIFICATIONS (Priority Order)**

### **Foundation (Must-Have)**
1. **CompTIA Security+**
2. **CompTIA Network+**

### **Offensive Track**
3. **OSCP** (Offensive Security Certified Professional)
4. **BSCP** (Burp Suite Certified Practitioner)

### **Defensive Track**
3. **CompTIA CySA+** (Cybersecurity Analyst)
4. **Blue Team Level 1 (BTL1)**

### **Cloud (Essential in 2024+)**
5. **AWS Certified Security - Specialty** OR **AZ-500** (Azure Security)

### **Management/Architecture**
6. **CISSP** (Certified Information Systems Security Professional)

---

## **CRITICAL HANDS-ON PLATFORMS**

1. **TryHackMe** (structured learning path)
2. **Hack The Box** (real-world scenarios)
3. **PortSwigger Web Security Academy** (web application security - FREE)
4. **LetsDefend** (SOC analyst skills)
5. **CyberDefenders** (DFIR challenges)

---

## **CRITICAL TOOLS (Must Master)**

### **Offensive**
- **Nmap**
- **Burp Suite**
- **Metasploit**
- **BloodHound**
- **sqlmap**

### **Defensive**
- **Splunk** or **Elastic Stack**
- **Wireshark**
- **Volatility** (memory forensics)
- **FTK Imager** (disk forensics)
- **Sysmon** (Windows monitoring)

---

## **CRITICAL KNOWLEDGE PRIORITIES**

**If you can only focus on 5 things:**
1. **Networking fundamentals** (TCP/IP, DNS, HTTP/HTTPS)
2. **Web application security** (OWASP Top 10, Burp Suite)
3. **Active Directory attacks & defense**
4. **SIEM & log analysis** (Splunk or ELK)
5. **Cloud security** (AWS/Azure basics)

**If you can focus on 10 things, add:**
6. **Linux command line & Bash scripting**
7. **Python for automation**
8. **Windows Event Log forensics**
9. **MITRE ATT&CK Framework**
10. **Incident Response process**

---

**⏱️ Minimum time to job-ready: 6-12 months of focused, daily practice on these critical topics**