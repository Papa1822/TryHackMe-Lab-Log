# TryHackMe-Lab-Log
This repository documents my journey through multiple Cyber-security labs completed in Pre-security and Cyber101.

### 📊 Lab Progress Summary

> 💡 **Strategy Note:** While progressing through **Cyber101**, I am concurrently completing the updated **Pre-Security (Sections 4-7)**. This ensures I have a deep-dive understanding of OS Internals and Web Architecture, which strengthens my ability to perform manual exploitation and privilege escalation in the Cyber101 labs.

### 🛡️ Pre-Security (Sections 4-7)
*Focus: Deep-dive into Operating Systems and Web Architecture.*


| Lab Name | Section | Key Skill Learned | Status |
| :--- | :--- | :--- | :--- |
| Computer Fundamentals | Sec 4 | Hardware ID & BIOS/UEFI Boot Process | ✅ Completed  |
| Computer Types | Section 5 | Getting to know the various computer systems | ✅ Completed |
| Client Server Basics | Sec 6 | How client server communication occurs using IPs, ports and protocols | ✅ Completed |
| Virtualization Basics | Sec 7 | Hardware Optimization, Lab Building & Environment Management | ✅ Completed |
| Cloud Computing Fundamentals | Sec 8 | Cloud Service Models & shared responsibility framework | ✅ Completed  |
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
---
## ⚡ The Boot Process (Step-by-Step)
Understanding the boot sequence is critical for identifying where a system might be failing or where an exploit could be injected.

1. **Power On**: The PSU sends power to the Motherboard.
2. **POST (Power-On Self Test)**: The BIOS/UEFI checks if the CPU, RAM, and Video Card are working.
3. **BIOS/UEFI**: The firmware initializes the hardware and looks for a bootable device.
4. **Bootloader**: The system hands off control to a small program (like GRUB or Windows Boot Manager) that knows how to load the OS.
5. **OS Kernel**: The "heart" of the Operating System is loaded into RAM, taking full control of the hardware.

## 🔍 Key Takeaways
- **Volatile vs. Non-Volatile**: Learned that RAM loses data without power, while SSDs keep it.
- **BIOS/UEFI Security**: These are the first lines of defense; if the BIOS is compromised, the entire OS above it is untrustworthy.
- **Peripherals**: Distinguished between input (Mouse/Keyboard) and output (Monitor/Speakers) devices.

  ---
  ![Boot-Sequence](images/Boot-Sequence.png)

  ---
  
## Lab: Computer Types (TryHackMe)
## 🖥️ Overview
This module explores the diverse landscape of computing hardware, from everyday devices to high-powered enterprise infrastructure. Understanding these types is the first step in identifying "attack surfaces."

| Computer Type | Purpose | Security Perspective |
| :--- | :--- | :--- |
| **Personal Computers** | Laptops/Desktops for individual use. | High risk of social engineering (phishing). |
| **Workstations** | High-performance machines (NASA, Video Editing). | Targets for high-value data theft. |
| **Servers** | Provide services (Web, Email, File storage). | The "Main Prize" for hackers; requires strict access control. |
| **Mainframes** | Bulk data processing (Banks, Census). | Legacy systems that are often hard to patch. |
| **Supercomputers** | Complex calculations (Weather, Physics). | Extremely rare; high physical security. |
| **Embedded / IoT** | Single-purpose (Toasters, Smart Watches). | Often lack updates; easy entry point into a network. |


## 🔍 Key Takeaways
- Anything with a microchip is a computer,if a device is not segmented properly in a network ,it will create a doorway for an attacker into the system.
- Redundant power reduces a single failure point.
- Laptops throttle more than desktops due to less cooling space.
- Smartphones are optimized for efficiency hence have long lasting batteries compared to laptops.
- ECC RAM and certified drivers are more common in workstations.
- A hub or cloud server coordinates devices in smart homes.

  ---
  ## Lab: Client-Server Basics
  ## 🖥️ Overview
  This lab explores the fundamental relationship that powers the internet—the interaction between a requester (Client) and a provider (Server). It transitions from isolated computing to networked environments, focusing on how devices offer and consume services across a network.
  ## 🔍 Key Takeaways
  - **Client:** The device or software (like your web browser) that initiates a request for data or a service.
- **Server:** A powerful machine that "listens" for requests and provides the resource (like a website or file) back to the client.
- **Request-Response Cycle:** The fundamental way the web works—a client asks, and the server answers.
- **IP Address:** The unique numerical "home address" used to identify a server on the network so the client knows where to send requests.
- **Port:** A specific "doorway" on a server used for different services (e.g., Port 80 for web traffic, Port 25 for email).
- **Protocol:** The set of rules (like HTTP or HTTPS) that both the client and server agree to use so they can understand each other.
- **Security Insight:** Because servers are centralized hubs for data, they are primary targets for attacks like Denial of Service (DoS) or unauthorized access.

### 🌐 Web Communication in Practice (Lab)

In this lab, I simulated a real web request to see how data travels between my browser (the client) and the hosting server.

- **Status Code 200 OK:** Confirmed the request was successful and the server delivered the resource.
- **GET Method:** Used this protocol command to retrieve data from the host.
- **Loopback Address (127.0.0.1):** Identified that the server was hosted locally for this simulation.

![Lab Screenshot](images/web-comm-practice.png)

--

## Lab: Virtualization Basics
## 📖 Module Overview
This room explains how virtualization solves the problem of expensive, underutilized physical hardware. It introduces the Hypervisor—the "referee" software that manages and isolates multiple Virtual Machines (VMs) on a single host machine.

## 🧠 Key Takeaways:
- **Virtualization:** Technology that enables one physical computer to act as multiple separate, isolated systems.
- **Hypervisor:** The "manager" software that creates and runs VMs. There are two types:
- **Type 1:** Runs directly on hardware (best for big data centers).
- **Type 2 (Hosted):** Runs as an app on your regular OS (best for learning/home labs).
- **Virtual Machine (VM):** A complete, isolated computer running inside your real one, with its own CPU, RAM, and OS.
- **Container:** A lightweight "room" that shares the host's OS kernel to run a single app quickly—more efficient than a full VM.
** Security Insight:** Virtualization is essential for security because it allows you to run malicious files in an isolated sandbox where they can't harm your actual computer.

  ### 🛠️ Practical Lab: Virtualization Management
Successfully managed a simulated virtual environment for "AutoGalo" to resolve infrastructure issues:
- **Troubleshooting:** Identified a halted 'Mail-SERVER' and restored service to a running state.
- **Provisioning:** Created a new 'Marketing-VM' with specific resource allocations (4 CPU Cores, 8GB RAM, 100GB Disk).
- **Environment Audit:** Monitored host performance across physical servers (HV-PROD-01/02) to ensure hardware utilization.

--
## Lab: Cloud Computing Fundamentals
## Module Overview
This module explains how companies rent computing power over the internet instead of owning physical servers and also focuses on the different "as-a-Service" models (IaaS, PaaS, SaaS) .

## 🔍 Key Takeaways:
- **Service Models:** 
  - **IaaS:** Provider gives the hardware; I manage the OS and apps.
  - **PaaS:** Provider manages the OS; I just provide the code.
  - **SaaS:** Provider manages everything; I just use the software.
- **Shared Responsibility:** A critical security concept where the Cloud Provider secures the physical infrastructure, but the user is responsible for securing their own data and access credentials.
- **Deployment:** Differentiated between Public (shared), Private (dedicated), and Hybrid (mixed) cloud environments.



 ----
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
