# Phishing Email Analysis and Defensive Measures

This repository documents an in-depth analysis of a phishing email, showcasing methods to investigate and identify malicious artifacts, and implementing defensive measures to mitigate potential threats.

## Table of Contents
- [Overview](#overview)
- [Phishing Email Details](#phishing-email-details)
- [Analysis Steps](#analysis-steps)
  - [Email Header Analysis](#email-header-analysis)
  - [Attachment Hash Verification](#attachment-hash-verification)
  - [URL Investigation](#url-investigation)
- [Defensive Measures](#defensive-measures)
- [Tools Used](#tools-used)
- [Conclusion](#conclusion)
- [Contribution](#contribution)

---

## Overview
This project provides a practical approach to identifying and mitigating phishing attacks. It includes a detailed analysis of phishing email artifacts, extraction of key Indicators of Compromise (IOCs), and steps to defend against similar attacks in the future.

### Objectives
1. Analyze phishing email details and identify malicious artifacts.
2. Extract key IOCs such as URLs, file hashes, and email headers.
3. Suggest and implement defensive measures to protect users and systems.

---

## Phishing Email Details
- **Subject:** Don’t miss your chance to play
- **Sender:** `return@e-narucivanje.com`
- **Malicious URLs:**
  - `https://e-narucivanje.com/r3bfd.php?...`
- **Attachment:** `5704452.pdf` (12.8 KB)
- **Client IP:** `173.209.60.250`

### Screenshots
- Email content:
  ![EMAIL](https://github.com/user-attachments/assets/ea1d576f-e97a-45ed-89e5-7f7f3ffdbbb7)
- File properties:
  ![FILE NAME AND SIZE](https://github.com/user-attachments/assets/3a14bcad-da17-4edb-916d-5564f28f1407)

---

## Analysis Steps

### Email Header Analysis
The email header analysis revealed several suspicious details:
- **Client IP:** `173.209.60.250`
- **Sender:** `return@e-narucivanje.com`
- **Authentication:** Failed DKIM/SPF verification

#### Screenshots
- Header analysis:
  ![EMAIL HEADER](https://github.com/user-attachments/assets/45df4389-3640-4841-96d7-bc7f137ee046)
- HTTP content:
  ![HTTP](https://github.com/user-attachments/assets/b5f0d41f-d5a3-4473-b172-942164c9b20b)

---

### Attachment Hash Verification
The attachment (`5704452.pdf`) was analyzed to generate its cryptographic hashes. The results are as follows:
- **SHA256:** `39166946342DDB09216FDAECCBDA9868E4686B293060AF5A16578999D581BFC0`
- **MD5:** `B81723980BF000CF04BF6BAB00A5548D`
- **SHA1:** `F7423AEE068BB2356543C081467D5B93DE6449DB`

#### Screenshot

  ![SHA 256 MD5 SHA1](https://github.com/user-attachments/assets/0a489ecb-1d5f-439c-bd44-6b5a89d24d29)
- Hash verification:
---

### URL Investigation
The embedded URLs in the email pointed to domains such as `e-narucivanje.com`, which were flagged as malicious. The URLs were part of a credential harvesting scheme disguised as legitimate forms.

#### Screenshot

  ![URL Investigation](https://github.com/user-attachments/assets/575910a5-eaaa-4eb2-a793-7fe7a38dcfe3)
- URL analysis:
---

## Defensive Measures
The following actions were implemented to mitigate this phishing attack:

1. **Email Artifact Blocking**:
   - Blocked subject line: `"Don’t miss your chance to play"`
   - Blocked sender address: `return@e-narucivanje.com`

2. **Web Artifact Blocking**:
   - Blocked domain: `e-narucivanje.com`

3. **Attachment Artifact Blocking**:
   - Blocked file hash: `39166946342DDB09216FDAECCBDA9868E4686B293060AF5A16578999D581BFC0`

---

## Tools Used
- **PowerShell:** To generate cryptographic file hashes.
- **Email Header Analysis Tools:** Manual inspection and online header parsers.
- **URL Analysis Tools:** DomainTools, WHOIS lookup, and online scanners.

---

## Conclusion
This project demonstrates a step-by-step analysis of a phishing email, including artifact extraction and defensive measures. It serves as a practical guide for cybersecurity professionals and enthusiasts seeking to strengthen their skills in phishing analysis and mitigation.

---

## Contribution
Contributions are welcome! If you have additional techniques, tools, or improvements to enhance this repository, feel free to submit a pull request.

---

This repository aims to educate others on the importance of analyzing suspicious emails and proactively defending against cyber threats.
