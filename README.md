# System design cheat sheet
It can be used for interviews or assessments.
# 1. Understand problem and scope:
- Recognize stakeholders and prioritize them. Create RACI matrix
- Understand business drivers of the project
- Recognize end-users of the project and understand how they will use that system
- Check functional requirements
- Define external dependencies
- Suggest additional features
- Remove items that interviewer considers out of scope
# 2. Think about constraints and non-functional requirements:
- (use PASS ME if you do not remember all of NFRs)
- Recognize number of users
- Estimate users growth rate (for the next year/next 5 years)
- Define average response time
- Understand database size (current / for the next year/ for the next 5 years)
- Understand storage size (current / for the next year/ for the next 5 years)
- Recognize security needs
- Define acceptable downtime of the system
- Recognize number of requests (per month/per second)
- Estimate reads vs. writes operations percentage
- Define time to market
- Check customer related nfr: legacy/proprietary soft, etc
# 3. Detect Architecture Significant Requirements
- Mix between FRs and NFRs to detect ASRs
# 4. Abstract design:
- Choose which architectural views to define based on the stakeholders matrix. Use common C4/4+1/etc otherwise
- Choose Architecture Style (Monolith, SOA - microservices, layered architecture, etc)
- Choose between cloud solution or on-premise servers
- Consider authentication/authorization and privacy
- Suggest security rules and protocols
- Define infrastructure: load balancing, messaging
- Make rough overview of any key algorithm that drives the service
- Consider bottlenecks and determine solutions
- Choose storage type (SQL or NoSQL)
- Understand what data should be cached and how to improve performance/security/availability with caching
- Choose monitoring system and logging. Analytics and automatically reboot system in case of exceptions
- Define separation between public and restricted areas
