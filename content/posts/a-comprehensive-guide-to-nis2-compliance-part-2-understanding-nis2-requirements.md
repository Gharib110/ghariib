---
title: "<div>A comprehensive guide to NIS2 Compliance: Part 2 – Understanding NIS2 requirements</div>"
date: 2025-01-19
---

![](https://res.cloudinary.com/canonical/image/fetch/f_auto,q_auto,fl_sanitize,c_fill,w_720/https://ubuntu.com/wp-content/uploads/3a8a/NIS2-compliance-blog-no-button.png)

In my previous blog, we ran through what NIS2 is and who it applies to. In this second part of the series, I’ll break down the main requirements you’ll find in NIS2 and help translate them into actionable and practical measures you can take to achieve NIS2 compliance. Join me in this post and start understanding what NIS2 is all about.

# **Ok, NIS2 is applicable to you. Now, what do you need to do to achieve NIS2 Compliance?** 

If you are reading this, you probably came to the conclusion that EU NIS2 is applicable to your company. Let’s dig into the requirements and what you need to do to become compliant.

The Directive says that entities must implement cybersecurity risk management measures and that those must be “appropriate and proportionate.” While that might seem a broad requirement that is open to interpretation, there is a list of minimum cybersecurity risk management measures to be implemented. 

Below I’ll discuss them in more detail and  translate them into actionable measures you can implement in your company.

The set of requirements are listed as below:

![](https://res.cloudinary.com/canonical/image/fetch/f_auto,q_auto,fl_sanitize,c_fill,w_3832,h_2184/https://ubuntu.com/wp-content/uploads/cee4/NIS2-blog-post-final-illustrations_1.png)

## **_Information Systems Risk Management_** 

Requirement: Your company should implement a Risk Management program, approved and sponsored by the management body.

Action: Practically speaking, this means having a Risk Policy, a Risk Assessment Process, a Risk Register and document Risk treatment plans. On top of that, there needs to be management/board level approval and oversight of this process, i.e. risks and controls need to be properly monitored and reported.

## **_Incident Handling and Reporting_** 

Requirement: Your company must identify, respond to and communicate incidents to customers and regulators within a strict timeframe.

Action_:_ Practically speaking, this means defining and implementing specific policies, procedures and playbooks which cover the specific timelines and details involved in the NIS2 reporting requirements. Remember: these resources should be used proactively, so people know how to respond before a potential incident occurs. Communicate your policies and procedures, and provide training to relevant personnel beforehand.

## **_Business Continuity_** 

Requirement: Your company must be resilient and ensure proper continuity of operations or service delivery in the case of a security incident or breach.

Action: Practically speaking, this means having procedures such as backup management (execution and integrity testing) and disaster recovery/crisis management plans in place that are tested periodically. This ensures that your company can recover quickly in the case of a disruption event. 

## **_Supply chain security_** 

Requirement: Your company must address the risks posed by  third parties and how they can affect the security of your product or service.

Action: Practically speaking, this means evaluating your critical suppliers and service providers from a security perspective and managing security-related aspects in the relationships between your company and these third-parties (e.g. contract clauses, SLAs for vulnerability reporting and patching).

## **_Security in network and information systems_**  

Requirement: Your company must define the criteria (architecture and control requirements) which your network and information systems must satisfy. This applies regardless of whether you are the developer of those systems, or acquire those systems/services from a third-party.

Action: Practically speaking, this means having a set of defined control and security measures that can be leveled up depending on the criticality of assets. Their criticality is determined by the type of data they hold, their integrity and availability requirements, and other aspects you choose to base your risk-assessment on. Encryption, strong authentication, least privilege principle, access controls, data governance and vulnerability management play an important part here.

## **_Assessment of the effectiveness of cybersecurity risk-management measures_** 

Requirement: Your company should periodically monitor the effectiveness of the controls and risk management measures it has implemented.

_Action:_ Practically speaking, this means defining and monitoring KRIs or KPIs for risks/controls and having periodic audits and/or assessments (internal or external) to identify, report and then remediate any findings.

## **_Cybersecurity Training_** 

Requirement: Your company must train the management body and its personnel on cybersecurity.

Action: Practically speaking, this means delivering annual cyber hygiene training and security awareness – from management/board members to employees. You might also want to consider other specific cybersecurity training for company specific departments or functions such as Secure Development, Secure IT Operations, and Data Handling.

## **_Cryptography_** 

Requirement: Your company must encrypt data, whenever deemed necessary.

Action: Practically speaking, this means having documented policies and procedures regarding the use of cryptography and encryption, and implementing them throughout your company’s systems. To be effective in this, you should take a risk based approach and understand where sensitive, confidential or PII (personally identifiable information) data is collected, processed and stored.  You can then apply measures accordingly.

## **_Human Resources Security and Access Control_** 

Requirement: Your company must have proper measures in place for employee security and ensure control of access to sensitive/confidential data.

Action_:_ Practically speaking, this means having policies and procedures for personnel security and access controls for sensitive/important data. Background checks and confidentiality clauses in contracts are the most common measures related to personnel. From an Access Control perspective, we’d recommend a set of policies and procedures that govern how you grant, revoke and periodically review access, based on least privilege and need to know principles.

## **_Multi-factor authentication and Secure communications_** 

Requirement: Your company must employ multi-factor authentication and secure communications systems, when deemed appropriate.

Action: Practically speaking, this means adding a second factor of authentication, such as TOTP (Authenticator apps, email, SMS), hardware tokens or biometrics to enhance access security and, where applicable, secure voice, video and text communications and emergency communication systems.

**_Note:_**  These are the general guidelines from the Directive, however member states are allowed to be stricter (but no less strict than the Directive itself). Member states may also prescribe the use of specific ICT products and services that have been certified under the regulation or EU certification scheme to the entities under the scope of EU NIS2, to ensure compliance with the cyber risk management measures. Make sure to also understand which member state’s specific transposition of the regulation applies to you.

# **More on Incident Reporting timescales**

With the above said, I want to specifically call out the new Incident Reporting requirements which have become stricter and are now divided into a 3-step process:

![](https://res.cloudinary.com/canonical/image/fetch/f_auto,q_auto,fl_sanitize,c_fill,w_2866,h_1398/https://ubuntu.com/wp-content/uploads/25f8/NIS2-blog-post-final-illustrations_2.png)

Having effective procedures and personnel properly trained will be key to achieving the above. The expected timescales are tight, so we strongly recommend being thorough in your preparations.

With that, it’s time to wrap up the second post of this series. I hope that it helped you understand the requirements and what you need to do to get compliant.  Stay tuned for our third and final post of the series, where I’ll break down how you can set up your roadmap for NIS2 compliance and discuss how you can effectively demonstrate your compliance to the regulation.

**How Canonical can help you with NIS2 cybersecurity compliance**

Canonical is committed to helping organizations become EU NIS2 compliant. We’re committed to delivering trusted open source that enables organizations to put security at the heart of their stack. Through Ubuntu Pro, our comprehensive security and support subscription, organizations can receive up to 12 years of expanded security maintenance for over 36,000 packages, wherever they use Ubuntu in their stack. Ubuntu Pro also includes patching automation and compliance auditing tools like Landscape and Livepatch, as well as access to compliance and hardening features. 

Learn more about Ubuntu Pro by visiting our dedicated page, or get in touch with our team for a conversation about how we can help you meet your needs.

# **Further resources about EU regulations and Compliance**

Thank you for reading! Below you will find more resources on EU Regulations and how to achieve security and compliance using an Infrastructure Hardening approach.

- Read our CISO’s comprehensive overview of the Cyber Resilience Act 
- Watch a webinar about the CRA’s impact on device manufacturers 
- Read  our Infra Hardening whitepaper to understand a little bit more on how to approach hardening.

Go to Source
