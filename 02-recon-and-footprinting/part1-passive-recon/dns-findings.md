
# DNS Findings — testphp.vulnweb.com

**Tool used:** nslookup / dig (Kali Linux terminal)  
**Date:** April 2026

## Results

| Field        | Value                  |
|--------------|------------------------|
| Domain       | testphp.vulnweb.com    |
| IP Address   | 44.228.249.3           |
| Record Type  | A                      |

## Key Observations

- The domain resolves to a single IPv4 address via an A record, meaning
  it points directly to a server rather than an alias or CDN.
- No CNAME records observed, suggesting straightforward hosting
  without load balancing or domain aliasing.

## Security Relevance

A direct A record exposes the actual hosting IP address, which an
attacker could use to probe the server directly, potentially bypassing
any domain-level protections.
