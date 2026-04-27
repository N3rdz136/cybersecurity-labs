# Netcraft Findings — testphp.vulnweb.com

**Tool used:** Netcraft Site Report  
**Date:** April 2026

## Network Results

| Field                  | Value                                                    |
|------------------------|----------------------------------------------------------|
| Hosting Provider       | Amazon Web Services (AWS)                                |
| Hosting Location       | US West — Oregon datacenter                              |
| Netblock Owner         | Amazon.com, Inc.                                         |
| ASN                    | AS16509                                                  |
| IPv4 Address           | 44.228.249.3                                             |
| Reverse DNS            | ec2-44-228-249-3.us-west-2.compute.amazonaws.com         |
| IPv6                   | Not Present                                              |
| Organization           | Invicti Security Limited, Malta                          |
| Domain Registrar       | gandi.net                                                |
| DNS Security (DNSSEC)  | Enabled                                                  |

## Site Technology

| Category       | Technology                          | Description                        |
|----------------|-------------------------------------|------------------------------------|
| Cloud & PaaS   | Amazon Web Services - EC2           | Cloud computing service (Elastic Compute Cloud) |

## Security Findings

| Control        | Status         | Risk                                          |
|----------------|----------------|-----------------------------------------------|
| SPF Record     | Not Present    | Domain vulnerable to email spoofing           |
| DMARC Record   | Not Present    | No enforcement policy against spoofed emails  |
| Web Trackers   | None detected  | Expected for a training/lab target            |
| DNSSEC         | Enabled        | Positive control — protects against DNS spoofing |

## Key Observations

- The server runs on AWS EC2 in Oregon, confirmed by both the 
  hosting company listing and the reverse DNS record which 
  publicly exposes the cloud provider and region.
- No traditional web server technology (Apache, Nginx) or 
  application language (PHP) was detected by Netcraft, possibly 
  due to limited crawl data or suppressed server headers.
- The absence of SPF and DMARC records is a meaningful security 
  gap — an attacker could send spoofed emails appearing to come 
  from this domain with no technical controls to stop it.
- DNSSEC being enabled is a positive finding, reducing the risk 
  of DNS cache poisoning or spoofing attacks.

## Security Relevance

Cloud hosting details exposed via reverse DNS make infrastructure 
reconnaissance trivial. Missing SPF and DMARC records represent 
low-effort, high-impact fixes a defender should prioritize. 
The lack of web trackers reduces the site's fingerprint but 
does not compensate for missing email authentication controls.
