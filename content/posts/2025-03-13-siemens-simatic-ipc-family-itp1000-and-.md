---
title: "Siemens SIMATIC IPC Family ITP1000 and Field PGs"
date: Thu, 13 Mar 25 12:00:00 +0000
draft: false
type: posts
categories: 
- 
---
# Siemens SIMATIC IPC Family ITP1000 and Field PGs

<br/>

<br/>
As of January 10, 2023, CISA will no longer be updating ICS security advisories for Siemens product vulnerabilities beyond the initial advisory. For the most up-to-date information on vulnerabilities in this advisory, see [Siemens' ProductCERT Security Advisories (CERT Services | Services | Siemens Global).](https://new.siemens.com/global/en/products/services/cert.html#SecurityPublications "(opens in a new window)")

[**View CSAF**](https://github.com/cisagov/CSAF)

1\. EXECUTIVE SUMMARY
---------------------

-   **CVSS v4 8.4**
-   **ATTENTION**: Low attack complexity
-   **Vendor**: Siemens
-   **Equipment**: SIMATIC IPC Family, SIMATIC ITP1000, SIMATIC Field PGs
-   **Vulnerabilities**: Protection Mechanism Failure

2\. RISK EVALUATION
-------------------

Successful exploitation of these vulnerabilities could allow an authenticated attacker to alter the secure boot configuration or to disable the BIOS password.

3\. TECHNICAL DETAILS
---------------------

### 3.1 AFFECTED PRODUCTS

Siemens reports that the following products are affected:

-   Siemens SIMATIC Field PG M5: All versions
-   Siemens SIMATIC IPC377G: All versions
-   Siemens SIMATIC IPC427E: All versions
-   Siemens SIMATIC IPC477E: All versions
-   Siemens SIMATIC IPC477E PRO: All versions
-   Siemens SIMATIC IPC527G: All versions
-   Siemens SIMATIC IPC627E: Versions prior to 25.02.15
-   Siemens SIMATIC IPC647E: Versions prior to V25.02.15
-   Siemens SIMATIC IPC677E: Versions prior to V25.02.15
-   Siemens SIMATIC IPC847E: Versions prior to V25.02.15
-   Siemens SIMATIC IPC3000 SMART V3: All versions
-   Siemens SIMATIC Field PG M6: Versions prior to V26.01.12 (CVE-2024-56182)
-   Siemens SIMATIC IPC BX-21A: Versions prior to V31.01.07
-   Siemens SIMATIC IPC BX-32A: Versions prior to V29.01.07
-   Siemens SIMATIC IPC BX-39A: Versions prior to V29.01.07
-   Siemens SIMATIC IPC BX-59A: Versions prior to V32.01.04
-   Siemens SIMATIC IPC PX-32A: Versions prior to V29.01.07
-   Siemens SIMATIC IPC PX-39A: Versions prior to V29.01.07
-   Siemens SIMATIC IPC PX-39A PRO: Versions prior to V29.01.07
-   Siemens SIMATIC IPC RC-543B: All versions
-   Siemens SIMATIC IPC RW-543A: All versions
-   Siemens SIMATIC ITP1000: All versions
-   Siemens SIMATIC IPC127E: All versions
-   Siemens SIMATIC IPC277G PRO: All versions
-   Siemens SIMATIC IPC227E: All versions
-   Siemens SIMATIC IPC227G: All versions
-   Siemens SIMATIC IPC277E: All versions
-   Siemens SIMATIC IPC277G: All versions
-   Siemens SIMATIC IPC327G: All versions
-   Siemens SIMATIC IPC347G: All versions

### 3.2 VULNERABILITY OVERVIEW

#### **3.2.1** [**PROTECTION MECHANISM FAILURE CWE-693**](https://cwe.mitre.org/data/definitions/693.html)

The affected devices have insufficient protection mechanism for the EFI (Extensible Firmware Interface) variables stored on the device. This could allow an authenticated attacker to alter the secure boot configuration without proper authorization by directly communicating with the flash controller.

[CVE-2024-56181](https://www.cve.org/CVERecord?id=CVE-2024-56181) has been assigned to this vulnerability. A CVSS v3 base score of 8.2 has been calculated; the CVSS vector string is ([CVSS:3.1/AV:L/AC:L/PR:H/UI:N/S:C/C:H/I:H/A:H](https://www.first.org/cvss/calculator/3.1#CVSS:3.1/AV:L/AC:L/PR:H/UI:N/S:C/C:H/I:H/A:H)).

A CVSS v4 score has also been calculated for [CVE-2024-56181](https://www.cve.org/CVERecord?id=CVE-2024-56181). A base score of 8.4 has been calculated; the CVSS vector string is ([CVSS:4.0/AV:L/AC:L/AT:N/PR:H/UI:N/VC:N/VI:H/VA:H/SC:H/SI:H/SA:H](https://www.first.org/cvss/calculator/4.0#CVSS:4.0/AV:L/AC:L/AT:N/PR:H/UI:N/VC:N/VI:H/VA:H/SC:H/SI:H/SA:H)).

#### **3.2.2** [**PROTECTION MECHANISM FAILURE CWE-693**](https://cwe.mitre.org/data/definitions/693.html)

The affected devices have insufficient protection mechanism for the EFI (Extensible Firmware Interface) variables stored on the device. This could allow an authenticated attacker to disable the BIOS password without proper authorization by directly communicating with the flash controller.

[CVE-2024-56182](https://www.cve.org/CVERecord?id=CVE-2024-56182) has been assigned to this vulnerability. A CVSS v3 base score of 8.2 has been calculated; the CVSS vector string is ([CVSS:3.1/AV:L/AC:L/PR:H/UI:N/S:C/C:H/I:H/A:H](https://www.first.org/cvss/calculator/3.1#CVSS:3.1/AV:L/AC:L/PR:H/UI:N/S:C/C:H/I:H/A:H)).

A CVSS v4 score has also been calculated for [CVE-2024-56182](https://www.cve.org/CVERecord?id=CVE-2024-56182). A base score of 8.4 has been calculated; the CVSS vector string is ([CVSS:4.0/AV:L/AC:L/AT:N/PR:H/UI:N/VC:N/VI:H/VA:H/SC:H/SI:H/SA:H](https://www.first.org/cvss/calculator/4.0#CVSS:4.0/AV:L/AC:L/AT:N/PR:H/UI:N/VC:N/VI:H/VA:H/SC:H/SI:H/SA:H)).

### 3.3 BACKGROUND

-   **CRITICAL INFRASTRUCTURE SECTORS:** Critical Manufacturing
-   **COUNTRIES/AREAS DEPLOYED:** Worldwide
-   **COMPANY HEADQUARTERS LOCATION:** Germany

### 3.4 RESEARCHER

Siemens reported these vulnerabilities to CISA.

4\. MITIGATIONS
---------------

Siemens has identified the following specific workarounds and mitigations users can apply to reduce risk:

-   Restrict access to root/administrator permission for the operating system
-   SIMATIC IPC627E, SIMATIC IPC647E, SIMATIC IPC677E, SIMATIC IPC847E: Update to [V25.02.15](https://support.industry.siemens.com/cs/ww/en/view/109763408/) or later version
-   SIMATIC IPC BX-39A, SIMATIC IPC PX-39A, SIMATIC IPC PX-39A PRO, SIMATIC IPC BX-32A, SIMATIC IPC PX-32A: Update to [V29.01.07](https://support.industry.siemens.com/cs/ww/en/view/109763408/) or later version
-   SIMATIC IPC BX-21A: Update to [V31.01.07](https://support.industry.siemens.com/cs/ww/en/view/109763408/) or later version
-   SIMATIC IPC BX-59A: Update to [V32.01.04](https://support.industry.siemens.com/cs/ww/en/view/109763408/) or later version
-   SIMATIC Field PG M6: Update to [V26.01.12](https://support.industry.siemens.com/cs/ww/en/view/109763408/) or later version
-   SIMATIC Field PG M5, SIMATIC IPC RC-543B, SIMATIC IPC RW-543A, SIMATIC IPC127E, SIMATIC IPC227G, SIMATIC IPC277G, SIMATIC IPC277G PRO, SIMATIC IPC3000 SMART V3, SIMATIC IPC327G, SIMATIC IPC347G, SIMATIC IPC377G, SIMATIC IPC427E, SIMATIC IPC477E, SIMATIC IPC477E PRO, SIMATIC IPC527G, SIMATIC ITP1000, SIMATIC IPC227E, SIMATIC IPC277E: Currently no fix is available

As a general security measure, Siemens recommends protecting network access to devices with appropriate mechanisms. To operate the devices in a protected IT environment, Siemens recommends configuring the environment according to [Siemens' operational guidelines for industrial security](https://www.siemens.com/cert/operational-guidelines-industrial-security) and following recommendations in the product manuals.

Additional information on industrial security by Siemens can be found on the [Siemens industrial security webpage](https://www.siemens.com/industrialsecurity)

For more information see the associated Siemens security advisory SSA-216014 in [HTML](https://cert-portal.siemens.com/productcert/html/ssa-216014.html) and [CSAF](https://cert-portal.siemens.com/productcert/csaf/ssa-216014.json).

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

No known public exploitation specifically targeting these vulnerabilities has been reported to CISA at this time. These vulnerabilities are not exploitable remotely.

5\. UPDATE HISTORY
------------------

-   March 13, 2025: Initial Publication

#### [Source](https://www.cisa.gov/news-events/ics-advisories/icsa-25-072-11)

<br/>
---
