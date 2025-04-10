---
title: "The Good, the Bad and the Ugly in Cybersecurity – Week 4"
date: 2025-01-25
---

U.S. sanctions DPRK front companies, Click-Fix tactic lures users into running malware, and breach of edutech giant exposes student data.

## The Good | OFAC Sanctions DPRK IT Workers & Attackers Linked to Salt Typhoon Treasury Attack

The U.S. Treasury Department’s OFAC issued back-to-back sanctions this week, aiming to box in North Korean IT workers as well as a Chinese-based actor and firm for their roles in the recent breach of the Treasury’s systems.

Long cautioned by the FBI, “IT warriors” from North Korea pose as U.S. professionals, seeking employment with IT firms to fund the sanctions-riddled regime. The DPRK relies on this network of front companies and individuals to funnel their wages, thus funding the state’s weapons programs and other destabilizing activities. The IT worker scheme has so far produced a stream of revenue worth over $88 million in the last six years.

![](https://www.sentinelone.com/wp-content/uploads/2025/01/DPRK_ITworkers_wanted.jpg)

Sanctioned entities include Korea Osong Shipping Co., Chonsurim Trading Corporation, and Liaoning China Trade, an electronics supplier working with North Korean weapons-traders. The sanctions freeze U.S.-based assets and ban transactions with all listed entities. Currently, the State Department offers up to $5 million for tips on disrupting DPRK-based front companies.

Chinese cybersecurity firm Sichuan Juxinhe and Shanghainese threat actor Yin Kecheng have also been sanctioned for the December attack on Treasury networks and their ties to Salt Typhoon. OFAC states that Yin Kecheng is a notable actor, linked to China’s Ministry of State Security (MSS) and accused of targeting government agencies and critical infrastructure networks. Both the MSS and Sichuan Juxinhe reportedly had direct involvement in the Treasury attack, as well as the exploitation of multiple U.S. telecom giants and internet service providers.

Investigators note that 400 laptops and desktop machines were compromised, allowing access to thousands of sensitive files. The department’s Rewards for Justice program also offers up to $10 million for information that helps identify actors targeting the U.S. government and critical infrastructure.

## The Bad | Fake Accounts on X Use ‘Click-Fix’ Tactic to Lure Users & Deploy Malware

News of Ross Ulbricht’s presidential pardon this week has now become a lure used by threat actors on X to trick unsuspecting users into running a PowerShell code that distributes malware. Discovered by vx-underground, the attack leverages a new variant of the ‘Click-Fix’ tactic that has been popular with cybercriminals this past year.

Threat actors are observed using fake ‘verified’ Ulbricht accounts to direct X users to malicious Telegram channels that claim to be official portals. Once on Telegram, users are presented with a fake identity verification process called ‘Safeguard’, leading them to a Telegram mini-app that copies the PowerShell command to the user’s clipboard. The users are then instructed to paste and run the command in a Windows Run dialog, which triggers a script downloading a ZIP file from `http://openline[.]cyou`.

<figure>

![](https://www.sentinelone.com/wp-content/uploads/2025/01/click_fix_safeguard.jpg)

<figcaption>

Source: BleepingComputer

</figcaption>

</figure>

The ZIP file includes `identity-helper.exe`, suspected to be a Cobalt Strike loader. Though Cobalt Strike is a legitimate penetration testing tool, it is often repurposed by attackers for remote access, data theft, and ransomware deployment. The attack leverages the latest version of the ‘Click-Fix’ tactic, which disguises malware distribution as a verification or troubleshooting process. Language used throughout the attack is noted to be specially crafted to avoid suspicion and prolong the deception.

As a best practice, users are advised to avoid executing commands or scripts copied from unknown sources, especially via PowerShell or Windows Run. Whenever unsure, paste the script into a text editor to inspect it for suspicious or obfuscated code.

## The Ugly | Attack on Educational Tech Provider Exposes 60 Million Student’s Personal Data

The threat actor behind the recent attack on PowerSchool, a cloud-based education technology provider, has claimed they stole the personally identifiable information (PII) of 62.4 million students and 9.5 million teachers across over 6500 U.S and Canadian school districts.

<figure>

![](https://www.sentinelone.com/wp-content/uploads/2025/01/powerschool_news.jpg)

<figcaption>

Source: Wbay.com

</figcaption>

</figure>

The threat actor used stolen credentials to access PowerSchool’s customer support portal and downloaded data from PowerSIS (student information system) databases via a maintenance tool. Investigations report that exposed data from the breach includes Social Security Numbers, medical records, and grades, varying by district. PowerSchool’s FAQ states that it paid a ransom to prevent public data leaks and that the tech solutions provider has not experienced any operational disruptions or seen continued signs of unauthorized activity within PowerSchool environments.

Collected reports allege that the top three affected districts include the Toronto District School Board, Peel District School Board, and Dallas Independent School District by number of students impacted. According to PowerSchool representatives, the type of data exposed in the breach varies by district, following individual district or state policies.

Given the differing policies across those affected, the tech company notes that less than a quarter of impacted students had Social Security Numbers exposed. PowerSchool now provides two years of free identity protection and credit monitoring services for impacted individuals and is notifying stakeholders on customers’ behalf. A public website and updates to a customer-only FAQ are available for ongoing developments.

Educational institutions continue to be a lucrative target for cyberattackers for the wealth of personal, medical, and financial information they hold. Sold often on dark markets and forums, this diversity of data is often exploited later in identity fraud, financial schemes, and instances of blackmailing.

Go to Source
