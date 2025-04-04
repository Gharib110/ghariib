---
title: "Building RAG with enterprise open source AI infrastructure"
date: 2025-01-02
categories: 
  - "general"
---

One of the most critical gaps in traditional Large Language Models (LLMs) is that they rely on static knowledge already contained within them. Basically, they might be very good at understanding and responding to prompts, but they often fall short in providing current or highly specific information. This is where Retrieval-augmented Generation (RAG) comes in;  RAG addresses these critical gaps in traditional LLMs by incorporating current and new information that serves as a reliable source of truth for these models. 

In our previous blog in this series on understanding and deploying RAG, we walked you through the basics of what this technique is and how it enhances generative AI models by utilizing external knowledge sources such as documents and extensive databases. These external knowledge bases enhance machine learning models for enterprise applications by providing verifiable, up-to-date information that reduces errors, simplifies implementation, and lowers the cost of continuous retraining.

In this second blog of our four-part series on RAG, we will focus on creating a robust enterprise AI infrastructure for RAG systems using open source tooling for your Gen AI project.  This blog will discuss AI infrastructure considerations such as hardware, cloud services, and generative AI software. Additionally, it will highlight a few open source tools designed to accelerate the development of generative AI.

# RAG AI infrastructure considerations

AI infrastructure encompasses the integrated hardware and software systems created to support AI and machine learning workloads to carry out complex analysis, predictions, and automation. The main challenge when introducing AI in any project is operating the underlying infrastructure stack that supports the models and applications. While similar to regular cloud infrastructures, machine learning tools require a tailored approach to operations to remain reliable and scalable, and the expertise needed for this approach is both difficult to find and expensive to hire. Neglecting proper operations can lead to significant issues for your company, models, and processes, which can seriously damage your image and reputation.

Building a generative AI project, such as a RAG system, requires multiple components and services. Additionally, it’s important to consider the cloud environment for deployment, as well as the choice of operating system and hardware. These factors are crucial for ensuring that the system is scalable, efficient, secure, and cost-effective. The illustration below maps out a full-stack infrastructure delivery of RAG and Gen AI systems:

![](https://res.cloudinary.com/canonical/image/fetch/f_auto,q_auto,fl_sanitize,c_fill,w_720/https://lh7-rt.googleusercontent.com/docsz/AD_4nXcd0nIhhKndN2IO3F8ARHQEBP77EpJMps4KiEVWgdwrbDcbGJuFNJxtcMOX8QMcFcJKJCdZvuGlQtkQMzw6lSY4M89Nd20_PGBAlukXMVJiB3Aicj9L4nIYDJyeoflF7qkTQIPjIg?key=bWiOXP50Qv6mRzi9JmPlbdNX)

Let’s briefly examine each of these considerations and explore their pros and cons.

## Hardware

The hardware on which your AI will be deployed is critical. Choosing the right compute options—whether CPUs or GPUs—depends on the specific demands and use cases of your AI workloads. Considerations such as throughput, latency, and the complexity of applications are important; for instance, if your AI requires massive parallel computation and scalable inference, GPUs may be necessary. Additionally, your chosen storage hardware is important, particularly regarding read and write speeds needed for accessing data. Lastly, the network infrastructure should also be carefully considered, especially in terms of workload bandwidth and latency. For example, a low-latency and high-bandwidth network setup is essential for applications like chatbots or search engines

## Clouds

Cloud infrastructure provides computing power, storage, and scalability, and meets the demands of AI workloads. There are multiple types of cloud environments – including private, public, and bare-metal deployments – and each one has its pros and cons. For example, bare-metal infrastructure offers high performance for computing and complete control over security. However, managing and scaling a bare-metal setup can be challenging. In comparison, public cloud deployments are currently very popular due to their accessibility, but these infrastructures are owned and managed by public cloud providers. Finally, private cloud environments provide enhanced control over data security and privacy compared to public clouds. 

The good thing is that you can relatively easily blend these different elements of the cloud together into hybrid cloud environments that offer the pros of each one while covering the flaws that single-environment cloud setups may present.

## Operating system 

The operating system (OS) plays a crucial role in managing AI workloads, serving as the foundational layer for overseeing hardware and software resources. There are several OS options suitable for running AI workloads, including Linux and enterprise systems like Windows.

Linux is the most widely used OS for AI applications due to its flexibility, stability, and extensive support for machine learning frameworks such as TensorFlow, PyTorch, and Hugging Face. Common distributions used for AI workloads include Ubuntu, Debian, Fedora, CentOS, and many more. Additionally, Linux environments provide excellent support for containerized setups like docker containers and CNCF-compliant setups like Kubernetes. 

## Gen AI services

Generative AI projects, such as RAG, may involve multiple components, including a knowledge base, large language models, retrieval systems, generators, inferences, and more. Each of these services will be defined and discussed in greater detail in the upcoming section titled “Advanced RAG and Gen AI Reference Solutions with Open Source.”

While the RAG services may offer different functionalities, it is essential to choose the components that best fit your specific use case. For example, in small-scale RAG deployments, you might need to set aside fine-tuning and early-stage model repositories as these are advanced Gen AI reference solutions. Additionally, it is crucial that all these components integrate smoothly and coherently to create a seamless workflow. This helps reduce latency and accommodates the required throughput for your project.

# RAG reference solution

When a query is made in an AI chatbot, the RAG-based system first retrieves relevant information from a large dataset or knowledge base, and then uses this information to inform and guide the generation of the response. The RAG-based system consists of two key components. The first component is the Retriever, which is responsible for locating relevant pieces of information that can help answer a user query. It searches a database to select the most pertinent information. This information is then provided to the second component, the Generator. The Generator is a large language model that produces the final output.

Before using your RAG-based system, you must first create your knowledge base, which consists of external data that is not included in your LLM training data. This external data can originate from various sources, including documents, databases, and API calls. Most RAG systems utilize an AI technique called model embedding, which converts data into numerical representations and stores it in a vector database. By using an embedding model, you can create a knowledge model that is easily understandable and readily retrievable in the context of AI.  Once you have a knowledge base and a vector database set up, you can now perform your RAG process; here is a conceptual flow:

![](https://res.cloudinary.com/canonical/image/fetch/f_auto,q_auto,fl_sanitize,c_fill,w_720/https://lh7-rt.googleusercontent.com/docsz/AD_4nXcJjaB4NVMu351t4KcBKmXgOFHBkkkfdK-m-RGVjhpxEqoieVIDwEkndFijDcorQ2HDTb1Z3HXAMYGao-C_Q9yENvF0_yTk83XyzHR6fQiKLxEY59OqYPeU5TW5m5fmiHaTMIQJ?key=bWiOXP50Qv6mRzi9JmPlbdNX)

This conceptual flow follows 5 general steps:

1. The user enters a prompt or query. 
2. Your Retriever searches for relevant information from a knowledge base. The relevance can be determined using mathematical vector calculations and representations through a vector search and database functionality.
3. The relevant information is retrieved to provide enhanced context to the generator. 
4. The query and prompts are now enriched with this context and are ready to be augmented for use with a large language model using prompt engineering techniques. The augmented prompt enables the language model to respond accurately to your query. 
5. Finally, the generated text response is delivered to you.

## Advanced RAG and Gen AI reference solution with open source

RAG can be used in various applications, such as AI chatbots, semantic search, data summarization, and even code generation. The reference solution below outlines how RAG can be combined with advanced generative AI reference architectures to create optimized LLM projects that provide contextual solutions to various Gen AI use cases.

![](https://res.cloudinary.com/canonical/image/fetch/f_auto,q_auto,fl_sanitize,c_fill,w_720/https://lh7-rt.googleusercontent.com/docsz/AD_4nXeUfVjUIYyCfdDI4MUw2coGG4L69S8j116gQ5Q5KjrLLRpUN2uw8R4r1JxOSC2OuFA89v6wfop5eoFPSzJT1xzyMLt87WapnhtauyPPfPgLkb9cIGe2F6GtgWd_cD-6biR1brWltw?key=bWiOXP50Qv6mRzi9JmPlbdNX)

Figure: RAG enhanced GenAI Ref solution (source: https://opea.dev/) 

The GenAI blueprint mentioned above was published by Opea (Open Platform for Enterprise AI), a project of the Linux Foundation. The aim of creating this blueprint is to establish a framework of composable building blocks for state-of-the-art generative AI systems, which include LLM,  data storage, and prompt engines. Additionally, it provides a blueprint for RAG and outlines end-to-end workflows. The recent release 1.1 of the Opea project showcased multiple GenAI projects that demonstrate how RAG systems can be enhanced through open source tools.

Each service within the blocks has distinct tasks to perform, and there are various open source solutions available that can help to accelerate these services based on enterprise needs. These are mapped in the table below:  

| Services | Description | Some open source solutions |
| --- | --- | --- |
| Ingest/data processing | The ingest or data processing is a data pipeline layer. This is responsible for data extraction, cleansing, and the removal of unnecessary data that you will run.  | Kubeflow   OpenSearch |
| Embedding model | The embedding model is a machine-learning model that converts raw data to vector representations. | Hugging face sentence transformer   Sentence transformer used by OpenSearch  |
| Retrieval and ranking | This component retrieves the data from the knowledge base; it also ranks the relevance of the information being fetched based on relevance scores. | FAISS (Facebook AI Similarity Search) – such as the one being used in OpenSearch   HayStack    |
| Vector database | A vector database stores vector embeddings so data can be easily searched by the ‘retrieval and ranking services’. | Milvus   PostgreSQL Pg\_VectorOpenSearch: KNN Index as a vector database |
| Prompt processing | This service formats queries and retrieved text into a readable format so it is structured to the LLM model.  | Langchain   OpenSearch: ML – agent predict |
| LLM | This component provides the final response using multiple GenAI models. | GPT   BART   and many more |
| LLM inference | This refers to operationalizing machine learning in production by processing running data into a machine learning model so that it gives an output. | Kserve   VLLM |
| Guardrail | This component ensures ethical content in the Gen AI response by creating a guardrail filter for the inputs and outputs. | Fairness Indicators   OpenSearch: guardrail validation model  |
| LLM Fine-tuning | Fine-tuning is the process of taking a pre-trained machine learning model and further training it on a smaller, targeted data set. | Kubeflow   LoRA |
| Model repository | This component is used to store and version trained machine learning (ML) models, especially within the process of fine-tuning. This registry can track the model’s lifecycle from deployment to retirement. | Kubeflow   MLFlow |
| Framework for building LLM application | This simplifies LLM workflow, prompts, and services so that building LLMs is easier. | Langchain |

This table provides an overview of the key components involved in building a RAG system and advanced Gen AI reference solution, along with associated open source solutions for each service. Each service performs a specific task that can enhance your LLM setup, whether it relates to data management and preparation, embedding a model in your database, or improving the LLM itself.

The rate of innovation in this field, particularly within the open source community, has become exponential. It is crucial to stay updated with the latest developments, including new models and emerging RAG solutions.

# Conclusion 

Building a robust generative AI infrastructure, such as those for RAG, can be complex and challenging. It requires careful consideration of the technology stack, data, scalability, ethics, and security. For the technology stack, the hardware, operating systems, cloud services, and generative AI services must be resilient and efficient based on the scale that enterprises require.

There are multiple open-source software options available for building generative AI infrastructure and applications, which can be tailored to meet the complex demands of modern AI projects. By leveraging open source tools and frameworks, organizations can accelerate development, avoid vendor lock-in, reduce cost and meet the enterprise needs.

Now that you’ve been introduced to Blog Series #1 – What is RAG? and this Blog Series #2 on how to prepare a robust RAG AI infrastructure, it’s time to get hands-on and try building your own RAG using open source tools in our next blog in this series, “Build a one-stop solution for end-to-end RAG workflow with open source tools”. Stay tuned for part 3, to be published soon!

# Canonical for your RAG and AI Infra needs

### Build the right RAG architecture and application with Canonical RAG and MLOps workshop

Canonical provides workshops and enterprise open source tools and services and can advise on securing the safety of your code, data, and models in production.

Canonical offers a 5-day workshop designed to help you start building your enterprise RAG systems. By the end of the workshop, you will have a thorough understanding of RAG and LLM theory, architecture, and best practices. Together, we will develop and deploy solutions tailored to your specific needs. Download the datasheet here.  
  
Explore more and contact our team for your RAG needs.

## Learn and use best-in-class Gen AI tooling  on any hardware and cloud

Canonical offers enterprise-ready AI infrastructure along with open source data and AI tools to help you kickstart your RAG projects. Canonical is the publisher of Ubuntu, a Linux operating system that operates on public cloud platforms, data centres, workstations, and edge/IOT devices. Canonical has established partnerships with major public cloud providers such as Azure, Google Cloud, and AWS. Additionally, Canonical collaborates with silicon vendors, including Intel, AMD, NVIDIA, and RISC-V, ensuring their platform is silicon agnostic.

## Secure your stack with confidence

Enhance the security of your GenAI projects while mastering best practices for managing your software stack. Discover ways to safeguard your code, data, and machine learning models in production with Confidential AI.

Go to Source
