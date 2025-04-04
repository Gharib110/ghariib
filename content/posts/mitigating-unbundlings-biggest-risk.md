---
title: "Mitigating Unbundling’s Biggest Risk"
date: 2025-01-07
categories: 
  - "cloud"
  - "cloudnative"
  - "devops"
  - "linux"
---

If you haven’t already read Unbundling the Enterprise: APIs, Optionality, and the Science of Happy Accidents you might want to check that off your to-do list before diving into the deep end of the pool. While we’re about to share the risk that was most frequently mentioned by the interviewees we spoke to, along with the primary tools and concepts for how to mitigate that risk, it may be a bit tough for you to fully understand the details of how the various details work together without having first read the book. Either way, you’re here now, so let’s begin.

## Unbundling’s Impact on Coordination Costs

A significant theme of _Unbundling the Enterprise_ lies in the concept of “prepare early, decide late.” When we advocate for decomposing your capabilities into individually addressable APIs that don’t presume a fixed context, we’re aligning to a strategy where we make the process of adapting to changes in the market easier, and we shift the impact of coordination costs from a primarily variable cost that is incurred with every instance of consumption to one that is primarily fixed and only paid one time.

For example, imagine a restaurant that wants to engage in taking to-go and delivery orders. In a pre-API world, the coordination costs of taking, fulfilling, and then delivering the order are variable costs that are incurred with each and every order given that the orders have to be taken, fulfilled, and then delivered by a human who works for the restaurant. In an API-centric world, a large percentage of the coordination costs are shifted to a single fixed cost that is incurred when the restaurant opens and integrates its order-taking and fulfillment capabilities with third-party specialty firms like Yelp, Doordash, Uber Eats, and Deliveroo. When the restaurant designs its interfaces well, adding or removing ordering and delivery partners is a low-cost endeavor that can be accomplished with low effort.

If you’ve ever had a hand in enabling this type of integrated capability, you’ll know that these two types of coordination costs vary greatly. In a pre-API world, an individual occurrence of a variable coordination cost for a single transaction may be much smaller than the fixed coordination cost that is incurred a single time, but that does not account for the idea that the plan is to have A LOT of transactions.

The difference in the volume of occurrences is the foundation underneath the concept that “Automation doesn’t cost money. It saves money while improving speed and quality.” These financial value concepts are what are behind organizations moving the coordination costs from “multiple occurrences of a lower variable cost” to “a singular occurrence of a fixed cost.”

While it is clear that most businesses like to have a high volume of transactions and as long as that is true, it is only a matter of time before the aggregate occurrences of the smaller variable cost will exceed the singular occurrence of the larger variable cost, there is second and perhaps more impactful factor in the shift: The day-to-day labor savings of individual workers (i.e., a primary component of operational expenses) who no longer have to spend their time on logistics and busy work can transform your enterprises operating model to bring greater focus to building revenue and other important business objectives.

In the context of our restaurant example, the restaurant eliminates a drag on order profitability and the staff can now serve more diners and drive up return visits and check sizes because they’re no longer encumbered by taking phone orders, checking delivery addresses, or managing delivery staff.

While it’s not really possible to drive coordination costs to zero, it is possible to significantly drive coordination costs down through migrating your value exchange activities to digital channels and elevating the use of standardized integrations (i.e., using APIs as a primary channel for value exchange).

As the book closes, we share a model that illustrates how value exchange activities have migrated channels over time from the dawn of the Industrial Revolution (when almost all exchanges were done in person, using fixed physical locations, with an event that is synchronous for all stakeholders) up to present day (where value exchanges are primarily done remotely, with no fixed location, with a series of events that is often asynchronous).

![](https://images.squarespace-cdn.com/content/v1/66100f53281c2570d57743d1/824824ce-402e-4667-8af7-8304f3e804b8/Screenshot+2024-04-18+at+12.42.29%E2%80%AFPM.png)

This migration in channels is primarily instigated by a steep drop in coordination costs that translates to a sustained improvement in operating margins that is accompanied by a decoupling of revenue and labor (i.e., in the new channel, you can earn more revenue without growing your labor as fast as you would have to in the old channel).

## The Risk of Rising Coordination Costs

After you’ve read _Unbundling the Enterprise_, you may notice a few quotes from our interviewees that suggest that “changing APIs is hard and, at times, expensive” (most prominently when we talk with Thor Mitchell about his time at Google in chapter 1 and then again when we talk with Saurabh Sahni about his time with Yahoo! and Slack in chapter 8).

So, which is it? Does an API-driven interaction model make adapting to change easier or does it make digesting change harder? After all, if the prime thesis of the book is that using APIs at scale will make the process of change easier and less expensive, how can it be that many of the most prominent advocates say that “changing APIs is really hard”?

Bad news first. Yep. Changing APIs can be hard (don’t worry too much yet… we’ll show you how to avoid most of the difficulty). To fully understand this issue, let’s jump into our time machine and look at the history of the Twitter API.

In August of 2012, the company formerly known as Twitter made a series of changes to its API that included a set of different rules and mechanisms around authentication, partnering, visualization standards, and rate limiting. While these technical and branding changes are individually interesting in a technical and product strategy context, the details of the changes themselves are not important to understand the risk itself and the financial impacts that come along with it.

The only important factors to understand are that:

- The consumers of Twitter’s API would have to allocate labor and time to make, test, and deploy software changes in the code where they consumed Twitter’s API.

- Twitter has no formal control on those consumers because they’re all external to Twitter.

- If the consumers did not make the required changes by a certain date, the consuming software that called the Twitter API would stop working.

- The consumers of Twitter’s API made a series of negative comments online, complaining about the change.

Even if you’ve never written a line of code, you’ve probably experienced the impact of an API change. More often than not, when an app on your smartphone stops working and notifies you that you must update the app to continue using their service, that is usually the result of an API change that requires a new app (with new consuming code) be installed on your phone. From your perspective, this can be mildly annoying as it interrupts your individual task flow. For a business that was consuming the Twitter API, this “mild annoyance” could have important consequences, as the company might have to rework its roadmaps and commitments to account for this instance of “unplanned work” that has a near-term deadline.

The takeaway: When an API provider makes a change to their service that requires a corresponding change from an API consumer, coordination costs will rise for a period of time as the producer and consumer manage the required change.

The good news in 3 parts:

1. This risk is avoidable in many cases and manageable in all of them.

3. The rise in coordination costs is a fixed moment in time and doesn’t last very long.

5. Engaging with your consumers can be a good thing, even when it’s on a topic that your consumers would rather not deal with.

## Building Your Hedge Against Coordination Costs

Change isn’t a bad thing. APIs change for very good reasons, and there’s no part of the book that attempts to convey the message that changes are bad and you should avoid them. The real goal here is to understand, “How can we plan for changes in a way that has the least impact to us and our consumers?” Successfully architecting your change processes can be complex, but it’s not impossible and it turns out it’s not very expensive either. It just takes some expertise and willingness to articulate and follow a process.

Before we get to the mitigations, we need to be familiar with the two types of API changes:

1. Breaking Changes: In the context of API changes, a change is said to be a “breaking change” when the API change requires a consumer to make changes in their consumption code. If the consumer does not make the required change, the consumer’s code will no longer work correctly and will likely result in predictable errors.

3. Non-Breaking Changes: In the context of API changes, a change is said to be a “non-breaking change” when it does NOT require a consumer to make changes in their consumption code if they don’t want to.

While the definitions above may seem obvious, some people still struggle with the concept of a non-breaking change. To make it clear, here are a few examples of breaking and non-breaking changes.

- Breaking Change: An API supplier makes a change where all API methods now require a new piece of information. When a consumer attempts to use the API method without the information, the API doesn’t know how to handle that and returns an error code.

- Breaking Change: An API supplier makes a change to the names of resources and/or methods. When a consumer attempts to use the API by referencing the old names, the API doesn’t know how to handle that and returns an error code.

- Breaking Change: An API supplier makes a change by removing resources and/or methods they no longer support. When a consumer attempts to use the API by referencing the old resources or methods, the API doesn’t know how to handle that and returns an error code.

- Non-Breaking Change: An API supplier makes a change so that all API methods allow but don’t require _a new piece of information_ to be included. When a consumer attempts to use the API method without the information, the API ignores that it is not present and responds as designed.

- Non-Breaking Change: An API supplier makes a change by adding a new method. When a consumer attempts to use the API but does not use the new method, the API responds as designed because there is no requirement that the consumer call the new method.

- Non-Breaking Change: An API supplier makes a change where an API adds new information in a response. When a consumer uses the API method, the API returns the new information, and the consumer can choose to use it or not. There is no programmatic requirement for the new information to be used, so the consumer code and the API continue to function.

Either type of change to an API will often cause a change in the major/minor version number of the “latest available version” of the API. The guidepost on approaching changes in the context of API products can be made extremely simple: “Avoid breaking changes because they force a consumer to make changes to the code on their end of the solution.”

While having a process for managing how changes impact the version numbers of your APIs is important, that specific process and policy set will not make a major impact on how coordination costs will be incurred and/or absorbed by your delivery and service teams. To impact these types of costs, we have to move up one level and start exploring the big components of your API versioning strategy.

## Versioning Strategy as a Hedge Against Coordination Costs

The basic idea behind a versioning strategy is very simple: “Have a formal process for API changes with regard to making and releasing changes inclusive of communicating these changes to consumers.” The components of this strategy vary across organizations, and most organizations do not necessarily publish and share all the intimate details and internal policies that influence how it all comes together. Aggregated below, is an enumeration of the major components and strategies that will help your organization get a firm grip on how your proposed API changes will impact coordination costs, along with several specific tactics to help you keep these costs low for you and your consumers.

### **Have a supported versions window**.

With scaled usage, having a single version in production is unlikely to be feasible given that all of your API consumers have business priorities of their own. A foundational element of your versioning strategy is to have a published policy for how versions will move through a life cycle window of support (like the one shown below). While the exact number of supported versions can vary, the real point of having this type of framework is that it sets the table for several topics (e.g., “We’re always looking to improve our products, and that means our APIs will change over time”, “When you adopt and consume our APIs, you should have a plan in place to digest changes”, “We won’t cut off consumers at a moment’s notice, but we will expect that our consumers will use the time windows provided to migrate off of versions that are exiting support”, etc.).

![](https://images.squarespace-cdn.com/content/v1/66100f53281c2570d57743d1/a285cf2f-813d-48e2-a633-d7f2e846cea9/Screenshot+2024-04-23+at+3.52.58%E2%80%AFPM.png)

### **Have and adhere to a policy and plan for backward compatibility**.

Having a policy and plan for backward compatibility is one of the most powerful tools for managing coordination costs. In concept, backward compatibility is very simple. To have an API that is “backward compatible” means that a specific API version will work with client software that was designed for the previous version of the API. This ensures that existing users and customers can continue to access the API and its services without disruption or degradation. When creating a policy on backward compatibility, there are some basic guideposts that your delivery teams can follow.

- Avoid removing or renaming existing API endpoints or fields: If an existing endpoint or field needs to be removed or renamed, consider keeping the old endpoint or field for a transition period or providing a new endpoint or field with the new name or functionality. This ensures that existing integrations continue to work without disruption.

- Avoid changing the data type or format of existing fields: If an existing field needs to change its data type or format, consider providing a new field with the new data type or format and keeping the old field for a transition period. This ensures that existing integrations continue to work without requiring significant changes.

### Have and adhere to a policy and plan for forward compatibility.

Having a policy and plan for forward compatibility is a bit more complex than a backward compatibility plan, but maintaining a plan for forward compatibility can deliver impactful (but somewhat invisible) results by avoiding the need for breaking changes. Where “backward compatibility” is a reactive posture that asks delivery teams to tweak their designs in ways that don’t require consumption-code changes, “forward compatibility” is a proactive posture that asks delivery teams to make their designs scalable for future changes. The most pervasive example of forward compatibility is web browser support for HTML. You can see it at work by opening your browser and seeing it function normally for web pages written over a decade ago (try it out now by visiting the world’s very first website made by Sir Tim Berners Lee himself). To maintain forward compatibility, have a set of design standards that encourage:

- Making new fields optional rather than required where new fields are added to the schema, and older consumers can ignore these fields.

- Changing field types to be less constrained by strict data types so older consumers can still read data with compatible types (e.g., changing from an int to long)

- Using enumerations rather than individual parameters given that you can add items to an enumeration without requiring a change in consumption code

- Using patterns like “partial response” to enable new data to be added to a response pattern without making any change to provider or consumer code

### Have and adhere to a structured communications plan.

Now that we’ve covered the prime levers for making changes less impactful to consumers (from a cost perspective), we can shift to messaging and expectations management. Having a structured plan and resource model for staying engaged with your consumer audience will be a significant element in your ability to manage changes and keep your consumers positively engaged with you while you introduce changes that, from their perspective, look and smell like unplanned work. Just like any SaaS company you currently work with, your consumers will expect you to give them insights into:

- Your product roadmap… so they can make plans for changes

- Your support policies (inclusive of “end-of-life/end-of-support” dates)… so they can justify and plan for migrations

### Commit to a DX

Commit to a Developer Experience capability that creates and distributes enablement content, code samples, and migration tools to remove friction from your consumer’s migration path.

## Transcending the Captive Audience Fallacy

Coordination costs resulting from API changes are not exclusive to your digital interactions with external customers. Just because some of your consumers work for the same organization as you do, doesn’t mean they are immune to the cost and impact of changes within your API infrastructure. All of the risk factors and mitigations discussed above, apply to your internal consumers as well. Every internal or external API-consuming organization has a list of priorities and business goals they are working toward, and making code changes for something they think is already working is unlikely to be on that list.

Product, platform, and API owners everywhere have sincere debates on the value of developer productivity, or sometimes regarding the exclusive use of product language for APIs with external audiences. After conducting the multiyear research effort behind _Unbundling the Enterprise_, including both historical industry analysis and interviewing digital leaders from the most successful organizations around the world, we can conclude that these conversations revolve around an assumption that is both obscured and unfortunate – all APIs are classified as exclusively internal or externally available.

The tendency for delivery teams to frame their capabilities as “exclusively for internal use” comes out of a well-meaning desire to conserve costs and time for a business initiative. Despite the good intentions of the cost-conscious scope-cops, this bias toward compression brings its own set of costs that are both visible and quantifiable. While you will have to buy the book to get an in-depth understanding of the financial impacts relevant to API-based optionality, we can give you access to two critical elements that will help you navigate collaborative conversations with your stakeholders:

- **The Happy Accident that is AWS**: When looking at the unparalleled success that is AWS, it is hard not to attribute that success to the brilliance and foresight of Amazon founder Jeff Bezos. Thanks to an altogether different accident (where former Amazon employee Steve Yegge accidentally posted a message to a public channel), we have the good fortune to know there is a bit more to the story. _“Around 2002, Bezos sent a memo to all Amazon employees, according to Yegge’s account. The memo—now often referred to as the “Bezos API Mandate”—was directed at Amazon’s software development teams. It stated that all data and functionality must always and only be exposed via network-based interfaces (such as APIs) designed to be used by developers in the world outside Amazon, and these APIs must be the only interaction point between teams internally. Given that the “Dread Pirate Bezos,” as Yegge referred to him, generally followed up his company edicts with ruthless governance, the organization took note and the platform culture took hold.” – Unbundling the Enterprise_

<figure>

![](https://images.squarespace-cdn.com/content/v1/66100f53281c2570d57743d1/1a85a3c0-8661-41c6-a058-d34ed6a2b521/Screenshot+2024-04-30+at+11.11.16%E2%80%AFAM.png)

<figcaption>

Tenets of the “Bezos Mandate” as recounted by Steve Yegge – Source https://gist.github.com/kislayverma/d48b84db1ac5d737715e8319bd4dd368

</figcaption>

</figure>

Point 5 of this mandate, where Bezos requires all APIs, without exception, to be designed to be “externalizable” without any justification or pre-defined use case is perhaps the most important factor in the emergence and success of the AWS happy accident where Amazon created the IaaS (Infrastructure as a Service) category.

> _“A key distinction in the realm of APIs is that the use of externalized APIs dramatically reduces the effort needed in any future efforts to unbundle or bundle existing offerings. This inverse relationship between the presence of externally available, decomposed capabilities and the cost of introducing new bundled/unbundled offerings is the specific reason that APIs have perhaps the most powerful leverage available in an organization’s attempts to create and conserve optionality.”_
> 
> _—Unbundling the Enterprise_

When Bezos made all teams’ designs include the possibility of external consumption, he created and conserved the option to make any and all of his digital capabilities available for public use. While the community can debate how much Bezos foresaw the possibility of AWS in 2002, what cannot be denied are the financial results of the decision (AWS generated more than $90B in revenue for 2024) or the operating realities regarding how organizations treat deferred risk and balloon payments.

While “operating realities” and “deferred risk” might sound complex, they’re easier to understand with an anecdote that any experienced professional would understand. Imagine asking your organization’s board or senior leadership and asking them to fund a highly expensive and time-consuming recreation of a large section of your infrastructure and capabilities for a possible but unproven opportunity in a category that did not exist.

This counter example shows the crucial impact of Bezos switching the default from “funding for external use cases requires business justification” to “all capabilities must be externalizable”. By making every team accountable for supporting the concept of external users in their delivery, the possibility of creating and releasing the first AWS services became cheap and fast (because product teams did not have to rebuild everything from the ground up or engage in problematic and complex refactoring).

The lesson of AWS emerging from a collection of digital infrastructure-management capabilities isn’t that everyone should compete in the IaaS category. The real lesson to be had here is – Defining a narrow context of use (like “internal only”) scuttles optionality and has a series of other financial and operational tradeoffs that should not be ignored.

- **The Quantified Impacts:** The 2023 research study, “How APIs Create Growth by Inverting the Firm”, by Marshal Van Alstyne, Seth Benzell, and Jonathan Hersh quantified the economic impact of API adoption for organizations:  
      
    _“According to their research, ‘firms adopting public APIs grew an additional 38.7% over sixteen years relative to similar non-adopters.’ The study shows that growth is not limited to a longer time scale, as market value of public firms grew ‘an additional 12.9% versus similar firms two years after \[public API\] adoption.’ The authors use specific analysis to conclude that the relationship between APIs and firm growth is causal, not just correlated. Despite performing similar analysis on organizations using APIs internally, the study finds no statistically significant relationship between internal API adoption and firm performance. The paper is clear in its conclusion: organizations who want to benefit the most from APIs should be focusing on externalizing APIs.”_ —_Unbundling the Enterprise_  
      
    Separate from the causal improvement to financial growth, the study also cites counter-intuitive evidence that organizations with wide use of external APIs have less risk of incidents of breaches by malicious insiders than enterprises who use APIs in an exclusively internalized context. While the reduced risk of breaches might seem surprising at first, it makes complete sense when looking back at the AWS example – When delivery teams are asked, from day one, to secure a digital service and the data it has access to, they have an inherently more secure posture than teams that depend upon other systems/layers/teams to secure their services via obscurity.

## Forewarned Can Be Forearmed If You Choose to Act

Understanding a risk is not the same as mitigating it. The choices made by your organization to acknowledge and act upon the full set of risks that come with an API-driven unbundling initiative will likely make or break the success and sustainability of your program. While this paper covers the most pervasive risk found in our research, _Unbundling the Enterprise_ devotes a complete chapter to identifying and mitigating the most likely and impactful risks to an API-based initiative (including increased performance risk, increased risk to quality issues, misapplying the MVP concept, choosing the wrong interface to control, and several others).

As your enterprise embarks on a journey to create optionality and liberate its capabilities into an API-driven future, preparing yourself for the obstacles on the horizon is the surest way to ensure you’ll reach your planned destination.

The post Mitigating Unbundling’s Biggest Risk appeared first on IT Revolution.

Go to Source
