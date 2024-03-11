# Kubernetes
## Concept
#### Cluster 
A collection of hosts that aggregate their available resources including cpu, ram, disk, and their devices into a usable pool.
#### Master 
The master(s) represent a collection of components that make up the control plane of Kubernetes. These components are responsible for all cluster decisions including both scheduling and responding to cluster events.
#### Node 
A single host, physical or virtual capable of running pods. A node is managed by the master(s), and at a minimum runs both kubelet and kube-proxy to be considered part of the cluster.
#### Namespace  
A logical cluster or environment. Primary method of dividing a cluster or scoping access.
#### Label 
Key-value pairs that are used to identify, describe and group together related sets of objects. Labels have a strict syntax and available character set. *
#### Annotation 
Key-value pairs that contain non-identifying information or metadata. Annotations do not have the the syntax limitations as labels and can contain structured or unstructured data.
#### Selector 
Selectors use labels to filter or select objects. Both equality-based (=, ==, !=) or simple key-value matching selectors are supported.
#### Pod
A pod is the smallest unit of work or management resource within Kubernetes. It is comprised of one or more containers that share their storage, network, and context (namespace, cgroups etc).
#### ReplicationController 
Method of managing pod replicas and their lifecycle. Their scheduling, scaling, and deletion.
#### ReplicaSet 
Next Generation ReplicationController. Supports set-based selectors.
#### Deployment 
A declarative method of managing stateless Pods and ReplicaSets. Provides rollback functionality in addition to more granular update control mechanisms.
#### Service 
Services provide a method of exposing and consuming L4 Pod network accessible resources. They use label selectors to map groups of pods and ports to a cluster-unique virtual IP.
+ Acts as the unified method of accessing replicated pods.
+ Four major Service Types:
    + CluterIP - Exposes service on a strictly cluster-internal IP (default)
    + NodePort - Service is exposed on each node’s IP on a statically defined port.
    + LoadBalancer - Works in combination with a cloud provider to expose a service outside the cluster on a static external IP.
    + ExternalName - used to references endpoints OUTSIDE the cluster by providing a static internally referenced DNS name.
#### Ingress 
An ingress controller is the primary method of exposing a cluster service (usually http) to the outside world. These are load balancers or routers that usually offer SSL termination, name-based virtual hosting etc.
+ Deployed as a pod to one or more hosts
+ Ingress controllers are an external controller with multiple options.
    + Nginx
    + HAproxy 
    + Contour 
    + Traefik
+ Specific features and controller specific configuration is passed through annotations.
### Storage
+ Volume - Storage that is tied to the Pod Lifecycle, consumable by one or more containers within the pod.
+ PersistentVolume - A PersistentVolume (PV) represents a storage resource. PVs are commonly linked to a backing storage resource, NFS, GCEPersistentDisk, RBD etc. and are provisioned ahead of time. Their lifecycle is handled independently from a pod.
+ PersistentVolumeClaim - A PersistentVolumeClaim (PVC) is a request for storage that satisfies a set of requirements instead of mapping to a storage resource directly. Commonly used with dynamically provisioned storage.
### ConfigMap 
Externalized data stored within kubernetes that can be referenced as a command line argument, environment variable, or injected as a file into a volume mount. Ideal for separating containerized application from configuration.
### Secret 
Functionally identical to ConfigMaps, but stored encoded as base64, and encrypted at rest (if configured).
## What is Kubernetes?
Kubernetes (K8s) is an open-source container orchestration platform that automates the deployment, scaling, and management of containerized applications.

Originally developed by Google, Kubernetes is now maintained by the Cloud Native Computing Foundation (CNCF) and has gained widespread adoption in the industry.

At its core, Kubernetes provides a platform for automating the deployment, scaling, and management of containerized applications.

## What Does Kubernetes do?
+ **Container Orchestration:** Kubernetes schedules and manages containers, ensuring they run in a reliable and scalable manner.
+ **Automated Scaling:** It can automatically scale applications up or down based on demand.
+ **Load Balancing:** Kubernetes can distribute traffic across multiple containers for high availability.
+ **Self-Healing:** It detects and replaces failed containers to maintain application health.
+ Rollouts and Rollbacks: Kubernetes facilitates controlled updates and rollbacks of application versions.
+ **Resource Management:** It efficiently allocates computing resources to containers.

## Architecture
![](./img/Kubernetes%20Architecture.png)
### Masters
Acts as the primary control plane for Kubernetes. Masters are responsible at a minimum for running the API Server, scheduler, and cluster controller. They commonly also manage storing cluster state, cloud-provider specific components and other cluster essential services.

#### Master Components
+ Kube-apiserver
    - central control point for the entire Kubernetes cluster
    - Exposes the Kubernetes API
    - Accepts and processes RESTful API requests
    - Implements authentication, authorization, and admission control for security.
+ Etcd
    - A distributed and highly-available key-value store that acts as Kubernetes' primary database.
    - Stores all configuration data and cluster state information.
+ Kube-controller-manager
    - Manages controllers that regulate the state of the system to match the desired state.
    - Ensures that the correct number of Pod replicas are running and healthy, helping in fault tolerance.
    - Reconciles the current state of resources with the desired state specified in the configuration, making necessary adjustments.
    - Helps in automatic scaling and self-healing of applications.
+ Cloud-controller-manager(CCM)
    - offloads cloud-specific functionality from the core Kubernetes control plane. 
    - used in managed Kubernetes services provided by cloud providers (such as AWS EKS, GKE, or Azure AKS) and is designed to improve the separation of concerns between Kubernetes and cloud provider-specific operations
+ Kube-scheduler
    - Monitors the API Server for new Pods without assigned nodes.
    - Selects an appropriate node for each Pod based on resource requirements, constraints, and policies.
    - Takes into account factors like CPU and memory availability, anti-affinity rules, and node capacity.

### Nodes 
Are the ‘workers’ of a Kubernetes cluster. They run a minimal agent that manages the node itself, and are tasked with executing workloads as designated by the master.
- Kubelet
    - Pod Supervisor
    - Pod Lifecycle Management
    - Health Checks
    - Resource Management
- Kube-proxy
    - Network Proxy: responsible for network routing within the cluster.
    - Service Load Balancing
    - Packet Forwarding
- Container runtime engine

## Network
### Fundamental Rules
+ All nodes can communicate with all Pods (and vice-versa) without NAT. 
+ The IP that a Pod sees itself as is the same IP that others see it as.

### Fundamentals Applied
+ **Containers** in a pod exist within the same network namespace and share an IP; allowing for intrapod communication over localhost.
+ **Pods** are given a cluster unique IP for the duration of its lifecycle, but the pods themselves are fundamentally ephemeral.
+ **Services** are given a persistent cluster unique IP that spans the Pods lifecycle.
+ **External Connectivity** is generally handed by an integrated cloud provider or other external entity (load balancer)