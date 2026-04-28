# Nmap Scan Results — Metasploitable 2

**Tool used:** nmap -sV  
**Target:** 192.168.56.3  
**Date:** April 2026

## Scan Command
```bash
nmap -sV 192.168.56.3
```

## Full Results Summary

- **Total open ports found:** 23
- **Operating System:** Unix/Linux (Ubuntu)
- **Host status:** Up (0.00047s latency)
- **Scan duration:** 12.36 seconds

## Port & Service Table

| Port | Protocol | Service | Version | Risk Level |
|---|---|---|---|---|
| 21 | tcp | ftp | vsftpd 2.3.4 | Critical |
| 23 | tcp | telnet | Linux telnetd | High |
| 1524 | tcp | bindshell | Metasploitable root shell | Critical |
| 3306 | tcp | mysql | MySQL 5.0.51a-3ubuntu5 | High |
| 5900 | tcp | vnc | VNC protocol 3.3 | High |

## Detailed Risk Analysis

### Port 21 — FTP (vsftpd 2.3.4)
- **Risk:** This specific version of vsftpd contains a known backdoor
  vulnerability that allows an attacker to gain unauthorized root
  access without credentials. FTP also transmits usernames and
  passwords in plain text, making credentials trivially interceptable
  on the network.
- **Defense:** Disable FTP entirely and replace with SFTP or SCP
  for secure file transfer. If FTP must be used, upgrade to a
  patched version immediately and restrict access by IP.

### Port 23 — Telnet (Linux telnetd)
- **Risk:** Telnet transmits all data including usernames, passwords,
  and commands in plain text with no encryption. Anyone monitoring
  network traffic can intercept and read everything exchanged during
  a Telnet session, making credential theft trivial.
- **Defense:** Disable Telnet immediately and replace with SSH
  for all remote access. SSH encrypts all traffic making
  interception significantly harder.

### Port 1524 — Bindshell (Metasploitable root shell)
- **Risk:** This port is running a root-level shell that is directly
  accessible over the network. Root is the highest privilege level
  on a Linux system — anyone who connects to this port has complete
  control over the entire system with no authentication required.
  This is the most dangerous finding on the system.
- **Defense:** Immediately close this port and audit the system
  for any other backdoors or unauthorized services. This should
  be treated as a critical incident on any production system.

### Port 3306 — MySQL (MySQL 5.0.51a)
- **Risk:** A database exposed directly to the network can lead to
  leaked sensitive information including usernames, passwords, and
  personal data. An attacker with access could read, modify, or
  delete records, inject malicious data, or use database
  credentials to escalate privileges across the system.
- **Defense:** MySQL should never be exposed to the network
  directly. Bind it to localhost only (127.0.0.1), place it
  behind a firewall, and require strong authentication for
  all database users.

### Port 5900 — VNC (Protocol 3.3)
- **Risk:** VNC provides full graphical remote desktop access
  including mouse and keyboard control. If the VNC service has
  no password or a weak password, an attacker gains complete
  visual and interactive control of the system and could install
  malware, exfiltrate files, or use the machine as a launching
  pad to attack other systems.
- **Defense:** Disable VNC if not required. If remote desktop
  access is needed use a VPN with strong authentication rather
  than exposing VNC directly to the network.

## Additional Notable Ports

| Port | Service | Why It Matters |
|---|---|---|
| 22/tcp | SSH | Legitimate remote access — should be hardened with key auth only |
| 25/tcp | SMTP | Mail server exposed — potential for spam relay abuse |
| 512/tcp | exec | r-services allow remote access from any host — extremely dangerous |
| 6667/tcp | IRC | UnrealIRCd running — this version contains a known backdoor |
| 8180/tcp | http | Apache Tomcat exposed — often targeted for web shell uploads |
