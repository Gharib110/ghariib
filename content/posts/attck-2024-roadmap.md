---
title: "<div>ATT&CK 2024 Roadmap</div>"
date: 2025-01-02
categories: 
  - "security"
---

![](https://cdn-images-1.medium.com/max/1024/1*NdNL-P_jvIn29chXCd8RmA.jpeg)

#### Enhancing usability, expanding scope, optimizing defenses

2023 was dynamic year for ATT&CK. We marked a decade of progress since the framework’s inception and achieved some key milestones to make ATT&CK more accessible for a wider community. Our scope (slightly) expanded to encompass activities adjacent to direct Enterprise interactions, such as non-technical, deceptive practices and social engineering techniques (Financial Theft, Impersonation, and Spearphishing Voice). We enhanced detection capabilities with integrated notes, pseudocode from CAR, and BZAR\-based analytics. The ICS matrix welcomed the addition of Assets to enhance inter-sector communication and mapping. We rolled out Mobile-specific data sources, structured detections, and behaviors like smishing, quishing, and vishing. Website navigation was improved, along with a faster Search bar, and updates that hit you faster than you can say “resources/changelog.html”. We also maintained a steady cadence of updates and new content from the ATT&CK team and external contributors.

In October, we successfully held ATT&CKcon 4.0, with new insights shared and realistic applications demonstrated by practitioners. And finally, we kickstarted the ATT&CK Benefactor program.

<figure>

![](https://cdn-images-1.medium.com/max/1024/1*BMDwDsQqdUFRS-B-t7MyTA.jpeg)

<figcaption>

ATT&CKcon 4.0 Themed Snacks

</figcaption>

</figure>

### **2024 Roadmap: Vision & Goals**

Since launching ATT&CK, we’ve been humbled to witness how the community has integrated it across widely varied spheres and around the globe. The vision for ATT&CK has always been to enable the broadest use across the widest spectrum of stakeholders — whether you’re cross-mapping between domains, annotating and developing tailored Navigator layers, or using the framework as a blueprint to build multi-platform threat models. ATT&CK was designed to empower defenders precisely where they need it most. This is the core thesis for ATT&CK, and as its stewards, we’ll continue prioritizing measures that advance a more inclusive, relevant, and actionable framework.

In line with this vision, our 2024 goals are to bolster broader usability and enhance actionable defensive measures for practitioners across every domain. This includes exploring scope adjustments and platform rebalancing, as well as implementing structural modifications with the introduction of ICS sub-techniques. A core focus will be reinforcing defensive mechanisms and optimizing their user-friendliness. We’ll be bridging Linux and macOS information gaps and enhancing prominent adversary representation. The ATT&CK Navigator, Workbench, and website will feature reengineering to improve accessibility and enable swifter ATT&CK Group/Software/Campaign updates. We’ll also be sunsetting the TAXII 2.0 server by December 18 in favor of the upgraded TAXII 2.1 version. Finally, we’ll continue amplifying the key driver behind ATT&CK — community collaboration. This includes hosting ATT&CKcon 5.0 in October, and maintaining support for the European Union (EU) and Asia-Pacific (APAC) ATT&CK Community Workshops.

### **Enterprise | Integrated Defense**

In tune with ATT&CK’s vision, we’re continuously re-evaluating Enterprise’s scope to more accurately reflect the threats faced by real defenders. Matrices and platforms are conceptual schematics, not real-world structures, and we’re assessing realignments, expansions, and refinements of platforms to represent interconnected organizations, the adversaries they encounter, and the reality of defenders. Our goal is to advance a cohesive and integrated framework that provides more functional use cases and empowers users to visualize and create adaptable defenses against cross-platform threats.

**Cloud | Matrix Balance & More Actionability**

Our Cloud goal this year is to enable defenders (both new and seasoned) to better leverage the Cloud matrix for defensive action. This includes focusing on emerging and significant threats to the domain, upgrading Cloud analytics, and optimizing the balance between generalization and detail in the matrix.

With a considerable portion of cloud identities retaining super admin access, and the frequency of identity-related intrusions across the domain, we’ve been reinforcing and creating more detailed techniques for identity-based attacks. We’ll also be diving into the exploitation of Continuous Integration/Continuous Deployment (CI/CD) pipelines and the malicious use of Infrastructure as Code (IaC). Our Cloud analytics effort will elevate your actionability, by outlining the steps to detect specific behaviors, and providing additional context on what to find and collect.

We’ll also be evaluating how to best refine the balance between abstraction and specificity in the matrix. Our exploration will assess if the platforms are broad enough to cover a wide range of cloud environments and threats, yet specific enough to inform defensive actions. This balance is crucial for the matrix to remain practical and useful for defenders operating in diverse cloud environments. Our aim is to make navigating the Cloud matrix more intuitive and enable users to prioritize techniques relevant to their specific platform.

Ready to navigate the Cloud with us? Sail over to #**cloud\_attack**.

**macOS/Linux | Countermeasures for Priv Esc and Defense Evasion**

Our goal for Linux and macOS is to equip practitioners with more robust countermeasures and help bridge the information gap on defending these systems. We’ll continue tracking down in-the-wild adversary behaviors and building more macOS and Linux-only (sub)techniques to optimize defensive arsenals. For Linux we’ll be exploring privilege escalation and defense evasion to better align with in-the-wild adversary activity. On the macOS side, we’ll be strategically bolstering the platform, with a particular emphasis on threats associated with elevated permissions.

If you have intelligence or technique ideas, we would love to collaborate. We rely on the practitioners who work with these systems day-in and day-out to help us identify gaps and provide invaluable insights. Ready to contribute? email us and join our **#****linux\_attack** or **#macos\_attack** slack channel.

### **Defensive Coverage | Upgrading, Converting & Restructuring Defensive Measures**

Our Defensive goal this year is to expand detections and mitigations to help you better optimize your detection engineering — and maybe get a little more actionable. The April release will include both new and updated mitigations that incorporate best practices from contributors, and industry standards meticulously mapped by our defense team.

Over the past few months, we’ve also been examining analytic language approaches. Our aim? Transforming detection logic into formats compatible with different security tools, including more consistent with real-world query languages such as Splunk . This will simplify the process of aligning your SIEM data with ATT&CK detections, making it easier to understand. We’re also incorporating data collection sources for a given detection query. For example, pulling information from Windows Event logs or Sysmon and the associated Event Code. The new analytic style in ATT&CK will overhal the previously used CAR-like pseudocode, and will be the model for future analytics. This will enhance compatibility across various environments and help you hunt threats more efficiently.

Lately, we’ve been prioritizing improving detections under the Execution tactic, where some of the most employed techniques fall. v15 will showcase a subset of these enhanced detections, featuring the trifecta of CAR (Cyber Analytics Repository) pseudocode, BZAR\-based analytics (Bro/Zeek ATT&CK-based Analytics and Reporting) and detection notes.

Gearing up for October, we’ll be completing the enhanced detections for Execution, sculpting out Credential Access detections, exploring the universe of Cloud analytics, and navigating how to restructure our data sources for improved accessibility. This means sprucing up data source definitions and matching them to everyday use cases like sensor mappings. This way, you can more easily identify the tools and events that clue you in on shady activity. Additionally, you can opt for the data sources that best align with your specific needs. The revamp will also include the introduction of STIX IDs for data components, making it more intuitive to reference and integrate data sources.

Join our ranks at **#defensive\_attack** channel.

### **ICS | Subs, Asset Expansion, & Cross-Domain Integration**

ICS is leveling up this year. Our goals include broadening ICS horizons with new asset coverage, exploring platform scope expansion, and continuing our multi-domain integration quest. We’ll also be diving deeper into adversary behaviors with the introduction of sub-techniques. v15 will showcase some of integration efforts, with the release of cross-mapped campaigns. These campaigns track IT to OT attack sequences, helping defenders better understand multi-domain intrusions and informing unified defense strategies across technology environments.

The October release will feature a structural shake-up, with the first tranche of the long-awaited sub-techniques. Like Enterprise and Mobile sub-techniques, ICS subs will break down techniques into more detail. This increased granularity allows defenders to understand the nuances of adversaries’ execution of a given technique, enhancing their ability to detect and mitigate them. The technique restructuring will involve modifying the name and scope of techniques and integrating them more effectively with other domains. This integration will foster a more comprehensive defensive approach on both the right and left of launch. You can expect a subs crosswalk to help you understand our decisions and how things map between deprecated and new techniques.

October will also include some additional treats with Asset coverage expansion, building upon the Asset refactoring in v14. The refactoring strived to provide a clearer picture of the devices, systems, or platforms a specific technique could target and introduced the concept of Related Assets. Related Assets links cross-sector Assets that share similar functions, capabilities, and architectural locations/properties, highlighting that they may also be susceptible to the same techniques. v16 will feature additional Related Assets, as well as more in-depth definitions and refined mappings of technique relationships for different devices and systems. You can start leveraging Assets for your defensive activities by viewing the technique mappings from Asset pages, or by reviewing Asset mappings from a technique page. We’ll also be scouting how to incorporate additional sectors such as such as maritime, rail, and electric.

We welcome input from all sectors on how to improve identification of key assets and any additional adversary behaviors you have observed in the wild. Reach out to us at attack@mitre.org or **#****ics\_attack**

### **Mobile | Detections & Mitigations Optimization + PRE Exploration**

Mobile’s goal is to dial up the pre-and-post-compromise defensive measures this year, with a detections and mitigations upgrade and an exploratory mission into pre-intrusion behaviors for the matrix. We introduced Mobile structured detections in v14 and will continue building out structured detections as well as expanding our mitigations across the matrix. For optimal actionability, we’ll be leveraging the best practices and tangible experiences from the mobile security community.

In the coming months we’ll also be evaluating how to enhance inter-domain connectivity across platforms and exploring integrating proactive tactics into the Mobile matrix. Our goal is to better reflect evolving adversary activity targeting the domain. This research quest will examine adversary actions before attacks, like active and passive Reconnaissance, and acquiring or developing resources for targeting purposes.

Collaboration and knowledge-sharing with the community will to be a driver for Mobile’s development in 2024. In addition to ramping up detections and mitigations, we’re particularly interested in partnering with mobile defenders to examine potential areas where communications platforms or domains could be added into ATT&CK. If you’re interested, connect via attack@mitre.org or join **#****mobile\_attack****.**

### **Software Development | Enhanced Usability & Streamlined Workflows**

Our Software goals this year are to increase usability across ATT&CK Workbench and Navigator, and streamline Groups and Software releases. Adversaries evolve quickly, so we’re optimizing Workbench workflows to harmonize Group and Software releases more closely to their cadence. This includes developing enhanced search capabilities, improving ATT&CK object-collection association, and overhauling the Collection Manager UI for the ATT&CK Workbench. These renovations will fine-tune the approval of ATT&CK object changes and the matching of collection bundle differences with official ATT&CK changelog types, resulting in swifter releases.

For ATT&CK Navigator, we’re refining the user experience, _and_ the experience of anyone reading your reports. We’ll be upgrading SVG export function for sleeker output designs, providing smoother navigation with intuitive export controls, and rolling out an in-website tutorial for mastery of all the key features. We’ll also be updating the official content source to the STIX 2.1 repository — making everything a little more robust and flexible.

Finally, we’re taking our TAXII server to the next level! We’ll be sunsetting the TAXII 2.0 server by December 18, as we transition to the upgraded TAXII 2.1 version. You can access the documentation for TAXII 2.1 server in our GitHub repository. Remember to switch URLs for TAXII 2.1 clients to connect to https://attack-taxii.mitre.org instead of https://cti-taxii.mitre.org. And get ready to experience enhanced features and smoother operations.

### **Cyber Threat Intelligence | More Cybercriminal, Underrepresented Groups**

With CTI, our mission is to better reflect the reality of the threat landscape by infusing more cybercriminal and underreported adversary activity into the framework. By bridging gaps in representation and minimizing those unknowns, we aim to provide defenders with better insights and tools to counter a wider array of threats. A pivotal aspect of this effort includes gap assessments of Groups, Software, and Campaigns. These evaluations will help us pinpoint any disparities between the current content and the reality of adversary activities.

Our releases this year will feature more cybercriminal operations and under-monitored regions, including Latin America, offering a more nuanced understanding of global threats. We’re also collaborating with ATT&CK domain leads to expand coverage of cross-domain intrusions to inform a more unified approach to undermining adversaries.

To join this quest, engage at attack@mitre.org

### **Community Collaboration**

**ATT&CK Community Workshops | Practitioner-led Forums for Activating ATT&CK**

We’re always inspired to see how ATT&CK is being used in innovative ways to upgrade defensive capabilities. The regional ATT&CK community workshops — organized by practitioners, for practitioners — provide forums to share insights, use cases, and collaborative approaches for leveraging ATT&CK.

- The European Union (EU) ATT&CK Community workshop, hosted by the Centre for Cybersecurity Belgium and supported by the Center for Threat-Informed Defense (CTID) was the first regional ATT&CK workshop, The 2024 iteration will take place in Brussels, Belgium on May 17, in-person and virtually.
- The Asia-Pacific (APAC) ATT&CK Community Workshop, hosted by the by the CTID, launches this April 25–26 in Singapore, and virtual attendance is still open. The Workshop will advance threat-informed defense through hands-on training, ATT&CK best practices, worst practices, and moonshot approaches.

**ATT&CKcon 5.0 | Great Speakers, Content, & Conversations around ATT&CK**

**ATT&CKcon 5.0** will be arriving October 22–23, featuring both virtual and in-person attendance from McLean, VA. Stay tuned to our Twitter and LinkedIn channels for updates on our Call for Presentations, which will open in the coming months, followed by our illustrious speaker lineup. If your organization is thinking about joining the ATT&CKcon adventure as a sponsor, please reach out to us at attackcon@mitre.org.

**Benefactor Program | Empowering Defenders, Sustaining Independence**

We want to take a moment to share some insights into the foundational tenants and financial realities of ATT&CK. Much like we crowd-source intelligence and rely on community contributions, ATT&CK itself was built to be independent, responsive, and part of the global community.

From the outset, we deliberately chose not to align ATT&CK with any specific government department or agency. This decision was made to maintain autonomy, flexibility, and to foster collaboration across the broadest spectrum of stakeholders. While this approach has facilitated agility and international partnerships, it also means that ATT&CK lacks a dedicated funding source.

To bridge this funding gap and ensure the continuity of our operations, as well as expanding into new domains, we launched the Benefactor Program last year. This program enables tax-deductible, charitable donations from individuals and organizations who believe in ATT&CK’s mission. These contributions allow us to continue offering free and accessible services while also advancing our capabilities and scope.

We are **immensely grateful** for the support we have received thus far from initial benefactors SOC Prime, Tidal Cyber, and Zimperium. We remain committed to serving the community with transparency; whether you’re a contributor, a fellow defender, or just getting started, we thank you for being part of ATT&CK’s journey.

### **Looking Forward**

Mark your calendars for the v15 release on April 23! You’ll see some novel content interspersed with familiar elements, as well as more practical defensive measures.

As always, we value the opportunity to collaborate with you in ensuring that ATT&CK remains a living framework, where each contribution, conversation, or new implementation fuels its evolution. We look forward to continuing this adventure with you.

Connect with us on email, Twitter, LinkedIn, or Slack.

©2024 The MITRE Corporation. ALL RIGHTS RESERVED. Approved for public release. Distribution unlimited 24–00779–2.

![](https://medium.com/_/stat?event=post.clientViewed&referrerSource=full_rss&postId=8dfc46d1ad1b)

* * *

ATT&CK 2024 Roadmap was originally published in MITRE ATT&CK® on Medium, where people are continuing the conversation by highlighting and responding to this story.

Go to Source
