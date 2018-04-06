# System design cheat sheet 

It can be used for interviews or assesments.

## 1. Understand the problem and scope:
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

## 2. Think about constraints and non-functional requirements:
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

## 3. Abstract design:
- layers (presentation, service, data, caching)
- cloud or ownership servers
- authorization
- security rules and protocols
- infrastructure: load balancing, messaging
- rough overview of any key algorithm that drives the service
- consider bottlenecks and determine solutions
- SQL or NoSQL




-----


Category	Key Engineering Decisions
Authentication and Authorization	
How to store user identities.
How to authenticate callers.
How to authorize callers.
How to flow identity across layers and tiers.
Caching and State	
How to choose effective caching strategies.
How to improve performance with caching.
How to improve security with caching.
How to improve availability with caching.
How to keep the cached data up to date.
How to determine when and why to use a custom cache.
How to determine what data to cache.
How to determine where to cache the data.
How to determine the expiration policy and scavenging mechanism.
How to load the cache data.
How to monitor a cache.
How to synchronize caches across a farm.
How to determine which caching technique provides the best performance and scalability for a specific scenario and configuration.
How to determine which caching technology complies with the application's requirements for security, monitoring, and management.
Communication	
How to communicate between layers / tiers.
How to perform asynchronous communication.
How to pass sensitive data.
Composition	
How do design for composition.
How to design loose coupling between modules.
How to handle dependencies in a loosely coupled way.
Concurrency and Transactions	
How to handle concurrency between threads.
How to choose between optimistic and pessimistic concurrency.
How to handle distributed transactions.
How to handle long running transactions.
How to determine appropriate transaction isolation levels.
How to determine when compensating transactions are required.
Configuration Management	
How to determine which information needs to be configurable.
How to determine where and how to store configuration information.
How to handle sensitive information.
How to handle configuration information in a farm/cluster.
Coupling and Cohesion	
How to separate concerns
How to structure the application.
How to choose an appropriate layering strategy.
How to establish boundaries.
Data Access	
How to manage database connections.
How to handle exceptions.
How to improve performance.
How to improve manageability.
How to handle blobs.
How to page records.
How to perform transactions.
Exception Management	
How to handle exceptions.
How to log exceptions.
Logging and Instrumentation	
How to determine which information to log.
How to make the logging configurable
User Experience	
How to improve task efficiency and effectiveness.
How to improve responsiveness.
How to improve user empowerment.
How to improve look and feel.
Validation	
How to determine where and how to perform validation.
How to validate for length, range, format, and type.
How to constrain and reject input.
How to sanitize output.
Workflow	
How to handle concurrency issues within a workflow
How to handle task failure within a workflow
How to orchestrate processes within a workflow

-----

Category	Key Issues
Authentication and Authorization	
Clear text credentials in configuration files
Passing clear text credentials over the network
Over-privileged accounts
Long sessions
Mixing personalization with authentication
Reliance on a single gatekeeper
Failing to lock down system resources against application identities
Failing to limit database access to specified stored procedures
Inadequate separation of privileges
Caching and State	
Cache misses.
Failure to expire items
Poor cache design
Lack of a cache synchronization mechanism for scaling out.
Communication	
Increased network traffic and latency due to chatty calls between layers.
Inappropriate transport protocols and wire formats.
Large data volumes over limited bandwidth networks.
Composition	Tightly coupled modules Duplication of code
Concurrency and Transactions	
Blocking calls
Nongranular locks
Misuing threads
Holding onto locks longer than necessary
Inappropriate isolation levels
Configuration Management	
Insecure administration interfaces
Insecure configuration stores
Clear text configuration data
Too many administrators
Over-privileged process accounts and service accounts
Coupling and Cohesion	
Limited scalability due to server and resource affinity.
Mixed presentation and business logic, which limits your options for scaling out your application.
Lifetime issues due to tight coupling.
Data Access	
Per user authentication and authorization when not required.
Chatty calls to database
Intersperse of business logic
Exception Management	
Leaving system / application in unstable state
Revealing sensitive information to end users.
Using exceptions for logic
Not logging enough details about the exception.
Logging and Instrumentation	
Lack of logging and instrumentation
Too fine grained logging and instrumentation
Not making logging and instrumentation configurable option at runtime
Failure to log business critical functionality.
User Experience	
Inefficient or ineffective task support.
Poor responsiveness.
Disempowered users.
Validation	
Application-only filters for malicious input
Non-validated input in the Hypertext Markup Language (HTML) output stream
Non-validated input used to generate SQL queries
Reliance on client-side validation
Use of input file names, URLs, or user names for security decisions
Workflow	
Tight coupling
Inflexible processes
Race and deadlock issues


-----



Category	Key Guidelines
Authentication and Authorization	
Consider single-sign on requirements.
Separate public and restricted areas.
Use account lockout policies for end-user accounts.
Support password expiration periods.
Be able to disable accounts.
Do not store passwords in user stores.
Require strong passwords.
Do not send passwords over the wire in plaintext.
Protect authentication cookies.
Use multiple gatekeepers.
Restrict user access to system-level resources.
Consider authorization granularity.
Caching and State	
Avoid caching per-user data.
Avoid caching volatile data which is required by the user to be accurate and updated in real time.
Cache data that does not change very frequently or is completely static.
Do not cache shared expensive resources.
Cache transformed data, keeping in mind the data use.
Evaluate stateful versus stateless design.
Consider your state store options.
Minimize session data.
Free session resources as soon as possible.
Avoid accessing session variables from business logic.
Communication	
Choose the appropriate remote communication mechanism.
Design chunky interfaces.
Consider how to pass data between layers.
Minimize the amount of data sent across the wire.
Batch work to reduce calls over the network.
Reduce transitions across boundaries.
Consider asynchronous communication.
Consider message queuing.
Consider a "fire and forget" invocation model.
Cut call chains with queues and caches as much as possible. Doing so will enhance the scalability and availability of the overall solution.
Push out asynchronous boundaries close to the user, service interfaces, and service agents, to isolate your service from external dependencies.
If you need to expose functionality as a synchronous operation, evaluate whether you can wrap an internally asynchronous operation as described in the following discussion
Composition	
Avoid using dynamic layouts that are difficult to load and maintain.
Be careful with dependencies between components. Use abstraction patterns when possible to avoid issues with maintainability.
Consider creating templates with placeholders. For example use the Template View pattern to compose dynamic web pages to ensure reuse and consistency.
Consider composing views from reusable modular parts. For example use the Composite View pattern to build a view from modular, atomic component parts.
Use well-known design patterns to implement a composite interface containing separate modules or user controls where appropriate.
Modules should not directly reference one another or the application that loaded them.
Modules should use services to communicate with the application or with other modules.
Modules should not be responsible for managing their dependencies.
Modules should support being added and removed from the system in a pluggable fashion.
Concurrency and Transactions	
Treat threads as a shared resource.
Pool shared or scarce resources.
Acquire late, release early.
Consider efficient object creation and destruction.
Consider resource throttling.
Reduce contention by minimizing lock times.
Balance between coarse- and fine-grained locks.
Choose an appropriate transaction isolation level.
Avoid long-running atomic transactions.
Configuration Management	
Protect your administration interfaces.
Protect your configuration store.
Maintain separate administration privileges.
Use least privileged process and service accounts.
Coupling and Cohesion	
Partition application functionality into logical layers.
Choose the proper locality for your objects based on your reliability, performance, and scalability needs.
Design for loose coupling.
Design for high cohesion.
Use early binding where possible.
Evaluate resource affinity.
Data Access	
If your application uses a single database, use the database-specific data provider.
If you need to support multiple databases, you generally need to have an abstraction layer, which helps you transparently connect to the currently configured store.
Consider resource throttling.
Consider the identities you flow to the database.
Separate read-only and transactional requests.
Avoid unnecessary data returns.
Exception Management	
Avoid revealing sensitive data to users.
Do not use exceptions to control application flow.
Use validation code to avoid unnecessary exceptions.
Do not catch exceptions that you cannot handle.
Be aware that rethrowing is expensive.
Preserve as much diagnostic information as possible in your exception handlers.
Logging and Instrumentation	
Instrument your code up front.
Make your logging configurable.
User Experience	
Measure effectiveness against scenarios.
Improve user responsiveness where possible.
Model from effective user design.
Validation	
Validate for length, range, format, and type.
Constrain and reject input.
Sanitize output.
Don’t rely on client-side validation.
Workflow	
Determine management requirements. If a business user needs to manage the workflow, you’ll need a solution that provides an interface that the business user can understand.
Determine how exceptions will be handled.
With human workflow, you need to consider the un-deterministic nature of humans. In other words, you can’t determine when a task will be completed, or if it will be completed correctly.
Use service interfaces to interact with external workflow providers.
If supported, use designers and metadata to define the workflow instead of code to define the workflow.
