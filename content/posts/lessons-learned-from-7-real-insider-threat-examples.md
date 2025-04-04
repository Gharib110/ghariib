---
title: "Lessons Learned from 7 Real Insider Threat Examples"
date: 2025-01-06
categories: 
  - "cybersecurity"
  - "cybersecurity-awareness"
  - "security"
  - "security-awareness"
  - "vulnerabilities"
tags: 
  - "data-loss-prevention"
  - "endpoint-monitoring"
  - "insider-threat-prevention"
  - "insider-threats"
  - "use-cases"
---

Organizations must navigate myriad security threats. While many cyber threats come from malicious actors outside the organization, insider threats can be even more devastating to a business. Insider threat prevention should be a top priority for security teams. But what are these cyber attacks, and what do they teach us about how to protect critical assets?

Here, we examine several real-world examples of insider threats at major organizations and what those organizations did to remediate the threat.

## What Is an Insider Threat?

When you think of cyberattacks, your mind may go to external threats like phishing emails and advanced threats like malware or ransomware.

An insider threat, however, is any malicious attack or data breach that occurs due to the actions of someone inside a company or organization. That can mean an employee, a contractor, or someone close to trade secrets or sensitive data.

Many of these are unintentional threats caused by negligent insiders lacking a proper understanding of security controls and organizational policies.

Malicious insider threats are intentional and occur when someone with legitimate access to company systems pursues intellectual property theft, steals company data, or attacks the organization in some other way for personal gain. Other situations involve collusion between internal and external parties or outside hackers who exploit an employee or contractor to access sensitive information or systems.

Although there are many types of insider threats, and each one tends to look slightly different, some general principles and guidelines can help companies establish more robust security policies and mitigate the risk of insider threats.

![teramind free trial](https://www.teramind.co/blog/wp-content/uploads/2024/05/Trial-1024x97.webp)

## 7 Real Insider Attack Examples and Their Consequences

Some prominent insider threats affecting large companies show us how these attacks happen and how they can be avoided or mitigated.

### Proofpoint

Proofpoint bills itself as a leader in data loss prevention. But in 2021, the security company filed a lawsuit against a former executive for stealing confidential sales-enablement data before joining market rival – Abnormal Security. While this may not seem like a malicious activity that actively damaged the company, it still merited legal action because the executive took Proofpoint’s trade secrets directly to a competitor.

The data in question was Proofpoint’s playbook for competing specifically with Abnormal Security’s sales tactics, making it truly valuable only to Abnormal Security. Nonetheless, this is a typical example of an insider incident in which current employees with insider access legitimately infiltrate sensitive systems only to exfiltrate company data illegitimately.

Often, malicious actors do this by using personal devices. In this case, the ex-employee loaded data onto a personal USB drive and walked out the door. Proofpoint’s insider threat software failed to alert admins about suspicious activities, and it was months before Proofpoint’s security realized any theft occurred. With more robust employee monitoring or insider threat software, the data exfiltration may have been caught immediately.

<iframe width="560" height="315" src="https://www.youtube.com/embed/3TWU5aUg-lQ?si=g1Bb2M-XC2xW3Z1F" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

### Coca-Cola

Several years ago, at the Coca-Cola Company, a high-ranking engineer was indicted for taking trade secrets and delivering them to parties associated with Chinese companies and the Chinese government.

In this case, the guilty party was a principal engineer for global research. This role naturally gave the threat actor legitimate access to critical assets and sensitive systems. As such, some security leaders and corporate executives assert that it would have been hard to restrict that person’s access to sensitive data or detect anomalous behavior.

Still, there are things to take away from this insider threat. Rather than limiting access, monitoring how the data is handled and utilizing stricter data controls could have prevented the data exfiltration to which Coca-Cola was a victim.

In this case, it’s also important to note the employee’s access level. The more legitimate access a malicious inside threat actor has, the more damage they can do. User activity monitoring specifically addresses this issue.

Then comes the issue of the format the sensitive data is kept in. Keeping the data in less accessible formats may have made it harder for even a top-level employee to steal it and send it away without being detected. For example, some chemical analyses could have been kept in non-reproducible PDF form, where simple copy-pasting would be more difficult. Some companies also glue USB ports shut to prevent the transfer of files.

### Tesla

Another big insider threat scenario occurred at Elon Musk’s Tesla electric car company, a leader in its field and an enormous brand name in the American stock market. The security incident got a response from the technology mogul himself.

Musk said the hacker caused “quite extensive and damaging sabotage” to the company by exporting large amounts of data, including photo and video assets, and stealing many gigabytes of Tesla data associated with the company’s MOS source code.

One key potential solution to this insider threat involves monitoring each user account and verifying each one independently, even employees with remote access. If the hacker needed several accounts or verification levels to pull off the caper, this analysis may have prevented the plan from working.

Also, logging and monitoring the use of sensitive data or access to sensitive systems in real-time could have caught this cybercrime in action. If human operators had been looking closely at user behavior analytics or entity behavior analytics, they could have been tipped off in several ways: by the abnormal number of accounts created or by timestamps identifying anomalous behavior at unusual times. 

Another example of better Identity and Access Management (IAM) is privilege escalation monitoring, where observers can raise red flags when it looks like someone is doing something above their pay grade.

### Twitter

In the early days of the coronavirus pandemic, Twitter experienced a common insider threat incident.

At the social media giant, three people were charged with using the accounts of a small number of employees to exploit a phone spearfishing attack and hijack the Twitter accounts of some pretty big names, including Jeff Bezos.

The insider threat actors then made these prominent profiles look like the individuals in question were giving away Bitcoin and tied the accounts to a scam. As such, they could collect user data and make off with Bitcoin contributions. Mitigation research revealed that the people involved had access to internal tools and data.

One of the chief takeaways is to protect systems, not just data, from cyberattacks and practice good IAM protocols to prevent employees from stealing corporate data. This includes proper security protocols on social media accounts, cloud services like Amazon Web Services (AWS), and any other corporate software.

The processes through which Twitter accounts get updated would have been a good place to start locking down the access privileges attached to public profile publishing changes. More analysis of user behavior will often turn up abnormalities that can be used to identify suspicious network actions.

### Cisco

In the case of Cisco, an employee was able to delete 456 virtual machines and compromise parts of the company’s WebEx Teams application that handles things like video meetings and file sharing.

The 2018 attack was undertaken by an employee who had already resigned five months before the attack. Using his personal Google Cloud resources, the attacker reportedly gained access to cloud systems through AWS, which affected the parts of Cisco’s virtualization platform that were previously mentioned.

Cisco spokespersons cited a low dwell time for this attack and said the company added safeguards after the fact. However, the attack underscored the need to examine cloud vendors closely and a potential lack of proper vetting for decommissioned employee accounts. Attacks that happen after someone leaves the company can be avoided by correctly cutting digital ties to that company’s infrastructure.

On the VM side, there’s also a company’s capability to handle things like VM sprawl, decommissioning old machines (as well as employees mentioned above), and carefully counting the nodes in a virtualization schema.

### Target

Target’s massive data breach in 2014 garnered international headlines and showed the world how damaging malicious actions can be.

Hackers affected 110 million payment cards and personal records in less than one month.

The attack involved malware on point-of-sale infrastructure that siphoned off 11 GB of shoppers’ financial and identification data.

In Target’s case, the source of the data breach was instructive. According to Computerworld reporting, attackers exploited something very specific – Target’s account with a vendor that provided internet-connected HVAC services.

So, in this case, credentials were abused in remote facilities management. The source of this insider threat showcases how all vendors, even those not directly connected to merchant transactions or internal core services, need to be adequately vetted. It also shows how new markets like facilities management can blossom without appropriate safeguards and controls because companies still need to determine the security end of a new vendor provision.

As part of the company’s response, Target cited updating legitimate access controls and limiting access to parts of the platform – but that was after the data breach occurred, and it was too late!

One aspect of hardening these sensitive systems would be to isolate the vendor’s access to only the parts of the network that deal with facilities management so that somebody in that capacity can’t access the other sensitive data at all. 

The principle of data segmentation can be important here as a safeguard against people coming in from a tangential part of the system and obtaining core data assets. However, good identity and access management work is needed, too, to monitor what contractors and vendors do when they do have access.

### Uber

At the peak of the self-driving car tech race, a Google engineer working for the division that would become Waymo was sentenced to 18 months in prison for theft of trade secrets and intellectual property. The engineer used Waymo’s information to start the trucking company Otto, which he then sold to Uber.

In the Coca-Cola case, the engineer was a high-ranking member of a critical department of the organization. Like in the Proofpoint case, he became an internal threat due to his ambition.

While the tech industry’s cutthroat competition ensures that data theft for sharing with competitors and other insider threats may never be fully eliminated, insider threat software can help remediate these issues.

Google only filed suit after the engineer sold his company to Uber, giving Uber access to trade secrets that the engineer likely used to launch his company. This would suggest that Google was well aware of the insider threat posed by this engineer and pursued legal action only after the illegally taken information fell into the hands of a much more significant competitor.

## Types of Insider Threats

As we have mentioned, the types of insider threats vary depending on how attackers leverage the assistance of someone inside the organization or how motivated they are to act maliciously. Again, some threats are also unintentional.

### Negligent Insiders and Passive Threats

In some cases, the insider threat happens because of something that employees simply failed to do. Somebody should have done better on proactive cybersecurity, ignoring standard practices or neglecting more active systems management. The threat or accident was unintentional.

In these negligence scenarios, no one inside the company is actively rooting for its exposure to malware or other financial or technical risks. Either the attackers are outsiders—they just walked in through an open door because some key security component was missing—or an employee accidentally mishandled data or access privileges. 

It’s possible the company didn’t have effective identity and access management, proper firewalls, event logging, or behavior monitoring, for instance. When a deficiency is apparent, people often categorize the threat as a “negligence-related” problem.

Other insider threats are classic examples of what happens when someone is unhappy with an employer or, in some cases, a previous employer.

In the examples provided, we see employees stealing data or compromising systems of their present or past employers. We also see other cases where the attacker had already left the company before a threat emerged. Bringing company secrets to a competitor is a classic example of an insider threat.

But in these “disgruntled employee” cases, the source of the attack is obvious – a rogue agent who had a reason to target the company did so out of some sense of malice, ambition, or grievance with the company itself.

### Collusion with Third Parties

More malicious threats exist when employees or contractors actively collude with outsiders. They may be promised large sums of money, recruited through the dark web, or somehow enticed to give up access, controls, permissions, or something else. The mastermind may be an outsider, but they get in with an insider’s help.

### Spearphishing

Another category of insider threats has more to do with active work by hackers to seek out attack vectors in any way they can. Often, employees are the weakest link.

Social engineering attacks involve hackers pretending to be someone they’re not, such as a business partner, creating honeypot scenarios to trap unsuspecting users or otherwise tricking someone into giving up privileged access to systems or files.

Spearphishing can happen through email, text messages, over the phone, or some other company platform. In these days of multichannel communications, the attack surface available to spear phishers is wide open. This is why it’s crucial to monitor all corporate communication channels.

However it happens, it can be devastating as an insider threat enabled using trickery—something as old as humanity itself.

### Double Agents

Finally, the most malicious threat actors are ‘moles’ or ‘double agents’ inside the company. It may sound like something from a spy movie, but these are hazardous insider threat incidents.

Procedures like penetration testing and physical site security may be somewhat effective against double agents, but there’s also the need to vet employees and contractors thoroughly. And in the end, if the double agent is good enough, the threat becomes even more challenging to detect, as we saw in the Coca-Cola case above. It can be challenging to know if a most senior and trusted specialist might be willing to sell out secrets. That’s why many security leaders today advocate zero-trust architecture, which requires continuous authentication and validation of users to provide more ironclad protections.

## Possible Consequences of Insider Threats

The above cases show what happens when companies suffer from insider threats. The results can harm a business profoundly in a few different ways. In these examples, each company gained restitution through legal action or remediated the problem before it worsened. Nonetheless, insider threats can have serious consequences.

First, there’s the actual cost of the attack: a widely cited Ponemon study puts the current average cost at $15 million per attack, noting in February of 2022 that the frequency of insider threats has increased 44% since 2020.

There’s also the reality that as the details are made public, the company’s name is splashed across various headlines – and not in a good way. Loss of reputation is one of the major soft costs of successful insider attacks.

Insider threats aren’t common, but they are becoming more so. Any organization must take the proper security measures to prevent insider threats.

### Implement Insider Threat Software

The first step to preventing insider threats is to implement insider threat software. Many tools are available on the market, but Teramind is one of the most robust. Teramind can track both in-office and remote system access, monitor more than 15 communication channels, and leverage advanced security tools like keystroke logging, automated alerts, and remote desktop takeover to help mitigate threats.

With insider threat software like Teramind, you can observe access to critical assets, identify potentially problematic patterns, and know whenever suspicious activities occur. And you can do it all passively, with automated tools that don’t take up valuable human IT or security resources.

![teramind free trial](https://www.teramind.co/blog/wp-content/uploads/2024/05/Trial-1024x97.webp)

### Set Up an Insider Threat Program

Because insider threats come from employees, educating them on company policies and security protocols is crucial to avoid unintentional insider threats and ensure employees understand that the organization is watching for them.

Launching an insider threat program means working with your security team and insider threat software to create observational and mitigation strategies to prevent insider cyber attacks or data breaches. Getting organizational buy-in is essential because sometimes, the best insider threat prevention is simply an employee reporting suspicious behavior.

### Use User Activity Monitoring

User and Entity Behavior Analytics (UEBA) is a security innovation that leverages user behavioral analytics and machine learning to understand employee work patterns and identify potential insider threat indicators. Good insider threat software will utilize UEBA to recognize when someone is illicitly accessing a system or file, exfiltrating large amounts of data, or engaging in other suspicious activities outside the realm of their normal behavior.

### Leverage DLP Tools

As the name suggests, Data Loss Prevention (DLP) tools help organizations avoid data loss. These tools can automate user access policy, analyze data access and usage, and enforce security protocols to help prevent insider threats. While specialty DLP tools are on the market, comprehensive insider threat software like Teramind also includes DLP tools.

## FAQs

**What is the best example of an insider threat?**

One of the best examples of an insider threat is the case of Edward Snowden, a former NSA contractor who leaked classified information in 2013. Snowden exploited his position to gain access to sensitive documents and leaked them to the media, causing significant damage to national security. This example highlights the importance of implementing robust insider threat prevention measures to protect organizations from potential harm.

**What are considered insider threats?**

Insider threats refer to risks that arise within an organization, typically caused by employees or contractors. Examples of insider threats include unauthorized access to sensitive data, data theft, sabotage, and leaks of sensitive information to external parties. Implementing robust insider threat prevention measures is crucial to mitigate these risks and protect organizational security.

**What are 4 examples of accidental threats?**

Four examples of accidental threats include employees unintentionally sending sensitive information to the wrong recipients, accidentally deleting critical data, falling victim to phishing attacks, and accidentally downloading malware onto company devices. These accidental actions can lead to significant security breaches and highlight organizations’ need for comprehensive security training and protocols.

**How many types of insider threats are there?**

The two types of insider threats are malicious and negligent. Malicious insiders intentionally exploit their access and privileges to harm the organization, while negligent insiders unknowingly put sensitive data at risk through careless actions or negligence.

**What is one way you can detect an insider threat?**

One way to detect an insider threat is by leveraging User and Entity Behavior Analytics (UEBA). UEBA can analyze user behavior patterns and identify anomalies such as unauthorized access, unusual data transfers, or suspicious activity, helping organizations detect potential insider threats before they cause harm.

**What is an example of an intentional threat?**

An example of an intentional threat is Chelsea Manning, a former US Army intelligence analyst who leaked classified military documents to WikiLeaks. Manning deliberately accessed and transferred classified information, causing significant harm to national security. This example underscores the importance of implementing robust security measures to detect and mitigate insider threats within organizations.

## Conclusion

Insider threats — intentional and unintentional — are among the most challenging security risks facing organizations today.

How do you stop someone within the organization who wants to cause it harm? How do you keep employees from making mistakes that compromise organizational security? Insider threat prevention is challenging, but protecting company data is vital. Understanding these examples of insider threats gone wrong and implementing the right insider threat prevention program can help your organization avoid the consequences of a successfully executed insider threat.

![teramind free trial](https://www.teramind.co/blog/wp-content/uploads/2024/05/Trial-1024x97.webp)

The post Lessons Learned from 7 Real Insider Threat Examples first appeared on Teramind Blog | Content For Business.

Go to Source
