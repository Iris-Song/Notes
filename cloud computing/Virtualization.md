# Virtualization

### Physical Machines/ Virtual Machines/ Containers
![](./img/Physical%20Machines:%20Virtual%20Machines:%20Containers.png)
Hypervisor = VMM(Virtual Machine Monitor)

### Virtualization
+ Actually an old concept since 1960's invented by IBM,available on mainframes
+ Virtualization is a technology
+ Cloud computing is a service that is enabled by virtualization technology
![](./img/Before%20and%20After%20Virtualization.png)

### Advantages of virtualization
+ Run **multiple** operating systems on a single physical system and share the underlying hardware resources - known as **partitioning**.
+ A virtual infrastructure gives administrators the advantage of **managing pooled resources** across the enterprise.
+ Enables **Server Consolidation and Containment** - Eliminating 'server sprawl' via deployment of systems as virtual machines (VMs) that can run safely and move transparently across shared hardware, and increase server utilization rates from 5-15% to 60-80%. Can also help save power (smaller energy bills via consolidation).
+ **Test and Development Optimization** - Rapidly provisioning test and development servers by reusing pre-configured systems, enhancing developer collaboration and standardizing development environments.
+ **Improved Business Continuity** - Reducing the cost and complexity of business continuity (high availability and disaster recovery solutions) by encapsulating entire systems into single files that can be replicated and restored on any target server, thus minimizing downtime.

### Types of Virtualization
+ Hardware emulation
    - Most complex: a hardware VM is created for each instance
+ Full Virtualization
    - Uses hypervisor to share underlying hardware across guest VMs
    - Mediates between guest OS and underlying h/w
+ Paravirtualization
    - Differs from full virtualization in that integrates virtualization handling code into OS – thus the guest OS code is modified
+ Operating system level virtualization
    - Virtualizes server on top of operating systems
    - Single OS that isolates the servers

### Three types of virtualization (for CPU)
Depending on how hypervisor handles the critical instructions from OS (ring 0), there are different virtualization methods
- Full virtualization using binary translation
- OS assisted virtualization or Paravirtualization 
- Hardware assisted virtualization
![](./img/Three%20types%20of%20virtualization.png)
![](./img/Comparison%20of%20Three%20Virtualization%20Methods.png)
### Hypervisor and VMM
Hypervisor runs on bare metal machine
Functionality/role of hypervisor is dependent of type of virtualization

### Memory Virtualization
Memory virtualization requires further virtualization of OS level virtual memory

Another level of MMU virtualization that maps multiple MMU into physical memory
![](./img/Memory%20Virtualization.png)

### Device and I/O Virtualization
+ Requires managing the routing of I/O requests between virtual devices and shared physical hardware
+ Example: Virtual Network Interface and switches
+ Virtual devices emulate the physical devices