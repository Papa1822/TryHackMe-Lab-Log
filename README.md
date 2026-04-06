# TryHackMe-Lab-Log
This repository documents my journey through multiple Cyber-security labs completed in Pre-security and Cyber101.

### 📊 Lab Progress Summary

> 💡 **Strategy Note:** While progressing through **Cyber101**, I am concurrently completing the updated **Pre-Security (Sections 4-7)**. This ensures I have a deep-dive understanding of OS Internals and Web Architecture, which strengthens my ability to perform manual exploitation and privilege escalation in the Cyber101 labs.

### 🛡️ Pre-Security (Sections 4-7)
*Focus: Deep-dive into Operating Systems and Web Architecture.*


| Lab Name | Section | Key Skill Learned | Status |
| :--- | :--- | :--- | :--- |
| Computer Fundamentals | Sec 4 | Hardware ID | 🔄 In Progress |
---
### 🔍 Technical Evidence & Writeups
## Lab: Inside a Computer System (TryHackMe)

## 🖥️ Overview
This lab covers the physical hardware components of a computer and the logical sequence of events that occur from the moment the power button is pressed until the Operating System (OS) is ready for use.

## 🏗️ Hardware Component Breakdown

| Component | Function | Analogy |
| :--- | :--- | :--- |
| **Motherboard** | The main circuit board that connects all parts. | The "Skeleton/Nervous System" |
| **CPU** | Performs all calculations and instructions. | The "Brain" |
| **RAM** | Short-term, volatile memory for active tasks. | The "Work Desk" |
| **Storage (HDD/SSD)** | Long-term, non-volatile data storage. | The "Filing Cabinet" |
| **PSU** | Converts AC power to DC for components. | The "Heart" |
---
![Hardware-Identification](images/hardware-identification(motherboard).png)

 ----
 ----

# **Cyber-101**

| Lab Name | Category | Key Skill Learned | Status |
| :--- | :--- | :--- | :--- |
| **Intro to Networking** | Networking | OSI Model & TCP/IP Handshake | ✅ Completed |
| **Linux Fundamentals** | Operating Systems | Terminal Navigation & Permissions | ✅ Completed |
| **Nmap Basics** | Enumeration | Network Scanning & Port Discovery | ✅ Completed |
| **Cryptography** | Security | Mastered Hashing (SHA-256) vs Encryption (AES/RSA) | ✅ Completed |
| **Moniker** | Exploitation | CVE-2024-21413 (MonikerLink) NTLM leaks via SMB | ✅ Completed |
| **Metasploit Intro** | Tools | MSF Framework, Meterpreter, and msfdb management | ✅ Completed |
| **Metasploit Exploitation** | Tools | SMB Enumeration & Credential Auditing | ✅ Completed |
| **Metasploit Meterpreter** | Post Exploitation | Process Migration, Hash dumping, and Enumeration | ✅ Completed |
| **Blue (MS17-010)** | Exploitation |  	Full Kill-Chain: Recon, MS17-010 Exploit, PrivEsc & Hash Cracking. | ✅ Completed |

---

### 🔍 Technical Evidence & Writeups

#### **Metasploit: SMB Credential Audit**
Successfully identified weak credentials for user `penny` using a dictionary attack.
![SMB Login Success](images/msf-smb-success.png)

#### **Metasploit: Exploitation (EternalBlue)**
- **Vulnerability:** MS17-010 (EternalBlue)
- **Payload:** `windows/x64/meterpreter/reverse_tcp`
- **Result:** Gained **NT AUTHORITY\SYSTEM** privileges.
![Exploitation Success](images/msf-exploitation-system-access.png)

#### **Post-Exploitation & Data Exfiltration**
- **Proof of Access:** Read `flag.txt` via Meterpreter.
- **Credential Harvesting:** Executed `hashdump` to extract NTLM hashes.
- **Finding:** Retrieved NTLM hash for user `pirate` for potential Pass-the-Hash attacks.

#### **Privilege Escalation & Credential Harvesting**
- **Method:** Local Privilege Escalation via `sudo` misconfiguration.
- **Action:** Leveraged root-level permissions to access restricted files.
![Root Access Proof](images/linux-priv-esc.png)

> [!IMPORTANT]
> **Internship-Level Insight:** 
> "While standard Metasploit modules were restricted, I successfully pivoted to manual Linux enumeration. By identifying a sudoers misconfiguration, I achieved full system compromise, demonstrating the ability to maintain momentum when automated tools reach their limits."

---

### 🛠️ Meterpreter Deep Dive
1. **Recon:** ![Sys info Proof](images/meterpreter-sys-info.png)
2. **PrivEsc:** ![GetSystem](images/meterpreter-getsys.png)
3. **Hashes:** ![Hashdump](images/meterpreter-hashdump.png)
4. **Exfiltration:** ![Cat Secrets](images/cat_secrets.png)

---

### 📑 Lab Notes: Blue (MS17-010)
* **Phase 1(Recon):
After scanning the target with Nmap, I ran a vulnerability script to check for common SMB flaws.

 **Vulnerability Scan:** ![Nmap Scan showing VULNERABLE](images/blue-vuln-scan.png)
 *The scan confirms the target is vulnerable to MS17-010 (EternalBlue).*

### 2. Exploitation & System Information
After confirming the vulnerability, I used the `ms17_010_eternalblue` Metasploit module to gain a stable Meterpreter session. 

**System Verification:**
![Meterpreter Sysinfo & GetUID](images/blue-system-access.png)

*   **Target OS:** Windows 7 (64-bit)
*   **Access Level:** NT AUTHORITY\SYSTEM

### 3. Persistence & Privilege Verification
To ensure a permanent foothold, I migrated the Meterpreter session into the **lsass.exe** process. This is a critical system service responsible for security policy enforcement.

![Migration to lsass.exe](images/blue-migration.png)

*   **Migration Target:** lsass.exe (System Process)
*   **Access Level:** NT AUTHORITY\SYSTEM

### 4. Credential Harvesting & Cracking
After gaining SYSTEM access, I dumped the local SAM database hashes. I then performed an offline dictionary attack against the user **Jon's** NTLM hash.

![Cracking NTLM Hash with John the Ripper](images/blue-hash-crack.png)

*   **Tool:** John the Ripper
*   **Wordlist:** rockyou.txt
*   **Result:** Successfully recovered plain-text password for user: **Jon**


  Post-Exploitation: Successfully located three system flags hidden across the machine (System Root, SAM Database config, and Administrative Documents) to confirm full system compromise.

## 💼 Virtual Internships (Job Simulations)

| Company | Program | Task Completed | Key Skill |
| :--- | :--- | :--- | :--- |
| **Mastercard** | [Cybersecurity](https://www.theforage.com) | Phishing Analysis (Task 1) | Threat Detection & Social Engineering |
.
