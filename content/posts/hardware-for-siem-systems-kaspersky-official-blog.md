---
title: "Hardware for SIEM systems | Kaspersky official blog"
date: 2025-01-03
categories: 
  - "cybersecurity"
  - "security"
---

What hardware is needed for security information and event management (SIEM) systems?

At some point, the information security department of any large company inevitably begins to consider introducing a SIEM system — or replacing the existing one, and must therefore estimate the budget required for its deployment. But SIEM isn’t a lightweight product that can be deployed within existing infrastructure. Almost all solutions in this category require additional hardware, meaning that equipment must be purchased or rented.

So, for accurate budgeting, it’s necessary to take into account the expected hardware configuration. In this post, we discuss how SIEM hardware requirements change depending on the company’s profile and system’s architecture, and provide rough parameters to help estimate the preliminary cost of such equipment.

## Evaluating the data flow

Essentially, a SIEM system collects event data from internal and external sources and identifies security threats by correlating this data. Therefore, before considering what hardware will be required, it’s essential to first assess the volume of information the system will process and store. To this end, you need to first identify critical risks to the infrastructure, and then determine the data sources that must be analyzed to help detect and address threats related to these risks. These are the data sources to focus on. Such an assessment is necessary not only to determine the required hardware, but also to estimate the cost of licensing. For example, the cost of licensing for our Kaspersky Unified Monitoring and Analysis Platform SIEM system directly depends on the number of events per second (EPS). Another important aspect is to check how the vendor calculates the number of events for licensing. In our case, we take the events per second after filtering and aggregation, calculating the average number of events over the past 24 hours rather than their peak values — but not all vendors follow this approach.

The most common sources include endpoints (Windows events, Sysmon, PowerShell logs, and antivirus logs), network devices (firewalls, IDS/IPS, switches, access points), proxy servers (such as Squid and Cisco WSA), vulnerability scanners, databases, cloud systems (such as AWS CloudTrail or Office 365), and infrastructure management servers (domain controllers, DNS servers, and so on).

As a rule, to form preliminary expectations about the average event flow, the size of the organization can serve as a guide. However, the architectural particularities of specific IT infrastructure can make company size a less decisive parameter.

In general, for small and medium-sized organizations with just one office — or up to several offices with good communication channels among them and IT infrastructure located in a single data center — an average event flow of 5000–10 000 EPS can be expected. For large companies, making an estimate is more challenging: depending on the complexity of the infrastructure and the presence of branches, EPS can range from 50 000 to 200 000 EPS.

## Architectural components of an SIEM system

An SIEM system generally consists of four main components: the management subsystem, event collection subsystem, correlation subsystem, and storage subsystem.

**Core (management subsystem).** You can think of this as the control center of the system. It allows managing the other components, and provides visualization tools for SOC analysts — enabling them to easily configure operational parameters, monitor the SIEM system’s state, and, most importantly, view, analyze, sort and search events, process alerts, and work with incidents. This control center needs to also support log viewing through widgets and dashboards, and enable quick data search and access.

The core is an essential component and can be installed as a single instance or as a cluster to provide a higher level of resilience.

**Event collection subsystem.** As the name suggests, this subsystem collects data from various sources and converts it into a unified format through parsing and normalization. To calculate the required capacity of this subsystem, one must consider both the event flow intensity and the log format in which events arrive from sources.

The server load depends on how the subsystem processes logs. For example, even for structured logs (Key Value, CSV, JSON, XML), you can use either regular expressions (requiring significantly more powerful hardware) or the vendor’s built-in parsers.

**Correlation subsystem.** This subsystem analyzes data collected from logs, identifies sequences described in correlation rule logic, and, if necessary, generates alerts, determines their threat levels, and minimizes false positives. It’s important to remember that the correlator’s load is also determined not only by the event flow but by the number of correlation rules and the methods used to describe detection logic as well.

**Storage subsystem.** An SIEM system must not only analyze but also store data for internal investigations, analytics, visualization and reporting, and in certain industries — for regulatory compliance and retrospective alert analysis. Thus, another critical question at the SIEM system design stage is how long you want to store collected logs. From an analyst’s perspective, the longer the data is stored, the better. However, a longer log retention period increases hardware requirements. A mature SIEM system provides the ability to strike a balance by setting different retention periods for different log types. For example, 30 days for NetFlow logs, 60 days for Windows informational events, 180 days for Windows authentication events, and so on. This allows data to be optimally allocated across available server resources.

It’s also important to understand what volume of data will be stored using hot storage (allowing quick access) and cold storage (suitable for long-term retention). The storage subsystem must offer high performance, scalability, cross-storage search capabilities (both hot and cold), and data viewing options. Additionally, the ability to back up stored data is essential.

## Architectural features of Kaspersky SIEM

So, we’ve laid out the ideal requirements for an SIEM system. It probably won’t surprise you that our Kaspersky Unified Monitoring and Analysis Platform meets these requirements. With its built-in capability to scale for data flows reaching hundreds of thousands of EPS within a single instance, our SIEM system isn’t afraid of high loads. Importantly, it doesn’t need to be split into multiple instances with correlation results reconciled afterwards — unlike many alternative systems.

The event collection subsystem of the Kaspersky Unified Monitoring and Analysis Platform system is equipped with a rich set of parsers optimized for processing logs in each format. Additionally, the multi-threading capabilities of Go mean the event flow can be processed using all available server resources.

The data storage subsystem used in our SIEM system consists of servers that store data, and servers with the clickhouse-keeper role, which manage the cluster (these servers don’t store data themselves but facilitate coordination among instances). For data flows of 20 000 EPS with a relatively low number of search queries, these services can operate on the same servers that store the data. For higher data flows, it’s recommended to separate these services. For instance, they can be deployed on virtual machines (a minimum of one is required, though three are recommended).

The Kaspersky Unified Monitoring and Analysis SIEM storage system is flexible — allowing event flows to be distributed across multiple spaces, and specifying the storage depth for each space. For example, inexpensive disks can be used to create cold storage (where searches are still possible, just slower). This cold storage can house data that is unlikely to require analysis but must be stored due to regulatory requirements. Such information can be moved to cold storage literally the day after it’s collected.

Thus, the data storage approach implemented in our SIEM system enables long-term data retention without exceeding the budget on expensive equipment, thanks to hot and cold storage capabilities.

## SIEM architecture deployment using our SIEM as an example

The Kaspersky Unified Monitoring and Analysis Platform supports multiple deployment options, so it’s important first to determine your organization’s architecture needs. This can be done based on the estimated EPS flow, and the particularities of your company. For simplicity, let’s assume the required data retention period is 30 days.

### Data flow: 5000–10 000 EPS

For a small organization, the SIEM system can be deployed on a single server. For example, our SIEM system supports the All-in-One installation option. In this case, the required server configuration is 16 CPUs, 32GB of RAM, and a 2.5TB of disk space.

### Data flow: 30 000 EPS

For larger organizations, separate servers are needed for each SIEM component. Dedicating a server exclusively for storage ensures that search queries don’t affect the processing of events by the collector and correlator. However, the collector and correlator services can still be deployed together (or separately, if desired). An approximate equipment configuration for this scenario is as follows:

- Core: 10 CPUs, 24GB of RAM, 0.5TB of disk space
- Collector: 8 CPUs, 16GB of RAM, 0.5TB of disk space
- Correlator: 8 CPUs, 32GB of RAM, 0.5TB of disk space
- Storage: 24 CPUs, 64GB of RAM, 14TB of disk space

### Data flow: 50 000–200 000 EPS

For large enterprises, additional factors must be considered when defining the architecture. These include ensuring resilience (as the substantial data-flow increases the risk of failure) and the presence of company divisions (branches). In such cases, more servers may be required to install the SIEM system, as it’s preferable to distribute collector and correlator services across different servers for such high EPS flows.

### Data flow: 200 000 EPS

As EPS flows grow and the infrastructure divides into separate independent units, the amount of equipment required increases accordingly. Additional servers will be needed for collectors, storage, correlators, and keepers. Moreover, in large organizations, data availability requirements may take precedence. In this case, the Kaspersky Unified Monitoring and Analysis Platform storage cluster divides all collected events into shards. Each shard consists of one or more data replicas. And each shard replica is a cluster node, meaning a separate server. To ensure resilience and performance, we recommend deploying the cluster with two replicas per shard. For processing such large EPS volumes, three collector servers may be required, installed in the offices with the highest event flows.

## Kaspersky SIEM in holding companies

In large enterprises, the cost of implementing an SIEM system increases not only with the volume of data, but also depending on the usage profile. For example, in some cases (such as MSP and MSSP environments, as well as large holding companies with multiple subsidiaries or branches), multi-tenancy is required. This means the company needs to maintain multiple “mini-SIEMs”, which operate independently. Our solution enables this through a single installation at the head office, without the need to install separate systems in/at each branch/tenant. This significantly reduces equipment costs.

![SIEM scheme](https://media.kasperskydaily.com/wp-content/uploads/sites/92/2024/12/20142316/SIEM-hardware-1.png)

Let’s imagine either (i) a holding company, (ii) a vertically-integrated enterprise, or (iii) a geographically-distributed corporation with either various independent security teams or a need to isolate data access among branches. The Kaspersky Unified Monitoring and Analysis Platform tenant model allows for segregated access to all resources, events, and third-party integration settings. This means one installation functions as multiple separate SIEM systems. In this case, while each tenant can develop its own content (correlation rules), there’s also the option of distributing a unified set of resources across all divisions. In other words, each division can have its own collectors, correlators, and rules, but the HQ security team can also assign standardized bundles of security content for everyone — ensuring consistent protection across the organization.

![SIEM in holding](https://media.kasperskydaily.com/wp-content/uploads/sites/92/2024/12/20141948/SIEM-hardware-2.png)

Thus, using the Kaspersky Unified Monitoring and Analysis Platform ensures the necessary performance with relatively modest computing resources. In some cases, savings on hardware can reach up to 50%.

For a more accurate understanding of the required resources and implementation costs, we recommend talking with our specialists or integration partners. We (or our partners) can also provide premium support, assist in developing additional integrations (including using API capabilities for connected products), and oversee the deployment of a turnkey solution covering system design, equipment estimation, configuration optimization, and much more. Learn more about our SIEM system, the Kaspersky Unified Monitoring and Analysis Platform, on the official product page.

Go to Source
