# On-demand Infrastructure
## Storage Cloud from IaaS
Storage provided as a service
### example
+ AWS EBS(Elastic Block Store)
– Object based storage
    + Amazon S3(Simple Storage Service)
    + Google Storage Cloud
### Usage scenarios
– Snapshot VMs and stop VM and restart later on
– Customize AMIs(Amazon Machine Images)
– High availability

## Supporting Elasticity
### What do we need for elasticity?
- Detect when current resources are not able to meet the demand
- Request right amount of resources in time
- Add these resources to existing deployment
- Application should be able to use the additional capacity
- State vs stateless issues
### AWS
RightScale, Amazon AWS Autoscale and Elastic Load balancer

## AWS Cloud Front
+ S3 
+ HPC 
+ iRadeo

## public cloud
A multi-tenant cloud environment accessed over the internet

A public cloud is a cloud deployment model in which users access infrastructure and application services remotely via the internet from a third-party provider in a multi-tenant environment. Some of the top service providers in this market include AWS, Microsoft and Google. Services from the public cloud are often offered through a subscription model, such as pay per usage or on demand. The main benefits of public cloud are scalability, lower levels of wasted resources and reduced costs.

## benefit of private cloud? 

Three reasons:

1. **Enhanced Security and Compliance**: Private clouds offer greater control over data security and compliance requirements compared to public clouds. Enterprises can implement strict access controls, encryption protocols, and compliance measures tailored to their industry regulations or internal policies, ensuring sensitive data remains protected.

2. **Increased Performance and Reliability**: By hosting resources on-premises or in a dedicated infrastructure, enterprises can achieve higher performance and reliability compared to shared public cloud environments. Private clouds enable organizations to allocate resources based on their workload demands, ensuring consistent performance and availability for critical applications.

3. **Customization and Flexibility**: Private clouds provide greater customization and flexibility in resource allocation, infrastructure configurations, and deployment models. Enterprises can tailor the cloud environment to meet their specific business requirements, integrate with existing IT infrastructure seamlessly, and scale resources according to evolving needs without being constrained by the limitations of a public cloud provider.

## benefit of hybrid cloud? 
1. **Flexibility:** 
Hybrid cloud allows enterprises to leverage the scalability and cost-effectiveness of public cloud services while maintaining control over sensitive data and critical workloads in a private cloud environment.

2. **Disaster Recovery:** 
Enterprises can use hybrid cloud architectures to implement robust disaster recovery strategies. Critical workloads can run in the private cloud, while backup and failover resources are available in the public cloud, ensuring business continuity in case of disruptions.

3. **Cost Optimization:** 
Hybrid cloud enables enterprises to optimize costs by dynamically allocating workloads between public and private clouds based on resource requirements, performance demands, and budget constraints. This ensures efficient resource utilization while minimizing operational expenses.
Hybrid cloud complements the benefits of a private cloud by offering additional flexibility and versatility in workload deployment. 

## What does it mean when a public cloud provider has an availability of five nines?
Unavailable for potentially five minutes a year