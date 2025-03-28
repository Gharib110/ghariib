---
title: "3 priorities for adopting proactive identity and access security in 2025"
date: 2025-02-03
---

If 2024 taught us anything, it’s that a proactive, no-compromises approach to security is essential for 2025 and beyond.

Nation-states and advanced cybercriminals are making significant investments in infrastructure and automation to intensify familiar cyberattack patterns; password attacks, for example, escalated from 579 incidents per second in 20211 to 7,000 in 2024.2 These groups are also adopting emerging technologies such as AI to create deepfakes and personalized spear-phishing campaigns that manipulate people into granting unauthorized access.

Adopting proactive defensive measures is the only way to get ahead of such determined efforts to compromise identities and gain access to your environment.

Microsoft is strengthening our own defenses through the Secure Future Initiative (SFI), a multiyear commitment to advance the way we design, build, test, and operate Microsoft technology to ensure it meets the highest possible standards for security. One of our first steps was to conduct a full inventory of our environment and do a thorough “spring cleaning,” deleting 730,000 outdated and non-compliant apps and removing 5.75 million unused or outdated Microsoft Entra ID systems from production and test areas.3 As part of this process, we deeply examined identity and network access controls, addressed top risks, implemented standard practices, and improved our incident response.

Learn more about the Microsoft Secure Future Initiative

We learned from talking with our largest customers that many are dealing with the exact same issues; they’re also assessing their environments to surface potential vulnerabilities and strengthen their defenses. Based on these learnings and on the evolving behavior of threat actors, we’ve identified three priorities for enhancing identity and access security measures for 2025:

1. Start secure, stay secure, and prepare for new cyberthreats.

4. Extend Zero Trust access controls to all resources.

7. Use generative AI to tip the scales in favor of defenders.

## 1\. Start secure, stay secure, and prepare for new cyberthreats

Many organizations struggle to eliminate technical and security debt while continuing to add new users, resources, and applications. While more of our customers are implementing basic identity security measures, such as multifactor authentication, they may still not enforce them everywhere. Moreover, basic measures aren’t enough to protect against advanced identity attacks such as token theft4 or adversary-in-the-middle phishing.5

It’s essential to understand your entire attack surface, identify all potential entry points, and proactively apply access security that closes any gaps.

Traditional security approaches deploy security tools and measures “as needed.” Unfortunately, the additive approach of starting at 100% open and then dialing up defenses leaves holes that bad actors can exploit and use as launching pads for lateral movement. Reactive security isn’t enough to safeguard your environment. Our guidance for 2025 is to always start at the highest level of security (Secure by Default), then dial back as needed for compatibility or other reasons. It’s also critical to protect _all_ identities: employees, contractors, partners, customers, and, most importantly, machine, service, and AI identities.

Security defaults in Microsoft Entra ID

Learn more

To encourage Secure by Default practices with customers, Microsoft last year mandated the use of multifactor authentication across the Microsoft Azure portal, Microsoft Entra admin center, and Microsoft Intune admin center. To complement security defaults, we started rolling out Microsoft-managed Conditional Access policies for all new tenants to ensure you benefit from baseline risk-based security policies that are pre-configured and turned on by default.6 Tenants that retain security defaults experience 80% fewer compromised accounts than unprotected tenants, while compromise rates have fallen by 20.5% for Microsoft Entra ID Premium tenants with Microsoft-managed policies enabled.6

Outlined below are practical measures that any security leader can implement to improve hygiene and safeguard identities within their organization:

- **Implement multifactor authentication**: Prioritize phishing-resistant authentication methods like passkeys, which are considered the most secure option currently available. Require multifactor authentication for all applications, including private and legacy ones. Also consider using high-assurance credentials like digital employee IDs with facial matching for workflows such as new employee onboarding and password resets.

- **Employ risk-based Conditional Access policies and continuous access evaluation**: Configure strong Conditional Access policies that initiate additional security measures, such as step-up authentication, automatically for high-risk sign-ins. Allow only just-enough access, and ideally just-in-time access, to critical resources. Augment Conditional Access with continuous access evaluation to ensure ongoing access checks and to protect against token theft.

- **Discover and manage shadow IT**: Detect unauthorized apps (also known as shadow IT) and tenants, so you can control access to them. Shadow IT often lacks essential security controls that organizations enforce and manage to prevent compromise. Shadow tenants, often created for development and testing, may lack sufficient security policies and controls. Establish standard processes for creating new tenants that are secure by default and then safely retiring them when they’re no longer needed.

- **Secure access for non-human identities**: Start by taking an inventory of your workload identities. Replace secrets, credentials, certificates, and keys with more secure authentication, such as managed identities for Azure resources. Implement least privilege and just-in-time access coupled with granular Conditional Access policies for workload identities.  

> **To get started**: Explore Microsoft Entra ID capabilities for multifactor authentication, Conditional Access, continuous access evaluation, and Microsoft Entra ID Protection. Confirm that security defaults or Microsoft-managed Conditional Access Policies are enabled on all your tenants and obtain guidance on the phishing-resistant authentication methods available in Microsoft Entra ID, including passkeys. Use Microsoft Defender for Cloud Apps to discover and manage shadow IT in your Microsoft network. Adopt managed identities for Azure and workload identity federation, and strengthen access controls for non-human identities with Microsoft Entra Workload ID.

Try Microsoft Entra ID for free

## 2\. Extend Zero Trust access controls to all resources

It’s essential to have visibility, control, and governance over who and what has access to your environment, what they’re trying to do, and why. The goal is to enable flexible work while protecting against escalating cyberthreats. This requires extending Zero Trust access controls to _every_ resource and entry point, including legacy on-premises applications and services, legacy devices and infrastructure, and any internet destinations. Consider how you can reduce effort and errors using automation, while also making it easier for security teams to share insights and collaborate.

Outlined below are key strategies for extending Zero Trust access controls to all resources.

- **Unify your access policy engines** across all users, applications, endpoints, and networks to simplify your Zero Trust architecture. Converge access policies for identity security tools and network security tools to eliminate coverage gaps and enforce more robust access controls.

- **Extend modern access controls to all apps and internet resources**: Use modern network security tools like Secure Access Service Edge to extend strong authentication, Conditional Access, and continuous access evaluation to legacy on-premises apps, shadow IT apps, and any internet destination. Retire your outdated VPN and configure granular per-app access policies to prevent lateral movement inside your network.

- **Enforce least privilege access**: Automate your identity and access lifecycle to ensure that all users only have necessary access as they join your organization and change jobs, and that their access is revoked as soon as they leave. Use cloud human resources systems as a source of authority in join-move-leave workflows to enforce real-time access changes. Eliminate standing privileges and require just-in-time access for sensitive workloads and data. Regularly review access permissions to help prevent lateral movement in case of a user identity compromise.

> **To get started**: Explore the Microsoft Entra Suite to secure user access and simplify Zero Trust deployments. Use entitlement management and lifecycle workflows to automate identity and access lifecycle processes. Use Microsoft Entra Private Access to replace legacy VPN with modern access controls, and use Microsoft Entra Internet Access to extend Conditional Access and conditional access evaluation to any resource, including shadow IT apps and internet destinations. Use Microsoft Entra Workload ID to secure access for non-human identities.

Explore the Microsoft Zero Trust approach

## 3\. Use generative AI to tip the scales in favor of defenders

Generative AI is indispensable for staying ahead of cyberthreats in 2025. It helps defenders identify policy gaps, detect risks, and automate processes to strengthen security practices and defend against threats. A recent study found that within three months, organizations using Microsoft Security Copilot experienced a 30.13% reduction in average time to resolve security incidents.7 For identity teams, the impact is even more pronounced. IT admins using Copilot in the Microsoft Entra admin center spent 45.41% less time troubleshooting sign-ins, and increased accuracy by 46.88%.8

Outlined below are opportunities available to transform the daily work of identity professionals with generative AI:

- **Enhance risky user investigations**: Investigate identity compromises faster with AI-powered recommendations for proactive mitigation and defense. Use natural language conversations to investigate risky users and to gain insights into elevated risk levels and risky sign-ins.

- **Troubleshoot sign-ins**: Use natural language conversations to uncover root causes of sign-in failures, interruptions, or multifactor authentication prompts. Automate troubleshooting tasks and let AI discover actionable insights across user details, group details, sign-in logs, audit logs, and diagnostic logs.

- **Mitigate app risks**: Use intuitive prompts to manage and remediate application risks as well as gain detailed insights into permissions, workload identities, and cyberthreats.

At Microsoft Ignite 2024, we announced the preview of Security Copilot embedded directly into the Microsoft Entra admin center that included new skills to empower identity professionals and security analysts. We’re committed to enhancing Security Copilot to help identity and network security professionals collaborate effectively, respond more swiftly, and get ahead of emerging threats. We encourage you to participate in shaping these tools as we develop them.

> **To get started**: Learn more about getting started with Microsoft Security Copilot.

Learn more about Microsoft Security Copilot

## Our commitment to supporting proactive security measures

By investing in proactive measures in 2025, you can significantly improve your security hygiene and operational resilience. To help you strengthen your defenses, we’re committed to innovating ahead of malicious actors, simplifying security to reduce the burden on security teams, and sharing everything we learn from protecting Microsoft and our customers.

To learn more about Microsoft Security solutions, visit our website. Bookmark the Security blog to keep up with our expert coverage on security matters. Also, follow us on LinkedIn (Microsoft Security) and X (@MSFTSecurity) for the latest news and updates on cybersecurity.

* * *

1The passwordless future is here for your Microsoft account, Vasu Jakkal. September 15, 2021.

2Microsoft Digital Defense Report 2024.

3Secure Future Initiative: September 2024 Progress Report, Microsoft.

4How to break the token theft cyber-attack chain, Alex Weinert. June 20, 2024.

5Defeating Adversary-in-the-Middle phishing attacks, Alex Weinert. November 18, 2024.

6Automatic Conditional Access policies in Microsoft Entra streamline identity protection, Alex Weinert. November 3, 2023.

7Generative AI and Security Operations Center Productivity: Evidence from Live Operations, Microsoft. November 2024.

8Randomized Controlled Trials for Security Copilot for IT Administrators, Microsoft. November 2024.

The post 3 priorities for adopting proactive identity and access security in 2025 appeared first on Microsoft Security Blog.

Go to Source
