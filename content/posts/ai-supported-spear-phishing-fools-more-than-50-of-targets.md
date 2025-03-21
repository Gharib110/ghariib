---
title: "AI-supported spear phishing fools more than 50% of targets"
date: 2025-01-08
---

One of the first things everyone predicted when artificial intelligence (AI) became more commonplace was that it would assist cybercriminals in making their phishing campaigns more effective.

Now, researchers have conducted a scientific study into the effectiveness of AI supported spear phishing, and the results line up with everyone’s expectations: AI is making it easier to do crimes.

The study, titled Evaluating Large Language Models’ Capability to Launch Fully Automated Spear Phishing Campaigns: Validated on Human Subjects, evaluates the capability of large language models (LLMs) to conduct personalized phishing attacks and compares their performance with human experts and AI models from last year.

To this end the researchers developed and tested an AI-powered tool to automate spear phishing campaigns. They used AI agents based on GPT-4o and Claude 3.5 Sonnet to search the web for available information on a target and use this for highly personalized phishing messages.

With these tools, the researchers achieved a click-through rate (CTR) that marketing departments can only dream of, at 54%. The control group received arbitrary phishing emails and achieved a CTR of 12% (roughly 1 in 8 people clicked the link).

Another group was tested against an email generated by human experts which proved to be just as effective as the fully AI automated emails and got a 54% CTR. But the human experts did this at 30 times the cost of the AI automated tools.

The AI tools with human assistance outperformed the CTR of these groups by scoring 56% at 4 times the cost of the AI automated tools. This means that some (expert) human input can improve the CTR, but is it enough to invest the time? Cybercriminals are proverbially lazy, which means they often exhibit a preference for efficiency and minimal effort in their operations, so we don’t expect them to think the extra 2% to be worth the investment.

The research also showed a significant improvement of the deceptive capabilities of AI models compared to last year, where studies found that AI models needed human assistance to perform on par with human experts.

The key to the success of a phishing email is the level of personalization that can be achieved by the AI assisted method and the base for that personalization can be provided by an AI web-browsing agent that crawls publicly available information.

<figure>

![Example from the paper showing how collected information is used to write a spear phishing email](https://www.malwarebytes.com/wp-content/uploads/sites/2/2025/01/Research_for_target.jpg)

<figcaption>

_Example from the paper showing how collected information is used to write a spear phishing email_

</figcaption>

</figure>

Based on information found online about the target, they are invited to participate in a project that aligns with their interest and presented with a link to a site where they can find more details.

The AI-gathered information was accurate and useful in 88% of cases and only produced inaccurate profiles for 4% of the participants.

Other bad news is that the researchers found that the guardrails which are supposed to stop AI models from assisting cybercriminals are not a noteworthy barrier for creating phishing mails with any of the tested models.

The good news is that LLMs are also getting better at recognizing phishing emails. Claude 3.5 Sonnet scored well above 90% with only a few false alarms and detected several emails that passed human detection. Although it struggles with some phishing emails that are clearly suspicious to most humans.

If you’re looking for some guidance how to recognize AI assisted phishing emails, we’d like you to read: How to recognize AI-generated phishing mails. But the best way is to always remember the general advice not to click on any links in unsolicited emails.

* * *

**We don’t just report on threats—we remove them**

Cybersecurity risks should never spread beyond a headline. Keep threats off your devices by downloading Malwarebytes today.

Go to Source
