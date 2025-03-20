---
title: "Siemens SCALANCE M-800 and SC-600 Families"
date: Thu, 13 Mar 25 12:00:00 +0000
draft: false
type: posts
categories: 
- 
---
# Siemens SCALANCE M-800 and SC-600 Families

<br/>

<br/>
As of January 10, 2023, CISA will no longer be updating ICS security advisories for Siemens product vulnerabilities beyond the initial advisory. For the most up-to-date information on vulnerabilities in this advisory, see [Siemens' ProductCERT Security Advisories (CERT Services | Services | Siemens Global).](https://new.siemens.com/global/en/products/services/cert.html#SecurityPublications "(opens in a new window)")

[**View CSAF**](https://github.com/cisagov/CSAF)

1\. EXECUTIVE SUMMARY
---------------------

-   **CVSS v4 6.3**
-   **ATTENTION**: Exploitable remotely
-   **Vendor**: Siemens
-   **Equipment**: SCALANCE M-800 family (incl. S615, MUM-800 and RM1224), SCALANCE SC-600 family
-   **Vulnerability**: Partial String Comparison

2\. RISK EVALUATION
-------------------

Successful exploitation of this vulnerability could allow an attacker to obtain partial invalid usernames accepted by the server. A remote attacker would need access to a valid certificate in order to perform a successful attack.

3\. TECHNICAL DETAILS
---------------------

### 3.1 AFFECTED PRODUCTS

Siemens reports that the following products are affected:

-   Siemens SCALANCE SC-600 family: All versions
-   Siemens RUGGEDCOM RM1224 LTE(4G) EU (6GK6108-4AM00-2BA2): All versions prior to V8.2.1
-   Siemens SCALANCE M876-3 (6GK5876-3AA02-2BA2): vers: All versions prior to V8.2.1
-   Siemens SCALANCE M876-3 (ROK) (6GK5876-3AA02-2EA2): All versions prior to V8.2.1
-   Siemens SCALANCE M876-4 (6GK5876-4AA10-2BA2): All versions prior to V8.2.1
-   Siemens SCALANCE M876-4 (EU) (6GK5876-4AA00-2BA2): All versions prior to V8.2.1
-   Siemens SCALANCE M876-4 (NAM) (6GK5876-4AA00-2DA2): All versions prior to V8.2.1
-   Siemens SCALANCE MUB852-1 (A1) (6GK5852-1EA10-1AA1): All versions prior to V8.2.1
-   Siemens SCALANCE MUB852-1 (B1) (6GK5852-1EA10-1BA1): All versions prior to V8.2.1
-   Siemens SCALANCE MUM853-1 (A1) (6GK5853-2EA10-2AA1): All versions prior to V8.2.1
-   Siemens SCALANCE MUM853-1 (B1) (6GK5853-2EA10-2BA1): All versions prior to V8.2.1
-   Siemens SCALANCE MUM853-1 (EU) (6GK5853-2EA00-2DA1): All versions prior to V8.2.1
-   Siemens RUGGEDCOM RM1224 LTE(4G) NAM (6GK6108-4AM00-2DA2): All versions prior to V8.2.1
-   Siemens SCALANCE MUM856-1 (A1) (6GK5856-2EA10-3AA1): All versions prior to V8.2.1
-   Siemens SCALANCE MUM856-1 (B1) (6GK5856-2EA10-3BA1): All versions prior to V8.2.1
-   Siemens SCALANCE MUM856-1 (CN) (6GK5856-2EA00-3FA1): All versions prior to V8.2.1
-   Siemens SCALANCE MUM856-1 (EU) (6GK5856-2EA00-3DA1): All versions prior to V8.2.1
-   Siemens SCALANCE MUM856-1 (RoW) (6GK5856-2EA00-3AA1): All versions prior to V8.2.1
-   Siemens SCALANCE S615 EEC LAN-Router (6GK5615-0AA01-2AA2): All versions prior to V8.2.1
-   Siemens SCALANCE S615 LAN-Router (6GK5615-0AA00-2AA2): All versions prior to V8.2.1
-   Siemens SCALANCE M804PB (6GK5804-0AP00-2AA2): All versions prior to V8.2.1
-   Siemens SCALANCE M812-1 ADSL-Router family: All versions prior to V8.2.1
-   Siemens SCALANCE M816-1 ADSL-Router family: All versions prior to V8.2.1
-   Siemens SCALANCE M826-2 SHDSL-Router (6GK5826-2AB00-2AB2): All versions prior to V8.2.1
-   Siemens SCALANCE M874-2 (6GK5874-2AA00-2AA2): All versions prior to V8.2.1
-   Siemens SCALANCE M874-3 3G-Router (CN) (6GK5874-3AA00-2FA2): All versions prior to V8.2.1
-   Siemens SCALANCE M874-3 (6GK5874-3AA00-2AA2): All versions prior to V8.2.1

### 3.2 VULNERABILITY OVERVIEW

#### **3.2.1** [**PARTIAL STRING COMPARISON CWE-187**](https://cwe.mitre.org/data/definitions/187.html)

Affected devices improperly validate usernames during OpenVPN authentication. This could allow an attacker to get partial invalid usernames accepted by the server.

[CVE-2025-23384](https://www.cve.org/CVERecord?id=CVE-2025-23384) has been assigned to this vulnerability. A CVSS v3 base score of 3.7 has been calculated; the CVSS vector string is ([CVSS:3.1/AV:N/AC:H/PR:N/UI:N/S:U/C:N/I:L/A:N](https://www.first.org/cvss/calculator/3.1#CVSS:3.1/AV:N/AC:H/PR:N/UI:N/S:U/C:N/I:L/A:N)).

A CVSS v4 score has also been calculated for [CVE-2025-23384](https://www.cve.org/CVERecord?id=CVE-2025-23384). A base score of 6.3 has been calculated; the CVSS vector string is ([CVSS:4.0/AV:N/AC:L/AT:P/PR:N/UI:N/VC:N/VI:L/VA:N/SC:N/SI:N/SA:N](https://www.first.org/cvss/calculator/4.0#CVSS:4.0/AV:N/AC:L/AT:P/PR:N/UI:N/VC:N/VI:L/VA:N/SC:N/SI:N/SA:N)).

### 3.4 BACKGROUND

-   **CRITICAL INFRASTRUCTURE SECTORS:** Critical Manufacturing
-   **COUNTRIES/AREAS DEPLOYED:** Worldwide
-   **COMPANY HEADQUARTERS LOCATION:** Germany

### 3.5 RESEARCHER

Siemens reported this vulnerability to CISA.

4\. MITIGATIONS
---------------

Siemens has identified the following specific workarounds and mitigations users can apply to reduce risk:

-   SCALANCE SC-600 family: Currently no fix is available.
-   RUGGEDCOM RM1224 LTE(4G) EU (6GK6108-4AM00-2BA2), RUGGEDCOM RM1224 LTE(4G) NAM (6GK6108-4AM00-2DA2), SCALANCE M804PB (6GK5804-0AP00-2AA2), SCALANCE M812-1 ADSL-Router family, SCALANCE M816-1 ADSL-Router family, SCALANCE M826-2 SHDSL-Router (6GK5826-2AB00-2AB2), SCALANCE M874-2 (6GK5874-2AA00-2AA2), SCALANCE M874-3 (6GK5874-3AA00-2AA2), SCALANCE M874-3 3G-Router (CN) (6GK5874-3AA00-2FA2), SCALANCE M876-3 (6GK5876-3AA02-2BA2), SCALANCE M876-3 (ROK) (6GK5876-3AA02-2EA2), SCALANCE M876-4 (6GK5876-4AA10-2BA2), SCALANCE M876-4 (EU) (6GK5876-4AA00-2BA2), SCALANCE M876-4 (NAM) (6GK5876-4AA00-2DA2), SCALANCE MUB852-1 (A1) (6GK5852-1EA10-1AA1), SCALANCE MUB852-1 (B1) (6GK5852-1EA10-1BA1), SCALANCE MUM853-1 (A1) (6GK5853-2EA10-2AA1), SCALANCE MUM853-1 (B1) (6GK5853-2EA10-2BA1), SCALANCE MUM853-1 (EU) (6GK5853-2EA00-2DA1), SCALANCE MUM856-1 (A1) (6GK5856-2EA10-3AA1), SCALANCE MUM856-1 (B1) (6GK5856-2EA10-3BA1), SCALANCE MUM856-1 (CN) (6GK5856-2EA00-3FA1), SCALANCE MUM856-1 (EU) (6GK5856-2EA00-3DA1), SCALANCE MUM856-1 (RoW) (6GK5856-2EA00-3AA1), SCALANCE S615 EEC LAN-Router (6GK5615-0AA01-2AA2), SCALANCE S615 LAN-Router (6GK5615-0AA00-2AA2): Update to [V8.2.1](https://support.industry.siemens.com/cs/ww/en/view/109983338/) or later version.
-   All affected products: Apply a strong password policy for your devices.

As a general security measure, Siemens recommends protecting network access to devices with appropriate mechanisms. To operate the devices in a protected IT environment, Siemens recommends configuring the environment according to [Siemens' operational guidelines for industrial security](https://www.siemens.com/cert/operational-guidelines-industrial-security) and following recommendations in the product manuals.

Additional information on industrial security by Siemens can be found on the [Siemens industrial security webpage](https://www.siemens.com/industrialsecurity)

For more information see the associated Siemens security advisory SSA-280834 in [HTML](https://cert-portal.siemens.com/productcert/html/ssa-280834.html) and [CSAF](https://cert-portal.siemens.com/productcert/csaf/ssa-280834.json).

CISA recommends users take defensive measures to minimize the risk of exploitation of this vulnerability, such as:

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

No known public exploitation specifically targeting this vulnerability has been reported to CISA at this time. This vulnerability has a high attack complexity.

5\. UPDATE HISTORY
------------------

-   March 13, 2025: Initial Publication

#### [Source](https://www.cisa.gov/news-events/ics-advisories/icsa-25-072-07)

<br/>
---
