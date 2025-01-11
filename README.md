# Phishing Email Analysis and Defensive Measures

This repository documents an analysis of a phishing email, highlighting methods used to investigate and identify malicious intent.

## Table of Contents
- [Overview](#overview)
- [Phishing Email Details](#phishing-email-details)
- [Analysis Steps](#analysis-steps)
  - [Email Header Analysis](#email-header-analysis)
  - [Attachment Hash Verification](#attachment-hash-verification)
  - [URL Investigation](#url-investigation)
- [Defensive Measures](#defensive-measures)
- [Tools Used](#tools-used)

---

## Overview
This project showcases a practical approach to identifying and mitigating a phishing attack using tools like PowerShell, email header analysis, and hash verification.

### Objectives
1. Analyze phishing email details.
2. Extract key indicators of compromise (IOCs).
3. Suggest defensive measures to protect users and systems.

---

## Phishing Email Details
- **Subject:** [Include Subject Line]
- **Sender:** [Include Sender]
- **Malicious URLs:**
  - `https://e-narucivanje.com/r3bfd.php?...`
- **Attachment:** `5704452.pdf` (12.8 KB)
- **Client IP:** `173.209.60.250`

---

## Analysis Steps

### Email Header Analysis
The email header revealed the following suspicious details:
- **Client IP:** `173.209.60.250`
- **Sender:** `return@e-narucivanje.com`
- **Authentication:** Failed DKIM/SPF verification

![Email Header Screenshot](./path-to-image/2025-01-11-14_39_50-email-header.png)

### Attachment Hash Verification
Using PowerShell, the following hashes were generated for the attachment:
- **SHA256:** `39166946342DDB09216FDAECCBDA9868E4686B293060AF5A16578999D581BFC0`
- **MD5:** `B81723980BF000CF04BF6BAB00A5548D`
- **SHA1:** `F7423AEE068BB2356543C081467D5B93DE6449DB`

![Hash Screenshot](./path-to-image/SHA-256-MD5-SHA1.png)

### URL Investigation
The URLs embedded in the email pointed to domains like `e-narucivanje.com`, which were flagged as malicious. They led to credential harvesting attempts disguised as legitimate forms.

---

## Defensive Measures
The following actions were taken to mitigate this phishing attack:
1. **Email Artifact Blocking**:
   - Subject line block: `"Don’t miss your chance to play."`
   - Sender address block: `return@e-narucivanje.com`
2. **Web Artifact Blocking**:
   - Domain block: `e-narucivanje.com`
3. **Attachment Artifact Blocking**:
   - File hash block: `39166946342DDB09216FDAECCBDA9868E4686B293060AF5A16578999D581BFC0`

---

## Tools Used
- **PowerShell:** For generating file hashes.
- **Email Header Analysis Tools:** Manual inspection and header parsers.
- **URL Analysis:** Online tools and manual investigation.

---

## Conclusion
This analysis demonstrates a step-by-step breakdown of how phishing emails are dissected, indicators of compromise are identified, and defensive measures are implemented. This repository serves as a practical guide for cybersecurity professionals and enthusiasts.

---

## Contribution
Feel free to contribute by suggesting additional techniques or tools to enhance this workflow.
