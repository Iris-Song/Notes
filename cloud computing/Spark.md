# Spark

## Motivation
Using Map Reduce for complex jobs, interactive queries and online processing involves lots of disk I/O

The price of memory is becoming lower. Lower cost means can put more memory in each server, can keep more data in memory.

### Issue with MapReduce
+ too much typing
+ too low level
+ not suitable for applications that processing streaming data

## RDD(Resilient Distributed Datasets)
### Why RDD immutable is a good choice?
1. **fault tolerance**
2. ensures data **consistency**, make easy for recovery
3. **Parallelism**: operations can be safely performed on different partitions concurrently, enabling efficient parallel processing and scaling to large datasets.

### Restricted form of distributed shared memory
- Immutable, partitioned collections of records
- Can only be built through coarse-grained deterministic transformations (map, filter, join, ...)
- Computations carried out and stored in memory
### Efficient fault recovery using lineage/provenance
- Track operations applied to data
- Re-execute operations to recompute lost partitions only on failure
- No cost if nothing fails 
  
## Spark vs Map Reduce
Difference:
![](./img/Spark%20and%20Map%20Reduce%20Differences.jpeg)

Other Spark and Map Reduce Differences
+ Generalized patterns
   - unified engine for many use cases
+  Lazy evaluation of the lineage graph
   - reduces wait states, better pipelining
+  Lower overhead for starting jobs
+  Less expensive shuffles
  
## Action & Transformation
Action: reduce, take, collect, takeOrdered, lookup, save
