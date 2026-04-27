# Light OSINT Findings — fullstackacademy.com

**Tool used:** Google Search with operators (no scanning performed)  
**Date:** April 2026

## Searches Performed

| Query | Example Result | Why It Matters |
|---|---|---|
| `site:fullstackacademy.com filetype:pdf` | Institutional disclosure, course catalog, enrollment agreement | Reveals org size, structure, and third party service relationships |
| `site:fullstackacademy.com "syllabus"` | Course syllabi, bootcamp offerings, alumni talks with real names | Exposes technology stack and real human targets connected to the org |
| `site:fullstackacademy.com inurl:start` | Privacy policy with physical address, CIRR Outcomes report | Reveals physical location, vendor ecosystem, and graduate outcome data |

## Key Findings

### Dork 1 — Institutional Documents (filetype:pdf)
- Publicly indexed PDFs included an institutional disclosure,
  course catalog, and enrollment agreement
- Institutional disclosure revealed student enrollment statistics
  and program demographics — no personally identifiable
  information found
- Course catalog exposes the full scope of programs offered and
  technologies taught
- Enrollment agreement reveals third party service relationships,
  legal structure, and data handling practices
- Together these documents profile the organization's size,
  business model, and operational structure

### Dork 2 — Course Syllabi & Alumni ("syllabus")
- Multiple course syllabi publicly accessible via Google
- Specific technologies identified: **Python, Linux, Metasploit**
- Knowing the exact tools taught enables highly targeted phishing
  attacks — an attacker could craft emails referencing these
  specific tools to appear legitimate to students and staff
- Alumni talks revealed **real names** of former students along
  with their career outcomes
- Real names can be cross-referenced with LinkedIn to build
  detailed profiles of people connected to the organization —
  prime targets for spear phishing or social engineering

### Dork 3 — Privacy Policy & CIRR Report (inurl:start)
- Privacy policy revealed a **physical mailing address** — no
  individual staff names found
- Physical address enables physical reconnaissance, tailgating
  attacks, or in-person social engineering
- Address can be cross-referenced with other OSINT sources such
  as business registration records or Google Street View
- **CIRR Outcomes Report** revealed:
  - Median annual salary of graduates
  - Most frequent job titles obtained after graduation
  - General employment outcomes (full-time, part-time,
    still seeking employment)
  - Graduation rates and cohort data
- Employment outcome data helps an attacker understand the
  typical career path and job titles of graduates — useful
  for crafting convincing impersonation or phishing scenarios

## Combined Intelligence Profile

| Intelligence Type | Source | Value to Attacker |
|---|---|---|
| Org size & structure | Institutional disclosure | Profile scale and resources |
| Technical environment | Course syllabi | Craft targeted phishing using known tools |
| Human targets | Alumni talks | Real names for spear phishing |
| Physical location | Privacy policy | Physical recon, tailgating |
| Graduate job titles | CIRR report | Impersonation and phishing scenarios |
| Employment outcomes | CIRR report | Profile graduate population |

## Security Relevance

Six distinct intelligence categories were built entirely from
three Google searches using publicly available documents. The
combination of real alumni names, specific technologies, a
physical address, and graduate outcome data gives an attacker
everything needed to launch a highly targeted spear phishing
campaign — without touching a single system. This demonstrates
why organizations must carefully audit what documents are
publicly indexable.

## Recommended Defensive Actions

- Audit all publicly accessible PDFs and restrict sensitive
  documents behind authentication
- Implement robots.txt rules to prevent indexing of internal
  documents and reports
- Review alumni and event pages — redact or remove full names
  unless individuals have explicitly consented to public listing
- Consider restricting CIRR and outcomes reports to
  authenticated users only to limit exposure of graduate data
