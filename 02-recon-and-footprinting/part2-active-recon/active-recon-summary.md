# Active Reconnaissance Summary

**Date:** April 2026  
**Target:** Metasploitable 2 (192.168.56.3)  
**Tool used:** nmap -sV

---

## Summary

Metasploitable's security posture can best be described as swiss 
cheese — with 23 open ports exposing a wide range of vulnerable, 
outdated, and misconfigured services. Nearly every port discovered represents a 
realistic attack vector, from plain text protocols like Telnet and 
FTP to a root-level bindshell that requires no authentication 
whatsoever. This system would be compromised within minutes on any 
real network.

The service that would be prioritized for immediate hardening is 
Port 21 running vsftpd 2.3.4. This specific version contains a 
well-documented backdoor vulnerability that allows any attacker to 
open a root shell on the system without any credentials — making it 
arguably the most dangerous single service on the machine. Combined 
with FTP's inherent lack of encryption, this port alone represents 
a complete system compromise waiting to happen.

From a defensive standpoint two actions should be taken immediately. 
First, vsftpd 2.3.4 should be replaced with a modern, patched 
alternative or disabled entirely in favor of a secure file transfer 
protocol such as SFTP. Second, the bindshell on port 1524 must be 
closed and made completely inaccessible from outside the system — 
a root shell exposed to the network with no authentication is a 
critical vulnerability that should be treated as an active incident 
on any production system. More broadly, a full audit of all 23 open 
ports should be conducted with the goal of closing or restricting 
every service that is not absolutely necessary for the system to 
function.

---

## Key Statistics

| Metric | Value |
|---|---|
| Total open ports | 23 |
| Critical risk ports | 2 (Port 21, Port 1524) |
| High risk ports | 3 (Port 23, Port 3306, Port 5900) |
| Plain text protocols | 2 (FTP, Telnet) |
| Known backdoors | 2 (vsftpd 2.3.4, UnrealIRCd) |

---

## Top Recommendations

1. **Replace vsftpd 2.3.4 immediately** — upgrade to a patched 
   version or disable FTP entirely and switch to SFTP
2. **Close port 1524** — a publicly accessible root shell is a 
   critical incident on any real system
3. **Disable Telnet** — replace with SSH for all remote access
4. **Restrict MySQL to localhost** — databases should never be 
   directly exposed to the network
5. **Audit all 23 open ports** — disable every service that is 
   not absolutely necessary
