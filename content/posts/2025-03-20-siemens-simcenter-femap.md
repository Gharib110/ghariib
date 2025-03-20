---
title: "Siemens Simcenter Femap"
date: Thu, 20 Mar 25 12:00:00 +0000
draft: false
type: posts
categories: 
- 
---
# Siemens Simcenter Femap

<br/>

<br/>
As of January 10, 2023, CISA will no longer be updating ICS security advisories for Siemens product vulnerabilities beyond the initial advisory. For the most up-to-date information on vulnerabilities in this advisory, see [Siemens' ProductCERT Security Advisories (CERT Services | Services | Siemens Global).](https://new.siemens.com/global/en/products/services/cert.html#SecurityPublications "(opens in a new window)")

[**View CSAF**](https://github.com/cisagov/CSAF)

1\. EXECUTIVE SUMMARY
---------------------

-   **CVSS v4 7.3**
-   **ATTENTION**: Low Attack Complexity
-   **Vendor**: Siemens
-   **Equipment**: Simcenter Femap
-   **Vulnerability**: Improper Restriction of Operations within the Bounds of a Memory Buffer

2\. RISK EVALUATION
-------------------

Successful exploitation of this vulnerability could allow an attacker to execute code within the current process of the product.

3\. TECHNICAL DETAILS
---------------------

### 3.1 AFFECTED PRODUCTS

Siemens reports that the following products are affected:

-   Simcenter Femap V2401: Versions prior to V2401.0003
-   Simcenter Femap V2406: Versions prior to V2406.0002

### 3.2 VULNERABILITY OVERVIEW

#### **3.2.1** [**IMPROPER RESTRICTION OF OPERATIONS WITHIN THE BOUNDS OF A MEMORY BUFFER CWE-119**](https://cwe.mitre.org/data/definitions/119.html)

Siemens Simcenter Femap contains a memory corruption vulnerability while parsing specially crafted .NEU files. This could allow an attacker to execute code in the context of the current process.

[CVE-2025-25175](https://www.cve.org/CVERecord?id=CVE-2025-25175) has been assigned to this vulnerability. A CVSS v3 base score of 7.8 has been calculated; the CVSS vector string is ([CVSS:3.1/AV:L/AC:L/PR:N/UI:R/S:U/C:H/I:H/A:H](https://www.first.org/cvss/calculator/3.1#CVSS:3.1/AV:L/AC:L/PR:N/UI:R/S:U/C:H/I:H/A:H)).

A CVSS v4 score has also been calculated for [CVE-2025-25175](https://www.cve.org/CVERecord?id=CVE-2025-25175). A base score of 7.3 has been calculated; the CVSS vector string is ([CVSS:4.0/AV:L/AC:H/AT:N/PR:N/UI:P/VC:H/VI:H/VA:H/SC:N/SI:N/SA:N](https://www.first.org/cvss/calculator/4.0#CVSS:4.0/AV:L/AC:H/AT:N/PR:N/UI:P/VC:H/VI:H/VA:H/SC:N/SI:N/SA:N)).

### 3.3 BACKGROUND

-   **CRITICAL INFRASTRUCTURE SECTORS:** Critical Manufacturing
-   **COUNTRIES/AREAS DEPLOYED:** Worldwide
-   **COMPANY HEADQUARTERS LOCATION:** Germany

### 3.4 RESEARCHER

Trend Micro Zero Day Initiative reported this vulnerability to Siemens.

4\. MITIGATIONS
---------------

Siemens has released new versions for the affected products and recommends to update to the latest versions.

-   Simcenter Femap V2401: [Update to V2401.0003 or later version.](https://support.sw.siemens.com/)
-   Simcenter Femap V2406: [Update to V2406.0002 or later version.](https://support.sw.siemens.com/)

Siemens has identified the following specific workarounds and mitigations users can apply to reduce risk:

-   All affected products: Do not open untrusted NEU files in affected application

As a general security measure, Siemens recommends protecting network access to devices with appropriate mechanisms. To operate the devices in a protected IT environment, Siemens recommends configuring the environment according to [Siemens' operational guidelines for industrial security](https://www.siemens.com/cert/operational-guidelines-industrial-security) and following recommendations in the product manuals.

Additional information on industrial security by Siemens can be found on the [Siemens industrial security webpage](https://www.siemens.com/industrialsecurity)

For more information see the associated Siemens security advisory SSA-920092 in [HTML](https://cert-portal.siemens.com/productcert/html/ssa-920092.html) and [CSAF](https://cert-portal.siemens.com/productcert/csaf/ssa-920092.json).

CISA recommends users take defensive measures to minimize the risk of exploitation of this vulnerability, such as:

-   Minimize network exposure for all control system devices and/or systems, ensuring they are [not accessible from the internet](https://www.cisa.gov/uscert/ics/alerts/ICS-ALERT-10-301-01).
-   Locate control system networks and remote devices behind firewalls and isolating them from business networks.
-   When remote access is required, use more secure methods, such as Virtual Private Networks (VPNs). Recognize VPNs may have vulnerabilities, should be updated to the most recent version available, and are only as secure as the connected devices.

CISA reminds organizations to perform proper impact analysis and risk assessment prior to deploying defensive measures.

CISA also provides a section for [control systems security recommended practices](https://www.cisa.gov/resources-tools/resources/ics-recommended-practices) on the ICS webpage on [cisa.gov](https://www.cisa.gov/topics/industrial-control-systems). Several CISA products detailing cyber defense best practices are available for reading and download, including [Improving Industrial Control Systems Cybersecurity with Defense-in-Depth Strategies](https://us-cert.cisa.gov/sites/default/files/recommended_practices/NCCIC_ICS-CERT_Defense_in_Depth_2016_S508C.pdf).

CISA encourages organizations to implement recommended cybersecurity strategies for [proactive defense of ICS assets](https://www.cisa.gov/sites/default/files/publications/Cybersecurity_Best_Practices_for_Industrial_Control_Systems.pdf).

Additional mitigation guidance and recommended practices are publicly available on the ICS webpage at [cisa.gov](https://www.cisa.gov/topics/industrial-control-systems) in the technical information paper, [ICS-TIP-12-146-01B--Targeted Cyber Intrusion Detection and Mitigation Strategies](https://www.cisa.gov/uscert/ics/tips/ICS-TIP-12-146-01B).

Organizations observing suspected malicious activity should follow established internal procedures and report findings to CISA for tracking and correlation against other incidents.

No known public exploitation specifically targeting this vulnerability has been reported to CISA at this time. This vulnerability is not exploitable remotely.

5\. UPDATE HISTORY
------------------

-   March 20, 2025: Initial Publication

#### [Source](https://www.cisa.gov/news-events/ics-advisories/icsa-25-079-03)

<br/>
---
