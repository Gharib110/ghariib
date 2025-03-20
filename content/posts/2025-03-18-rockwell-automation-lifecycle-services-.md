---
title: "Rockwell Automation Lifecycle Services with VMware"
date: Tue, 18 Mar 25 12:00:00 +0000
draft: false
type: posts
categories: 
- 
---
# Rockwell Automation Lifecycle Services with VMware

<br/>

<br/>
[**View CSAF**](https://github.com/cisagov/CSAF)

1\. EXECUTIVE SUMMARY
---------------------

-   **CVSS v4 9.4**
-   **ATTENTION**: Low attack complexity/public exploits are available/known public exploitation
-   **Vendor**: Rockwell Automation
-   **Equipment**: Industrial Data Center (IDC) with VMware, VersaVirtual Appliance (VVA) with VMware, Threat Detection Managed Services (TDMS) with VMware, Endpoint Protection Service with RA Proxy & VMware, Engineered and Integrated Solutions with VMware
-   **Vulnerabilities**: Time-of-check Time-of-use (TOCTOU) Race Condition, Write-what-where Condition, Out-of-bounds Read

2\. RISK EVALUATION
-------------------

Successful exploitation of these vulnerabilities could allow an attacker with local administrative privileges to execute code.

3\. TECHNICAL DETAILS
---------------------

### 3.1 AFFECTED PRODUCTS

The following versions of Rockwell Automation Lifecycle Services with VMware are affected:

-   Industrial Data Center (IDC) with VMware: Generations 1 through 4
-   VersaVirtual Appliance (VVA) with VMware: Series A and B
-   Threat Detection Managed Services (TDMS) with VMware: All versions
-   Endpoint Protection Service with RA Proxy & VMware only: All versions
-   Engineered and Integrated Solutions with VMware: All versions

### 3.2 VULNERABILITY OVERVIEW

#### **3.2.1** [**TIME-OF-CHECK TIME-OF-USE (TOCTOU) RACE CONDITION CWE-367**](https://cwe.mitre.org/data/definitions/367.html)

A time of check time of use (TOCTOU) vulnerability exists in VMware ESXi, which the affected products use. Exploitation of the vulnerability can allow a threat actor with local administrative privileges to execute code as the virtual machine's VMX process running on the host.

[CVE-2025-22224](https://www.cve.org/CVERecord?id=CVE-2025-22224) has been assigned to this vulnerability. A CVSS v3.1 base score of 9.3 has been calculated; the CVSS vector string is ([AV:L/AC:L/PR:N/UI:N/S:C/C:H/I:H/A:H](https://www.first.org/cvss/calculator/3.1#CVSS:3.1/AV:L/AC:L/PR:N/UI:N/S:C/C:H/I:H/A:H)).

A CVSS v4 score has also been calculated for [CVE-2025-22224](https://www.cve.org/CVERecord?id=CVE-2025-22224). A base score of 9.4 has been calculated; the CVSS vector string is ([AV:L/AC:L/AT:N/PR:N/UI:N/VC:H/VI:H/VA:H/SC:H/SI:H/SA:H](https://www.first.org/cvss/calculator/4.0#CVSS:4.0/AV:L/AC:L/AT:N/PR:N/UI:N/VC:H/VI:H/VA:H/SC:H/SI:H/SA:H)).

#### **3.2.2** [**WRITE-WHAT-WHERE CONDITION CWE-123**](https://cwe.mitre.org/data/definitions/123.html)

A code execution vulnerability exists in VMware ESXi, which the affected products use. Exploitation of the vulnerability can allow a threat actor with privileges within the VMX process trigger an arbitrary kernel write, leading to an escape of the sandbox.

[CVE-2025-22225](https://www.cve.org/CVERecord?id=CVE-2025-22225) has been assigned to this vulnerability. A CVSS v3.1 base score of 8.2 has been calculated; the CVSS vector string is ([AV:L/AC:L/PR:H/UI:N/S:C/C:H/I:H/A:H](https://www.first.org/cvss/calculator/3.1#CVSS:3.1/AV:L/AC:L/PR:H/UI:N/S:C/C:H/I:H/A:H)).

A CVSS v4 score has also been calculated for [CVE-2025-22225](https://www.cve.org/CVERecord?id=CVE-2025-22225). A base score of 9.3 has been calculated; the CVSS vector string is ([AV:L/AC:L/AT:N/PR:H/UI:N/VC:H/VI:H/VA:H/SC:H/SI:H/SA:H](https://www.first.org/cvss/calculator/4.0#CVSS:4.0/AV:L/AC:L/AT:N/PR:H/UI:N/VC:H/VI:H/VA:H/SC:H/SI:H/SA:H)).

#### **3.2.3** [**OUT-OF-BOUNDS READ CWE-125**](https://cwe.mitre.org/data/definitions/125.html)

An out-of-bounds vulnerability exists in VMware ESXi, which the affected products use. Exploitation of the vulnerability can allow a threat actor with administrative privileges to leak memory from the vmx process.

[CVE-2025-22226](https://www.cve.org/CVERecord?id=CVE-2025-22226) has been assigned to this vulnerability. A CVSS v3.1 base score of 7.1 has been calculated; the CVSS vector string is ([AV:L/AC:L/PR:N/UI:N/S:C/C:H/I:N/A:N](https://www.first.org/cvss/calculator/3.1#CVSS:3.1/AV:L/AC:L/PR:N/UI:N/S:C/C:H/I:N/A:N)).

A CVSS v4 score has also been calculated for [CVE-2025-22226](https://www.cve.org/CVERecord?id=CVE-2025-22226). A base score of 8.2 has been calculated; the CVSS vector string is ([AV:L/AC:L/AT:N/PR:N/UI:N/VC:H/VI:N/VA:N/SC:H/SI:N/SA:N](https://www.first.org/cvss/calculator/4.0#CVSS:4.0/AV:L/AC:L/AT:N/PR:N/UI:N/VC:H/VI:N/VA:N/SC:H/SI:N/SA:N)).

### 3.3 BACKGROUND

-   **CRITICAL INFRASTRUCTURE SECTORS:** Critical Manufacturing
-   **COUNTRIES/AREAS DEPLOYED:** Worldwide
-   **COMPANY HEADQUARTERS LOCATION:** United States

### 3.4 RESEARCHER

Rockwell Automation reported these vulnerabilities to CISA.

4\. MITIGATIONS
---------------

Rockwell Automation will contact impacted users to discuss actions needed for remediation efforts.

Users without Rockwell Automation managed services contract, refer to Broadcom's advisories below:

-   [Support Content Notification - Support Portal - Broadcom support portal](https://support.broadcom.com/web/ecx/support-content-notification/-/external/content/SecurityAdvisories/0/25390)
-   [https://techdocs.broadcom.com/us/en/vmware-cis/vsphere/vsphere/8-0/release-notes/esxi-update-and-patch-release-notes/vsphere-esxi-80u3d-release-notes.html](https://techdocs.broadcom.com/us/en/vmware-cis/vsphere/vsphere/8-0/release-notes/esxi-update-and-patch-release-notes/vsphere-esxi-80u3d-release-notes.html)
-   [https://techdocs.broadcom.com/us/en/vmware-cis/vsphere/vsphere/8-0/release-notes/esxi-update-and-patch-release-notes/vsphere-esxi-80u2d-release-notes.html](https://techdocs.broadcom.com/us/en/vmware-cis/vsphere/vsphere/8-0/release-notes/esxi-update-and-patch-release-notes/vsphere-esxi-80u2d-release-notes.html)
-   [https://techdocs.broadcom.com/us/en/vmware-cis/vsphere/vsphere/7-0/release-notes/esxi-update-and-patch-release-notes/vsphere-esxi-70u3s-release-notes.html](https://techdocs.broadcom.com/us/en/vmware-cis/vsphere/vsphere/7-0/release-notes/esxi-update-and-patch-release-notes/vsphere-esxi-70u3s-release-notes.html)

Additionally, those using the affected software who are unable to upgrade to one of the corrected versions are encouraged to apply security best practices, where possible.

-   [Security Best Practices](https://rockwellautomation.custhelp.com/app/answers/answer_view/a_id/1085012/loc/en_US#__highlight)

CISA recommends users take defensive measures to minimize the risk of exploitation of these vulnerabilities, such as:

-   Minimize network exposure for all control system devices and/or systems, ensuring they are [not accessible from the Internet](https://www.cisa.gov/uscert/ics/alerts/ICS-ALERT-10-301-01).
-   Locate control system networks and remote devices behind firewalls and isolating them from business networks.
-   When remote access is required, use more secure methods, such as Virtual Private Networks (VPNs), recognizing VPNs may have vulnerabilities and should be updated to the most current version available. Also recognize VPN is only as secure as the connected devices.

CISA reminds organizations to perform proper impact analysis and risk assessment prior to deploying defensive measures.

CISA also provides a section for [control systems security recommended practices](https://www.cisa.gov/resources-tools/resources/ics-recommended-practices) on the ICS webpage on [cisa.gov/ics](https://www.cisa.gov/topics/industrial-control-systems). Several CISA products detailing cyber defense best practices are available for reading and download, including [Improving Industrial Control Systems Cybersecurity with Defense-in-Depth Strategies](https://us-cert.cisa.gov/sites/default/files/recommended_practices/NCCIC_ICS-CERT_Defense_in_Depth_2016_S508C.pdf).

CISA encourages organizations to implement recommended cybersecurity strategies for [proactive defense of ICS assets](https://www.cisa.gov/sites/default/files/publications/Cybersecurity_Best_Practices_for_Industrial_Control_Systems.pdf).

Additional mitigation guidance and recommended practices are publicly available on the ICS webpage at [cisa.gov/ics](https://www.cisa.gov/topics/industrial-control-systems) in the technical information paper, [ICS-TIP-12-146-01B--Targeted Cyber Intrusion Detection and Mitigation Strategies](https://www.cisa.gov/uscert/ics/tips/ICS-TIP-12-146-01B).

Organizations observing suspected malicious activity should follow established internal procedures and report findings to CISA for tracking and correlation against other incidents.

CISA also recommends users take the following measures to protect themselves from social engineering attacks:

-   Do not click web links or open attachments in unsolicited email messages.
-   Refer to [Recognizing and Avoiding Email Scams](https://www.cisa.gov/uscert/sites/default/files/publications/emailscams0905.pdf) for more information on avoiding email scams.
-   Refer to [Avoiding Social Engineering and Phishing Attacks](https://www.cisa.gov/uscert/ncas/tips/ST04-014) for more information on social engineering attacks.

These vulnerabilities are not exploitable remotely.

5\. UPDATE HISTORY
------------------

-   March 18, 2025: Initial Publication

#### [Source](https://www.cisa.gov/news-events/ics-advisories/icsa-25-077-02)

<br/>
---
