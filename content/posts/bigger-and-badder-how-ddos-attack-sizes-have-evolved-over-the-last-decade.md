---
title: "Bigger and badder: how DDoS attack sizes have evolved over the last decade"
date: 2025-01-02
categories: 
  - "general"
---

Distributed Denial of Service (DDoS) attacks are cyberattacks that aim to overwhelm and disrupt online services, making them inaccessible to users. By leveraging a network of distributed devices, DDoS attacks flood the target system with excessive requests, consuming its bandwidth or exhausting compute resources to the point of failure. These attacks can be highly effective against unprotected sites and relatively inexpensive for attackers to launch. Despite being one of the oldest types of attacks, DDoS attacks remain a constant threat, often targeting well-known or high traffic websites, services, or critical infrastructure. Cloudflare has mitigated over 14.5 million DDoS attacks since the start of 2024 — an average of 2,200 DDoS attacks per hour. (Our DDoS Threat Report for Q3 2024 contains additional related statistics).

If we look at the metrics associated with large attacks mitigated in the last 10 years, does the graph show a steady increase in an exponential curve that keeps getting steeper, especially over the last few years, or is it closer to linear growth? We found that the growth is not linear, but rather is exponential, with the slope dependent on the metric we are looking at.

Why is this question interesting? Simple. The answer to it provides valuable insights into the evolving strategies of attackers, the sophistication of their tools, and the readiness of defense mechanisms. 

As an example, an upward curve of the number of requests per second (rps) suggests that the attackers are changing something on their side that enables them to generate larger volumes of requests. This is an insight that prompts us to investigate more and look at other data to understand if anything new is happening.

For instance, at one of those moments, we looked at the source of the traffic and saw a shift from subscriber/enterprise IP address space (suggesting IoT) to cloud provider IP address space (suggesting VMs), and realized there was a shift in the type and capabilities of devices used by attackers. 

As another example: when the HTTP/2 Rapid Reset attack happened, the record number of requests per second seen at that time suggested that a new technique was being employed by attackers, prompting us to swiftly investigate what was being executed and adapt our defenses.

## Defining individual attacks

Delimiting an individual attack in time is surprisingly blurry. First of all, an attack analysis can provide inconsistent observations at different layers of the OSI model. The footprint seen at all these different layers may tell different stories for the same attack. There are, however, some variables that together can allow us to create a fingerprint and enable us to group a set of events, establishing that they are part of the same individual attack. Examples include: 

- Do we see the same attack vector(s) being used across this set of events?
    
- Are all the attack events focused on the same target(s)?
    
- Do the payloads on events share the same signature? (Specific data payloads or request types unique to certain types of attacks or botnets, like Mirai, which may use distinctive HTTP request headers or packet structures).
    

## DDoS attack sizes 

Before we dive into a growth analysis of DDoS attacks over the last 10 years, let's take a step back and have a look at the metrics typically used to measure them: requests per second (rps), packets per second (pps), and bits per second (bps). Each metric captures a different aspect of the attack's scale and impact.

- **Requests per second (rps)**: Measures the number of HTTP or similar protocol requests made each second. This metric is particularly relevant for application-layer attacks (Layer 7), where the intent is to **overwhelm a specific application or service by overloading its request handling**, and is useful for measuring attacks targeting web servers, APIs, or applications because it reflects the volume of requests, not just raw data transfer.
    
- **Packets per second (pps):** Represents the number of individual packets sent to the target per second, regardless of their size. This metric is critical for network-layer attacks (Layers 3 and 4), where the goal is to **overwhelm network infrastructure by exceeding its packet-processing capacity**. pps measurements are useful for volumetric attacks, identifying a quantity of packets that can impact routers, switches, or firewalls.
    
- **Bits per second (bps):** This measures the total data transferred per second and is especially useful in evaluating network-layer attacks that aim to saturate the bandwidth of the target or its upstream provider. bps is widely used measuring Layer 3 and 4 attacks, such as UDP floods, where the attack intends to clog network bandwidth. This metric is often highlighted for DDoS attacks because high bps values (often measured in gigabits or terabits) signal **bandwidth saturation**, which is a common goal of large-scale DDoS campaigns.
    

## Evolution of DDoS attack sizes over the last decade

So, how have DDoS attack sizes changed in the last decade? During this period, DDoS attacks have grown bigger and stronger, each year having the potential to be more disruptive. 

If we look at the metrics associated with large attacks seen in the last 10 years, does it look like we have a steady increase in an exponential curve that keeps steepening, especially in the last few years, or is it closer to a linear growth? We found that it is exponential, so let’s have a look at the details around why we came to that conclusion.

In this analysis, we used attacks that Google has seen from 2010 until 2022 as a baseline (Figure 1) that we extended with attacks that Cloudflare has seen in 2023 and 2024 (Figure 2). 

Going back in time, early in the 2010s, the largest attacks were measured in the Gigabits per second (Gbps) scale, but these days, it’s all about Terabits per second (Tbps). The number of requests per second (rps) and bits per second (bps) are also significantly higher these days, as we will see.

The historical data from Google shown below in Figure 1 reveals a rising trend in requests per second during DDoS attacks observed between 2010 and 2022, peaking at 6 Million requests per second (Mrps) in 2020. The increase highlights a significant escalation in attack volume across the decade.

![](https://cf-assets.www.cloudflare.com/zkvhlag99gkb/1OLkt2rSuO6OBGH8H1k1o6/d63d32df3f56eab0fe105a00dec45e03/BLOG-2616_2.png)

_Figure 1_. _Largest known DDoS attacks, 2010 - 2022. (__Source: Google__)_ 

Figure 2 (below) provides a view of trends seen across the different metrics. The escalation seen in Google’s statistics is also visible in Cloudflare’s data regarding large mitigated DDoS attacks observed in 2023 and 2024, reaching 201 Mrps (green line) in September 2024. The rate of packets per second (pps) demonstrates (blue line) a slight exponential growth over time, rising from 230 Mpps in 2015 to 2,100 Mpps in 2024, suggesting that attackers are achieving higher throughput. For bits per second (bps), the trend is also exponential and with a steeper upwards curve (red line), building from a 309 Gbps attack in 2013 to a 5.6 Tbps (5,600 Gbps) attack in 2024. 

Over roughly the last decade, attacks driving these metrics have seen significant growth rates:

- Bits per second increased by 20x between 2013 and 2024
    
- Packets per second increased by 10x between 2015 and 2024
    
- Requests per second increased by 70x between 2014 and 2024
    

![](https://cf-assets.www.cloudflare.com/zkvhlag99gkb/38ps28b6t40SAtoQxMp0z1/90d59911b3bcf8b55cf7ac36d56f8a5b/BLOG-2616_3.png)

_Figure 2. Data from Figure 1 extended with large attacks observed by Cloudflare in 2023 and 2024._

The blog posts listed in Table 1 highlight some of the attacks that we observed from 2021 to 2024.

|   **Month**   |   **Attack size**   |   **Blog post**   |
| --- | --- | --- |
|   August 2021   |   17.2 Mrps   |   _Cloudflare thwarts 17.2M rps DDoS attack — the largest ever reported_   |
|   April 2022   |   15 Mrps   |   _Cloudflare blocks 15M rps HTTPS DDoS attack_   |
|   June 2022   |   26 Mrps   |   _Cloudflare mitigates 26 million request per second DDoS attack_   |
|   February 2023   |   71 Mrps   |   _Cloudflare mitigates record-breaking 71 million request-per-second DDoS attack_   |
|   September 2024   |   3.8 Tbps   |   _How Cloudflare auto-mitigated world record 3.8 Tbps DDoS attack_   |
|   October 2024   |   4.2 Tbps   |   _4.2 Tbps of bad packets and a whole lot more: Cloudflare's Q3 DDoS report_    |
|   October 2024   |   5.6 Tbps   |   5.6 Tbps attack   |

**Table 1.** Notable DDoS attacks observed by Cloudflare between 2021 - 2024.

An overview of other selected significant high volume DDoS attacks that have occurred over the last decade, including 2018’s Memcached abuse and 2023’s HTTP/2 “Rapid Reset” attacks, can be found on the Cloudflare Learning Center.

## Attack duration as a metric

Attack duration is not an effective metric to use to qualify attack aggressiveness because establishing a duration of a single attack or campaign is challenging, due to their possible intermittent nature, the potential for a multitude of attack vectors being used at the same time, or how the different defense layers triggered over time. 

The attack patterns can differ considerably, with some consisting of a single large spike, while others featuring multiple tightly grouped spikes, or a continuous load maintained over a period of time, along with other changing characteristics.

## Trend in types of devices used to create attacks

DDoS attacks are increasingly shifting from IoT-based botnets to more powerful VM-based botnets. This change is primarily due to the higher computational and throughput capabilities of cloud-hosted virtual machines, which allow attackers to launch massive attacks with far fewer devices. 

This shift is facilitated by several factors: VM botnets can be easier to establish than IoT botnets, as they don’t necessarily require widespread malware infections, since attackers can deploy them on cloud provider infrastructure anonymously using stolen payment details from data breaches or Magecart attacks.

This trend points to the evolution of DDoS tactics, as attackers exploit both the processing power of VMs and anonymized access to cloud resources, enabling smaller, more efficient botnets capable of launching large-scale attacks without the complexities involved in infecting and managing fleets of IoT devices.

## How does Cloudflare help protect against DDoS attacks?

Cloudflare's Connectivity Cloud, built on our expansive anycast global network, plays a crucial role in defending against DDoS attacks by leveraging automated detection, traffic distribution, and rapid response capabilities. Here’s how it strengthens DDoS protection:

**Automated attack detection and mitigation**: Cloudflare’s DDoS protection relies heavily on automation, using machine learning algorithms to identify suspicious traffic patterns in real time. By automating the detection process, Cloudflare can quickly recognize and block DDoS attacks without requiring manual intervention, which is critical in high-volume attacks that would overwhelm human responders.

**Global traffic distribution with IP anycast**: Cloudflare's network spans over 330 cities worldwide, and DDoS traffic gets distributed across our multiple data centers. IP anycast allows us to distribute traffic across this global network, and this wide distribution helps absorb and mitigate large-scale attacks, as attack traffic is not directed towards a single point, reducing strain on individual servers and networks. 

**Layered defense**: Cloudflare’s Connectivity Cloud offers defense across multiple layers, including network (Layer 3), transport (Layer 4), and application (Layer 7). This layered approach allows for tailored defense strategies depending on the attack type, ensuring that even complex, multi-layered attacks can be mitigated effectively. Learn more about DDoS protection at layers 3, 4, and 7 in our DDoS protection documentation.

**Unmetered DDoS mitigation**: Pioneering this approach since 2017 to ensure Internet security, Cloudflare provides unmetered DDoS protection, meaning customers are protected without worrying about bandwidth or cost limitations during attacks. This approach helps ensure that businesses, regardless of size or budget, can benefit from robust DDoS protection.

Cloudflare’s distributed cloud infrastructure and advanced technology allows us to detect, absorb, and mitigate DDoS attacks in a way that is both scalable and responsive, avoiding downtime and maintaining service reliability, providing a robust solution to tackle the rising intensity and frequency of DDoS attacks compared to traditional options.

Protecting against DDoS attacks is essential for organizations of every size. Although humans initiate these attacks, they’re carried out by bots, so effective defense requires automated tools to counter bot-driven threats. Real-time detection and mitigation should be as automated as possible, since relying solely on human intervention puts defenders at a disadvantage as attackers adapt to new barriers and can change attack vectors, traffic behavior, payload signatures, among others, creating an unpredicted scenario and thus rendering some manual configurations useless. Cloudflare’s automated systems continuously identify and block DDoS attacks on behalf of our customers, enabling tailored protection that meets individual needs.

Our mission is to help build a better Internet, and providing resilience in the face of DDoS threats is a part of accomplishing that mission.

Read more about Cloudflare DDoS protection in our public technical documentation.

Go to Source
