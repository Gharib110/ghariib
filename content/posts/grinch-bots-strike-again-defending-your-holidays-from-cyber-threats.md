---
title: "Grinch Bots strike again: defending your holidays from cyber threats"
date: 2025-01-02
categories: 
  - "general"
---

## Grinch Bots are still stealing Christmas

Back in 2021, we covered the antics of Grinch Bots and how the combination of proposed regulation and technology could prevent these malicious programs from stealing holiday cheer.

Fast-forward to 2024 — the Stop Grinch Bots Act of 2021 has not passed, and bots are more active and powerful than ever, leaving businesses to fend off increasingly sophisticated attacks on their own. During Black Friday 2024, Cloudflare observed:

- **29% of all traffic on Black Friday was Grinch Bots**. Humans still accounted for the majority of all traffic, but bot traffic was up 4x from three years ago in absolute terms. 
    
- **1% of traffic on Black Friday came from AI bots.** The majority of it came from Claude, Meta, and Amazon. 71% of this traffic was given the green light to access the content requested. 
    
- **63% of login attempts across our network on Black Friday were from bots**. While this number is high, it was down a few percentage points compared to a month prior, indicating that more humans accessed their accounts and holiday deals. 
    
- **Human logins on e-commerce sites increased 7-8%** compared to the previous month. 
    

These days, holiday shopping doesn’t start on Black Friday and stop on Cyber Monday. Instead, it stretches through Cyber Week and beyond, including flash sales, pre-orders, and various other promotions. While this provides consumers more opportunities to shop, it also creates more openings for Grinch Bots to wreak havoc.

## Black Friday - Cyber Monday by the numbers

Black Friday and Cyber Monday in 2024 brought record-breaking shopping — and grinching. In addition to looking across our entire network, we also analyzed traffic patterns specifically on a cohort of e-commerce sites. 

Legitimate shoppers flocked to e-commerce sites, with requests reaching an astounding 405 billion on Black Friday, accounting for 81% of the day’s total traffic to e-commerce sites. Retailers reaped the rewards of their deals and advertising, seeing a 50% surge in shoppers week-over-week and a 61% increase compared to the previous month.

Unfortunately, Grinch Bots were equally active. Total e-commerce bot activity surged to 103 billion requests, representing up to 19% of all traffic to e-commerce sites. Nearly one in every five requests to an online store was not a real customer. That’s a lot of resources to waste on bogus traffic. Cyber Week was a battleground, with bots hoarding inventory, exploiting deals, and disrupting genuine shopping experiences.

![](https://cf-assets.www.cloudflare.com/zkvhlag99gkb/6XOfNPFabXiMzIrZrXGES2/9fa1eb6d1ca558ef9f405826999bcea2/image9.png)

The upside, if there is one, is that there was more human activity on e-commerce sites (81%) than observed on our network more broadly (71%). 

## The Grinch Bot’s Modus Operandi

Cloudflare saw 4x more bot requests than what we observed in 2021. Being able to observe and score all this traffic at scale means we can help customers keep the grinches away. We also got to see patterns that help us better identify the concentration of these attacks: 

- 19% of traffic on e-commerce sites was Grinch Bots
    
- 1% of traffic to e-commerce sites was from AI Bots. 
    
- 63% of login attempt requests across our network were from bots 
    
- 22% of bot activity originated from residential proxy networks
    

![](https://cf-assets.www.cloudflare.com/zkvhlag99gkb/6Lo8y9dRRZGKujWxwfxBaf/4be5c93638b3dabe7acc823adac5ed6f/image3.png)

What are all of these bots up to? 

### AI bots

This year marked a breakthrough for AI-driven bots, agents, and models, with their impact spilling into Black Friday. AI bots went from zero to one, now making up 1% of all bot traffic on e-commerce sites. 

AI-driven bots generated 29 billion requests on Black Friday alone, with Meta-external, Claudebot, and Amazonbot leading the pack. Based on their owners, these bots are meant to crawl to augment training data sets for Llama, Claude, and Alexa respectively. 

![](https://cf-assets.www.cloudflare.com/zkvhlag99gkb/6jzXxH2fR5KWRWc252SbNH/ad40f4a4cb8cf1fdc36558dc4324b717/image10.png)

We looked at e-commerce sites specifically to find out if these bots were treating all content equally. While Meta-External and Amazonbot were still in the Top 3 of AI bots reaching e-commerce sites, Bytedance’s Bytespider crawled the most shopping sites.

![](https://cf-assets.www.cloudflare.com/zkvhlag99gkb/6jOsfPtliY01FSNVVgb2bZ/f444cee15d3818d24ef2e3e53731896c/image2.png)

### Account Takeover (ATO) bots

In addition to scraping, crawling, and shopping, bots also targeted customer accounts on Black Friday. We saw 14.1 billion requests from bots to /login endpoints, accounting for 63% of that day’s login attempts. 

While this number seems high, intuitively it makes sense, given that humans don’t log in to accounts every day, but bots definitely try to crack accounts every day. Interestingly, while humans only accounted for 36% of traffic to login pages on Black Friday, this number was **_up 7-8% compared to the prior month_**. This suggests that more shoppers logged in to capitalize on deals and discounts on Black Friday than in preceding weeks. Human logins peaked at around 40% of all traffic to login sites on the Monday before Thanksgiving, and again on Cyber Monday.  

Separately, we also saw a 37% increase in leaked passwords used in login requests compared to the prior month. During Birthday Week, we shared how 65% of internet users are at risk of ATO due to re-use of leaked passwords. This surge, coinciding with heightened human and bot traffic, underscores a troubling pattern: both humans and bots continue to depend on common and compromised passwords, amplifying security risks.

![](https://cf-assets.www.cloudflare.com/zkvhlag99gkb/1DDDcH41X7fhmfk2VdNaNV/de40dce017459752ba366e5fea331377/image7.png)

**Proxy bots:** Regardless of whether they’re crawling your content or hoarding your wares, 22% of bot traffic originated from residential proxy networks. This obfuscation makes these requests look like legitimate customers browsing from their homes rather than large cloud networks. The large pool of IP addresses and the diversity of networks poses a challenge to traditional bot defense mechanisms that rely on IP reputation and rate limiting. 

Moreover, the diversity of IP addresses enables the attackers to rotate through them indefinitely. This shrinks the window of opportunity for bot detection systems to effectively detect and stop the attacks. The use of residential proxies is a trend we have been tracking for months now and Black Friday traffic was within the range we’ve seen throughout this year.

![](https://cf-assets.www.cloudflare.com/zkvhlag99gkb/1Rk3c2sq0kLpl9Y71NdL8K/1186c343f760dda1f64adb4dd8716170/image1.png)

If you’re using Cloudflare’s Bot Management, your site is already protected from these bots since we update our bot score based on these types of network fingerprints. In May 2024, we introduced our latest model optimized for detecting residential proxies. Early results show promising declines in this type of activity, indicating that bot operators may be reducing their reliance on residential proxies. 

## The Christmas “Yule” log: how customers can protect themselves

35% of all traffic on Black Friday was Grinch Bots. To keep Grinch Bots at bay, businesses need year-round bot protection and proactive strategies tailored to the unique challenges of holiday shopping.

Here are 4 yules (aka “rules”) for the season:

**(1) Block bots**: 22% of bot traffic originated from residential proxy networks. Our bot management score automatically adjusts based on these network signals. Use our Bot Score in rules to challenge sensitive actions. 

![](https://cf-assets.www.cloudflare.com/zkvhlag99gkb/3yNb5lIJ0kUuUkwrwRIFV4/21bd315b382663d5601d4629c8bec3a2/image8.png)

**(2) Monitor potential Account Takeover (ATO) attacks**: Bots often test stolen credentials in the months leading up to Cyber Week to refine their strategies. Re-use of stolen credentials makes businesses even more vulnerable. Our account abuse detections help customers monitor login paths for leaked credentials and traffic anomalies.

![](https://cf-assets.www.cloudflare.com/zkvhlag99gkb/20ICo3eYcY6BTdqAJE5Kj9/90b1373280aaeef54dfbed3c41e5ea8c/Screenshot_2024-12-21_at_17.52.17.png)

Check out more examples of related rules you can create.

**(3) Rate limit account and purchase paths:** Apply rate-limiting best practices on critical application paths. These include limiting new account access/creation from previously seen IP addresses, and leveraging other network fingerprints, to help prevent promo code abuse and inventory hoarding, as well as identifying account takeover attempts through the application of detection IDs and leaked credential checks.

**(4) Block AI bots** abusing shopping features to maintain fair access for human users. If you’re using Cloudflare, you can quickly block all AI bots by enabling our automatic AI bot blocking feature.  

![](https://cf-assets.www.cloudflare.com/zkvhlag99gkb/5vfiWs6fEkloTwGblzkltR/53c9a89a323a4bb9107ea8f3e83e9b49/image11.png)

## What to expect in 2025? 

Over the next year, e-commerce sites should expect to see more humans shopping for longer periods. As sale periods lengthen (like they did in 2024) we expect more peaks in human activity on e-commerce sites across November and December. This is great for consumers and great for merchants.

More AI bots and agents will be integrated into e-commerce journeys in 2025. AI bots will not only be crawling sites for training data, but will also integrate into the shopping experience. AI bots did not exist in 2021, but now make up 1% of all bot traffic. This is only the tip of the iceberg and their growth will explode in the next year. We expect this to pose new risks as bots mimic and act on behalf of humans.

More sophisticated automation through network, device, and cookie cycling will also become a bigger threat. Bot operators will continue to employ advanced evasion tactics like rotating devices, IP addresses, and cookies to bypass detection.

Grinch Bots are evolving, and regulation may be slowing, but businesses don’t have to face them alone. We remain resolute in our mission to help build a better Internet ... and holiday shopping experience.

Even though the holiday season is closing out soon, bots are never on vacation. It’s never too late or too early to start protecting your customers and your business from grinches that work all year round.

Wishing you all happy holidays and a bot-free new year!

![](https://cf-assets.www.cloudflare.com/zkvhlag99gkb/1E192osHHmrXszsfbE2fIa/f7d04ea59ef6355eb78fed4e2fa15bd4/image6.png)

Go to Source
