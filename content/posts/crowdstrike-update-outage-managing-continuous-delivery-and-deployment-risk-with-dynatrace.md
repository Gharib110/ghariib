---
title: "CrowdStrike update outage: Managing continuous delivery and deployment risk with Dynatrace"
date: 2025-01-07
categories: 
  - "ci-cd"
  - "devops"
  - "devops-cloud"
  - "linux"
  - "open-source"
tags: 
  - "application-security"
  - "automationengine"
  - "blue-green-deployment"
  - "canary-release"
  - "continuous-delivery"
  - "site-reliability-guardian"
---

![Site Reliability Guardian, CrowdStrike outage](https://dt-cdn.net/wp-content/uploads/2023/05/b94c1fe7-371e-4894-a3b8-8a96f593307f-300x169.png)

After organizations struggled to recover from the CrowdStrike update outage on their Windows hosts in July, teams are now looking for ways to bolster the resiliency of their software update and continuous delivery practices.

The widespread impact of the CrowdStrike issue demonstrated how critical it is to avoid outages and failures during software deployments to maintain user trust and satisfaction. Traditional deployment techniques that roll out updates or patches directly into full production can present significant risks and lead to potential downtime.

Modern deployment techniques using progressive delivery—such as rolling, blue/green, canary, and feature flagging—offer a more controlled and gradual approach to releasing software. By implementing these strategies, organizations can minimize the impact of potential failures and ensure a smoother transition for users.

Eliminating the potential for outages may not be possible in all situations. That said, a unified observability and security platform such as Dynatrace can enhance modern deployment practices and enable teams to proactively monitor performance, validate changes, and best protect their downstream customers and end users from disruptions.

## Bolster continuous delivery with software development lifecycle integrations

Software testing is critical, yet issues can still make it into production that negatively impact the customer experience. Dynatrace strives to protect its own customers through extensive automated test validation, complemented by staged rollouts to customer segments, which include quick feedback loops to determine whether the software is safe to continue deployments. Customers can adopt many modern and safe continuous delivery practices with Dynatrace in combination with their existing software pipelines.

By embedding Dynatrace observability into their own CI/CD pipeline, customers can prevent issues from ever leaving pre-production environments. This integration enhances the pre-release phase and plays a crucial role in the quick feedback cycle after deployment, allowing teams to identify issues immediately. Furthermore, the Dynatrace Site Reliability Guardian ensures service-level objectives (SLOs) and further validation thresholds are not violated both before and after deployment.

## Progressive delivery methods to release higher-quality software, faster

The following common progressive delivery methods enable organizations to release software in a more controlled manner. 

### Rolling deployments

In a rolling deployment, software is gradually rolled out, replacing previous software in a serial one-by-one fashion or in batch sets. Dynatrace can monitor production environments for performance degradations and outage events that may cause customers to lose access. The Dynatrace AutomationEngine, in conjunction with the existing deployment platforms, enables immediate and automatic software rollbacks to previous versions, limiting the blast radius for customers.

### Blue/green deployments

A blue/green deployment strategy involves selecting a “blue” group to run the new software while the “green” group continues to run the previous version. The Davis AI engine immediately recognizes any anomalies, performance issues, or outages between the two groups. In case there is a degradation of service, Dynatrace picks it up and, embedded by the pipeline, can ensure all customers are rooted back to the proven, stable deployment.

### Canary deployments

The Canary deployment strategy releases software to customers in incremental phases, gradually increasing the production load on the new deployment. Dynatrace enables customers to set quality measures or SLO targets for performance, outages, or other usage metrics to mitigate risk. By integrating AutomationEngine into the pipeline, customers can safely increase or decrease the load on canary deployments.

### Feature flagging

Feature flagging is another popular technique used in progressive delivery that allows teams to roll out new features incrementally and with minimal risk. It supports A/B testing, canary releases, and quick rollbacks, ensuring smoother transitions and more controlled feature releases. The result is testing features in production with specific user segments, gathering feedback and making data-driven decisions on a broader rollout. Embedding feature flags in the codebase can make it easier to control the visibility and behavior of features in real time without redeploying or disrupting an application. This leads to enhanced agility, improves quality, and accelerates time-to-market, all while maintaining a seamless user experience.

As organizations implement progressive delivery strategies to enhance their release processes, integrating automated validation tools such as the Dynatrace Site Reliability Guardian (SRG) becomes essential for further optimizing these practices and ensuring robust performance monitoring

## Site Reliability Guardian and AutomationEngine bolster continuous delivery tools and technologies

**Dynatrace Site Reliability Guardian (**SRG) integrates with continuous deployment practices and platforms to provide the following capabilities:

1. **Automated change impact analysis**: SRG automates analyzing the impact of changes on service availability, performance, and capacity objectives across various systems before a deployment goes live or during any of the deployment strategies.
2. **Integration with CI/CD pipelines:** Teams can integrate SRG into existing delivery pipelines including Jenkins, Github, GitLab, AWS, or Azure pipelines. This integration enables teams to validate releases automatically as part of their software development lifecycle before they are released to customers.
3. **Workflow automation:** AutomationEngine and workflows automate the execution of guardians or problem remediation. This can be tied to specific events such as deployments or configuration changes, allowing for automated validation and response to changes.
4. **Service-level objectives (SLOs):** SLOs enable site reliability engineers (SREs) to manage and track thresholds for critical services. The Davis AI engine proactively monitors these SLOs for degradations and acts before an SLO violation happens.
5. **Automated release validation:** The platform supports automated release validation for security and quality gates to ensure that only high-quality code progresses through the delivery pipeline. This integration reduces the risk of deploying faulty code to production.

## Embed Dynatrace into your release process and gain even more control

The Dynatrace platform is an essential tool for customers deploying software. It provides critical data that enables rapid, fact-based decisions about continuing or rolling back deployments. By offering real-time performance metrics and insights into application health, the Dynatrace platform empowers teams to assess the impact of changes quickly. This capability minimizes downtime and ensures potential issues are addressed before affecting end users, allowing organizations to navigate software deployment complexities and enhance reliability confidently.

## Enhance continuous delivery quality and manage the risk of another CrowdStrike update outage

Incidents like the CrowdStrike update outage illustrate the importance of adopting modern progressive delivery strategies to enhance software reliability and customer satisfaction. By adopting approaches like rolling, blue/green, and canary deployments, teams can mitigate risks associated with large-scale releases and ensure a smoother user experience. Integrating Dynatrace into these processes provides invaluable insights and automated monitoring capabilities, allowing DevOps teams to detect issues early and respond swiftly.

As organizations continue to navigate the complexities of software delivery, prioritizing modern deployment techniques and leveraging robust monitoring solutions will be key to avoiding outages and failures. Embracing these practices will ultimately lead to more resilient applications, happier users, and a stronger competitive edge in the market.

Contact us to learn how you can bolster the resiliency of your progressive delivery techniques with AI-driven automation that can help you avoid the effects of an outage like CrowdStrike.

To learn more about the recent CrowdStrike update outage and explore more resources to help you maintain business resilience, check out the resource center, Business Resilience through CrowdStrike and Beyond.

Learn more

The post CrowdStrike update outage: Managing continuous delivery and deployment risk with Dynatrace appeared first on Dynatrace news.

Go to Source
