# System design cheat sheet 

It can be used for interviews or assesments.

## 1. Understand the problem and scope:
- Recognize stakeholders
i. Prioritaze them
ii. Create RACI matrix
- What is the business drivers of the project? <br>
i. Who is going to use it? <br>
ii. How are they going to use it? <br>
iii. How many users are there? <br>
iv. What does the system do? <br>
v. What are the inputs and outputs of the system? <br>
vi. How much data do we expect to handle? <br>
vii. How many requests per second do we expect? <br>
viii. What is the expected read to write ratio? <br>
- define the use cases, with interviewer's help
- suggest additional features
- remove items that interviewer deems out of scope
- assume high availibility is required, add as a use case
- Check functional requirements <br>

## 2. Think about constraints and non-functional requirements:
- (PASS ME if you not remember it)
- number of customers
- number of business growth in future
- average response time
- database size (current / for the next year/ for the next 5 years)
- storage size (current / for the next year/ for the next 5 years)
- using security protocols
- acceptable downtime of the system
- ask how many requests per month
- ask how many requests per second (they may volunteer it or make you do the math)
- estimate reads vs. writes percentage
- keep 80/20 rule in mide when estimating
- how much data written per second
- how much data read per second
- time to market

## 3. Detect Architecture Significant Requirements
- Mix between FRs and NFRs

## 4. Abstract design:
- Choose Architecture Style (Monolith, SOA - microservices, etc)
- Layers (presentation, service, data, caching)
- Cloud-solution or on-premise servers
- Authentication and Authorization	
- Security rules and protocols
- Infrastructure: load balancing, messaging
- Rough overview of any key algorithm that drives the service
- Consider bottlenecks and determine solutions
- Storage type (SQL or NoSQL)
- What data should be cached. How to improve performance/security/availability with caching.
- Monitoring system and logging. Analytics and automatical reboot system in case of exceptions.
- Separation between public and restricted areas.
