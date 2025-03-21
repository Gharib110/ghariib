---
title: "Weekly Cybersecurity Update: Recent Cyber Attacks, Vulnerabilities, and Data Breaches"
date: 2025-02-03
---

Welcome to this week’s Cybersecurity Newsletter, which presents the latest updates and key insights from the continuously evolving domain of cybersecurity.

In the fast-paced digital environment of today, it is imperative to remain informed, and our objective is to provide you with the most relevant information to navigate these challenges effectively.

This edition emphasizes emerging threats and the transforming dynamics of digital defenses. Topics of critical importance include advanced ransomware attacks and the increasing influence of state-sponsored cyber activities on global security.

Our analysis offers a comprehensive examination of the changing nature of these threats, in conjunction with actionable strategies to fortify your organization’s defenses. We will assess how state-of-the-art technologies, such as artificial intelligence (AI), machine learning (ML), and quantum computing, are redefining cybersecuritynot only as tools for protection but also as potential mechanisms for exploitation by adversaries.

Specific examples include AI-driven phishing attacks, ML-enhanced malware, and the capability of quantum computing to compromise encrypted systems. Additionally, we shall explore how various industries are responding to pressing cybersecurity challenges, such as securing remote work environments and addressing vulnerabilities in Internet of Things (IoT) devices.

These matters underscore the urgent need for proactive measures in safeguarding digital infrastructure.

Furthermore, we will review recent regulatory developments that are shaping global cybersecurity practices, including frameworks like the European Union’s General Data Protection Regulation (GDPR) and California’s Consumer Privacy Act (CCPA). These regulations are establishing new standards for data privacy and security, ensuring that your compliance strategies are up-to-date.

We invite you to remain engaged each week as we address these complex topics and more, equipping you with the knowledge necessary to remain ahead in the rapidly evolving cybersecurity landscape.

Data Breaches

## Weekly Cybersecurity Newsletter – February 2, 2025

### **1\. UnitedHealth Ransomware Attack Exposes 190 Million Records**

In what is now the largest medical data breach in U.S. history, UnitedHealth Group has disclosed that a February 2024 ransomware attack on its subsidiary, Change Healthcare, compromised the personal and healthcare data of approximately 190 million individuals—nearly double the initial estimate of 100 million. The breach exposed sensitive information such as insurance details and medical records, some of which were leaked online.

The attack caused widespread disruptions across the U.S. healthcare system, delaying claims processing and impacting patient care. Change Healthcare reportedly paid multiple ransoms to prevent further leaks. This incident has intensified scrutiny from regulators and raised concerns about the resilience of cybersecurity in the healthcare sector.

_Read more: UnitedHealth Ransomware Attack_

### **2\. DeepSeek Database Breach Exposes Sensitive AI Data**

A major security lapse at DeepSeek, a leading Chinese AI startup, exposed a publicly accessible ClickHouse database containing over one million log entries. The breach included sensitive information such as chat logs, plaintext API keys, backend service metadata, and operational data. Unauthorized access to this database could have allowed attackers to execute malicious commands or exfiltrate proprietary information.

The vulnerability highlights the growing risks in the AI industry as companies rapidly scale without robust security frameworks. DeepSeek has since secured the database following notification from researchers but has not issued an official statement on the incident.

_Read more: DeepSeek Database Leaked_

### **Vulnerabilities**

#### **1\. Meta’s Llama Framework Vulnerability**

A critical flaw (CVE-2024-50050) in Meta’s Llama Stack framework allows remote attackers to execute arbitrary code via unsafe deserialization of Python objects using the `pickle` module. Meta has released a patch (version 0.0.41) to address this issue. Users are advised to update immediately to mitigate risks.  
_Read more:_ Meta’s Llama Framework Vulnerability

#### **2\. GitHub Credential Vulnerabilities**

Multiple vulnerabilities in Git-related projects, including GitHub Desktop and Git Credential Manager, could lead to credential leaks through improper handling of text-based protocols. Patches have been deployed to address these issues.  
_Read more:_ GitHub Credential Vulnerabilities

#### **3\. GitLab XSS Vulnerability Patched**

GitLab has addressed a high-severity cross-site scripting (XSS) vulnerability (CVE-2025-0314) in file rendering. Users are urged to update to versions 17.8.1, 17.7.3, or 17.6.4 to avoid potential session hijacking and data theft.  
_Read more:_ GitLab XSS Vulnerability

#### **4\. Apache Solr Path Write Vulnerability**

Apache Solr users on Windows are urged to update to version 9.8.0 after a vulnerability (CVE-2024-52012) was found allowing arbitrary path write-access via the “configset upload” API, potentially leading to system compromise.  
_Read more:_ Apache Solr Vulnerability

#### **5\. Chrome Memory Corruption Fixes**

Google Chrome has patched two critical vulnerabilities in its V8 JavaScript engine that could allow remote code execution and memory corruption. Users should update their browsers immediately.  
_Read more:_ Chrome Security Update

#### **6\. Apple Zero-Day Exploited**

Apple has released updates addressing a zero-day vulnerability (CVE-2025-24085) actively exploited against iPhone users. The flaw, a use-after-free issue in Core Media, allows privilege escalation. Update to iOS 18.3 or later immediately.  
_Read more:_ Apple Zero-Day Vulnerability

#### **7\. VMware Avi Load Balancer SQL Injection**

A critical SQL injection vulnerability (CVE-2025-22217) in VMware Avi Load Balancer could allow unauthorized database access. Administrators should apply the latest patches immediately.  
_Read more:_ VMware Avi Load Balancer Vulnerability

#### **8\. DeepSeek R1 Jailbroken for Ransomware**

The AI model DeepSeek R1 has been jailbroken, enabling it to generate ransomware scripts and other malicious content due to inadequate safeguards against harmful queries.  
_Read more:_ DeepSeek R1 Exploit

#### **9\. TeamViewer Privilege Escalation Flaw**

A vulnerability (CVE-2025-0065) in TeamViewer for Windows allows attackers with local access to escalate privileges to the system level. Users must update to version 15.62 or later.  
_Read more:_ TeamViewer Privilege Escalation

#### **10\. OPNsense 25.1 Released**

OPNsense celebrates its 10th anniversary with version 25.1, introducing enhanced security zones, a redesigned UI, and FreeBSD 14.2 integration for improved performance and stability.  
_Read more:_ OPNsense 25.1 Release

### **PoC Releases**

### 1\. **Hidden Windows Admin Account Exploited via RID Hijacking**

The Andariel hacking group, linked to North Korea’s Lazarus Group, has been exploiting the Relative Identifier (RID) hijacking technique to create hidden administrator accounts on Windows systems. This stealthy method manipulates the RID of low-privilege accounts to grant them administrative privileges. Attackers use tools like PsExec and JuicyPotato for SYSTEM-level access and modify the Security Account Manager (SAM) registry to remain undetected.  
**Read more:** Hidden Windows Admin Account Exploiting RID

### 2\. **Windows Charset Conversion Feature Exploited for Remote Code Execution**

Researchers have discovered a critical vulnerability in Windows’ “Best-Fit” character conversion feature, which attackers exploit for remote code execution (RCE). Dubbed “WorstFit,” this flaw allows argument injection, path traversal, and filename smuggling in applications like PHP-CGI and Cuckoo Sandbox. The vulnerability has already been linked to active ransomware campaigns.  
**Read more:** Windows Charset Conversion Feature Exploited

### 3\. **FortiOS Authentication Bypass Vulnerability Actively Exploited**

A critical authentication bypass vulnerability in Fortinet’s FortiOS has been exploited in the wild, allowing attackers to gain unauthorized access to systems. Organizations using affected versions are urged to patch immediately or implement mitigations to prevent exploitation.  
**Read more:** FortiOS Auth Bypass Vulnerability Exploited

### 4\. **PoC Exploit Released for TP-Link Router XSS Vulnerability**

A proof-of-concept (PoC) exploit has been released for a Cross-Site Scripting (XSS) vulnerability in TP-Link Archer A20 v3 routers running firmware version 1.0.6. This flaw allows attackers to inject malicious scripts via the router’s web interface. As the router is no longer supported by TP-Link, users are advised to replace it with a newer model or restrict access using firewall rules.  
**Read more:** PoC Exploit for TP-Link Router Web Interface

### 5\. **PoC Released for Actively Exploited Vulnerabilities**

Security researchers have disclosed proof-of-concept exploits for vulnerabilities currently being exploited in the wild, emphasizing the importance of timely patching and proactive security measures. These vulnerabilities highlight gaps in legacy systems and underscore the need for robust defenses against emerging threats.  
**Read more:** PoC Exploit Released for Actively Exploited Vulnerabilities

### **Threats**

#### **1\. Hackers Take 11 Days to Deploy LockBit Ransomware**

Threat actors demonstrated a methodical approach, taking 11 days from initial compromise to fully deploy LockBit ransomware across a network. The attack involved advanced tools like Cobalt Strike and SystemBC proxies, data exfiltration via Mega.io, and disabling Windows Defender to propagate ransomware.  
**Read More**

#### **2\. Intel TDX Vulnerability Exposes Sensitive Data**

Researchers uncovered a critical flaw in Intel’s Trust Domain Extensions (TDX) technology, enabling attackers to infer sensitive data processed in virtualized environments. Intel is working on mitigations, but the findings highlight gaps in cloud computing security.  
**Read More**

#### **3\. Malware Campaign Leveraging 7-Zip and UltraVNC**

A new malware campaign uses 7-Zip self-extracting archives and UltraVNC remote access tools to target Russian-speaking entities. The campaign, attributed to the GamaCopy group, focuses on espionage and data exfiltration with military-themed lures.  
**Read More**

#### **4\. Akira Ransomware Targets VMware ESXi Servers**

The Akira ransomware group has launched a new Linux variant targeting VMware ESXi servers. This Rust-based ransomware uses advanced encryption techniques and exploits ESXi vulnerabilities for large-scale attacks on virtualized environments.  
**Read More**

#### **5\. Exploiting EDR with Windows Symbolic Links**

Attackers are combining the “Bring Your Own Vulnerable Driver” (BYOVD) technique with Windows symbolic links to disable Endpoint Detection and Response (EDR) services by overwriting critical files, bypassing traditional defenses.  
**Read More**

#### **6\. Fake DeepSeek Campaign Targets macOS Users**

A campaign exploiting the popularity of the DeepSeek AI chatbot is delivering Poseidon malware to macOS users. The malware steals sensitive information like credentials and cryptocurrency wallets while establishing persistence mechanisms.  
**Read More**

#### **7\. SSL Intelligence Uncovers Malicious Infrastructure**

Threat hunters are using historical SSL certificate data to expose hidden threat actor infrastructure and malware activity. This technique has already uncovered operations linked to advanced cyber groups like RedGolf/APT41. 
**Read More**

#### **8\. Google Blocks 2.28 Million Malicious Apps**

In 2023, Google prevented over 2 million malicious apps from entering the Play Store through enhanced machine learning and stricter developer vetting processes, setting new benchmarks for app store security.  
**Read More**

## **Cyber Attack**

#### **1\. DeepSeek Faces Large-Scale Cyber Attack**

DeepSeek, the Chinese AI startup that recently surpassed OpenAI’s ChatGPT as the top-rated free app on Apple’s App Store, has been hit by a significant cyber attack. The incident has forced the company to temporarily halt new user registrations while ensuring continued service for existing users. This attack coincides with DeepSeek’s meteoric rise, attributed to its highly efficient DeepSeek-V3 model. Cybersecurity experts warn that rapid growth often makes companies a prime target for cybercriminals.  
_Read more:_ DeepSeek Cyber Attack

#### **2\. $85 Million Cryptocurrency Theft from Phemex Exchange**

Singapore-based cryptocurrency exchange Phemex suffered a major breach, losing $85 million in digital assets. Hackers targeted the platform’s hot wallets, exploiting vulnerabilities across multiple blockchains, including Ethereum and Bitcoin. Phemex has since upgraded its security measures and resumed limited withdrawal services. Experts speculate that North Korean hacking groups may be involved.  
_Read more:_ Hackers Stolen $85 Million Worth of Cryptocurrency

#### **3\. API Supply Chain Flaw Exposes Millions of Airline Users**

A vulnerability in a third-party travel service API exposed millions of airline users to potential account takeovers. Attackers manipulated OAuth redirects to steal session tokens, enabling unauthorized access to loyalty points and personal data. The flaw has since been patched, but the incident highlights the growing risks in API supply chain integrations.  
_Read more:_ API Supply Chain OAuth Redirects

#### **4\. Vulnerable IIS, Apache, and SQL Servers Exploited in Espionage Campaign**

A cyberespionage campaign targeting South Asian government and telecom networks exploited vulnerabilities in public-facing IIS, Apache Tomcat, and MSSQL servers. The attackers used advanced techniques like PowerShell reverse shells and Cobalt Strike beacons for data exfiltration. Organizations are urged to patch known vulnerabilities and monitor DNS traffic for anomalies.  
_Read more:_ Hackers Exploit Public-Facing Vulnerable IIS, Apache, SQL Servers

#### **5\. Zero-Click Spyware Targets WhatsApp Users**

A zero-click spyware attack attributed to Israeli firm Paragon targeted nearly 100 WhatsApp users globally, including journalists and civil society members. The spyware allowed attackers to access encrypted messages, activate microphones, and steal passwords without user interaction. WhatsApp has disrupted the campaign and notified affected users.  
_Read more:_ Zero-Click Spyware Attack on WhatsApp

The post Weekly Cybersecurity Update: Recent Cyber Attacks, Vulnerabilities, and Data Breaches appeared first on Cyber Security News.

Go to Source
