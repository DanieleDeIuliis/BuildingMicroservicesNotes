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
### Cohesion
*The code that changes together stays together.*

We need to find boundaries within our problem domain that help ensure related behaviour is in one place and that communicate with other boundaries as loosely as possible.
### Coupling
*A change in one part of system shouldn't require another change elsewhere.* 

When services are loosely coupled, a chage to one service shoul not require a change to another.

**A structure is stasble if cohesion is strong and coupling is low**
### Types of Coupling
#### Domain Coupling
One microservice needs to interact with another microservice, because the first microservice needs to make use of the functionality that the other microservice provides.
This type of interaction is largely unavoidable, but we still want to keep this to a minimum. A microservice that speaks with too many microservices it might be one that is doing too much.
#### Pass-Through Coupling 
One microservice passes data to another microservice purely because the data is needed by some other microservice further downstream.

It's one of the most problematic form of coupling because it implies that microservices know internalities of other microservices.
#### Common Coupling
Two or more microservices make use of a common set of data. The key point here is that the services know that they're using a shared resource.
#### Content Coupling
An upstream service reaches into the internals of a downstream service and changes its internal state.

It's more subtle than *Common Coupling* because the resource has not been devised to be shared, making the system harder to change.

