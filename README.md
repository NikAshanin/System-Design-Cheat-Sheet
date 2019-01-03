# System design cheat sheet
It can be used for interviews or assessments.

## 1. Understand the problem and scope:
- Recognize stakeholders and prioritize them. Create RACI matrix
- Understand the business drivers of the project
- Recognize the end-users of the project and understand how they will use that system
- Check the functional requirements
- Define the external dependencies
- Suggest additional features
- Remove items that interviewer deems out of scope

## 2. Think about constraints and non-functional requirements:
- (use PASS ME if you not remember all of NFRs)
- Recognize number of users
- Check the number of users growth in future (next year/next 5 years)
- Define average response time
- Understand database size (current / for the next year/ for the next 5 years)
- Understand storage size (current / for the next year/ for the next 5 years)
- Recognize security needs
- Define acceptable downtime of the system
- Recognize how many requests (per month/per second)
- Estimate reads vs. writes operations percentage
- Define time to market
- Check customer-related nfr: legacy/proprietary soft, etc

## 3. Detect Architecture Significant Requirements
- Mix between FRs and NFRs to detect ASRs

## 4. Abstract design:
- Choose design views style (C4, 4+1, etc)
- Choose Architecture Style (Monolith, SOA - microservices, etc)
- Define layers (presentation, service, data, caching)
- Choose between cloud-solution or on-premise servers
- Consider authentication and authorization
- Suggest security rules and protocols
- Define infrastructure: load balancing, messaging
- Rough overview of any key algorithm that drives the service
- Consider bottlenecks and determine solutions
- Choose storage type (SQL or NoSQL)
- Understand what data should be cached and how to improve performance/security/availability with caching
- Monitoring system and logging. Analytics and automatically reboot system in case of exceptions
- Define separation between public and restricted areas
