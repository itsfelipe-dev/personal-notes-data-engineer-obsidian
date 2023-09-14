 
### Impala is  [[MPP]]  a query engine that runs on Hadoop

Apache _Impala_ is a distributed SQL query engine for Apache _Hadoop_.

 Compared with MapReduce Impala divides the entire query into an execution plan tree instead of a series of MapReduce tasks. After distributing the execution plan, Impala uses the pull method to obtain the results, and the result data is composed according to the execution tree.

![[Pasted image 20220614160542.png]]



**Difference Between Hive Vs Impala**

**Hive**: Relying on the MapReduce execution framework, the execution plan is divided into a model of map->shuffle->reduce->map->shuffle->reduce. 
If a query will be compiled into multiple rounds of MapReduce, there will be more writing intermediate results

Due to the characteristics of the MapReduce execution framework itself, too many intermediate processes will increase the execution time of the entire query.

**Impala**: The execution plan is represented as a complete execution plan tree, which can more naturally distribute the execution plan to each Impalad to execute the query, instead of combining it into a pipeline map->reduce mode like Hive.

It proves that Impala has better concurrency and avoids unnecessary intermediate sort and shuffle.


impala has a [[MPP]] architecture
Doesn't use a Map/Reduce, and make the queries directly in HDFS

Use more CPU and memory than hive 

![[Pasted image 20220614161742.png]]