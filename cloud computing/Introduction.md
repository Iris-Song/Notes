# Introduction

## What is Cloud?
Allows users to request computing/storage resources and services through web interfaces
- You do not need to own or install or manage these resources.
- Pay as you go - Resources on-demand
- Elastic: Use as much as you want or as less as you want
    + Users can assume infinite amount of compute and storage resources are available.
    + Users can request resources when and what they need and release/remove resources when they don’t need.
- Compute and storage resources are now treated as software entities. You get access to such resources programmatically – not by physical hardware anymore!
- Example Clouds:
    + AWS
    + Google Cloud
    + Azure

## Why Cloud?
- **on-demand** 
- **elastic**

## Web App
an application program that is stored on a remote server and delivered over the internet through a browser interface.
#### Key Components
- backend server stack
    + web server
    + application server
    + database
- frontend/client
- APIs
- network connectivity
#### Different Architecture
![](./img/Web%20App%20Arch1.png)
![](./img/Web%20App%20Arch2.png)
![](./img/Web%20App%20Arch%20scaling1.png)
![](./img/Web%20App%20Arch%20scaling2.png)
write can only on Masrer DB
![](./img/Web%20App%20Arch%20scaling%20cache.png)
A Content Delivery Network (CDN) is a distributed network of servers that deliver web content to users based on their geographic location.

## Service Model
### Cloud Software as a Service (SaaS)
The capability provided to the consumer is to use the provider’s **applications** running on a cloud infrastructure. The applications are accessible from various client devices through a thin client interface such as a web browser (e.g., web-based email). The consumer does not manage or control the underlying cloud infrastructure including network, servers, operating systems, storage, or even individual application capabilities, with the possible exception of limited user-specific application configuration settings.
### Cloud Platform as a Service (PaaS) 
The capability provided to the consumer is to deploy onto the cloud infrastructure consumer-created or acquired applications created using programming languages and tools supported by the provider. The consumer does not manage or control the underlying cloud infrastructure including network, servers, operating systems, or storage, but has control over the deployed applications and possibly application hosting environment configurations.
- Azure App Service
- AWS Elastic Beanstalk
- Google App Engine
### Cloud Infrastructure as a Service (IaaS) 
The capability provided to the consumer is to **provision processing, storage, networks, and other fundamental computing resources** where the consumer is able to deploy and run arbitrary software, which can include operating systems and applications. The consumer does not manage or control the underlying cloud infrastructure but has control over operating systems, storage, deployed applications, and possibly limited control of select networking components (e.g., host firewalls).
- EC2
![](./img/The%20Layers%20of%20IT-as-a-Service.png)
- Higher the stack, less control but more automation for user
- Lower the stack, more control but more responsibility for user