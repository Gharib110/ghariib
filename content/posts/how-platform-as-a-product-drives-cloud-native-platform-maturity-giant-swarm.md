---
title: "How Platform-as-a-Product drives cloud native platform maturity  » Giant Swarm"
date: 2025-01-02
categories: 
  - "general"
---

In the dynamic landscape of cloud native technologies, a standout trend emerges: platform engineering is the new cool kid in class! In the last few months alone, it’s hard to find a CNCF event without a spotlight on platform engineering. Notably, the 2024 KubeCon EU takes it a step further, dedicating a co-located event exclusively to this rising star.

Why the buzz? Simply put, it’s the evolution of the DevOps mindset, now taking center stage to empower countless developer teams. At its core, platform engineering revolves around making developers’ lives significantly easier by bootstrapping development capabilities into a developer platform. Imagine a world where requesting cloud native products doesn’t lead to drowning in a sea of tickets, relying on that one infrastructure guy you know or deciphering the nuances among myriad similar-sounding AWS offerings. No, DevOps is not dead; rather, platform engineering is the formalization of the DevOps mindset, especially driven within large enterprises. Developer platforms reduce the cognitive overload of developer teams while still empowering them with self-service infrastructure.

### Good platforms: Platform-as-a-Product

Sure, having a developer platform is good — but when is a developer platform itself good? The CNCF Platforms Working Group dove into this question and crafted a whitepaper on the subject. It’s not just a guide to what developer platforms are; it also highlights the key attributes of successful platforms and their teams. According to the whitepaper, the number-one quality for a successful platform is treating it as a product. But what does that _really_ mean? 

Let’s take a step back and look at product management, which is essentially all about managing risks. To explain product teams, Teresa Torres introduced the concept of the "Product Trio" in her book Continuous Discovery Habits. This trio comprises a product manager, a designer and at least one engineer. Each role tackles a specific risk: engineers ensure the product can be built (feasibility risk), designers ensure it’s user-friendly (usability risk) and product managers handle the value and viability risk. That last one is crucial – it’s about ensuring the product has enough value for customers that they will actually use it and offers a return on investment to cover its development costs. To address these risks, a product team must understand the needs and pains of their customers and can derive opportunities to further improve their product out of these.

The same applies to platform products. Here the customers are typically internal developers, but still, the product teams need to understand their needs and pains to address the risks for the platform. This can be achieved by using common product management tools and patterns like customer interviews, surveys, prototypes, and others. Platform product teams must evolve the platform based on identified opportunities, similar to any other software product. This task becomes even more critical as platforms abstract highly technical and complex capabilities across various development teams. To provide maximum value without compromising the platform’s viability with too many customizations, platform product teams must find common ground, often following patterns like the "golden path".

In essence, to have a top-notch platform, treating it as a product is non-negotiable. It’s about understanding and addressing the needs of your internal developer customers, continuously evolving the platform based on insights and finding that sweet spot where value meets viability. It’s product management principles in action, tailored for the unique challenges of platform development.

### Where to start: The CNCF Platform Maturity Model

Sure, having a platform as a product is good — but where do we even start? Fortunately, the CNCF Platforms Working Group dove into this question as well and crafted the Platform Engineering Maturity Model. This model serves as a tool guiding platform people on their journey to a successful platform, offering key indicators tied to different platform maturity levels. It helps platform teams identify their current position in the journey and suggests the next steps. The Platform Engineering Maturity Model quotes the fantastic Martin Fowler: "The true outcome of a maturity model assessment isn’t what level you are at but the list of things you need to work on to improve. Your current level is merely a piece of intermediate work in order to determine that list of skills to acquire next."

![Platform Engineering Maturity Model Table](https://www.giantswarm.io/hs-fs/hubfs/Screenshot%202024-07-11%20at%2012.59.25.png?width=2714&height=1172&name=Screenshot%202024-07-11%20at%2012.59.25.png)

The Platform Engineering Maturity Model covers various aspects of platform engineering, neatly organized into four maturity levels. The transition to product management patterns typically occurs during the move from Operational (Level 2) to Scalable (Level 3). Following product management principles, you should always focus on delivering the highest value. So, the starting point is identifying the pain points of your platform and looking at these aspects’ maturity levels.

Struggling with funding for your platform? Craft a roadmap, shift your focus from tools to higher-level capabilities and highlight the value your team delivers. Stuck with a plateau in user adoption? Collect user feedback, share your roadmap and establish open communication channels like office hours or forums. The Platform Engineering Maturity Model provides indicators to assess your current and target states, enabling you to create an actionable roadmap for your platform product.

A crucial point to note is that considering the viability risk of your platform, reaching the highest level in this maturity model might not always be the best investment. Platform engineering’s effectiveness is closely tied to the organizational context. In a scenario with small teams and limited capabilities, the overhead of fully productizing the platform might outweigh the benefits. However, as your platform scales, managing it as a product becomes the optimal choice.

### Conclusion

In the dynamic cloud native landscape, platform engineering emerges as the driving force for developer empowerment. Rooted in the DevOps mindset, it streamlines cloud native operations within large enterprises, offering self-service infrastructure while reducing cognitive load.

Treating platforms as products is paramount. Drawing from product management principles, understanding internal developer needs and utilizing product management tools are key. The CNCF Platform Engineering Maturity Model serves as a strategic guide, helping teams assess their current state, align pain points with maturity levels and refine their platform strategies.

Ultimately, success lies in managing your Platform-as-a-Product. As your platform scales, this approach becomes indispensable for sustained success in cloud native innovation.

This article was originally published on February 26th on Cloud Native Now. 

![](https://track.hubspot.com/__ptq.gif?a=430224&k=14&r=https%3A%2F%2Fwww.giantswarm.io%2Fblog%2Fhow-platform-as-a-product-drives-cloud-native-platform-maturity&bu=https%253A%252F%252Fwww.giantswarm.io%252Fblog&bvt=rss)

Go to Source
