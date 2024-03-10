# Micro-Service

### Challenges with Monolithic Systems
- Code complexity and maintainability
- Deployment becomes the bottleneck
- Fear to change
- Lack of ownership
- Failure dependencies
- One size doesn’t fit all
- Hard to scale out

### Microservices to the rescue!
- An architectural pattern
- Split the application into multiple services that:
    + Are small
    + Use simple protocols
    + Are loosely-coupled
    + Can be independently deployed
    + each can be written in a different language

### Benefits of Microservices
#### Speed
Faster development & deployments
#### Innovation
+ Autonomy of teams, culture of change
+ Ownership and DevOps culture
#### Quality
● Composability and
reusability
● More maintainable
code
● Better scaling and
optimizations
● Failure Isolation
and Resiliency

### Microservices++: Serverless Components
+ No servers to manage
+ Scalability out of the box
+ Minimize codebase size
+ Pay per usage
+ Extremely low cost (usually fractions of a cent)
#### AWS example
+ Lambda 
+ API Gateway 
+ Cognito 
+ IAM

### Asynchronous Workflows
#### What?
process credit card transactions asynchronously
#### Why?
+ defend against traffic spikes
    + 3rd party services are subject to downtime too
+ defend against programming errors and bugs
+ execute intricate order workflows, without impacting the user experience
#### AWS example
+ SQS
+ Lambda
+ SNS