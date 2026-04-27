# Google Dork Findings — testphp.vulnweb.com

**Tool used:** Google Search with operators  
**Date:** April 2026

## Dork 1 — Full Site Index

**Query:** `site:testphp.vulnweb.com`

| Field | Detail |
|---|---|
| Interesting Result | `/admin` login page publicly indexed |
| URL | testphp.vulnweb.com/admin |
| Status | Page currently times out but remains indexed |

**Why it matters:** An indexed admin panel means the administrative 
interface was publicly accessible long enough for Google to crawl it. 
Even though it currently times out, attackers know it exists and can 
monitor for it to become accessible again for brute force or 
credential stuffing attacks.

---

## Dork 2 — PHP Pages

**Query:** `site:testphp.vulnweb.com inurl:php`

| Field | Detail |
|---|---|
| Interesting Result | "Add a new user" page |
| Significance | Exposed user creation functionality |

**Why it matters:** A publicly accessible user creation page reveals 
the application has a user management system backed by a database. 
If this is an admin-level function it could allow an attacker to 
create privileged accounts and take over the application.

---

## Dork 3 — PHP File Enumeration

**Query:** `site:testphp.vulnweb.com filetype:php`

| Field | Detail |
|---|---|
| Results Found | login.php, logout.php, guestbook, signup.php |

**Why it matters:**

- **login.php** — Authentication entry point, target for brute 
  force and SQL injection attacks
- **logout.php** — Reveals session management exists, potential 
  target for session fixation vulnerabilities
- **guestbook** — Accepts and displays user input, classic target 
  for Cross Site Scripting (XSS) attacks
- **signup.php** — Open registration confirms anyone can create 
  accounts, potential for mass account creation attacks

---

## Overall Attack Surface Summary

| Page Found | Risk Level | Attack Vector |
|---|---|---|
| /admin | Critical | Brute force, credential stuffing |
| Add a new user | High | Unauthorized account creation |
| login.php | High | SQL injection, brute force |
| guestbook | High | Cross Site Scripting (XSS) |
| signup.php | Medium | Mass account creation |
| logout.php | Low | Session fixation |
