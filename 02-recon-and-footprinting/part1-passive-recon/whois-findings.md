# Whois Findings — testphp.vulnweb.com

**Tool used:** whois.com public lookup  
**Date:** April 2026

## Results

| Field             | Value                          |
|-------------------|--------------------------------|
| Domain            | vulnweb.com                    |
| Registrar         | Gandi SAS (IANA ID: 81)        |
| Organization      | Invicti Security Limited       |
| Country           | Malta (MT)                     |
| Registered On     | 2010-06-14                     |
| Expires On        | 2027-06-14                     |
| Last Updated      | 2025-11-17                     |
| Name Servers      | ns-105-a.gandi.net             |
|                   | ns-11-b.gandi.net              |
|                   | ns-140-c.gandi.net             |
| Domain Status     | Client Transfer Prohibited     |

## Key Observations

- The domain is owned by Invicti Security Limited, the company that 
  maintains vulnweb.com as an intentional penetration testing 
  training target.
- Registered in 2010, indicating a long-standing and established domain 
  rather than a newly spun-up or suspicious site.
- All three name servers are managed through Gandi, meaning DNS 
  infrastructure is centralized under one provider — a single point 
  of failure if that provider were compromised.
- Domain status is "client transfer prohibited," a standard lock that 
  prevents unauthorized domain hijacking.

## Security Relevance

Whois data exposes the real organization behind a domain, its registrar, 
and DNS infrastructure. An attacker could use this to identify the 
hosting provider, map out related domains owned by the same organization, 
or target the registrar as an attack vector. For defenders, this 
highlights the importance of enabling domain lock statuses and using 
privacy protection where appropriate.
