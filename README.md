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
| Operating System Introduction | Sec 9 | OS Architecture,Privilege Seperation,Process Isolation,Access Control and Resource Management |  ✅ Completed |
| Windows Basics | Sec 10 | Windows GUI navigation, NTFS permissions, and essential administrative/security tools | ✅ Completed  |
| Linux CLI Basics | Sec 11 | Linux directory navigation, file manipulation, and fundamental terminal commands | ✅ Completed |
| Windows CLI Basics | Sec 12 | Command Prompt (CMD) and PowerShell core commands, file structure management, and system queries | ✅ Completed  |
| Operating System Security | Sec 13 | OS hardening, user privileges, firewall configurations, and endpoint protection layers | 🟩 In Progress |
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

--
## Lab: Introduction to Operating Systems (TryHackMe)
## 🖥️ Overview
This module explores how an operating system (OS) acts as the vital bridge between a computer's physical hardware and user applications. Understanding the core structure of an OS is essential for identifying how systems protect themselves and where vulnerabilities can emerge.


| OS Component | Purpose | Security Perspective |
| :--- | :--- | :--- |
| **The Kernel** | Core program with complete, unrestricted hardware control. | High-value target; a compromise here grants total system control. |
| **User Space** | Restricted area where standard user programs and apps run. | Low-level privilege area; prevents buggy apps from crashing the whole system. |
| **Process Management** | Allocates CPU time and memory slices to active apps. | Ensures process isolation so malware in one app can't steal data from another. |
| **User Management** | Manages accounts, authentication, and file permissions. | Enforces the "Principle of Least Privilege" to restrict unauthorized file access. |
| **Device Management** | Uses drivers to communicate with hardware peripherals. | Malicious or unverified drivers can bypass security to inject malware. |


## 🔍 Key Takeaways
- The kernel handles the heavy lifting, while user space keeps regular applications isolated.
- Applications must use "System Calls" to request the kernel to perform tasks like reading a file.
- Process isolation ensures that if one application crashes, it does not bring down the entire OS.
- File permissions are the primary defense against users accessing data they shouldn't see.
- Antivirus software requires high-level privileges close to the kernel to monitor system threats effectively.
- Hardware is useless without an OS to coordinate resources and schedule CPU tasks.

## Lab: Windows Basics (TryHackMe)

## 🖥️ Overview
This lab provides a foundational look into the Windows Operating System environment, focusing on navigating the Graphical User Interface (GUI), understanding how files are organized and secured, and monitoring system behavior using native tools.

## ⚙️ Core Windows Components & Security

| Tool / Concept | Function | Security Perspective |
| :--- | :--- | :--- |
| **NTFS File System** | The standard file system structure for Windows NT branch. | Allows granular access control lists (ACLs) like Read, Write, and Execute permissions. |
| **Task Manager** | Provides real-time metrics on CPU, Memory, Disk, and Network usage. | Crucial for identifying unauthorized background processes, resource spikes, or persistent malware. |
| **Windows Security** | Built-in central hub for antivirus, firewall, and device health status. | The first line of defense; security analysts monitor this to ensure real-time protection isn't disabled. |
| **Control Panel / Settings** | Centralized interfaces for adjusting system configuration settings. | Targets for administrative modification; hardening a system involves locking these menus down. |
---
## 📖 Key Terminology & Applications (Security Perspective)

*   **Desktop:** The primary visual workspace. *Security Context:* Often cluttered by users with sensitive files or credentials exposed in plain sight.
*   **Taskbar:** The bottom control strip for quick access. *Security Context:* Used to quickly launch critical defensive tools like Task Manager or terminal instances during an incident response.
*   **Start Menu:** The central launchpad for applications and power controls. *Security Context:* Attackers often target the "Startup" folder hidden within here to maintain persistence after a reboot.
*   **Search:** The built-in indexing tool. *Security Context:* Allows defenders to rapidly locate deeply buried system administrative utilities or configuration panels.
*   **File Explorer:** The native file management interface. *Security Context:* Crucial for navigating the directory structure to audit NTFS permissions, locate hidden folders, or find malicious payloads.
*   **Windows Update:** The OS patch management system. *Security Context:* The single most critical tool for closing security gaps and fixing critical vulnerabilities before they can be weaponized.
*   **Microsoft Store:** The repository for trusted, signed applications. *Security Context:* Minimizes "shadow IT" risks by ensuring users download verified software instead of untrusted internet binaries.
*   **Windows Settings:** The modern configuration hub. *Security Context:* The go-to menu for managing user account privacy configurations, app permissions, and basic system hardening.
*   **Control Panel:** The legacy system management interface. *Security Context:* A high-value target for attackers looking to manipulate deeper network settings, device drivers, or local user accounts.
*   **Task Manager:** The real-time system monitoring tool. *Security Context:* Used to hunt for anomalous processes, detect unauthorized resource spikes, and forcibly terminate suspected malware executables.
*   **Windows Security:** The centralized defensive dashboard. *Security Context:* Provides an immediate health check on real-time antivirus protection, ransomware mitigations, and account security.
*   **Windows Defender Firewall:** The native network traffic filter. *Security Context:* Configured to enforce strict inbound and outbound rules, blocking unauthorized network connections and lateral movement.
---

## Lab: Linux CLI Basics (TryHackMe)

## 🖥️ Overview
This lab introduces the Linux Command Line Interface (CLI), focusing on text-based system navigation, file management, and understanding how the Linux operating system handles data structure without a graphical user interface.

## ⚙️ Core Linux Commands & Security Context

| Command | Function | Security Perspective |
| :--- | :--- | :--- |
| **`pwd`** (Print Working Directory) | Displays the exact absolute path of the current directory. | Helps orientation during a terminal session to ensure commands aren't executed in the wrong system folder. |
| **`ls`** (List) | Lists directory contents. Frequently used with `-la` flags. | Used to reveal hidden files (like `.bash_history` or hidden scripts) and audit file permissions. |
| **`cd`** (Change Directory) | Navigates between folders in the file system hierarchy. | Essential for moving into system configuration directories (like `/etc`) to inspect system settings. |
| **`cat`** (Concatenate) | Displays the contents of a text file directly in the terminal. | Used to quickly read configuration files, logs, or scripts without opening a heavy text editor. |
| **`find`** (Search Tool) | Recursively searches the directory tree for files matching specific criteria. | A critical tool for hunting down hidden web shells, unusual files, or specific logs across the system. |

## 🔍 Deep Dive: Master the `find` Command

Understanding how to construct search strings is essential for both privilege escalation and malware hunting. 

*   **Syntax Breakdown (`find ~ -name "filename"`)**:
    *   `find`: Invokes the search utility.
    *   `~` (The Tilde): Specifies the starting location. This tells Linux to look *only* inside the current user's **Home Directory**.
    *   `-name`: A flag telling the system to look for files based on their literal text name.
*   **Example Usage**: `find ~ -name "*.txt"` will scan your home folder and pull up every single plain text file, helping you quickly identify hidden notes or unencrypted credentials.

---
## 📖 Key Linux Terminology

*   **The Shell:** The command language interpreter that executes commands read from standard input devices like keyboards.
*   **Root Directory (`/`):** The top-most directory in a Linux system. Every single file and folder branches out from here.
*   **Home Directory (`~`):** The personal workspace storage area designated for the currently logged-in user.
*   **Flags/Switches:** Extra arguments added to commands (e.g., `-h` or `--help`) to modify their behavior or output format.

---

## 🔍 Key Takeaways
- **The Power of CLI**: Operating via the terminal is significantly faster and consumes fewer system resources than a GUI, making it ideal for remote server management.
- **Case Sensitivity**: Unlike Windows, Linux is strictly case-sensitive. Filenames like `Secret.txt` and `secret.txt` are treated as completely different files.
- **Absolute vs. Relative Paths**: Learned to distinguish between referencing a file from the root directory (`/var/log/syslog`) versus referencing it from the current working folder (`./syslog`).
- **Targeted Searching**: Using the `find` command allows security operators to sift through thousands of system files in seconds instead of clicking through directories manually.

---

## Lab: Windows CLI Basics (TryHackMe)

## 🖥️ Overview
This lab covers the essential utilities of the Windows Command Line Interface, bridging the gap between legacy Command Prompt (CMD) and modern, object-oriented PowerShell. It focuses on command-line system navigation, configuration discovery, and administrative management.

## ⚙️ Core Windows CLI Commands & Security Context

| Command | Function | Security Perspective |
| :--- | :--- | :--- |
| **`whoami`** | Displays the domain and username of the currently logged-in user. | The very first command execution run by both red teams (reconnaissance) and blue teams (audit) to confirm current privileges. |
| **`hostname`** | Prints the netbios name assigned to the specific local computer system. | Used to quickly identify where you are in a network infrastructure during pivot or lateral movement operations. |
| **`systeminfo`** | Displays detailed configuration data including OS version, patch levels, and hardware specs. | A goldmine for attackers looking for missing security updates/patches to plan local privilege escalation exploits. |
| **`ipconfig`** | Displays all current TCP/IP network configuration values and refreshes DHCP/DNS settings. | Vital for mapping out the local network footprint, identifying gateways, and finding internal IP subnets to target. |
| **`dir`** | Lists the contents, subdirectories, and files within the current directory. | Used to inspect file creation dates and look for hidden or unexpected executable payloads (`.exe`, `.bat`). |
| **`cd`** | Changes the current working directory path. | Crucial for traversing administrative file trees to locate system configurations or log directories. |
| **`type`** | Displays the contents of a text file directly on the command screen. | The Windows equivalent to Linux `cat`; allows rapid manual inspection of scripts, batch files, or text logs without a GUI editor. |
| **`cls`** | Clears the visible screen buffer of the command prompt window. | Standard housekeeping command used to keep the workspace clean and remove historical command outputs from immediate view. |

---
---
---

## Lab: Operating System Security (TryHackMe)

## 🖥️ Overview
This lab focuses on the principles of operating system hardening, defensive configurations, and securing both Windows and Linux environments against unauthorized access, privilege escalation, and network-based threats.

## ⚙️ Core OS Security Concepts & Controls

| Concept / Tool | Function | Defensive Objective |
| :--- | :--- | :--- |
| **Principle of Least Privilege (PoLP)** | Restricting user access rights to only the absolute minimum necessary to perform a job. | Limits the blast radius if an individual user account becomes compromised by an attacker. |
| **User Account Control (UAC)** | A Windows security feature that prevents unauthorized changes to the operating system. | Forces applications to run in a standard user context until an administrator explicitly authorizes elevated rights. |
| **Authentication & Authorization** | Verifying identity (Passwords/MFA) and determining what resources that identity can access. | Ensures threat actors cannot easily spoof user profiles or access restricted system resources. |
| **Endpoint Security** | Deploying anti-malware, host-based firewalls, and monitoring tools directly onto target systems. | Detects, blocks, and alerts security teams to malicious behavior right at the workstation level. |

---
## 🛡️ Operating System Hardening Techniques

Securing an operating system requires turning off unnecessary features and locking down access points to shrink the system's "attack surface."

*   **Disabling Unused Services:** Every active service running in the background is a potential entry point. If a server does not need a web interface, turning off HTTP services removes that vector entirely.
*   **Patch Management:** Routinely applying security updates ensures that known vulnerabilities (CVEs) are closed before threat actors can weaponize them.
*   **Host-Based Firewalls:** Configuring strict inbound and outbound traffic filtering rules on the local machine prevents lateral movement within an internal network.
  ---

## 🔍 Key Takeaways
- **Defense in Depth**: Relying on a single password isn't enough. True OS security combines strict user permissions, robust logging, host firewalls, and active endpoint monitoring.
- **The Human Element**: Implementing technical blocks like UAC helps save users from accidentally executing malicious attachments or modifying critical system settings.
- **Continuous Auditing**: Systems change constantly. Regularly auditing who belongs to administrative groups is vital for catching privilege creeping.

 ----
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
