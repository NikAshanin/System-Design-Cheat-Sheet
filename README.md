# System design cheat sheet 

It can be used for interviews or assesments.

## 1. Understand the problem and scope:
- What is the business drivers of the project?
- define the use cases, with interviewer's help
- suggest additional features
- remove items that interviewer deems out of scope
- assume high availibility is required, add as a use case

## 2. Think about constraints and non-functional requirements:
- number of customers
- number of business growth in future
- average response time
- database size
- using security protocols
- acceptable downtime of the system
- ask how many requests per month
- ask how many requests per second (they may volunteer it or make you do the math)
- estimate reads vs. writes percentage
- keep 80/20 rule in mide when estimating
- how much data written per second
- total storage required over 5 years
- how much data read per second

## 3. Abstract design:
- layers (service, data, caching)
- infrastructure: load balancing, messaging
- rough overview of any key algorithm that drives the service
- consider bottlenecks and determine solutions





-----

Step 1: Outline use cases, constraints, and assumptions
Gather requirements and scope the problem. Ask questions to clarify use cases and constraints. Discuss assumptions.

Who is going to use it?
How are they going to use it?
How many users are there?
What does the system do?
What are the inputs and outputs of the system?
How much data do we expect to handle?
How many requests per second do we expect?
What is the expected read to write ratio?
Step 2: Create a high level design
Outline a high level design with all important components.

Sketch the main components and connections
Justify your ideas
Step 3: Design core components
Dive into details for each core component. For example, if you were asked to design a url shortening service, discuss:

Generating and storing a hash of the full url
MD5 and Base62
Hash collisions
SQL or NoSQL
Database schema
Translating a hashed url to the full url
Database lookup
API and object-oriented design
Step 4: Scale the design
Identify and address bottlenecks, given the constraints. For example, do you need the following to address scalability issues?

Load balancer
Horizontal scaling
Caching
Database sharding
Discuss potential solutions and trade-offs. Everything is a trade-off. Address bottlenecks using principles of scalable system design.

