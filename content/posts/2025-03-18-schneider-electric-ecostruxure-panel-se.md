---
title: "Schneider Electric EcoStruxure Panel Server"
date: Tue, 18 Mar 25 12:00:00 +0000
draft: false
type: posts
categories: 
- 
---
# Schneider Electric EcoStruxure Panel Server

<br/>

<br/>
[**View CSAF**](https://github.com/cisagov/CSAF)

1\. EXECUTIVE SUMMARY
---------------------

-   **CVSS v4 4.0**
-   **ATTENTION**: Low attack complexity
-   **Vendor**: Schneider Electric
-   **Equipment**: EcoStruxure Panel Server
-   **Vulnerability**: Insertion of Sensitive Information into Log File

2\. RISK EVALUATION
-------------------

Successful exploitation of this vulnerability could allow disclosure of sensitive information, including the disclosure of credentials.

3\. TECHNICAL DETAILS
---------------------

### 3.1 AFFECTED PRODUCTS

Schneider Electric reports the following versions of EcoStruxure Panel Server are affected:

-   EcoStruxure Panel Server: Versions v2.0 and prior

### 3.2 VULNERABILITY OVERVIEW

#### **3.2.1** [**Insertion of Sensitive Information into Log File CWE-532**](https://cwe.mitre.org/data/definitions/532.html)

There is an insertion of sensitive information into log files vulnerability that could cause the disclosure of FTP server credentials when the FTP server is deployed, and the device is placed in debug mode by an administrative user and the debug files are exported from the device.

[CVE-2025-2002](https://www.cve.org/CVERecord?id=CVE-2025-2002) has been assigned to this vulnerability. A CVSS v3.1 base score of 6.0 has been calculated; the CVSS vector string is ([CVSS:3.1/AV:L/AC:L/PR:H/UI:N/S:C/C:H/I:N/A:N](https://www.first.org/cvss/calculator/3.1#CVSS:3.1/AV:L/AC:L/PR:H/UI:N/S:C/C:H/I:N/A:N)).

A CVSS v4 score has also been calculated for [CVE-2025-2002](https://www.cve.org/CVERecord?id=CVE-2025-2002). A base score of 4.0 has been calculated; the CVSS vector string is ([CVSS:4.0/AV:L/AC:L/AT:P/PR:H/UI:N/VC:N/VI:N/VA:N/SC:H/SI:N/SA:N](https://www.first.org/cvss/calculator/4.0#CVSS:4.0/AV:L/AC:L/AT:P/PR:H/UI:N/VC:N/VI:N/VA:N/SC:H/SI:N/SA:N)).

### 3.3 BACKGROUND

-   **CRITICAL INFRASTRUCTURE SECTORS:** Commercial Facilities, Critical Manufacturing, Energy
-   **COUNTRIES/AREAS DEPLOYED:** Worldwide
-   **COMPANY HEADQUARTERS LOCATION:** France

### 3.4 RESEARCHER

Schneider Electric reported this vulnerability to CISA.

4\. MITIGATIONS
---------------

Version 2.1 or later of EcoStruxure Panel Server includes a fix for this vulnerability and is available for [download.](https://www.se.com/ww/en/product-range/40739468-ecostruxure-panel-server/?parent-subcategory-id=4160#software-and-firmware) Users should download EcoStruxure Power Commission Software v2.33.0 or later, and version v2.1 or later of EcoStruxure Panel Server firmware to complete the upgrade process.

Users should employ appropriate patching methodologies when applying these patches to their systems. Schneider Electric strongly recommends the use of back-ups and evaluating the impact of these patches in a test and development environment or on an offline infrastructure. [Contact Schneider Electric's Customer Care Center](https://www.se.com/us/en/work/support/contacts.jsp) for assistance removing a patch.

If users choose not to apply the remediation provided above, they should immediately ensure that debug mode is off will prevent the credentials from being improperly exposed.

Schneider Electric strongly recommends the following industry cybersecurity best practices.

-   Locate control and safety system networks and remote devices behind firewalls and isolate them from the business network.
-   Install physical controls so no unauthorized personnel can access your industrial control and safety systems, components, peripheral equipment, and networks.
-   Place all controllers in locked cabinets and never leave them in the "Program" mode.
-   Never connect programming software to any network other than the network intended for that device.
-   Scan all methods of mobile data exchange with the isolated network such as CDs, USB drives, etc. before use in the terminals or any node connected to these networks.
-   Never allow mobile devices that have connected to any other network besides the intended network to connect to the safety or control networks without proper sanitation.
-   Minimize network exposure for all control system devices and systems and ensure that they are not accessible from the Internet.
-   When remote access is required, use secure methods, such as virtual private networks (VPNs). Recognize that VPNs may have vulnerabilities and should be updated to the most current version available. Also, understand that VPNs are only as secure as the connected devices.
-   For more information refer to the [Schneider Electric Recommended Cybersecurity Best Practices document.](https://www.se.com/us/en/download/document/7EN52-0390/)

Please see Schneider Electric Security Notification [SEVD-2025-070-01](https://download.schneider-electric.com/files?p_Doc_Ref=SEVD-2025-070-01&p_enDocType=Security+and+Safety+Notice&p_File_Name=SEVD-2025-070-01.pdf) for more information about this issue.

CISA recommends users take defensive measures to minimize the risk of exploitation of this vulnerability. CISA reminds organizations to perform proper impact analysis and risk assessment prior to deploying defensive measures.

CISA also provides a section for [control systems security recommended practices](https://www.cisa.gov/resources-tools/resources/ics-recommended-practices) on the ICS webpage on [cisa.gov/ics](https://www.cisa.gov/topics/industrial-control-systems). Several CISA products detailing cyber defense best practices are available for reading and download, including [Improving Industrial Control Systems Cybersecurity with Defense-in-Depth Strategies](https://us-cert.cisa.gov/sites/default/files/recommended_practices/NCCIC_ICS-CERT_Defense_in_Depth_2016_S508C.pdf).

CISA encourages organizations to implement recommended cybersecurity strategies for [proactive defense of ICS assets](https://www.cisa.gov/sites/default/files/publications/Cybersecurity_Best_Practices_for_Industrial_Control_Systems.pdf).

Additional mitigation guidance and recommended practices are publicly available on the ICS webpage at [cisa.gov/ics](https://www.cisa.gov/topics/industrial-control-systems) in the technical information paper, [ICS-TIP-12-146-01B--Targeted Cyber Intrusion Detection and Mitigation Strategies](https://www.cisa.gov/uscert/ics/tips/ICS-TIP-12-146-01B).

Organizations observing suspected malicious activity should follow established internal procedures and report findings to CISA for tracking and correlation against other incidents.

CISA also recommends users take the following measures to protect themselves from social engineering attacks:

-   Do not click web links or open attachments in unsolicited email messages.
-   Refer to [Recognizing and Avoiding Email Scams](https://www.cisa.gov/uscert/sites/default/files/publications/emailscams0905.pdf) for more information on avoiding email scams.
-   Refer to [Avoiding Social Engineering and Phishing Attacks](https://www.cisa.gov/uscert/ncas/tips/ST04-014) for more information on social engineering attacks.

No known public exploitation specifically targeting this vulnerability has been reported to CISA at this time. This vulnerability is not exploitable remotely.

5\. UPDATE HISTORY
------------------

-   March 18, 2025: Initial Publication

#### [Source](https://www.cisa.gov/news-events/ics-advisories/icsa-25-077-04)

<br/>
---
