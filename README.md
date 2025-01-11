# Phishing Email Analysis and Defensive Measures

The analysis of a phishing email, highlighting methods used to investigate and identify malicious intent.

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

- ![EMAIL](https://github.com/user-attachments/assets/ea1d576f-e97a-45ed-89e5-7f7f3ffdbbb7)
![FILE NAME AND SIZE](https://github.com/user-attachments/assets/3a14bcad-da17-4edb-916d-5564f28f1407)

---

## Analysis Steps

### Email Header Analysis
The email header revealed the following suspicious details:
- **Client IP:** `173.209.60.250`
- **Sender:** `return@e-narucivanje.com`
- **Authentication:** Failed DKIM/SPF verification

- ![EMAIL HEADER](https://github.com/user-attachments/assets/45df4389-3640-4841-96d7-bc7f137ee046)

![HTTP](https://github.com/user-attachments/assets/b5f0d41f-d5a3-4473-b172-942164c9b20b)


### Attachment Hash Verification
Using PowerShell, the following hashes were generated for the attachment:
- **SHA256:** `39166946342DDB09216FDAECCBDA9868E4686B293060AF5A16578999D581BFC0`
- **MD5:** `B81723980BF000CF04BF6BAB00A5548D`
- **SHA1:** `F7423AEE068BB2356543C081467D5B93DE6449DB`

![SHA 256 MD5 SHA1](https://github.com/user-attachments/assets/0a489ecb-1d5f-439c-bd44-6b5a89d24d29)

### URL Investigation
The URLs embedded in the email pointed to domains like `e-narucivanje.com`, which were flagged as malicious. They led to credential harvesting attempts disguised as legitimate forms.
![image](https://github.com/user-attachments/assets/575910a5-eaaa-4eb2-a793-7fe7a38dcfe3)

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
