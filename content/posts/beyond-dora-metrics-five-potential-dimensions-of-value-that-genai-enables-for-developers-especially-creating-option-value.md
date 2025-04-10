---
title: "Beyond DORA Metrics: Five Potential Dimensions Of Value That GenAI Enables for Developers — Especially Creating Option Value!"
date: 2025-01-10
categories: 
  - "cloud"
  - "cloudnative"
  - "devops"
  - "linux"
---

Over the past decade, the DORA metrics have been instrumental in measuring developer productivity and software delivery performance — my collaboration with Dr. Nicole Forsgren and Jez Humble from 2013 to 2019 remains one of the things I’m most professionally proud of in my career.

I’ve been working with Steve Yegge (Yes, that Steve Yegge, famous for his work at Amazon, Google, and his depiction of the famous Jeff Bezos “thou shalt communicate only by APIs” memo) and a group of amazing group of researchers and practitioners who are seeking to quantify the value of GenAI for developers. I’m excited that this could potentially build upon the amazing DORA work that continues at Google (hello, Nathen Harvey and Dr. Derek DeBellis!)

The latest 2024 DORA report had one intriguing anomaly — they found that the more teams used GenAI, the worse stability and throughput became. A genuinely surprising anomaly!

Explaining anomalies is often the source of huge scientific breakthroughs and better understanding reality. For instance, the precession of Mercury’s orbit revealed the true nature of gravity (1915), bent starlight during an eclipse validated Einstein’s theories (1919).

Over the last year, I’ve been extensively using GenAI and coding assistants while building a “writer’s workbench.” Not only has this been incredibly fun, coding assistants are helping me:

- build the things I want faster

- be more ambitious about things I can build

- be able to build them alone (as opposed to requiring other people or a team)

- and have so much more fun doing it

- more swings at bat, explore more options

This has led to me to believe that the DORA GenAI metric anomaly is telling us that we need to expand our field of view beyond “code committed to running in production” to more fully include the product exploration, design, and development process.

Specifically, my experiences with GenAI coding assistants over the past year suggest that we need to capture an entirely new dimension of value creation, especially around creating option value.

But in the meantime, I want to briefly discuss each of these dimensions, and give a primer on option value:

- A primer on option value

- The link between option value and modularity

- Case studies of modularity creating 25x more option value in the IBM System/360 project, and something similar happening at Amazon e-commerce in the early 2000s, when they transformed their monolith into microservices

- Some thought experiments to demonstrate option value (and linking it to A/B testing)

## 1\. Build Things Faster

Writing code faster is most probably the most talked about benefit of coding assistants (e.g., GitHub Copilot, Cursor, and the one I use most, which is Sourcegraph Cody). However, I think this metric is probably one of the most superficial benefits.

Make no mistake, with coding assistants, I’m able to build things in hours that would have otherwise taken me days.

The first working version of code that generates the video excerpts of my favorite parts of videos/podcasts was written in about 2 hours, in one pair programming session with the incredible Steve Yegge.

It was a mind-expanding experience of using “chat-oriented programming” — my big lesson was: **type less, lean on LLMs more.**

(And of course, afterward, I’ve spent hours and hours improving that code and adding functionality. But without a coding assistant, it would have taken me days… This level of effort was high enough that building it was something for “maybe next month.” More on this later.)

I can say with some confidence that 80-90% of the time, coding assistants make coding faster and easier.

(But let’s be honest: 10% of the time, coding assistants and LLMs make things maddeningly slower and more frustrating. Like last Friday when every LLM was telling me that you could put any DOM element into the Slate.js editor DOM. After reading the documentation, I know now that is absolutely false.

…or when I spent hours going around in circles trying to get ffmpeg to put captions and a static image in the center of a video file… These things happen, and woe be to those who always blindly follow what the LLM tells you to do. Madness awaits.)

That notwithstanding, here’s my new reality: if I want to do coding, and my coding assistant or LLM isn’t available (like on a transoceanic flight), I’ll choose not to code… because it’s just too difficult without it.

(Another “let’s be honest” qualification: development is more than just “writing code” — a developer probably only spends 25% of the time writing code, spending twice that reading code. And in many organisations, development is only 15% of the total wall-clock time to get features to users.)

In other words, who wants to write code by hand, like some savage from 2010?

By the way, prototyping an app using Claude Artifacts is still the most amazing thing ever. (e.g., “build me a React app with three columns: editor on left, 3 buttons in the middle, and editor on the right.” 4 minutes later, you have a working prototype app. Who could possibly go back to the old way of doing this?)

(Another “let’s be honest” qualification: development is more than just “writing code” — a developer probably only spends 25% of the time writing code, spending twice that reading code. And in many organisations, development is only 15% of the total wall-clock time to get features to users.)  

## 2\. Tackle More Ambitious and Impactful Projects

Recall how my first working version of my video excerpt tool took two hours, which before would have taken me days — because of the time required, I had deferred even trying. It was always a “maybe next month.”

There could have been many reasons: maybe the perceived benefit wasn’t high enough to warrant the work, or maybe the difficulty made the “juice not worth the squeeze,” or perhaps another opportunity offered a higher, more immediate payoff.

Last month, I learned some amazing terms from labor economics to frame the importance of this from Dr. Joe Davis, Chief Economist of Vanguard ($9.5T assets under management):

- Substitutes: Two types of labor (or labor and technology) are substitutes if one can replace the other without significantly reducing output. For example, skilled workers and automated machinery might be substitutes. When the cost of one falls, the demand for the other may drop, possibly leading to job displacement.

- Complements: Two types of labor (or labor and technology) are complements if they are more productive together. For example, human workers and specialized software often complement each other, enhancing productivity when used in tandem. Higher demand for one usually boosts demand for the other.

(You can watch the entirety of my conversation with Dr. Joe Davis here. Just register with an email address.)

Returning to the example of my video excerpt creator, because coding assistants are such an effective complement to my own abilities, I was able to do the work I’d otherwise would not have done.

In other words, coding assistants are complements (especially for senior developers), not merely substitutes. They enable the creation of significant value that wouldn’t have been possible otherwise, as many projects would have been too difficult, costly, or time-consuming to undertake without them.

I’ve experienced this many times over the last few weeks as I’ve built out my writer’s workbench tool, of which the video excerpt creator is a part of. For instance:

- swapping out the standard HTML textarea editor with Slate.js React editor component, so I could introduce more editor controls. I’ve used React component a handful of times, but my lack of experience/knowledge with React, JavaScript and ClojureScript interop, and heck, JavaScript in general, would have guaranteed eventual defeat.

- (3-4 years ago, I put a React tree control in an app I wrote, which is still only half-working — but it’s working well enough for me to use, but I gave up trying to fix it years ago.)

- Heck, I’m finding that front-end app development is now sufficiently within reach for me. Even as a novice, having learned Tailwind and with the help from coding assistants, I’m building tools for myself that I’m using every day.

There are all tasks that would have been out of reach for me, and yet are things I’m tackling every week. Which brings us to the next important dimension…

## 3\. Ability To Build Do Things Yourself

One of the most fantastic things that happened after Steve Yegge wrote his “Death of the Junior Developer” post was that Dr. Matt Beane reached out to me. He introduced me to his research on the “novices optional” phenomenon, which he has studied for over 15 years.

Dr. Beane described how, for centuries, medical surgery has required multiple people because you need at least three hands to perform the needed work. This made novice surgeons an essential part of the team, which also provided them a way to learn.

However, with the advent of surgical robots, expert surgeons can now complete their surgical procedures alone. To be clear, they still need the anesthesiologist and the other support staff, but they no longer need a novice surgeon to help them.

The result is that most novice surgeons are deprived of the time and experience they need to become proficient. So how do they eventually become senior surgeons?

(Economic reasons reinforce this outcome, too. Novices not only take significantly more time to complete surgeries (time is money), but novices also make more mistakes (not great for anyone)).

What does this have to do with software development? A lot! Coding assistants allow experienced developers to avoid entirely the high costs of coordination, enabling them to build things themselves, just as surgical robots did for surgeons.

In his article, Yegge wrote about how his then Head of AI showed him a multi-class prediction model that he had trained and deployed in a single day with the help from a coding assistant. What is remarkable is that last year, creating this tool would have been a 6-week university senior-level intern project.

This story and Dr. Beane’s work suggests that, across almost every domain, the cost of coordination is so large that when given the opportunity for an expert to do something themselves, they will.

(It just occurred to me this fact is deeply ingrained in the DevOps community: “self-service” is so important because we know that task queues are very dangerous. Too often, assigned tickets will often not be completed in the time and level of quality expected. That’s even if a task requires opening one ticket, let alone opening twenty different tickets with twenty different departments. It is almost always better to enable the person to get what they need on-demand.)

Indeed, this is one of my key learnings working with Dr. Steven Spear over the last four years: “Leaders massively underestimate the difficulty of synchronizing disparate functional specialties toward a common purpose.” (from the preface of “Wiring the Winning Organization.”)

(One last somewhat tangential thought: Yegge’s Head of AI story illustrates coding assistants being a complement for seniors, but a potential substitute for a junior intern.)

## 4\. Have More Fun Doing The Work

I’ve talked about how coding assistants have enabled me to do work faster, do more ambitious and more impactful things, and increase the likelihood of being able to do something entirely on my own (which obviates entirely the cost of coordination).

But there’s another thing: when using coding assistants, the work is more fun.

For this, I’m going to cite my friend and co-conspirator from the State of DevOps Research (or DORA: DevOps Research and Assessment), Dr. Nicole Forsgren on the fantastic work she did with her colleagues on the SPACE framework metrics, as published in her ACM Queue article (citation at bottom).

To me, these metrics speak volumes about how much coding assistants changed how I feel about coding — I’ve picked a couple that seem relevant, and I know there are others that are as good, or even better:

(Satisfaction and Well-Being)

- I felt fulfilled while completing the programming task.

- I found myself frustrated while completing the programming task.

- The code I wrote was of high quality.

- I enjoyed completing this task.

(Effectiveness and Flow)

- I was focused on the task during the programming session.

- I was a productive programmer while completing the task.

- I made fast progress despite working with an unfamiliar system.

- I maintained a state of flow during the programming task.

- I completed the repetitive programming activities fast during the task.

(Communication and Collaboration)

- I spent considerable time searching for information or examples during the task.

So, if I were to score myself on the criteria above, it is clear: when I’m working with a coding assistant, the work is more fun, and I’m happier with the quality of what I’ve built. I’m happier!

(I’ve already mentioned that I don’t want to do coding without a coding assistant!)

And for non-solo projects, when developers are happier, there’s ample evidence that they do better work, and you have better retention, and it’s easier to recruit.

Citation: The SPACE of Developer Productivity

## 5\. One More Thing: Explore More Options

During the six years I was involved with the DORA State of DevOps research, we focused primarily on the “code committed” to “running successfully in production” portion of the technology value stream — this is indicated in the right-hand portion of the table below. This is the boundary of where Dev and Ops had to work together to create value for the customer.

This brought in the processes of code integration, testing, and deployment, as well as a bunch of other necessary activities that we explored over the years (e.g., environment creation, test data management, etc.).

![](https://itrevolution.com/wp-content/uploads/2025/01/Screenshot-by-Dropbox-Capture-1024x575.png)

All my excitement with coding assistants makes me super excited to explore how it could help with processes of ideation and discovery, research, design, development, and testing. (And while I’m thinking about it, infosec, architecture, and all that, too). After all, this is the area where the real value-creating activities take place.

One of the things that excites me is how coding assistants make ideation and research both easier and faster. The result is that it vastly increases the number of options we can evaluate, which vastly increases the design space we can explore.

I’ve written about the astonishing results of “coding with ChatGPT voice code while walking the dog,” as recommended by Simon Willison.

My opening question was:

“Hello! I’m trying to build a ‘writer’s workbench’ in ClojureScript. I want to integrate a text editor that allows you to edit text, but where I can select text and send it to an LLM for tasks like clarifying, extracting facts, or even suggesting rewrites. For example, in non-fiction, it might help rewrite for ‘showing, not telling.’

“Rather than the usual triple-click to select a paragraph and then clicking a button, I’d like to explore options that go beyond the standard text area. Specifically, I’d love to be able to associate buttons directly with sentences or phrases, so instead of dragging to select text, I could just click on a sentence or outline it visually to interact. What are tools or libraries in the React ecosystem that support this kind of interaction?”

Over the next 60 minutes, I asked it increasingly detailed questions, learning about the options, what factors were important to me, I asked it to write code using the three libraries it suggested (even though I couldn’t read it).

- What options are available for integrating buttons or interactive elements within a text editor in the React ecosystem?

- Can you provide simple examples for setting up interactive features in Slate.js, Draft.js, and ProseMirror?

- What does the JSON structure of a simple Slate.js editor look like?

- Could a simpler JSON structure work for a text editor, where formatting is only applied at the paragraph level?

- Let’s think about the ouliner use case: describe how I could move an item up or down, or promote it to a parent level, in a nested vector structure in Clojure?

That was amazing! By the end of the 45 minute walk, I had confidence that I had a promising option to explore using, and I was ready to try writing a trivial Slate.js application. And that conversation averted lots of risk by talking through the various scenarios, and eliminating less promising possibilities.

So what is that value of this? Option theory gives us a fantastic language for describing this! (Thank you ChatGPT.)

The design process is very similar to concept of “real options” in finance. Each option gives you the flexibility to explore a path without committing upfront. Coding assistants function similarly to these options, giving you previews of multiple paths so you can make smarter decisions before investing significant time or resources.

- Make It Cheaper and Faster to Explore Options: Normally, testing multiple solutions requires a lot of time. Coding assistants lower the “price” of exploring each path, so you can evaluate multiple approaches without the usual trade-offs. This is like having the freedom to explore new markets or projects cheaply before committing capital. (Think of the quote: “let a thousand flowers bloom.”)

- Able to Change Your Mind (and Avoid “One-Way Doors”): With coding assistants, you’re not locked into one approach early on. You can gather insights on a range of possibilities—Slate.js vs. Draft.js vs. ProseMirror. In options theory, this flexibility reduces the risk of sunk costs if a particular approach proves bad.

- Explore More of the Possible Design Space: Coding assistants also expand what you’re able to explore. You can quickly learn new libraries, tools, or frameworks that might have been daunting on your own. This is like gaining access to new, potentially profitable opportunities because exploration costs have dropped.

- Gain Knowledge and Reduce Risk: Exploring multiple options through your assistant is like accumulating information before committing to a decision. In finance, uncertainty drives risk, and more information reduces that risk. Similarly, by “trying” various approaches through the assistant, you reduce the likelihood of costly rework and increase the odds of a high-quality result.

- Increase Portfolio Diversification: Exploring different options through coding assistants is like managing a portfolio of real options. Each question you ask helps you gather insights across multiple potential paths. This portfolio approach reduces overall risk by diversifying your design possibilities, improving the quality of the final solution.

In short, coding assistants provide an “option portfolio” for design and development choices. They allow you to sample multiple approaches at low cost, build flexibility into your process, and ultimately make more informed, higher-quality decisions in a way that minimizes risks and maximizes potential value.

## Intermission: Before Diving More into Measuring Option Value

These five dimensions of value seem pretty orthogonal to me — and what is most exciting is that I believe that “writing code” faster is the least important measure.

So which will be the most important measure? Creating option value.

An option is defined as the right, but not the obligation, to act. Stock options

And here’s where life genuinely gets a bit strange. I’m going to tell you about three people: Dr. Carliss Baldwin, Dr. Steve Spear, and Steve Yegge.

To tell you about Dr. Baldwin’s work, I’m going to quote from Wiring the Winning Organization, which I co-authored with Dr. Steve Spear… (Who, believe it or not, had Dr. Carliss Baldwin as an advisor when he was working on his doctoral dissertation at the Harvard Business School. You think that’s a small world? Wait until I tell you about Steve Yegge fits in!)

> In their book Design Rules, Drs. Carliss Baldwin and Kim Clark show how system modularity creates option value. They build on the work of Drs. Robert Merton, Fischer Black, and Myron Scholes, who showed how to quantify the monetary value created by options on financial instruments. Merton, Black, and Scholes showed how one can decouple (temporally) decisions tomorrow from conditions today, giving latitude of action to decision-makers that they otherwise wouldn’t have. Baldwin and Clark showed how one can decouple actions (spatially) in one location from those in another, providing independence of action that otherwise wouldn’t have existed.
> 
> To illustrate this point, consider a system made up of ten gears that are all coupled together and therefore composed of only one module. To perform an experiment in this system, you must spin all ten gears at the same time because no gear is independent of the others. This means that for someone responsible for a gear to make a change, they must coordinate with the owners of the other nine gears, even if what is being changed doesn’t affect the other gears (e.g., changing only its material composition).
> 
> On the other hand, if each gear were its own module, each of the ten gears could be changed independently (that’s the spatial dimension), potentially more frequently (because of independence of action), and decisions could be delayed until after the result of the experiment is known (temporal dimension). The result is that the more modules there are in a system, the space that can be explored is greatly increased, often by orders of magnitude.
> 
> Source: Kim, Gene; Spear, Steven J.. Wiring the Winning Organization: Liberating Our Collective Greatness through Slowification, Simplification, and Amplification (p. 140). IT Revolution Press. Kindle Edition.

Furthermore, Baldwin and Clark describe how modularity also creates immense option value. In fact, their claim is that ONLY option value can explain the approximately 25x increase in value creation that they observed studying the IBM development of the System/360 system in the 1960s.

By the way, we use the following language:

- Layer 1: the actual work to be performed (e.g., the patient, the code, the binary running in production)

- Layer 2: the technologies used to perform the work (e.g., the MRI machine, the IDE, the Kubernetes platform)

- Layer 3: the social circuitry, the organizational wiring, the software architecture — the difference maker

> Case Study: Modularization in Computer Hardware and Software (1960s)
> 
> \[Amazon’s engineers creating APIs in the 2000s\] were not the first to modularize a large technical system (Layer 1) to reduce the cognitive overload of people in Layer 3 (social circuitry).
> 
> IBM adopted such an approach for similar reasons some fifty years earlier. In 1960, IBM was the leading mainframe computer company, with a revenue of $3.3 billion, but its market position was at risk. Competitors were entering the market, and IBM needed to figure out how to deliver faster computers (and the software that ran on them) to market more quickly.
> 
> Their time-to-market problem was due, at least in part, to coordination costs. Design teams had to be highly integrated, which meant they had limited independence of action (Layer 3), because the systems they designed were tightly coupled (Layer 1). A CPU change might require a memory change and maybe even software changes.
> 
> This coupling compounded to make any change difficult, requiring communication, coordination, or approvals across thousands of engineers. And worse, because software design was so tightly coupled to the underlying hardware design, software was incompatible from one hardware system to the next, requiring customers to rewrite their software every time they changed computer systems. And if customers had to rewrite their software anyway, it became easier for them to consider another vendor.
> 
> In response, IBM developed the System/360 family of computers. They varied by processing power, depending on customer needs, but they all ran the same software, solving for the compatibility and upgrade problem. This project was the first to decouple software from the hardware it ran on, giving software and hardware engineers the independence of action they lacked.
> 
> But the hardware designs were still highly coupled. This created the same struggle with coordination costs. This impacted development and delivery speed, as well as compatibility issues that affected customer migration from one system to the next. To address this, IBM made the revolutionary decision in 1961 to modularize hardware components (such as CPUs, memory, tape and disk drives, terminals, and keyboards), making them “plug compatible” and interchangeable, available to be used across the entire System/360 family of computers.
> 
> By partitioning the system into modular components that connected through stable interfaces, IBM made it possible for groups to work, experiment, and make improvements in parallel, without the constant communication, coordination, and joint approvals previously required.
> 
> In Design Rules, Dr. Carliss Baldwin and Dr. Kim Clark wrote, “For the first time in history, a computer system did not have to be created by a close-knit team of designers.” Like at Amazon fifty years later, changing the technical system’s architecture (Layer 1) created opportunities for designers to work independently (Layer 3) and for customers to have a range of options they previously lacked.
> 
> The System/360 program would be the largest hardware and software effort ever undertaken up to that point, with a cost estimated over $5 billion, two times higher than IBM’s annual revenue at the time,54 and involving thousands of engineers. When the System/360 computers were introduced four years later in 1964, they launched five compatible computers, with 150 interchangeable peripherals and software products.
> 
> It was an enormous commercial success, giving IBM market dominance that lasted thirty years. Revenue grew from $3.3 billion in 1960 to $7.5 billion in 1970 and $26.2 billion in 1980, with descendants of the System/360 increasing IBM’s cash flow by twenty times during that same period.
> 
> Source: Kim, Gene; Spear, Steven J.. Wiring the Winning Organization: Liberating Our Collective Greatness through Slowification, Simplification, and Amplification (pp. 181-182). IT Revolution Press. Kindle Edition.

According to Baldwin, modularity enables independence of action and creates massive option value. We know how important independence of action is — after all, we found that software architecture was one of the top predictors of performance! Check out these architectural attributes from the 2017 DORA report which is one of the top predictors of performance:

![](https://itrevolution.com/wp-content/uploads/2025/01/Screenshot-by-Dropbox-Capture-1-1024x575.png)

Oh, and by the way, modularity is exactly what enabled Amazon to regain independence of action, which had caused their ability to deploy code to grind to a halt.

Amazon went from having one module in 1998 to tens of modules in 2004. By 2011, they had hundreds of modules, each able to work independently of each other. The impact on teams’ ability to deploy to production is breathtaking.

- 1998: Hundreds of deployments per year (est.)

- 2002: Twenty deployments per year (est.)

- 2011: 5.4 million deployments per year (15,000 deployments per day)

- 2015: 49 million deployments per year (136,000 deployments per day)

(And I mentioned Steve Yegge, right? At Google, he famously chronicled the circa-2002 Jeff Bezos “thou shalt modularize and communicate only through APIs (or else)” memo, which accidentally got published to the entire world, landing him on the front page of the Wall Street Journal in 2011.)

But, modularity also creates option value — let’s quote Dr. Baldwin from her 2015 Technology and Innovation Management Distinguished Scholar Award acceptance speech (23m mark).

> When you achieve a modular structure… each individual component becomes flexible – you can experiment with different options. This architecture tolerates uncertainty, which immediately makes finance people think of options theory. The modular architecture is rich with options that can be analyzed using financial tools.  
>   
> Unlike a rigid system where you take it or leave it, modularity allows you to mix and match the best outcomes from many experiments. This was my biggest insight… The structure’s option-rich nature has profound implications for value creation.
> 
> To demonstrate this: if you look at the number of modules on one axis and the number of experiments per module on the other, you see exponential value creation. System/360 had about 25 modules with 25 experiments per module. This resulted in the system’s value increasing by 25 times. Such a dramatic increase in value can justify investing in many architects and experimenters.  
>   
> When I was younger, I told my Technology and Operations Management colleagues who dismissed finance: “You don’t understand – finance doesn’t serve you, finance drives you.” This kind of value proposition is unstoppable from a financial perspective. The economy will reorganize itself – old organizations will disappear, new ones will emerge, funded by aggressive venture capitalists. They’ll get the job done regardless of who stands in their way.  
>   
> Instead of the 0.25x improvement I saw in traditional finance models, here was a 25x factor. I told Kim \[Clark\], “This is what we have to explore – this is unstoppable.” That was in 1993. While I didn’t predict all the subsequent developments, I was certain we would see radical rearrangements of economic relationships because of this value creation potential.  
>   
> Source: Dr. Carliss Baldwin, 2015 Technology and Innovation Management Distinguished Scholar Award acceptance speech (23m mark)

What does she mean that the “industry was going to be blown apart?” Because customers want options, i.e., the ability to mix and match components. So what happened?

> What happened next was unexpected: by 1969, the first plug-compatible peripheral companies emerged, and by 1980, hundreds of firms were making System/360-compatible components.  
>   
> This shift forced major competitors like Burroughs, GE, and what’s now Unisys to retreat to protected niches. IBM hadn’t planned for this – they wanted to sell all System/360 components themselves. Their response was twofold: they sent a task force to improve engineer satisfaction (which only recommended new curtains) and aggressively sued compatible manufacturers. Though IBM won the legal battles a decade later, it was too late – Silicon Valley and a whole ecosystem of computer firms had already formed.  
>   
> The impact was dramatic. Our graphs show IBM \[market capitalization\] as a “blue mountain range” that took a major hit when the market realized they wouldn’t monopolize System/360 components. The industry transformed from a “Chandlerian” vertically-integrated structure into fragmented, specialized components. As Andy Grove of Intel described in “Only the Paranoid Survive,” it was a transition from vertical silos to horizontal layers.  
>   
> In 1979, IBM dominated about half the industry, alongside other vertical players like Xerox, Unisys, and Digital Equipment. By 2005, the landscape had completely changed: Microsoft, Intel, and Cisco led the industry, each specializing in complementary components rather than competing directly. IBM had fallen to fourth place.  
>   
> Source: Dr. Carliss Baldwin, 2015 Technology and Innovation Management Distinguished Scholar Award acceptance speech (25m mark)

PS: In our Wiring the Winning Organization book, we cite heavily Dr. Carliss Baldwin’s amazing book, “Design Rules, Vol. 1 (1999)”. And I’m delighted beyond words that her long-awaited “Design Rules, Vol. 2 (2024)” was just released!

## A Simple Thought Exercise

Let me give you a simple example which hopefully shows how powerful creating option value is. I’m going to give you two scenarios to choose from.

- A. One roulette wheel, where you have to pick a number before you know where the ball will land?

- B. Or 100 roulette wheels, where you can defer your decision until you see where all 100 balls land —  And then place your 100 bets.

The answer of course is B.

![](https://itrevolution.com/wp-content/uploads/2025/01/Screenshot-by-Dropbox-Capture-3-1024x520.png)

Let’s compare the returns in the two scenarios:

- Scenario A: ($0.973 – $1)/$1 = -2.7% return (a losing bet!)

- Scenario B: ($3500 – $100)/$100 = 3400% return

Scenario B has approximately a 3,500x better return than Scenario A (ignore for now that we’re dividing against a negative number). But we’re actually dramatically understating the power of perfect information in Scenario B because:

- You only need to risk $1 per winning number, not all numbers

- With perfect knowledge, you know exactly which bets will win

In fact, as Claude pointed out to me, our actual return approaches infinity because:

- Investment approaches zero (we only exercise our option and bet on winners)

- Payout remains constant (35:1)

- Return = (Payout – Investment)/Investment

- As Investment → minimum bet size, Return → infinity

The true advantage of perfect information isn’t just the 3,500x better return shown in the simple calculation – it’s that you can structure your bets to achieve theoretically infinite returns by minimizing investment while maintaining the same payout.

This is why option value is so powerful – having the right but not obligation to act with perfect information allows you to eliminate downside risk while preserving upside potential.

## We’re Already Familiar With Option Value — Think of A/B Testing!

Congratulations if creating option value by deferring decisions until we have more information might sound familiar! Because the widely used practice of A/B feature flagging (i.e., feature toggles) is an example of this.

Consider an A/B test where we deploy two “call to actions” into production, to determine which one results in higher user signup rates. We run both A and B variants in parallel, and when we discover which one performs better, we switch over to the winning one.

A/B testing creates option value in a way that perfectly matches financial option theory. When we deploy two features into production, we gain the right – but not the obligation – to run either feature. This creates value through flexibility, just like financial options do.

The mechanics directly parallel financial options. The cost of deploying both features is like paying an option premium – a small upfront cost that creates future flexibility. Once deployed, we can switch between features with minimal cost, observe their performance, and ultimately choose the better performer while abandoning the underperforming variant. This ability to maximize upside while limiting downside is the essence of option value.

The information generated has concrete value because it enables better decisions. While not providing perfect information like in the roulette wheel example, A/B testing creates us to opportunity to defer deciding between A and B until we know which performs better — and then we choose! We pay a small cost upfront (deploying both features) to create the option to choose the better outcome once we have more information about performance.

## Conclusion

I’m looking forward to working with some amazing like-minded thinkers on exploring this further — stay tuned!

The post Beyond DORA Metrics: Five Potential Dimensions Of Value That GenAI Enables for Developers — Especially Creating Option Value! appeared first on IT Revolution.

Go to Source
