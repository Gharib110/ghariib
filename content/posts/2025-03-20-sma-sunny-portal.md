---
title: "SMA Sunny Portal"
date: Thu, 20 Mar 25 12:00:00 +0000
draft: false
type: posts
categories: 
- 
---
# SMA Sunny Portal

<br/>

<br/>
[**View CSAF**](https://github.com/cisagov/CSAF)

1\. EXECUTIVE SUMMARY
---------------------

-   **CVSS v4 6.9**
-   **ATTENTION**: Exploitable remotely/low attack complexity
-   **Vendor**: SMA
-   **Equipment**: Sunny Portal
-   **Vulnerability**: Unrestricted Upload of File with Dangerous Type

2\. RISK EVALUATION
-------------------

Successful exploitation of this vulnerability could allow an attacker to upload and remotely execute code.

3\. TECHNICAL DETAILS
---------------------

### 3.1 AFFECTED PRODUCTS

The following versions of SMA Sunny Portal are affected:

-   Sunny Portal: All versions before December 19, 2024

### 3.2 VULERABILITY OVERVIEW

#### **3.2.1** [**UNRESTRICTED UPLOAD OF FILE WITH DANGEROUS TYPE CWE-434**](https://cwe.mitre.org/data/definitions/434.html)

The SMA Sunny Portal is vulnerable to an unauthenticated remote attacker who can upload a .aspx file instead of a PV system picture through the demo account. The code can only be executed in the security context of the user.

[CVE-2025-0731](https://www.cve.org/CVERecord?id=CVE-2025-0731) has been assigned to this vulnerability. A CVSS v3.1 base score of 6.5 has been calculated; the CVSS vector string is ([AV:N/AC:L/PR:N/UI:N/S:U/C:N/I:L/A:L](https://www.first.org/cvss/calculator/3.1#CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:N/I:L/A:L)).

A CVSS v4 score has also been calculated for [CVE-2025-0731](https://www.cve.org/CVERecord?id=CVE-2025-0731). A base score of 6.9 has been calculated; the CVSS vector string is ([AV:N/AC:L/AT:N/PR:N/UI:N/VC:N/VI:L/VA:L/SC:N/SI:N/SA:N](https://www.first.org/cvss/calculator/4.0#CVSS:4.0/AV:N/AC:L/AT:N/PR:N/UI:N/VC:N/VI:L/VA:L/SC:N/SI:N/SA:N)).

### 3.3 BACKGROUND

-   **CRITICAL INFRASTRUCTURE SECTORS:** Energy
-   **COUNTRIES/AREAS DEPLOYED:** Worldwide
-   **COMPANY HEADQUARTERS LOCATION:** Germany

### 3.4 RESEARCHER

Francesco La Spina from Forescout Technologies Inc. first reported this vulnerability to CERT@VDE. Daniel dos Santos from Forescout Technologies Inc. then reported this vulnerability to CISA.

4\. MITIGATIONS
---------------

No further action is required. The vulnerability was closed in the portal on December 19, 2024.

Please contact the [SMA service center](https://my.sma-service.com/s/?language=en_US) for more information.

CERT@VDE published advisory number [VDE-2025-012](https://cert.vde.com/en/advisories/VDE-2025-012) on this issue.

CISA recommends users take defensive measures to minimize the risk of exploitation of this vulnerability, such as:

-   Minimize network exposure for all control system devices and/or systems, ensuring they are [not accessible from the internet](https://www.cisa.gov/uscert/ics/alerts/ICS-ALERT-10-301-01).
-   Locate control system networks and remote devices behind firewalls and isolating them from business networks.
-   When remote access is required, use more secure methods, such as Virtual Private Networks (VPNs), recognizing VPNs may have vulnerabilities and should be updated to the most current version available. Also recognize VPN is only as secure as the connected devices.

CISA reminds organizations to perform proper impact analysis and risk assessment prior to deploying defensive measures.

CISA also provides a section for [control systems security recommended practices](https://www.cisa.gov/resources-tools/resources/ics-recommended-practices) on the ICS webpage on [cisa.gov/ics](https://www.cisa.gov/topics/industrial-control-systems). Several CISA products detailing cyber defense best practices are available for reading and download, including [Improving Industrial Control Systems Cybersecurity with Defense-in-Depth Strategies](https://us-cert.cisa.gov/sites/default/files/recommended_practices/NCCIC_ICS-CERT_Defense_in_Depth_2016_S508C.pdf).

CISA encourages organizations to implement recommended cybersecurity strategies for [proactive defense of ICS assets](https://www.cisa.gov/sites/default/files/publications/Cybersecurity_Best_Practices_for_Industrial_Control_Systems.pdf).

Additional mitigation guidance and recommended practices are publicly available on the ICS webpage at [cisa.gov/ics](https://www.cisa.gov/topics/industrial-control-systems) in the technical information paper, [ICS-TIP-12-146-01B--Targeted Cyber Intrusion Detection and Mitigation Strategies](https://www.cisa.gov/uscert/ics/tips/ICS-TIP-12-146-01B).

Organizations observing suspected malicious activity should follow established internal procedures and report findings to CISA for tracking and correlation against other incidents.

No known public exploitation specifically targeting this vulnerability has been reported to CISA at this time.

5\. UPDATE HISTORY
------------------

-   March 20, 2025: Initial Publication

#### [Source](https://www.cisa.gov/news-events/ics-advisories/icsa-25-079-04)

<br/>
---
