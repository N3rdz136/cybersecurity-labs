# Passive Reconnaissance Summary

**Date:** April 2026  
**Targets:** testphp.vulnweb.com | fullstackacademy.com

---

## Target Exposure Summary

### testphp.vulnweb.com
This target was extremely exposed from a passive reconnaissance 
perspective. Critical application entry points including an admin 
panel, user creation page, guestbook, login, and signup pages were 
all discoverable through basic Google Dork queries — requiring no 
advanced techniques or deep investigation. The site reads as an 
open book, with its full attack surface visible to anyone with a 
browser and basic knowledge of search operators.

### fullstackacademy.com
Fullstack Academy presented a significantly more secure posture. 
No PHP pages or application entry points were discoverable via 
Google (site:fullstackacademy.com inurl:php returned zero results), 
and sensitive information required deliberate digging through 
publicly available documents. However, the information that is 
public — alumni names, course syllabi listing specific tools, a 
physical address, and graduate outcome data — is sufficient to 
begin planning targeted phishing campaigns or in-person social 
engineering attacks, demonstrating that even well-secured 
organizations have a passive recon footprint worth addressing.

---

## Top 5 Passive Findings

### Finding 1 — Exposed Admin Panel
- **What was found:** Google indexed testphp.vulnweb.com/admin,
  publicly exposing the administrative interface of the application
- **Tool/Query:** Google Dork — `site:testphp.vulnweb.com`
- **Why it matters to a defender:** An indexed admin panel is a
  prime target for brute force and credential stuffing attacks.
  Admin interfaces should never be publicly accessible and should
  be restricted by IP allowlist or VPN access only.

### Finding 2 — User Creation Page Exposed
- **What was found:** A page allowing creation of new user accounts
  was publicly discoverable via Google
- **Tool/Query:** Google Dork — `site:testphp.vulnweb.com inurl:php`
- **Why it matters to a defender:** Exposed user creation
  functionality could allow an attacker to create unauthorized
  accounts or escalate privileges. User management functions
  should require authentication and should never be publicly
  accessible.

### Finding 3 — Full Application Structure Visible
- **What was found:** login.php, logout.php, guestbook, and
  signup.php all discoverable via Google — revealing the complete
  authentication and input surface of the application
- **Tool/Query:** Google Dork — `site:testphp.vulnweb.com filetype:php`
- **Why it matters to a defender:** A publicly visible application
  structure gives attackers a complete roadmap of entry points to
  probe for SQL injection, XSS, and session vulnerabilities.
  Server headers should be suppressed and sensitive paths should
  be blocked from indexing via robots.txt.

### Finding 4 — Alumni Names Publicly Listed
- **What was found:** Alumni talks on fullstackacademy.com revealed
  real names of former students and their career outcomes
- **Tool/Query:** Google Dork — `site:fullstackacademy.com "syllabus"`
- **Why it matters to a defender:** Real names associated with an
  organization can be cross-referenced with LinkedIn and other
  platforms to build detailed profiles for spear phishing attacks.
  Organizations should obtain explicit consent before publishing
  individual names publicly.

### Finding 5 — Physical Address & Graduate Data Exposed
- **What was found:** Privacy policy revealed a physical mailing
  address. CIRR report revealed median salaries, job titles, and
  employment outcomes of graduates
- **Tool/Query:** Google Dork — `site:fullstackacademy.com inurl:start`
- **Why it matters to a defender:** A physical address enables
  in-person social engineering and tailgating attacks. Graduate
  outcome data helps attackers craft convincing impersonation
  scenarios targeting former students or staff.

---

## Key Takeaway

The most striking observation across both targets was the contrast
between effort and reward. testphp.vulnweb.com required almost no
effort — high risk findings like admin access and user creation
pages appeared immediately in basic Google searches. fullstackacademy.com
required more deliberate investigation, but following the trail of
publicly available documents was enough to begin planning targeted
social engineering attacks. This demonstrates a critical security
principle: technical hardening alone is not enough. Organizations
must also audit their publicly accessible documents and human
intelligence footprint.

---

## Recommended Follow-Up Action for a Defender

**For testphp.vulnweb.com:**
Immediately restrict the admin panel and user management pages
behind authentication and IP allowlisting. Implement robots.txt
to prevent search engine indexing of sensitive application paths.
Conduct a full web application penetration test prioritizing the
guestbook (XSS), login page (SQL injection), and user creation
functionality (privilege escalation).

**For fullstackacademy.com:**
Audit all publicly indexed PDFs and restrict sensitive documents
behind authentication. Review alumni and event pages and obtain
explicit consent before publishing individual names. Consider
adding a security.txt file and implementing DMARC and SPF records
to close the email spoofing gap identified during Netcraft analysis.
