# **Phishing Email Analysis and Defensive Measures**  
**Platform:** Manual Analysis and Threat Investigation  
**Focus:** Phishing Email Investigation and Defensive Response  

---

## **1. Objective**
This report provides a detailed analysis of a phishing email investigation. The goal was to identify malicious artifacts, understand attacker tactics, and implement defensive measures to prevent similar threats. The findings showcase the process of analyzing email headers, verifying attachments, investigating URLs, and applying mitigation strategies.

---

## **2. Overview**
This project presents a structured approach to phishing analysis that combines forensic techniques and practical defensive applications. Each phase includes evidence screenshots, analysis steps, and actionable conclusions for cybersecurity professionals and SOC teams.

### **Objectives**
1. Analyze phishing email details and confirm malicious intent.  
2. Extract Indicators of Compromise (IOCs) including URLs, hashes, and IP addresses.  
3. Propose defensive measures and detection improvements.

---

## **3. Phishing Email Details**
- **Subject:** Don’t miss your chance to play  
- **Sender:** `return@e-narucivanje.com`  
- **Malicious URL:**  
  - `https://e-narucivanje.com/r3bfd.php?...`  
- **Attachment:** `5704452.pdf` (12.8 KB)  
- **Client IP:** `173.209.60.250`

### **Screenshots**
**Email Content:**  
![EMAIL](https://github.com/user-attachments/assets/ea1d576f-e97a-45ed-89e5-7f7f3ffdbbb7)  

**File Properties:**  
![FILE NAME AND SIZE](https://github.com/user-attachments/assets/3a14bcad-da17-4edb-916d-5564f28f1407)

---

## **4. Analysis Steps**

### **4.1 Email Header Analysis**
The email header review exposed multiple red flags that suggested spoofing and malicious intent.

**Key Observations**
- **Client IP:** `173.209.60.250`  
- **Sender:** `return@e-narucivanje.com`  
- **Authentication Results:** DKIM and SPF both failed verification  
- **Routing Path:** Relayed through a suspicious external mail host not aligned with sender domain

**Screenshots**  
Header Analysis:  
![EMAIL HEADER](https://github.com/user-attachments/assets/45df4389-3640-4841-96d7-bc7f137ee046)  

HTTP Content Capture:  
![HTTP](https://github.com/user-attachments/assets/b5f0d41f-d5a3-4473-b172-942164c9b20b)

**Interpretation**  
The message likely originated from an unauthorized host impersonating a legitimate sender domain. The failed authentication checks confirm that this was not a trusted communication.

---

### **4.2 Attachment Hash Verification**
The attachment `5704452.pdf` was analyzed for hash signatures to verify if it had been previously flagged in malware repositories.

**Results**
- **SHA256:** `39166946342DDB09216FDAECCBDA9868E4686B293060AF5A16578999D581BFC0`  
- **MD5:** `B81723980BF000CF04BF6BAB00A5548D`  
- **SHA1:** `F7423AEE068BB2356543C081467D5B93DE6449DB`

**Screenshot**  
![SHA 256 MD5 SHA1](https://github.com/user-attachments/assets/0a489ecb-1d5f-439c-bd44-6b5a89d24d29)

**Interpretation**  
The cryptographic signatures matched known phishing-related PDFs associated with credential harvesting lures. The attachment was flagged as suspicious across multiple threat intelligence sources.

---

### **4.3 URL Investigation**
The embedded URLs within the email redirected to domains associated with phishing kits that impersonated legitimate login portals.  

**Findings**
- The domain `e-narucivanje.com` was linked to prior phishing activity.  
- The URL path `/r3bfd.php` contained randomized query parameters typical of phishing form submissions.  
- The site attempted to collect user credentials via an HTML form disguised as a lottery entry page.

**Screenshot**  
![URL Investigation](https://github.com/user-attachments/assets/575910a5-eaaa-4eb2-a793-7fe7a38dcfe3)

**Interpretation**  
The analysis confirmed this was a credential harvesting domain. The server IP matched other domains used in similar phishing operations, suggesting part of a larger campaign.

---

## **5. Defensive Measures**
Based on the investigation results, the following mitigation steps were implemented to reduce exposure and prevent recurrence.

### **5.1 Email-Based Mitigations**
- Blocked the subject line **"Don’t miss your chance to play"** in the email security gateway.  
- Blacklisted sender address `return@e-narucivanje.com`.  
- Quarantined similar messages detected by the same sender IP.

### **5.2 Web and Network Mitigations**
- Blocked domain `e-narucivanje.com` and all associated subdomains at the proxy and firewall level.  
- Monitored outbound connections for similar patterns of PHP redirects.  

### **5.3 File-Based Mitigations**
- Blocked the identified PDF file hashes across email filters and EDR systems.  
- Added SHA256 signature to threat intelligence feeds for correlation.  

---

## **6. Tools Used**
- **PowerShell:** Generated cryptographic file hashes.  
- **Email Header Analysis Tools:** Manual inspection, MXToolbox, and online header parsers.  
- **URL and Domain Tools:** WHOIS, VirusTotal, DomainTools, and hybrid analysis sandboxes.  

---

## **7. Conclusion**
This analysis demonstrates a complete phishing investigation workflow. From email header validation to hash verification and domain analysis, each stage revealed critical indicators that supported attribution and defense. The findings reinforced the importance of multi-layered protection, including domain filtering, attachment control, and user awareness.

The repository serves as a practical guide for analysts to practice hands-on phishing analysis, IOC extraction, and defensive application using real-world techniques.

---

