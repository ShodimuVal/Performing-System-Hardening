# Applied Lab: Performing System Hardening 

##  Description
This project was completed as part of my learning path to attain the **CompTIA CySA+ certification**.  
The lab focused on **system hardening** across Windows and Linux environments, emphasizing removal of unnecessary components and updating critical ones.  
It was conducted in a simulated enterprise environment for **Structureality Inc.**, reinforcing practical skills in vulnerability mitigation and secure configuration.

---

##  Objective
To apply system hardening techniques by:
- Managing Windows device drivers
- Manipulating hosts file name resolution
- Removing unneeded software and services
- Setting firewall rules to block ICMP communications
- Configuring Linux file permissions for least privilege

---

##  Skills Learned
- Device driver management (update, disable/enable, uninstall/reinstall)
- Hosts file manipulation for DNS resolution control
- Application and service removal for reduced attack surface
- Firewall rule configuration to enforce ICMP blocking
- Linux file permission management using symbolic and octal notation
- Applying least privilege principles across operating systems

---

##  Tools Used
- **Windows Server 2016/2019** (MS10, DC10, PC10 VMs)
- **Device Manager**
- **Programs and Features / Server Manager**
- **Windows Defender Firewall with Advanced Security**
- **Kali Linux (Debian build)**
- **Linux utilities:** `ls -l`, `nano`, `chmod`, `wget`

---

##  Steps

### 1. Managing Device Drivers
- Scanned for hardware changes in Device Manager.
- Updated Microsoft Virtual DVD-ROM driver.
- Disabled and re-enabled the device for troubleshooting.
- Uninstalled and reinstalled the driver to validate removal/recovery.

### 2. Manipulating Hosts File Resolution
- Edited `/etc/hosts` on Kali Linux to force incorrect resolution for `juiceshop.local`.
- Verified failed connectivity with `wget`.
- Corrected entry to proper IP (`203.0.113.228`) and validated successful resolution.
- Demonstrated how hosts file entries override DNS queries for blocking or forcing resolution.

### 3. Removing Unneeded Applications & Services
- Uninstalled **CPUID CPU-Z** via Programs and Features.
- Removed insecure **FTP service** via Server Manager → Remove Roles and Features.
- Reduced attack surface by eliminating unused software and services.

### 4. Hardening with Firewall Rules
- Verified ICMP connectivity between PC10 and DC10 (ping responses).
- Configured inbound rules on DC10 to block ICMPv4 and ICMPv6 Echo Requests.
- Retested connectivity from PC10 → DC10, confirming ICMP blocked (Request timed out).
- Demonstrated explicit deny rules override multiple allow rules.

### 5. Setting Linux File Permissions
- Reviewed file permissions with `ls -l`.
- Applied symbolic changes (`chmod u+x`, `chmod g+w`, etc.).
- Practiced octal representation (`chmod 777`, `chmod 740`, `chmod 654`, `chmod 644`).
- Hardened `demofile.sh` with `chmod 710` → `-rwx--x---` (owner full access, group execute, others none).
- Validated execution and reviewed script contents with `./demofile.sh` and `cat`.

---

##  Shared Responsibility & Risks
- **Windows systems:** Risk of misconfigured drivers, insecure services, and open firewall rules.  
- **Linux systems:** Risk of overly permissive file permissions leading to privilege escalation.  
- **Mitigations:**  
  - Remove unnecessary software/services.  
  - Apply least privilege permissions.  
  - Explicit firewall deny rules for ICMP.  
  - Validate changes with testing tools (`ping`, `wget`, `ls -l`).  

---

## Results
- **Drivers managed:** Updated, disabled/enabled, uninstalled/reinstalled successfully.  
- **Hosts file hardened:** Demonstrated forced resolution and correction.  
- **Attack surface reduced:** Removed CPUID and FTP service.  
- **Firewall hardened:** ICMP blocked on DC10, compliance achieved.  
- **Linux permissions enforced:** `demofile.sh` restricted to owner and group only.  

This lab demonstrates practical system hardening across multiple platforms, reinforcing the principle of **remove what’s unnecessary, update what’s essential, and enforce least privilege** — all critical skills for the **CompTIA CySA+ certification journey**.
