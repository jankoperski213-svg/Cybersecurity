# [TryHackMe] Moniker Link (CVE-2024-21413) – Writeup

## Lab Overview
- **Platform:** TryHackMe
- **Box Name:** Moniker Link
- **CVE:** CVE-2024-21413 (Microsoft Outlook Protected View Bypass)
- **Category:** Email Exploitation / Privilege Escalation
- **Difficulty:** Medium
- **Goal:** Exploit Outlook vulnerability to gain initial access and escalate privileges to admin.

## Reconnaissance
### Network Enumeration
- Scanned target with **Nmap** to identify open ports and services
- Interesting findings:
  - SSH service running on standard port
  - Email service exposed
  - Web service with login portal

## Vulnerability Analysis
### CVE-2024-21413 Details
- **Vulnerability Type:** Protected View Bypass in Microsoft Outlook
- **Impact:** Allows execution of embedded OLE objects without proper sandbox checks
- **Attack Vector:** Specially crafted email attachment (.msg or .docm file with embedded exploit)

## Exploitation
### Initial Access
1. Identified email attachment vulnerability in user mailbox
2. Crafted malicious document with embedded executable
3. Bypassed Outlook's Protected View protection
4. Achieved code execution as email user

### Post-Exploitation
- Gained shell access to the system
- Enumerated user privileges and permissions
- Identified service running with elevated privileges

## Privilege Escalation
### Technique: Service Misconfiguration
1. Discovered misconfigured Windows service
2. Service runs with SYSTEM privileges but allows user modification
3. Replaced service executable with reverse shell payload
4. Restarted service to gain SYSTEM access

## Key Techniques Learned
- Email-based attack vectors and social engineering
- Windows service enumeration and exploitation
- OLE object manipulation in Office documents
- Bypass techniques for security features

## Lessons & Takeaways
- **Security Impact:** CVEs in everyday applications (like Outlook) can lead to complete system compromise
- **Defense:** Keep systems patched, use email gateways with sandboxing, enforce Protected View policies
- **For Future:** This technique demonstrates the importance of defense-in-depth; a single bypass isn't enough

## Tools Used
- `nmap` – Network scanning
- `msfvenom` – Payload generation
- `Metasploit` – Exploitation framework (optional)
- `PowerShell` – Post-exploitation enumeration

## References
- CVE-2024-21413 Official Advisory
- Microsoft Outlook Security Best Practices
- TryHackMe Room: Moniker Link
