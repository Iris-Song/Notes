# Docker
## What is Docker?
+ Software platform that allows you to build, test, and deploy applications quickly
+ The code, OS, libraries, etc. are bundled together as a unit called container, which is independently deployed at scale
+ Think of it as Open Source Lambda functions
## Why Docker?
+ All the benefits of microservices PLUS
+ Platform-independent
    + You can port your code between Cloud providers or accounts with less effort than porting provider-specific services
+ Widespread developer support
## Docker on AWS
The painful way:
+ Run and manage your own Docker "swarm" on EC2
+ A cluster of Docker images orchestrated to run across one or more machines

The easy way:
+ Use Elastic Container Service (ECS), a highly-scalable, managed Docker container service from AWS
![](./img/ECS%20example.png)

# DevOps
## What is DevOps?
DevOps is a set of practices that automates the processes between software development and IT teams, in order that they can build, test, and release software faster and more reliably.

## Release process stages
![](./img/Release%20process%20stages%201.png)
![](./img/Release%20process%20stages%202.png)
### Continuous integration goals
1. Automatically kick off a new release when new code is checked in
2. Build and test code in a consistent, repeatable environment
3. Continually have an artifact ready for deployment
4. Continually close feedback loop when build fails

### AWS CodePipeline
+ Continuous delivery service for fast and reliable application updates
+ Model and visualize your software release process
+ Builds, tests, and deploys your code every time there is a code change
+ Integrates with third-party tools and AWS

### AWS CodeBuild
+ Fully managed build service that compiles source code, runs tests, and produces software packages
+ Scales continuously and processes multiple builds concurrently
+ No build servers to manage
+ Pay by the minute, only for the compute resources you use
+ Monitor builds through CloudWatch Events

### Continuous deployment goals
1. Automatically deploy new changes to staging environments for testing
2. Deploy to production safely without impacting customers
3. Deliver to customers faster: Increase deployment frequency, and reduce change lead time and change failure rate
### AWS CodeDeploy
+ Automates code deployments to any instance and Lambda
+ Handles the complexity of updating your applications
+ Avoid downtime during application deployment
+ Roll back automatically if failure detected
+ Deploy to Amazon EC2, Lambda, or on-premises servers

## Infrustructure
### AWS CloudFormation
"Infrastructure as Code"

Infrastructure, configuration, and security all encoded in config files called "templates"

Reproducible infrastructure safely and reliably

## Data Science