---
title: "Testing the limits of generative AI: How red teaming exposes vulnerabilities in AI models"
date: 2025-01-03
categories: 
  - "security"
---

With generative artificial intelligence (gen AI) on the frontlines of information security, red teams play an essential role in identifying vulnerabilities that others can overlook.

With the average cost of a data breach reaching an all-time high of $4.88 million in 2024, businesses need to know exactly where their vulnerabilities lie. Given the remarkable pace at which they’re adopting gen AI, there’s a good chance that some of those vulnerabilities lie in AI models themselves — or the data used to train them.

That’s where AI-specific red teaming comes in. It’s a way to test the resilience of AI systems against dynamic threat scenarios. This involves simulating real-world attack scenarios to stress-test AI systems before and after they’re deployed in a production environment. Red teaming has become vitally important in ensuring that organizations can enjoy the benefits of gen AI without adding risk.

IBM’s X-Force Red Offensive Security service follows an iterative process with continuous testing to address vulnerabilities across four key areas:

1. Model safety and security testing
2. Gen AI application testing
3. AI platform security testing
4. MLSecOps pipeline security testing

In this article, we’ll focus on three types of adversarial attacks that target AI models and training data.

## Prompt injection

Most mainstream gen AI models have safeguards built in to mitigate the risk of them producing harmful content. For example, under normal circumstances, you can’t ask ChatGPT or Copilot to write malicious code. However, methods such as prompt injection attacks and jailbreaking can make it possible to work around these safeguards.

One of the goals of AI red teaming is to deliberately make AI “misbehave” — just as attackers do. Jailbreaking is one such method that involves creative prompting to get a model to subvert its safety filters. However, while jailbreaking can theoretically help a user carry out an actual crime, most malicious actors use other attack vectors — simply because they’re far more effective.

Prompt injection attacks are much more severe. Rather than targeting the models themselves, they target the entire software supply chain by obfuscating malicious instructions in prompts that otherwise appear harmless. For instance, an attacker might use prompt injection to get an AI model to reveal sensitive information like an API key, potentially giving them back-door access to any other systems that are connected to it.

Red teams can also simulate evasion attacks, a type of adversarial attack whereby an attacker subtly modifies inputs to trick a model into classifying or misinterpreting an instruction. These modifications are usually imperceptible to humans. However, they can still manipulate an AI model into taking an undesired action. For example, this might include changing a single pixel in an input image to fool the classifier of a computer vision model, such as one intended for use in a self-driving vehicle.

Explore X-Force Red Offensive Security Services

## Data poisoning

Attackers also target AI models during training and development, hence it’s essential that red teams simulate the same attacks to identify risks that could compromise the whole project. A data poisoning attack happens when an adversary introduces malicious data into the training set, thereby corrupting the learning process and embedding vulnerabilities into the model itself. The result is that the entire model becomes a potential entry point for further attacks. If training data is compromised, it’s usually necessary to retrain the model from scratch. That’s a highly resource-intensive and time-consuming operation.

Red team involvement is vital from the very beginning of the AI model development process to mitigate the risk of data poisoning. Red teams simulate real-world data poisoning attacks in a secure sandbox environment air-gapped from existing production systems. Doing so provides insights into how vulnerable the model is to data poisoning and how real threat actors might infiltrate or compromise the training process.

AI red teams can proactively identify weaknesses in data collection pipelines, too. Large language models (LLMs) often draw data from a huge number of different sources. ChatGPT, for example, was trained on a vast corpus of text data from millions of websites, books and other sources. When building a proprietary LLM, it’s crucial that organizations know exactly where they’re getting their training data from and how it’s vetted for quality. While that’s more of a job for security auditors and process reviewers, red teams can use penetration testing to assess a model’s ability to resist flaws in its data collection pipeline.

## Model inversion

Proprietary AI models are usually trained, at least partially, on the organization’s own data. For instance, an LLM deployed in customer service might use the company’s customer data for training so that it can provide the most relevant outputs. Ideally, models should only be trained based on anonymized data that everyone is allowed to see. Even then, however, privacy breaches may still be a risk due to model inversion attacks and membership inference attacks.

Even after deployment, gen AI models can retain traces of the data that they were trained on. For instance, the team at Google’s DeepMind AI research laboratory successfully managed to trick ChatGPT into leaking training data using a simple prompt. Model inversion attacks can, therefore, allow malicious actors to reconstruct training data, potentially revealing confidential information in the process.

Membership inference attacks work in a similar way. In this case, an adversary tries to predict whether a particular data point was used to train the model through inference with the help of another model. This is a more sophisticated method in which an attacker first trains a separate model – known as a membership inference model — based on the output of the model they’re attacking.

For example, let’s say a model has been trained on customer purchase histories to provide personalized product recommendations. An attacker may then create a membership inference model and compare its outputs with those of the target model to infer potentially sensitive information that they might use in a targeted attack.

In either case, red teams can evaluate AI models for their ability to inadvertently leak sensitive information directly or indirectly through inference. This can help identify vulnerabilities in training data workflows themselves, such as data that hasn’t been sufficiently anonymized in accordance with the organization’s privacy policies.

## Building trust in AI

Building trust in AI requires a proactive strategy, and AI red teaming plays a fundamental role. By using methods like adversarial training and simulated model inversion attacks, red teams can identify vulnerabilities that other security analysts are likely to miss.

These findings can then help AI developers prioritize and implement proactive safeguards to prevent real threat actors from exploiting the very same vulnerabilities. For businesses, the result is reduced security risk and increased trust in AI models, which are fast becoming deeply ingrained across many business-critical systems.

The post Testing the limits of generative AI: How red teaming exposes vulnerabilities in AI models appeared first on Security Intelligence.

Go to Source
