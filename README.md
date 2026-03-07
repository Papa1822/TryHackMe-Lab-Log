# TryHackMe-Lab-Log
This repository documents my journey through  multiple  Cyber-security labs completed in Pre-security and Cyber101

| Lab Name | Category | Key Skill Learned | Status |
| :--- | :--- | :--- | :--- |
| **Intro to Networking** | Networking | OSI Model & TCP/IP Handshake | ✅ Completed |
| **Linux Fundamentals** | Operating Systems | Terminal Navigation & Permissions | ✅ Completed |
| **Nmap Basics** | Enumeration | Network Scanning & Port Discovery | ✅ Completed |
| **Cryptography** | Security | Mastered Hashing (SHA-256) vs Encryption (AES/RSA) for data integrity. |  ✅ Completed |
| **Moniker** | Exploitation | Exploiting CVE-2024-21413 (MonikerLink) to leak NTLM hashes via SMB. | ✅ Completed |
| **Metasploit Intro** | Tools | Mastered the MSF Framework: Exploit selection, Payload configuration (Meterpreter), and Database (msfdb) management. |  ✅ Completed |
| **Metasploit Exploitation** | Tools | 	SMB Enumeration & Credential Auditing (Brute-force) | ✅ Completed  |
#### **Technical Evidence: SMB Credential Audit**
Successfully identified weak credentials for user `penny` using a dictionary attack.

![SMB Login Success](images/msf-smb-success.png)

### **Phase 3: Exploitation (Task 5)**
- **Vulnerability:** MS17-010 (EternalBlue)
- **Payload:** `windows/x64/meterpreter/reverse_tcp`
- **Result:** Successfully gained **NT AUTHORITY\SYSTEM** privileges on the target Windows machine.

![Exploitation Success](images/msf-exploitation-system-access.png)

#### **Post-Exploitation & Data Exfiltration**
After gaining SYSTEM access, I performed the following actions to demonstrate impact:
- **Proof of Access:** Located and read `flag.txt` using Meterpreter's `cat` command.
- **Credential Harvesting:** Executed `hashdump` to extract NTLM hashes.
- **Finding:** Successfully retrieved the NTLM hash for user `pirate`, which could be used for further "Pass-the-Hash" attacks.

### **Phase 5: Privilege Escalation & Credential Harvesting**
- **Method:** Local Privilege Escalation via `sudo` misconfiguration.
- **Action:** Leveraged root-level permissions to access restricted system files.
- **Finding:** Successfully extracted Linux password hashes (SHA-512) for offline cracking.

> [!IMPORTANT]
> **Internship-Level Insight:** 
> "While standard Metasploit post-exploitation modules were restricted by the environment's security , I successfully pivoted to manual Linux enumeration. By identifying a sudoers misconfiguration, I achieved full system compromise and credential harvesting, demonstrating the ability to maintain operational momentum when automated tools reach their limits."

[!Root Access Proof](images/linux-priv-esc.png)


## 💼 Virtual Internships (Job Simulations)

| Company | Program | Task Completed | Key Skill |
| :--- | :--- | :--- | :--- |
| **Mastercard** | [Cybersecurity](https://www.theforage.com) | Phishing Analysis (Task 1) | Threat Detection & Social Engineering |
.
