---
title: "AWS KMS: How many keys do I need?"
date: 2025-01-02
categories: 
  - "security"
---

As organizations continue their cloud journeys, effective data security in the cloud is a top priority. Whether it’s protecting customer information, intellectual property, or compliance-mandated data, encryption serves as a fundamental security control. This is where AWS Key Management Service (AWS KMS) steps in, offering a robust foundation for encryption key management on AWS.

One of the first questions that often arises for customers is, “How many keys do I actually need?” This seemingly simple question requires careful consideration of various factors. Although AWS KMS makes encryption straightforward, organizations need to consider several aspects of their key management strategy. These include choosing between AWS managed keys, customer managed keys, and importing your own keys (BYOK), as well as deciding between centralized and decentralized key management approaches. Each option has its own benefits and trade-offs in terms of security, control, and operational overhead. By understanding these choices and how they align with your organization’s needs, you can develop an effective and efficient key management strategy.

In this blog post, we explore the main considerations that drive your AWS KMS key strategy, from organizational structure to compliance requirements. Should you maintain a centralized key management approach with a single team controlling all keys, or adopt a decentralized model where individual teams manage their own keys? These decisions are important because they relate to the AWS shared responsibility model, where AWS maintains the security of the cloud, while customers remain responsible for security _in_ the cloud, including the proper management and use _of_ encryption keys.

## Overview – What is AWS Key Management Service?

AWS Key Management Service (AWS KMS) is an AWS managed service that makes it convenient for you to create and control the encryption keys that are used to encrypt your data. The keys that you create in AWS KMS are protected by FIPS 140 Level 3 validated hardware security modules (HSM). The keys never leave AWS KMS unencrypted. To use or manage your KMS keys, you interact with AWS KMS.

Customers are responsible for deciding what data to encrypt, choosing the appropriate encryption keys, and implementing encryption across AWS services with the help of the key policy. Customers are responsible for monitoring and auditing the use of encryption keys through services such as AWS CloudTrail.

A critical aspect of customer responsibility is determining how to manage the keys and how many KMS keys are needed. This decision depends on various factors such as data classification, application architecture, regulatory requirements, and operational needs. We look at these areas in more detail in the next sections.

## Guiding principles for key strategy

Following are four guiding engineering principles that, based on our experience, help create a secure and easier-to-maintain system. They will assist you in determining the approximate number of KMS keys for your organization based on your management requirements.

**Principle 1 – Data Classification:** If a system processes data of different classification levels, employ separate data resources and separate KMS keys to separately govern and audit access to the data. With similarly classified data or a single type of data, the usage of just one KMS key may be justified.

> **Why it matters:** This principle helps to ensure that data that is classified into different sensitivity levels is protected appropriately based on access to encryption keys for that same classification, reducing the risk of unauthorized access and simplifying governance.

**Principle 2 – Applications:** Multiple applications can run in one AWS account. We recommend that you use distinct KMS keys for each application, because managing access to an individual key can become a complex task when it is delegated to two or more application administrators. Use separate KMS keys for applications running in distinct AWS accounts to further make use of the account boundary, limiting the potential impact in case of a security incident. Use separate keys for distinct application stages (such as development, staging, or production).

> **Why it matters:** This approach isolates access to applications and application access to data. This reduces the potential impact of unintended access to a key.

**Principle 3 – AWS Services:** When you consider key management across multiple AWS services, focus on both the services and the nature of the data. If you are dealing with one type of data (for example, customer information) that flows through multiple AWS services as part of one application or workflow, consider using a single KMS key. This simplifies key management while maintaining consistent access control. For instance, a customer record that is stored in Amazon Simple Storage Service (Amazon S3), processed by AWS Lambda, and then stored in Amazon DynamoDB could use the same KMS key across these services as mentioned in Principle 1.

However, if you are handling different types of data (such as financial records and user preferences) across various AWS services, even within the same application, consider using separate KMS keys on a per-service basis. This allows for more granular access control and adheres to the principle of least privilege. For example, in an e-commerce application, you might use one KMS key for encrypting payment information in Amazon Relational Database Service (Amazon RDS) and a different key for encrypting user browsing history in Amazon Redshift.

The decision to use one key or multiple keys should be based on your data classification policies and access control requirements. With this approach, you can keep your key management strategy aligned with your data governance policies, regardless of which AWS services you are using.

> **Why it matters:** This principle balances the need for simplicity with the requirement for granular control over data access across different AWS services.

**Principle 4 – Separation of Duties:** Key policies define who can administer and who can use the key. In the case of distinct encryption use cases and distinct administrators, we recommend that you create separate KMS keys. Another aspect of separation of duties is that, with KMS key policies, two different principals can be made responsible for governing data and data decryption access. However, this does not influence the count of keys.

> **Why it matters:** This principle supports the implementation of least privilege access and helps maintain clear accountability in key management.

By applying these principles, you can develop a key management strategy that describes how many KMS keys you may need, and that balances security, compliance, and operational efficiency. In the following sections, we explore how to apply these principles in various scenarios.

## Examples of key management strategy and comparison of centralized and decentralized approaches

In addition to the guiding principles discussed earlier, the structure of your organization and its specific needs play a crucial role in determining the most suitable approach to key management. When implementing key management strategies, organizations generally choose from three main approaches: centralized, decentralized, or a hybrid model. The choice depends on the organization’s structure, needs, and operational context. Each approach offers distinct advantages for specific organizational scenarios.

A decentralized approach is our recommended approach, as most customers fit into the following scenarios:

- Organizations with autonomous business units or where governance controls provide oversight of key usage
- Companies where development teams are agile and ownership of keys can be centrally audited
- Companies that operate in multiple regulatory frameworks
- Companies that require to operate in a particular AWS Region

A centralized KMS approach is best suited for the following scenarios:

- Organizations that require strict compliance oversight and centralized management
- Companies with centralized security or data protection functions

In a hybrid model, there is a blend between centralized and decentralized:

- Core key policies are managed centrally
- Day-to-day key operations are handled by teams
    
    For example, organizations or companies could have independent product teams, but a centralized security team.
    

**Example 1 (Hybrid):** A retail website with public product catalog data and confidential customer data should use two KMS keys—one for the public catalog that is encrypted in Amazon S3, and one for customer data that is encrypted in Amazon RDS and other AWS services.

> **Rationale:** This recommendation is based primarily on Principle 1 (Data Classification). The public catalog data and confidential customer data represent different classification levels, justifying the use of separate keys. This approach is further supported by Principle 3 (AWS Services), because the data resides in different AWS services and is of a varied nature.

The benefits of this approach:

- Implement appropriate access controls for each data type
- Manage encryption independently for each data classification
- Enhance overall data security and compliance

**Example 2 (Decentralized):** A healthcare company with several application teams could use a separate KMS key for each application team, with distinct key policies for each key based on the data and roles of each team.

> **Rationale:** This recommendation is primarily based on Principle 2 (Applications). With multiple application teams operating within the healthcare company, each potentially dealing with distinct types of data and having different access requirements, separate KMS keys provide for independent management of encryption and access for each team. This approach is further supported by Principle 4 (Separation of Duties), allowing for team-specific key policies.

The benefits of this approach:

- Maintain granular control over data access.
- Implement team-specific encryption policies.
- Uphold the principle of least privilege across the organization.
- Enhance data security: By using separate keys, the company limits the impact of improper access to any given key, enables more precise access control, facilitates independent key rotation schedules, and improves the ability to monitor and audit key usage for each application.
- Simplify alignment with healthcare regulations: Separate keys support data segregation requirements, enable fine-grained role-based access control, provide clear audit trails for each application’s data access, and allow for tailored data lifecycle management. This functionality is crucial for aligning with various healthcare compliance standards such as HIPAA.
- Allow for efficient and distributed key management that is tailored to each application team’s needs.

These examples demonstrate how applying the guiding principles can lead to a well-structured key management strategy, tailored to the specific needs of different organizations and use cases.

### Considerations for key management

When you implement your key management strategy, several factors need to be considered beyond just the number of keys. This section explores these considerations to help you make informed decisions about your key management approach.

**Key types**

AWS offers different types of KMS keys, each with its own benefits and use cases.

AWS owned keys are managed by AWS in service accounts, used across multiple customer accounts, and provide no customer visibility or audit capability. Choose AWS owned keys when there are no management or audit requirements for the keys, but encryption of the data at rest is needed.

AWS managed keys are managed entirely by AWS and are used only for your AWS account. Although customers can view these keys in the AWS Management Console and track their usage in AWS CloudTrail logs, they have limited ability to directly control or modify these keys. Choose AWS managed keys when managing keys is not a requirement, but having an audit trail is. It’s worth noting that AWS managed keys are automatically rotated every year, which can be convenient for many use cases.

Customer-managed keys offer the highest level of control and customization, allowing creation of key policies and control over key rotation. However, customer managed keys provide more flexibility, allowing you to set your own rotation schedule or even enable rotation if you are required to do so for regulatory reasons. Choose customer managed keys when you need strict control over key usage and the ability to share keys or control access through key policies, detailed auditing capabilities, alignment with specific compliance requirements, or the ability to integrate key management with your existing processes and tools.

The decision between AWS managed and customer managed keys often comes down to balancing the convenience of automatic management with the need for granular control and customization. As the number of keys increases, so does the complexity of management. More keys mean more policies to create, manage, and audit. Making sure that the right people have access to the right keys becomes more challenging. However, to help audit KMS key access, you can use the IAM Access Analyzer to determine external access to your keys. Managing rotation schedules for multiple keys requires more effort, and more keys mean more policies to analyze and monitor, as well as growing costs.

**Cost**

Security should be the primary concern, but cost is also a factor. Each customer managed key incurs a monthly storage cost. Both AWS managed and customer managed KMS keys have API usage costs associated with them. Key rotation can increase costs over time, as old key versions are retained.

**Manageability**

Finding the right balance between security and manageability is crucial. Too few keys might not provide adequate separation of duties or granular access control, while too many keys can lead to increased complexity, higher costs, and potential mismanagement.

**Specific requirements**

Different industries and regions may have specific requirements for key management. Some regulations might require separation of duties, necessitating multiple keys. Certain compliance standards might dictate specific key rotation or audit trail requirements.

By carefully considering these factors alongside the guiding principles discussed earlier, you can develop a key management strategy that balances security, compliance, cost-effectiveness, and operational efficiency for your specific needs. It is important to approach your KMS strategy holistically, considering not just your immediate security needs, but also the long-term management implications. Regular review and adjustment of your key management strategy will provide assurance that it continues to meet your evolving needs while maintaining robust security and compliance.

## Conclusion

As we explored throughout this post, determining the optimal number of AWS KMS keys for your organization is a nuanced decision that balances security, compliance, cost, and operational efficiency. The guiding principles we discussed—data classification, application segregation, AWS service integration, and separation of duties—provide a solid framework for making these decisions. Remember that there’s no one-size-fits-all solution; the right approach depends on your specific needs and circumstances.

As you move forward in implementing or refining your KMS key strategy, consider these next steps: First, conduct a thorough audit of your current data assets, their classifications, and the applications and services that interact with them. Next, map out your ideal key management structure based on the principles we’ve discussed. Then, evaluate the costs and operational overhead of your proposed strategy, adjusting as necessary to find the right balance for your organization. Finally, implement your strategy incrementally, starting with your most sensitive or critical data assets.

Remember that key management is an ongoing process. Regularly review and update your strategy as your data landscape evolves, new compliance requirements emerge, or AWS introduces new features. By thoughtfully applying the principles and considerations we’ve discussed, you can create a robust, scalable, and efficient key management strategy that helps your overall security posture and meets your organization’s unique needs.

   
If you have feedback about this post, submit comments in the **Comments** section below. If you have questions about this post, contact AWS Support.  
 

![Ishva Kanani](https://d2908q01vomqb2.cloudfront.net/22d200f8670dbdb3e253a90eee5098477c95c23d/2024/03/25/ishvaka.jpg) Ishva Kanani  
Ishva is a Security Consultant at AWS. She assists customers with secure cloud migrations and accelerates their cloud journeys by delivering innovative solutions. Passionate about cybersecurity, Ishva provides strategic guidance and best practices for cloud environments. When not safeguarding digital assets, she enjoys exploring local hiking trails and trying new recipes in her kitchen.

![Hardik Thakkar](https://d2908q01vomqb2.cloudfront.net/22d200f8670dbdb3e253a90eee5098477c95c23d/2024/12/12/hardikvt.jpg) Hardik Thakkar  
Hardik is a Prototyping Solutions Architect at AWS Global Financial Services (GFS). He specializes in secure architecture design and foundations on AWS, leveraging his security expertise to serve financial services customers. His focus areas include security-first design patterns, financial services compliance frameworks, and helping institutions build robust cloud infrastructures on AWS.

Go to Source
