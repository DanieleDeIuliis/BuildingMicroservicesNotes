# Building Microservices (Sam Newman) notes
## Chapter 1: What are microservices?
### Advantages
- Technology heterogeneity
- Robustness: A fail in a microservice shouldn't cascade and involve the entire system.
- Scaling
- Ease of Deployment
- Organisational
- Composability
### Disadvantages/ Pain points
- Developer Experience: multiple services might impact the feasibility of local development
- Technology Overload: Using too many technologies might be overwhelming 
- Cost: Multiple services -> multiple costs
- Reporting: Splitting the database might compromise the reporting process.
- Monitoring and Troubleshooting: The system has to be observable, thus requiring a way to gather the logs in one place
- Security: Multiple services are more susceptible to man in the middle attacks. In general, more services means more points to be worried about
- Testing: Integration tests are trickier
- Latency
- Data Consistency: Achieving ACID properties requires a new set of challenges (e.g. *Sagas*)
## Chaopter 2: How to Model Microservices
In essence, microservices are just another form of modular decomposition. There are three main factors that decides whether a microservice is well tailored:
- Information Hiding
- Cohesion
- Coupling
### Information Hiding
Information hiding describes a desire to hide as many details as possible behind a module boundary.
Benefits:
- Improved development time: Having modules implies parallel work without friction
- Comprehensibility: Each module can be looked at in isolation and understood in isolation.
- Flexibility: Modules can be changed independently of one another.

From Parnas' Information Distribution Aspects: *The connections between modules are the assumptions which the modules make about each other*.

By reducing the number of assumptions that one module makes about another, we directly impact the connections between them. By keeping
the number of assumptions small, it's easier to ensure that we can change one module without impacting the others.
