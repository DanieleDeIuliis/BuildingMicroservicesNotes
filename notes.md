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