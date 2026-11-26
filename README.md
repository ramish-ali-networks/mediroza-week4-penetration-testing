
# 🔐 Mediroza General Hospital – Week 4 Penetration Testing Assessment

A detailed cybersecurity assessment documenting reconnaissance, DNS enumeration, network scanning, web technology fingerprinting, HTTP header analysis, WAF identification, and PDF security testing.

---

## 📌 Project Information

| Field | Details |
|---|---|
| Project | Mediroza General Hospital Security Assessment |
| Target | https://medirozahospital.com |
| Student | RAMISH ALI |
| Internship | NETWORKWALKS Cybersecurity Internship |
| Batch | B084C |
| Week | Week 4 |
| Date | 26 November 2026 |
| Assessment Type | Black-box Assessment |
| Environment | Simulated Training Target |
| Operating System | Kali Linux |
| Report Status | Findings and Observations |

---

# 1. Executive Summary

This repository documents the practical activities performed during Week 4 of the NETWORKWALKS Cybersecurity and Ethical Hacking Internship.

The assessment focused on examining the externally observable security posture of the Mediroza General Hospital demonstration website.

The primary objective was to understand how reconnaissance, network enumeration, service discovery, web technology fingerprinting, HTTP response analysis, and document security testing contribute to a structured penetration testing process.

Several commonly used cybersecurity tools were used to collect technical information and document the observed behavior of the target environment.

The assessment included:

- DNS lookup and domain reconnaissance.
- Identification of the target IP address.
- TCP port scanning using Nmap.
- HTTP response and server header analysis.
- Web technology fingerprinting.
- Web Application Firewall identification.
- PDF security concepts and hash analysis documentation.
- Evidence collection and technical reporting.

This repository is intended for educational documentation and demonstrates practical cybersecurity learning.

**Important:** Observed services and technology information are not automatically vulnerabilities. Each security finding requires sufficient evidence and validation.

---

# 2. Project Objectives

The main objectives of this assessment were:

1. Understand the reconnaissance phase of penetration testing.
2. Identify domain and DNS infrastructure information.
3. Discover externally accessible TCP services.
4. Analyze HTTP response headers.
5. Identify web server technologies.
6. Understand WAF and bot-protection behavior.
7. Explore PDF hashing and document security concepts.
8. Organize technical evidence professionally.
9. Understand security risks and defensive recommendations.
10. Improve practical reporting and documentation skills.

---

# 3. Scope and Assessment Rules

## Target

https://medirozahospital.com

## Assessment Scope

The assessment focused on externally observable information and the provided simulated training environment.

### Included Activities

- DNS reconnaissance.
- Network service discovery.
- HTTP header analysis.
- Web technology identification.
- WAF detection.
- Documentation of PDF security testing.

### Exclusions

- Unauthorized access to real patient records.
- Modification or deletion of target data.
- Disruption of production services.
- Access to confidential third-party information.
- Exploitation without explicit authorization.

No remediation changes were applied as part of this documentation exercise.

---

# 4. Methodology

The assessment followed a structured penetration testing workflow.

## M1 – Initial Access and Reconnaissance

Activities:

- Domain information lookup.
- DNS enumeration.
- IP address identification.
- HTTP response inspection.
- Network scanning.
- Web technology fingerprinting.
- WAF identification.

Tools:

- WHOIS
- nslookup
- Nmap
- cURL
- WhatWeb
- WAFW00F

## M2 – Document Security Analysis

Activities:

- Understanding PDF document protection.
- PDF hash extraction concepts.
- SHA-256 hash calculation.
- Document metadata inspection.
- Password security analysis using authorized sample files.

Tools:

- Python
- hashlib
- PDF metadata utilities

Only authorized training documents should be used for document security testing.

## M3 – Findings and Security Documentation

Activities:

- Reviewing collected evidence.
- Documenting observed network services.
- Recording server technology information.
- Identifying configuration questions requiring further validation.
- Preparing defensive recommendations.

---

# 5. Tools and Technologies

| Tool | Purpose |
|---|---|
| Kali Linux | Security testing environment |
| WHOIS | Domain registration lookup |
| nslookup | DNS lookup |
| Nmap | Network and port scanning |
| cURL | HTTP header inspection |
| WhatWeb | Web technology fingerprinting |
| WAFW00F | WAF identification |
| Python | Security scripting |
| SHA-256 | File integrity hashing |

---

# 6. Practical Testing and Commands

## 6.1 DNS Enumeration – nslookup

### Objective

Identify the IP address associated with the target hostname.

### Command

```bash
nslookup www.medirozahospital.com
```

### Observed Result

- DNS resolver: 192.168.0.1
- Resolved IP address: 199.188.201.16

### Security Relevance

DNS information helps security analysts understand how a domain resolves to its hosting infrastructure.

DNS reconnaissance is an important first step in an external security assessment.

---

## 6.2 WHOIS Lookup

### Objective

Understand domain registration information.

### Command

```bash
whois www.medirozahospital.com
```

### Observation

The WHOIS query for the supplied www hostname returned a no-match response.

This does not establish the registration information for the root domain.

### Security Relevance

WHOIS can provide information about domain registration, registrar details, and name servers when valid registration records are available.

---

## 6.3 HTTP Header Analysis – cURL

### Objective

Inspect the HTTP response returned by the web server.

### Command

```bash
curl -I -A "Mozilla/5.0" https://www.medirozahospital.com
```

### Observed Results

- HTTP response: 200 OK
- Protocol: HTTP/2
- Server: LiteSpeed
- Content-Type: text/html
- Content-Length: 5445
- Last-Modified: 04 September 2026
- X-Turbo-Charged-By: LiteSpeed

### Security Relevance

HTTP response headers provide useful information about web server behavior and technology configuration.

Security analysts should review whether appropriate security headers are configured.

---

## 6.4 Network Scanning – Nmap

### Objective

Identify open TCP ports and externally visible services.

### Command

```bash
nmap 199.188.201.16
```

### Observed Open Ports

| Port | Service |
|---|---|
| 21 | FTP |
| 25 | SMTP |
| 53 | DNS |
| 80 | HTTP |
| 110 | POP3 |
| 143 | IMAP |
| 443 | HTTPS |
| 587 | SMTP Submission |
| 993 | IMAPS |
| 995 | POP3S |

Additional observation:

- Host status: Up
- Reverse DNS: server274-1.web-hosting.com
- Port 990: Filtered

### Security Relevance

Open ports identify services that may require additional security review.

The presence of an open port does not automatically indicate a vulnerability.

Further authorized assessment is required to evaluate service configuration, authentication, encryption, and patch status.

---

## 6.5 Web Technology Fingerprinting – WhatWeb

### Objective

Identify publicly observable website technologies.

### Command

```bash
whatweb https://www.medirozahospital.com
```

### Observed Results

- HTTP response: 403 Forbidden
- HTML5 detected
- LiteSpeed identified
- Reported IP: 199.188.201.161

### Important Observation

The WhatWeb result reported IP address 199.188.201.161, while DNS lookup and Nmap reported 199.188.201.16.

This discrepancy should be independently validated before drawing conclusions.

### Security Relevance

Technology fingerprinting helps analysts understand the externally visible technology stack.

---

## 6.6 WAF Detection – WAFW00F

### Objective

Identify possible Web Application Firewall protection.

### Command

```bash
wafw00f https://www.medirozahospital.com
```

### Observed Result

- WAF identification: LiteSpeed WAF
- Detection completed after two requests.

### Security Relevance

WAF technology can help protect web applications by filtering suspicious requests.

However, identifying a WAF does not prove that every application vulnerability is prevented.

---

# 7. PDF Security and Hash Analysis

Document security was included as a learning area in the practical assessment.

## 7.1 Understanding File Hashes

A cryptographic hash is a fixed-length value generated from file contents.

SHA-256 is commonly used to verify file integrity.

### Python Example

```python
import hashlib

file_path = "sample.pdf"

sha256 = hashlib.sha256()

with open(file_path, "rb") as file:
    for chunk in iter(lambda: file.read(4096), b""):
        sha256.update(chunk)

print("SHA-256:", sha256.hexdigest())
```

### Purpose

- Generate a file fingerprint.
- Verify file integrity.
- Compare document versions.
- Support evidence documentation.

## 7.2 PDF Security Considerations

Password-protected PDF files may contain sensitive information.

Security assessments should evaluate:

- Password strength.
- Encryption configuration.
- Access control.
- Document distribution practices.
- Secure storage and handling.

Only authorized sample documents should be used for password-strength testing.

No real patient information, passwords, or confidential document contents should be published in this repository.

---

# 8. Assessment Observations

The following table summarizes the results directly supported by the collected screenshots.

| No. | Assessment Area | Observation |
|---|---|---|
| 1 | DNS Lookup | IP 199.188.201.16 identified |
| 2 | WHOIS | No-match response for www hostname |
| 3 | HTTP Analysis | HTTP/2 200 response |
| 4 | Web Server | LiteSpeed identified |
| 5 | Network Scanning | 10 open TCP ports observed |
| 6 | Web Fingerprinting | 403 response and LiteSpeed detected |
| 7 | WAF Detection | LiteSpeed WAF identified |
| 8 | IP Consistency | Different IP reported by WhatWeb |

These are technical observations, not a declaration that all listed services are vulnerable.

---

# 9. Security Recommendations

Based on the assessment observations, the following defensive measures are recommended for further review:

### Network Security

- Review all externally accessible services.
- Disable unnecessary services.
- Restrict administrative access.
- Apply appropriate firewall rules.
- Keep exposed services updated.

### Web Server Security

- Review HTTP security header configuration.
- Minimize unnecessary server information disclosure.
- Maintain current server software.
- Review WAF configuration and monitoring.

### DNS Security

- Regularly review DNS records.
- Remove obsolete records.
- Monitor unexpected DNS changes.
- Maintain secure domain administration.

### Document Security

- Store sensitive documents outside public web directories.
- Use strong encryption and passwords.
- Apply role-based access controls.
- Avoid publishing confidential documents.
- Maintain secure backup procedures.

---

# 10. Evidence and Screenshots

Screenshots are maintained as supporting evidence for the practical activities.

Suggested evidence structure:

```text
evidence/
├── screenshots/
│   ├── nslookup.png
│   ├── whois.png
│   ├── curl_headers.png
│   ├── nmap_scan.png
│   ├── whatweb.png
│   └── wafw00f.png
│
└── reports/
    └── penetration_testing_report.pdf
```

Each screenshot should clearly demonstrate:

- The tool used.
- The command executed.
- The relevant output.
- The assessment activity.

Sensitive information must be redacted before public sharing.

---

# 11. Limitations

This repository documents the activities and observations supported by the available assessment evidence.

The following limitations apply:

- Some observations require additional validation.
- The WhatWeb and DNS/Nmap IP results differ.
- The WHOIS query was performed against the www hostname.
- Open ports alone do not prove vulnerabilities.
- WAF detection does not establish complete application security.
- Additional PDF testing results should only be documented when supported by the tester's own evidence.

No unsupported vulnerability claims are presented as confirmed findings.

---

# 12. Conclusion

The Week 4 practical assessment provided valuable experience in understanding the external security posture of a web-hosted environment.

Through DNS enumeration, network scanning, HTTP header analysis, technology fingerprinting, and WAF identification, the assessment demonstrated how different tools contribute to the reconnaissance and analysis stages of penetration testing.

One important lesson was the need to validate technical observations before classifying them as security vulnerabilities.

Professional cybersecurity work requires more than running tools. It requires evidence collection, accurate interpretation, risk assessment, clear documentation, and practical defensive recommendations.

This project strengthened my understanding of network security, web infrastructure, document protection, and professional penetration testing methodology.

---

# 13. Internship Reflection

Week 4 of the NETWORKWALKS Cybersecurity Internship was an important learning experience.

Working through the assessment helped me understand how reconnaissance and enumeration provide a foundation for deeper security analysis.

I gained practical experience using Nmap, cURL, WhatWeb, WAFW00F, nslookup, and WHOIS.

I also learned the importance of checking evidence carefully, identifying inconsistencies, and distinguishing between an observed configuration and a confirmed vulnerability.

The experience improved my technical documentation and reporting skills and helped me develop a more structured approach to cybersecurity assessments.

A special thanks to **Mr. Waqas Karim (CCIE)** and **NETWORKWALKS** for providing this valuable learning opportunity and supporting my cybersecurity journey.

---

# 14. Disclaimer

This repository is intended strictly for educational and authorized cybersecurity training purposes.

All activities should be performed only against systems for which explicit permission has been granted.

Do not use this documentation to access, download, modify, or disclose private patient records or confidential information.

No real patient information, private credentials, or confidential database contents should be included in this public repository.

---

# 15. Author

**RAMISH ALI**

NETWORKWALKS Cybersecurity Internship  
Batch: B084C  
Week 4 – Penetration Testing Assessment

---

## Topics

`cybersecurity` `penetration-testing` `ethical-hacking` `kali-linux` `nmap` `network-security` `web-security` `pdf-security` `reconnaissance` `networkwalks`
