---
title: "The role of email security in reducing user risk amid rising threats"
date: 2025-01-02
categories: 
  - "general"
---

Phishing remains one of the most dangerous and persistent cyber threats for individuals and organizations. Modern attacks use a growing arsenal of deceptive techniques that bypass traditional secure email gateways (SEGs) and email authentication measures, targeting organizations, employees, and vendors. From business email compromise (BEC) to QR phishing and account takeovers, these threats are designed to exploit weaknesses across multiple communication channels, including email, Slack, Teams, SMS, and cloud drives.

Phishing remains the most popular attack vector for bad actors looking to gain unauthorized access or extract fraudulent payment, and it is estimated that 90% of all attacks start with a phishing email. However, as companies have shifted to using a multitude of apps to support communication and collaboration, attackers too have evolved their approach. Attackers now engage employees across a combination of channels in an attempt to build trust and pivot targeted users to less-secure apps and devices. Cloudflare is uniquely positioned to address this trend thanks to our integrated Zero Trust services, extensive visibility from protecting approximately 20% of all websites, and signals derived from processing billions of email messages a year.

Cloudflare recognizes that combating phishing requires an integrated approach and a more complete view of user-based risk. That’s why we’ve designed our email security solution to protect organizations before, during, and after message delivery, while also extending protection beyond email into the broader security ecosystem. Phishing is no longer just an email problem — it’s a multi-channel, cross-application threat.

## Assessing holistic user risk

When it comes to protecting against user-based threats, Cloudflare employs a platform approach to security. Instead of forcing customers to rely on an array of fragmented tools that create unnecessary complexity and blind spots, we treat email security as part of an overall strategy for assessing and responding to user-related risk. Our email security solution works in tandem with our network solutions so that SOC teams can quickly assert what actions their users are performing outside of email. Given our extensive network visibility, our platform is not limited by API integrations, and can provide SOC teams with the best visibility and protection. This helps SOC teams not only combat phishing, but begin to identify and take action against a wider range of insider threats.

Within a single, unified dashboard, SOC teams can quickly review detailed information regarding the following questions, which we discuss in more detail below: 

1. Who in the organization is being targeted?
    
2. Who are the attackers impersonating?
    
3. What risky behaviors are my users performing?
    

### Who in the organization is being targeted?

![](https://cf-assets.www.cloudflare.com/zkvhlag99gkb/7hCZ0UXnPA7Wx5iBHxkfjE/47a143332f6c22c7e11b568b43dfdd74/BLOG-2645_2.png)

Within the Cloudflare dashboard, SOC teams can view which users are the most targeted. This can help them determine which accounts should be hardened (e.g. MFA enforced), and identify risky users that should be monitored more closely for significant deviations in behavior. One way organizations can use this information is to require high-risk users to connect from a managed device. For instance, if they use Crowdstrike, we can require that these users be on a managed device and force a posture check before letting them access sensitive applications. 

SOC teams can also dive into what types of attacks are hitting their users and at what frequency.

![](https://cf-assets.www.cloudflare.com/zkvhlag99gkb/2nVgW0EXy3qzC2hDBeJRAx/5cf8408ec72339fe8985019629912cbb/BLOG-2645_3.png)

Customers can use these insights to adjust various platform policies, effectively blocking malicious content and securing sensitive resources. Above, we can see that attackers are frequently leveraging links to try to compromise users. Based on the link analysis we are seeing in email, SOC teams can use our gateway to block similar attacks, so that when attackers try to use other communication methods (LinkedIn, Teams, Slack, etc.) users will not be able to interact with those links.

To learn more about stopping these types of multichannel phishing attacks, please see our blog post, _A wild week in phishing, and what it means for you__._

### Who are the attackers impersonating?

![](https://cf-assets.www.cloudflare.com/zkvhlag99gkb/16lvS6lNsi4TuSgtMFqBtk/b093ecb444def1bd06fb84566b5eb05a/BLOG-2645_4.png)

SOC teams can also get visibility into impersonation attempts within their email environment. Customers can see which users are being impersonated the most, and can use this information to build policies within our email security solution and broader set of Zero Trust services.

A list of frequently impersonated users can be added to the impersonation registry, which changes the sensitivity of our models to apply more scrutiny on messages coming from those users. 

Given our unique position as a domain name registrar, customers can also report lookalike domains to Cloudflare for action to be taken against them. This helps prevent attackers from being able to impersonate our customers and negatively impact their reputation. 

Finally, customers can also use our free DMARC management to track who is sending emails on their behalf. This information can be used to update SPF records and get customers to `p=quarantine` or `p=reject` so that their brand is more resistant to being spoofed. 

### What risky behaviors are my users performing?

Cloudflare provides visibility into user actions in several ways. 

Within the email security solution, we can track internal messages and alert if we see any malicious or suspicious behaviors. This can be enhanced with our managed service offering, Phishguard, which can alert admins when they see any type of behavior that indicates fraud (like Business Email Compromise), account takeover, or insider threats.

SOC teams can also take advantage of our CASB solution to view the different actions that users have performed. Actions are labeled with different risk levels to let teams know which findings are critical and require remediation. 

![](https://cf-assets.www.cloudflare.com/zkvhlag99gkb/7aiDl5Qo2PGsGYF7NfYcDT/dc49eb88beffc7b9df099d71244489c9/BLOG-2645_5.png)

Customers are also able to view data loss prevention (DLP) violations that users have incurred to see if there is any unauthorized egress of data. We provide the ability to automatically block this egress based on different policies within our platform, making sure there is no exfiltration of sensitive data.

We also enable organizations to put internal applications behind our Access solution. This prevents any users with improper permissions or a high risk level from accessing critical applications. Our dashboard then provides metrics on these logins to see how many failures we observed, so that SOC teams can investigate the user further. 

![](https://cf-assets.www.cloudflare.com/zkvhlag99gkb/34LnlEK1lkpbeW5mYLSl8m/5d51092b134bfd7e2d6093a04fcfdc60/BLOG-2645_6.png)

These signals feed into our Unified Risk Score, which can be exported if needed to take automated actions within other platforms.

## Increasing SOC productivity

With all of our functionality unified within a single interface and fed by one data lake, we see an increase in SOC productivity because teams no longer have to spend time building rules or flipping between disparate interfaces and workflows. 

### AI-driven email security

Unlike legacy secure email gateways, our email security solution is driven by predictive AI models which eliminate the need for creating and updating rules. These models are also more effective than reactive measures because they are fed by a massive volume of diverse data from across Cloudflare’s network. This means models are trained on emerging threats earlier and can identify new tactics with a higher accuracy than legacy systems. 

### Automated isolation

To further reduce the risk posed by users visiting potentially malicious websites, customers can isolate browser sessions using our natively integrated, clientless remote browser that runs on our global network. Within an isolated browsing session, SOC teams can prohibit various behaviors such as copy/paste, upload/download, keyboard inputs, and more. This decreases the risk of users accessing a website and performing an action which could compromise the organization.

![](https://cf-assets.www.cloudflare.com/zkvhlag99gkb/65YXZvV78mjzNXvV4YLJRD/b0ef76d80edd7769a23d877ffdc25696/BLOG-2645_7.png)

Our browser isolation solution also decreases the time SOC teams need to maintain policies. Rather than adding domains and applications one by one, teams can choose to isolate based on content categories. These categories are based on our threat intelligence, and are constantly updated. This means that as new websites emerge, SOC teams do not have to spend the time to chase down and update the proper policy — rather, it is done automatically. 

![](https://cf-assets.www.cloudflare.com/zkvhlag99gkb/2aCMZRmIRp33YbGTU5Vxt6/44ca92e4e3cde07b1424b9875311dd59/BLOG-2645_8.png)

### Automated blocking

While some websites might require running in an isolated browser to mitigate the risk of users encountering malicious content, others may need to be fully blocked altogether. Customers can use the same process listed above to block any website that could be risky for users based on tags. However, we allow admins to also provide feedback to users to increase awareness. This can be done via a custom block page that allows SOC teams to communicate with users about their risky behaviors, so that they take actions to curb this behavior in the future and alert their SOC teams to attacks that might be occurring. 

## What's on the horizon for 2025

In 2024, our email security team focused on refining the user interface and improving the incident investigation experience. Looking ahead to 2025, we plan to introduce additional capabilities that deepen the integration of our email security solution with our SASE platform, delivering enhanced insight and protection against user-based threats. 

### Configurable browser isolation for email

Our Email Link Isolation feature currently applies to links we consider suspicious. However, we intend to allow customers to add customized configurations to meet their internal policies. This enhancement will provide more granular control over which websites users can access from an email message without using an isolated browser. 

### Outbound DLP for email

We will be releasing an add-in for Microsoft Outlook that will allow customers to use our DLP engine for inspecting outbound email messages. This client-side application enables customers to configure downstream policies that trigger action when a DLP policy is violated, all while minimizing disruption to existing email infrastructure. 

### Expanded user risk scoring

Cloudflare will be increasing the signals that feed into our user risk scores. This will enable SOC teams to create more policies within Cloudflare or to take automated actions externally based on the level of risk observed. 

These are just a few examples of significant releases that will be coming in 2025. Please stay tuned to the Cloudflare blog where we will be announcing these releases as they happen. 

## Try Cloudflare Email Security today

We provide all organizations (whether a Cloudflare customer or not) with free access to our Retro Scan tool, allowing them to use our predictive AI models to scan existing inbox messages. Retro Scan will detect and highlight any threats found, enabling organizations to remediate them directly in their email accounts. With these insights, organizations can implement further controls, either using Cloudflare Email Security or their preferred solution, to prevent similar threats from reaching their inboxes in the future.

Go to Source
