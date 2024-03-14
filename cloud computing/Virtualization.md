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
    -  the guest OS is unaware that it is running in a virtualized environment.
+ Paravirtualization
    - Differs from full virtualization in that integrates virtualization handling code into OS – thus the guest OS code is modified
    -  the guest OS is aware that it is running in a virtualized environment
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

## Live VM migration
Live VM migration is a process in virtualization where a running virtual machine (VM) is moved from one physical host to another without experiencing any noticeable downtime or interruption in service. This is typically done to balance resource utilization, perform maintenance on physical hosts, or mitigate failures.

### iterative copy
One method of live VM migration

1. **Pre-Migration Phase**:
   - The source VM is running on a source physical host.
   - The destination physical host is prepared to receive the migrated VM.

2. **Initialization**:
   - The live migration process begins by establishing a communication channel between the source and destination hosts.
   - Both hosts synchronize their clocks to ensure accurate tracking of migration progress.

3. **Memory Iterative Copy**:
   - Initially, the memory contents of the source VM are copied iteratively to the destination host.
   - During this phase, the VM continues to run on the source host, and any changes to memory are tracked.
   - The iterative copy process repeats until a relatively small and manageable amount of memory remains dirty (i.e., changed since the last copy).

4. **Stop-and-Copy**:
   - Once the amount of dirty memory falls below a threshold, the VM is briefly paused on the source host to perform a final memory copy.
   - During this pause, any remaining dirty memory is transferred to the destination host.
   - The downtime experienced during this phase is typically minimal, often measured in milliseconds.

5. **Finalization**:
   - After the memory is successfully transferred, the VM resumes execution on the destination host.
   - The source VM is then deactivated on the source host, and resources are released.

Regarding the requirement for **shared storage** between source and destination VM for live migration, it depends on the specific implementation and method of migration. In some cases, shared storage may be required to ensure data consistency and minimize downtime. However, newer techniques, such as live migration with iterative copy, can perform migration without the need for shared storage between hosts. In these cases, the migration process focuses on transferring the memory state of the VM between hosts, rather than relying on shared storage.