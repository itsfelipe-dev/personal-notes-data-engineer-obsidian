SparkContext represents the connection to a Spark cluster, and can be used to create RDDs, accumulators and broadcast variables on that cluster.


- Is created by your driver program
- Is responsible for making RDD's resilient and distributed, in case of failure this can be recoverd and share in other nodes inside the cluster
- Creates [[Spark-RDD]]'s
- The spark shell creates a "sc" object for you  