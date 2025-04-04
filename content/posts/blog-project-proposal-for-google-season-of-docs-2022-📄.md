---
title: "Blog: Project proposal for Google Season of Docs 2022 📄"
date: 2025-01-03
categories: 
  - "cloud"
  - "cloudnative"
  - "devops"
  - "general"
  - "linux"
tags: 
  - "jenkins"
---

We have put together a project proposal as part of our application to participate in the Google Season of Docs 2022 program.

### Project proposal

#### Better documentation for real world use cases - Jenkins X

##### About us

Jenkins X provides automated CI/CD for Kubernetes with Preview Environments on Pull Requests using Cloud Native pipelines from Tekton.

##### Problem

- End users of Jenkins X are unable to find information on how to use Jenkins X for real world use cases which includes:
    - Production best practices
    - Scanning images in Jenkins X pipelines
    - How to make your app use different configuration/secrets for each environment
    - Observability for your apps, logging, metrics, tracing
    - Tests (Integration, e2e)
    - Artifact management
    - Multi cluster
    - Integration with other tools in the cloud native sector

##### Project scope

- Audit the current Jenkins X documentation and create a friction log
- Use the friction log as a guide for understanding the gaps in the documentation
- Interact with the Jenkins X community to create a list of top use cases
    - Create a survey
    - Look at the github issues and slack messages
- Work with the volunteers to incorporate those changes into the documentation
- Establish a feedback loop (the target customers are the end users of Jenkins X) to improve the documentation

##### Measuring project success

- Decrease in the number of github issues raised by end users on documentation related to common real world use cases
- Short 1-2 minute videos on common tasks that end users of Jenkins X would like to perform.

##### Recommended skills

- Must have:
    - Experience with github
    - Communication skills to work with the Jenkins X community
    - Creating online surveys
- Nice to have:
    - Basic experience with docker compose (local development scripts use compose)
    - Good video editing skills.
    - Some knowledge working with the documentation of other tools in the kubernetes ecosystem

##### Mentors/Volunteers

- Ankit D Mohapatra
- Christoffer Vig
- Mårten Svantesson
- Tom Hobson

### Timeline

The project will take roughly 6 months to complete. Once the technical writer is selected, we will do an orientation to bring him up to speed. This is the timeline we have in mind, but we are flexible.

| Dates | Action Item |
| --- | --- |
| April 14 - May 16, 2022 | Hire technical writer |
| April 14 - May 31, 2022 | Orientation after hiring technical writer |
| June 1 - July 31 | Review documentation, create actions items, get familiar with Jenkins X |
| August 1 - October 31 | Work on the project |
| November | Project completion |

### Budget

| Budget item | Amount | Running Total | Notes |
| --- | --- | --- | --- |
| Technical writer stipend | 6000 | 6000 |  |
| Volunteer stipend | 2000 | 8000 | 4 volunteer stipend (500 each) X 4 |
| Jenkins X t-shirts | 300 | 8300 | 20 t-shirts X 15 |
| Shipping for t-shirts | 300 | 8600 | 15 dollars to ship, shipping rates can vary |

#### Notes about budget

- The cost of the t-shirt was taken from here.
- The t-shirts are for the technical writer, volunteers and any member of the jenkins X community (not officially listed as a volunteer) who helps out by answering the technical writer’s questions.

### Additional information

- Previous participation in Season of Docs, Google Summer of Code or others
    - Jenkins X participated in the 2020 Season of docs. The maturity level matrix created by the technical writer is still used by the community to evaluate if Jenkins X will work for their use case, as well as used by the Jenkins X maintainers to plan the roadmap for improving Jenkins X.
    - Jenkins X is also participating in the google summer of code 2022. We are seeing a lot of interest from new contributors. We are confident it will lead to some amazing improvements in the Jenkins X ecosystem and make it a sustainable open source project. We expect the technical writer will help the contributors create better documentation for their work.

### Other ideas

#### 2\. Reorganize documentation to make it more user friendly and easy to search

##### Problem

- The documentation does not feel coherent, it does not read like a book from start to finish
    - There’s no clear flow about how people should read documentation and no “next step” once they’ve finished reading a page.
    - There’s also a lot of missing _assumed_ knowledge in the documentation which makes it hard for new users to form a mental picture of Jenkins X
- Results from older documentation sometimes shows up higher than newer results creating confusion for users

##### How would we measure success?

- The number of repeated searches decrease (adding / removing terms)
- Decrease in the number of github issues raised by users on documentation related to missing information
- Decrease in slack messages from users not finding relevant information in the documentation.

#### 3\. Improve contributor/developer documentation on how to extend Jenkins X

##### Problem

- It is not clear from our documentation how to
    - add support for a new cloud provider
    - add support for a new git/scm provider
    - add a new quick start
    - add new language packs

##### How would we measure success?

- Increase in number of contributions to add support for more cloud providers
- Increase in number of contributions to add add or extend quickstart guides
- Decrease in slack messages from users not finding relevant information in the documentation.

We have put together a project proposal as part of our application to participate in the Google Season of Docs 2022 program.

### Project proposal

#### Better documentation for real world use cases - Jenkins X

##### About us

Jenkins X provides automated CI/CD for Kubernetes with Preview Environments on Pull Requests using Cloud Native pipelines from Tekton.

##### Problem

- End users of Jenkins X are unable to find information on how to use Jenkins X for real world use cases which includes:
    - Production best practices
    - Scanning images in Jenkins X pipelines
    - How to make your app use different configuration/secrets for each environment
    - Observability for your apps, logging, metrics, tracing
    - Tests (Integration, e2e)
    - Artifact management
    - Multi cluster
    - Integration with other tools in the cloud native sector

##### Project scope

- Audit the current Jenkins X documentation and create a friction log
- Use the friction log as a guide for understanding the gaps in the documentation
- Interact with the Jenkins X community to create a list of top use cases
    - Create a survey
    - Look at the github issues and slack messages
- Work with the volunteers to incorporate those changes into the documentation
- Establish a feedback loop (the target customers are the end users of Jenkins X) to improve the documentation

##### Measuring project success

- Decrease in the number of github issues raised by end users on documentation related to common real world use cases
- Short 1-2 minute videos on common tasks that end users of Jenkins X would like to perform.

##### Recommended skills

- Must have:
    - Experience with github
    - Communication skills to work with the Jenkins X community
    - Creating online surveys
- Nice to have:
    - Basic experience with docker compose (local development scripts use compose)
    - Good video editing skills.
    - Some knowledge working with the documentation of other tools in the kubernetes ecosystem

##### Mentors/Volunteers

- Ankit D Mohapatra
- Christoffer Vig
- Mårten Svantesson
- Tom Hobson

### Timeline

The project will take roughly 6 months to complete. Once the technical writer is selected, we will do an orientation to bring him up to speed. This is the timeline we have in mind, but we are flexible.

| Dates | Action Item |
| --- | --- |
| April 14 - May 16, 2022 | Hire technical writer |
| April 14 - May 31, 2022 | Orientation after hiring technical writer |
| June 1 - July 31 | Review documentation, create actions items, get familiar with Jenkins X |
| August 1 - October 31 | Work on the project |
| November | Project completion |

### Budget

| Budget item | Amount | Running Total | Notes |
| --- | --- | --- | --- |
| Technical writer stipend | 6000 | 6000 |  |
| Volunteer stipend | 2000 | 8000 | 4 volunteer stipend (500 each) X 4 |
| Jenkins X t-shirts | 300 | 8300 | 20 t-shirts X 15 |
| Shipping for t-shirts | 300 | 8600 | 15 dollars to ship, shipping rates can vary |

#### Notes about budget

- The cost of the t-shirt was taken from here.
- The t-shirts are for the technical writer, volunteers and any member of the jenkins X community (not officially listed as a volunteer) who helps out by answering the technical writer’s questions.

### Additional information

- Previous participation in Season of Docs, Google Summer of Code or others
    - Jenkins X participated in the 2020 Season of docs. The maturity level matrix created by the technical writer is still used by the community to evaluate if Jenkins X will work for their use case, as well as used by the Jenkins X maintainers to plan the roadmap for improving Jenkins X.
    - Jenkins X is also participating in the google summer of code 2022. We are seeing a lot of interest from new contributors. We are confident it will lead to some amazing improvements in the Jenkins X ecosystem and make it a sustainable open source project. We expect the technical writer will help the contributors create better documentation for their work.

### Other ideas

#### 2\. Reorganize documentation to make it more user friendly and easy to search

##### Problem

- The documentation does not feel coherent, it does not read like a book from start to finish
    - There’s no clear flow about how people should read documentation and no “next step” once they’ve finished reading a page.
    - There’s also a lot of missing _assumed_ knowledge in the documentation which makes it hard for new users to form a mental picture of Jenkins X
- Results from older documentation sometimes shows up higher than newer results creating confusion for users

##### How would we measure success?

- The number of repeated searches decrease (adding / removing terms)
- Decrease in the number of github issues raised by users on documentation related to missing information
- Decrease in slack messages from users not finding relevant information in the documentation.

#### 3\. Improve contributor/developer documentation on how to extend Jenkins X

##### Problem

- It is not clear from our documentation how to
    - add support for a new cloud provider
    - add support for a new git/scm provider
    - add a new quick start
    - add new language packs

##### How would we measure success?

- Increase in number of contributions to add support for more cloud providers
- Increase in number of contributions to add add or extend quickstart guides
- Decrease in slack messages from users not finding relevant information in the documentation.

Go to Source
