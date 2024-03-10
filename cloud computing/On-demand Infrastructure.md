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