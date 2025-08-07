Task 3 – Vulnerability Assessment Using Nmap
1. Objective
Conduct a vulnerability assessment scan on the host 192.168.29.208 using Nmap’s vulnerability scripts, and analyze and document the results.

2. Methodology
Tool: Nmap v7.95

Scan Command:

bash
nmap -sV --script vuln 192.168.29.208
Target: 192.168.29.208 (Internal Network Host)

3. Results
### 3.1 Open Ports and Services

| Port | State     | Service           | Details                              |
|------|-----------|-------------------|--------------------------------------|
| 135  | open      | msrpc             | Microsoft Windows RPC                |
| 139  | open      | netbios-ssn       | Windows NetBIOS Session Service      |
| 445  | open      | microsoft-ds?     | Windows SMB (file sharing)           |
| 902  | open      | ssl/vmware-auth   | VMware Authentication Daemon 1.10    |
| 912  | open      | vmware-auth       | VMware Authentication Daemon 1.0     |
| 514  | filtered  | shell             | Communication filtered/not scanned   |

### 3.2 Vulnerability Script Output

- **smb-vuln-ms10-054:** `false`  
  *System is NOT vulnerable to MS10-054.*

- **samba-vuln-cve-2012-1182** and **smb-vuln-ms10-061:**  
  *Could not negotiate a connection (likely not applicable, not vulnerable, or communication blocked).*

- **Other Scripts:**  
  *No other vulnerabilities were reported by the Nmap scripts.*

4. Analysis
No remotely exploitable vulnerabilities were detected by Nmap's vulnerability scripts for the open services.

A result of false means the system was specifically checked for that vulnerability and found secure.

Protocol negotiation errors likely indicate the service is patched, closed to Nmap probes, or does not match the vulnerable version.

Port 514/tcp could not be assessed due to being filtered.

5. Reflection
Why no vulnerabilities detected?

Exposed services are likely patched and configured securely.

Some checks require additional access/authentication or are blocked by the firewall.

Nmap scripts only detect network-exposed, signature-based issues.

Security implications:

Absence of detected network vulnerabilities is a good indicator, but does not guarantee complete system security.

Regular patching, broader assessments, and defense-in-depth should continue.

6. Conclusion
The Nmap vulnerability assessment of 192.168.29.208 revealed multiple common Windows/VMware network services, but no vulnerabilities were detected by the scripts used. This suggests the system is reasonably secure against the issues that Nmap can identify remotely.


Feel free to adjust for your name, date, or add screenshots as images using Markdown syntax if your repo contains them.
