# Vulnerability Scanner using Tenable Nessus Essentials

## Disclaimer
This project is intended for educational and ethical security improvement purposes only. Unauthorized use of vulnerability scanning tools for malicious activities is illegal and punishable by law. Always ensure ethical and legal compliance when using this tool.

## 📸 Project Screenshots
Click [here](https://github.com/Travis-N-W/Active-Directory/tree/main/screenshots) to view all screenshots.

## Project Objective
The objective of this project was to demonstrate the process of using Tenable Nessus Essentials to perform vulnerability scanning on a virtualized Windows 10 Pro machine. This included conducting both basic and credentialed scans to identify security vulnerabilities, followed by installing an outdated Firefox version to observe how the scanner detects vulnerabilities in legacy software. The project also involved applying remediations, such as uninstalling outdated software and updating the operating system to the latest patches, to assess the effectiveness of these actions in reducing vulnerabilities. The results showcased the importance of regular updates and the automation of simple remediation tasks to improve overall system security.

## Skills Learned
- Vulnerability Scanning  
- Patch Management  
- Remediation and Mitigation  
- Security Best Practices  
- Application Security Testing  

## Tools Used
- VMware Workstation Pro 17  
- Tenable Nessus Essentials  

## Installation & Setup
### VMware Workstation Pro 17 Installation and Guest OS Configuration
1. Download VMware Workstation Pro 17: [VMware Workstation Pro](https://www.vmware.com/products/desktop-hypervisor/workstation-and-fusion)
2. Install the software and set up a virtualized Windows 10 Pro guest OS.
3. Download Windows 10 Pro ISO: [Windows 10 Download](https://www.microsoft.com/en-us/software-download/windows10)
4. During VM setup, configure the network adapter to "Bridge Mode" (VMnet0) to allow the VM to function as a separate device on the network.

### Getting Started with Tenable Nessus Essentials
1. Download and install Nessus Essentials: [Nessus Essentials](https://www.tenable.com/products/nessus/nessus-essentials)
2. Sign up for an activation code.
3. Complete the installation and update all necessary plugins.

## Conducting a Vulnerability Scan
### Preparing the Target for Vulnerability Scanning
- Verify connectivity by pinging the guest OS from the host OS.
- Disable all Windows firewall profiles (`wf.msc`) to prevent interference.

### Conducting a Basic Vulnerability Scan
1. Open Nessus Essentials web UI.
2. Create a new scan using the **Basic Network Scan** template.
3. Target the Windows 10 Pro VM's IP address.
4. Run the scan and analyze the severity findings.
5. Review the CVSS (Common Vulnerability Scoring System) scores to prioritize issues.

## Credentialed Scanning
### Configuring Windows 10 Pro for Credentialed Scanning
1. Enable **Remote Registry** service.
2. Modify **User Account Control (UAC)** settings:
   - Set notifications to **"Never Notify"** (for test environments only).
3. Follow Nessus documentation for credentialed scans: [Nessus Credentialed Checks](https://docs.tenable.com/nessus/Content/CredentialedChecksOnWindows.htm#Configure-a-Local-Account)

### Configuring the Registry for Credentialed Scan Access
1. Open **Registry Editor** (`regedit`)
2. Navigate to: `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`
3. Add a new DWORD (32-bit) Value:
   - Name: `LocalAccountTokenFilterPolicy`
   - Value Data: `1` (Hexadecimal)
4. Restart the machine to apply changes.

### Running the Credentialed Scan
1. In Nessus, navigate to **Configure > Credentials**.
2. Add Windows machine credentials (username/password).
3. Save settings and run the credentialed scan.
4. Analyze the results:
   - 7 Critical vulnerabilities
   - 49 High-severity vulnerabilities
   - Recommended remediations provided

## Testing Vulnerabilities with Outdated Software
### Installing an Outdated Firefox Version
1. Download **Firefox 3.6.12**: [Firefox 3.6.12](https://ftp.mozilla.org/pub/firefox/releases/3.6.12/win32/en-US/)
2. Install using the setup wizard.
3. Run another credentialed scan to detect vulnerabilities.
4. Results showed new critical vulnerabilities related to the outdated browser.

## Applying Remediation and Re-scanning
### Remediation Steps
- **Uninstall** outdated Firefox version.
- **Update Windows 10**:
  - Navigate to **Settings > Windows Update**.
  - Check for and install updates until fully patched.

### Post-Remediation Scan Results
- **Before Remediation**: 7 Critical, 49 High-severity vulnerabilities
- **After Remediation**:
  - 1 Critical vulnerability
  - 13 High-severity vulnerabilities
  - 6 Medium-severity vulnerabilities
- Demonstrated the impact of applying updates and removing outdated software.

## Conclusion
This project showcased the importance of regular security scanning and patch management in maintaining a secure system. By performing both basic and credentialed scans, vulnerabilities were identified and remediations were applied to improve security posture. The experiment with installing outdated Firefox further emphasized the risks of legacy software. Automated security updates and proactive vulnerability management play a crucial role in reducing potential attack surfaces and strengthening overall cybersecurity defenses.
