---
title: "Siemens SiPass integrated AC5102ACC-G2 and ACC-AP"
date: Thu, 13 Mar 25 12:00:00 +0000
draft: false
type: posts
categories: 
- 
---
# Siemens SiPass integrated AC5102ACC-G2 and ACC-AP

<br/>

<br/>
As of January 10, 2023, CISA will no longer be updating ICS security advisories for Siemens product vulnerabilities beyond the initial advisory. For the most up-to-date information on vulnerabilities in this advisory, see [Siemens' ProductCERT Security Advisories (CERT Services | Services | Siemens Global).](https://new.siemens.com/global/en/products/services/cert.html#SecurityPublications "(opens in a new window)")

[**View CSAF**](https://github.com/cisagov/CSAF)

1\. EXECUTIVE SUMMARY
---------------------

-   **CVSS v4 9.4**
-   **ATTENTION**: Exploitable remotely/low attack complexity
-   **Vendor**: Siemens
-   **Equipment**: SiPass integrated AC5102 (ACC-G2), SiPass integrated ACC-AP
-   **Vulnerabilities**: Missing Authentication for Critical Function, Improper Input Validation

2\. RISK EVALUATION
-------------------

Successful exploitation of these vulnerabilities could allow an attacker to execute commands on the device with root privileges and access sensitive data.

3\. TECHNICAL DETAILS
---------------------

### 3.1 AFFECTED PRODUCTS

Siemens reports that the following products are affected:

-   Siemens SiPass integrated AC5102 (ACC-G2): All versions prior to V6.4.8 (CVE-2024-52285)
-   Siemens SiPass integrated AC5102 (ACC-G2): All versions prior to V6.4.9 (CVE-2025-27493, CVE-2025-27494)
-   Siemens SiPass integrated ACC-AP: All versions prior to V6.4.8 (CVE-2024-52285)
-   Siemens SiPass integrated ACC-AP: All versions prior to V6.4.9 (CVE-2025-27493, CVE-2025-27494)

### 3.2 VUNERABILITY OVERVIEW

#### **3.2.1** [**MISSING AUTHENTICATION FOR CRITICAL FUNCTION CWE-306**](https://cwe.mitre.org/data/definitions/306.html)

Affected devices expose several MQTT URLs without authentication. This could allow an unauthenticated remote attacker to access sensitive data.

[CVE-2024-52285](https://www.cve.org/CVERecord?id=CVE-2024-52285) has been assigned to this vulnerability. A CVSS v3 base score of 5.3 has been calculated; the CVSS vector string is ([CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:L/I:N/A:N](https://www.first.org/cvss/calculator/3.1#CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:L/I:N/A:N)).

A CVSS v4 score has also been calculated for [CVE-2024-52285](https://www.cve.org/CVERecord?id=CVE-2024-52285). A base score of 6.9 has been calculated; the CVSS vector string is ([CVSS:4.0/AV:N/AC:L/AT:N/PR:N/UI:N/VC:L/VI:N/VA:N/SC:N/SI:N/SA:N](https://www.first.org/cvss/calculator/4.0#CVSS:4.0/AV:N/AC:L/AT:N/PR:N/UI:N/VC:L/VI:N/VA:N/SC:N/SI:N/SA:N)).

#### **3.2.2** [**IMPROPER INPUT VALIDATION CWE-20**](https://cwe.mitre.org/data/definitions/20.html)

Affected devices improperly sanitize user input for specific commands on the telnet command line interface. This could allow an authenticated local administrator to escalate privileges by injecting arbitrary commands that are executed with root privileges.

[CVE-2025-27493](https://www.cve.org/CVERecord?id=CVE-2025-27493) has been assigned to this vulnerability. A CVSS v3 base score of 8.2 has been calculated; the CVSS vector string is ([CVSS:3.1/AV:L/AC:L/PR:H/UI:N/S:C/C:H/I:H/A:H](https://www.first.org/cvss/calculator/3.1#CVSS:3.1/AV:L/AC:L/PR:H/UI:N/S:C/C:H/I:H/A:H)).

A CVSS v4 score has also been calculated for [CVE-2025-27493](https://www.cve.org/CVERecord?id=CVE-2025-27493). A base score of 9.3 has been calculated; the CVSS vector string is ([CVSS:4.0/AV:L/AC:L/AT:N/PR:H/UI:N/VC:H/VI:H/VA:H/SC:H/SI:H/SA:H](https://www.first.org/cvss/calculator/4.0#CVSS:4.0/AV:L/AC:L/AT:N/PR:H/UI:N/VC:H/VI:H/VA:H/SC:H/SI:H/SA:H)).

#### **3.2.3** [**IMPROPER INPUT VALIDATION CWE-20**](https://cwe.mitre.org/data/definitions/20.html)

Affected devices improperly sanitize input for the pubkey endpoint of the REST API. This could allow an authenticated remote administrator to escalate privileges by injecting arbitrary commands that are executed with root privileges.

[CVE-2025-27494](https://www.cve.org/CVERecord?id=CVE-2025-27494) has been assigned to this vulnerability. A CVSS v3 base score of 9.1 has been calculated; the CVSS vector string is ([CVSS:3.1/AV:N/AC:L/PR:H/UI:N/S:C/C:H/I:H/A:H](https://www.first.org/cvss/calculator/3.1#CVSS:3.1/AV:N/AC:L/PR:H/UI:N/S:C/C:H/I:H/A:H)).

A CVSS v4 score has also been calculated for [CVE-2025-27494](https://www.cve.org/CVERecord?id=CVE-2025-27494). A base score of 9.4 has been calculated; the CVSS vector string is ([CVSS:4.0/AV:N/AC:L/AT:N/PR:H/UI:N/VC:H/VI:H/VA:H/SC:H/SI:H/SA:H](https://www.first.org/cvss/calculator/4.0#CVSS:4.0/AV:N/AC:L/AT:N/PR:H/UI:N/VC:H/VI:H/VA:H/SC:H/SI:H/SA:H)).

### 3.3 BACKGROUND

-   **CRITICAL INFRASTRUCTURE SECTORS:** Critical Manufacturing
-   **COUNTRIES/AREAS DEPLOYED:** Worldwide
-   **COMPANY HEADQUARTERS LOCATION:** Germany

### 3.4 RESEARCHER

Airbus Security reported these vulnerabilities to Siemens.

4\. MITIGATIONS
---------------

Siemens has identified the following specific workarounds and mitigations users can apply to reduce risk:

-   SiPass integrated AC5102 (ACC-G2), SiPass integrated ACC-AP: Update to V6.4.8 or later version (CVE-2024-52285)
-   SiPass integrated AC5102 (ACC-G2), SiPass integrated ACC-AP: Set an individual strong password for the administrator account "SIEMENS" (CVE-2025-27493, CVE-2025-27494)
-   SiPass integrated AC5102 (ACC-G2), SiPass integrated ACC-AP: Update to V6.4.9 or later version (CVE-2025-27493, CVE-2025-27494)

As a general security measure, Siemens recommends protecting network access to devices with appropriate mechanisms. To operate the devices in a protected IT environment, Siemens recommends configuring the environment according to [Siemens' operational guidelines for industrial security](https://www.siemens.com/cert/operational-guidelines-industrial-security) and following recommendations in the product manuals.

Additional information on industrial security by Siemens can be found on the [Siemens industrial security webpage](https://www.siemens.com/industrialsecurity)

For more information see the associated Siemens security advisory SSA-515903 in [HTML](https://cert-portal.siemens.com/productcert/html/ssa-515903.html) and [CSAF](https://cert-portal.siemens.com/productcert/csaf/ssa-515903.json).

CISA recommends users take defensive measures to minimize the risk of exploitation of these vulnerabilities, such as:

-   Minimize network exposure for all control system devices and/or systems, ensuring they are [not accessible from the internet](https://www.cisa.gov/uscert/ics/alerts/ICS-ALERT-10-301-01).
-   Locate control system networks and remote devices behind firewalls and isolating them from business networks.
-   When remote access is required, use more secure methods, such as Virtual Private Networks (VPNs). Recognize VPNs may have vulnerabilities, should be updated to the most recent version available, and are only as secure as the connected devices.

CISA reminds organizations to perform proper impact analysis and risk assessment prior to deploying defensive measures.

CISA also provides a section for [control systems security recommended practices](https://www.cisa.gov/resources-tools/resources/ics-recommended-practices) on the ICS webpage on [cisa.gov](https://www.cisa.gov/topics/industrial-control-systems). Several CISA products detailing cyber defense best practices are available for reading and download, including [Improving Industrial Control Systems Cybersecurity with Defense-in-Depth Strategies](https://us-cert.cisa.gov/sites/default/files/recommended_practices/NCCIC_ICS-CERT_Defense_in_Depth_2016_S508C.pdf).

CISA encourages organizations to implement recommended cybersecurity strategies for [proactive defense of ICS assets](https://www.cisa.gov/sites/default/files/publications/Cybersecurity_Best_Practices_for_Industrial_Control_Systems.pdf).

Additional mitigation guidance and recommended practices are publicly available on the ICS webpage at [cisa.gov](https://www.cisa.gov/topics/industrial-control-systems) in the technical information paper, [ICS-TIP-12-146-01B--Targeted Cyber Intrusion Detection and Mitigation Strategies](https://www.cisa.gov/uscert/ics/tips/ICS-TIP-12-146-01B).

Organizations observing suspected malicious activity should follow established internal procedures and report findings to CISA for tracking and correlation against other incidents.

CISA also recommends users take the following measures to protect themselves from social engineering attacks:

-   Do not click web links or open attachments in unsolicited email messages.
-   Refer to [Recognizing and Avoiding Email Scams](https://www.cisa.gov/uscert/sites/default/files/publications/emailscams0905.pdf) for more information on avoiding email scams.
-   Refer to [Avoiding Social Engineering and Phishing Attacks](https://www.cisa.gov/uscert/ncas/tips/ST04-014) for more information on social engineering attacks.

No known public exploitation specifically targeting these vulnerabilities has been reported to CISA at this time.

5\. UPDATE HISTORY
------------------

-   March 13, 2025: Initial Publication

#### [Source](https://www.cisa.gov/news-events/ics-advisories/icsa-25-072-04)

<br/>
---
