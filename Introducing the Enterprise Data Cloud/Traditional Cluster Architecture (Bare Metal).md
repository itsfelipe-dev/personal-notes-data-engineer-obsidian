![[Pasted image 20220510161259.png]]

	### Limitations of the Traditional Cluster Architecture

![[Pasted image 20220510170326.png]]



tart of transcript. Skip to the end.
Considering that thousands of organizations have
been using this architecture and production for more than a decade,
this architecture has been effective.
However, some limitations have become clear over time.
One is that the tight coupling of storage and compute
means that you can't scale them independently.
Some organizations need to rapidly expand storage capacity
in order to keep up with growth.
Other organizations may have sufficient storage
but require additional compute capacity
in order to support additional users,
new workloads or more sophisticated machine learning algorithms.
That storage,
the Hadoop distributed file system or HDFS
was designed to support a relatively modest number of large files,
at least several dozen megabytes in size.
This makes sense when using it to parse the
log files of a busy web server for example.
But what if you're trying to extract data from a few million documents
that might just be a few megabytes each?
Trying to store a large number of small files
leads to a problem so common that it has a name,
the small files problem.
It's the source of many blog posts and many support requests from our customers.
In short,
each file and HDFS has some associated metadata,
such as the file's owner,
group and its associated permissions.
For maximum performance
the HDFS name node service keeps all of this information in memory.
As you add more files,
the amount of memory required to maintain this metadata also increases.
At some point,
that amount of memory will approach the amount of
memory allocated to the name node process.
At which point you'll experience the small files problem.
Individual workloads compete with
one another for the clusters resources in a multi tenant environment.
To make an analogy,
imagine a large office with a single printer that's shared by everyone in that area.
It works well when a few people periodically print short documents,
but anyone who has ever worked in an office like this
knows that eventually an inconsiderate person will
print a 500 page report in the middle of the day,
causing everyone else's smaller jobs to queue up behind it.
Even though the boarding pass you're trying to print
before you head to the airport should just take 30 seconds,
it might actually take 30 minutes just to begin in this scenario.
Replace the word printer in this scenario with the word service
and you've got what's called the noisy neighbor problem.
Multiple teams might be using the cluster for data warehouse work,
perhaps doing simple queries for reporting purposes
and getting answers back in a few seconds or less.
Eventually someone is going to run a massive query that uses a lot of resources,
causing everyone else's queries to queue up and SLA's to be missed.
To avoid this sometimes organizations will move from
one big cluster to several smaller ones,
perhaps assigning one to each team.
Although that may solve the compute resource problem,
it creates a management problem because there are now multiple clusters to monitor,
upgrade, backup and maintain.
It also creates a data governance problem
because important business information is duplicated across multiple clusters
with no single source of truth
and very likely without consistent security policies.
When setting up a cluster,
the administrator must decide which services
such as Apache Spark, Hive or Impala
are going to run on that cluster.
As well as which service roles to deploy on each node.
This rigid mapping of services to nodes leads to an inefficient use of resources.
Imagine that an organization sets up a cluster with two specific workloads in mind.
The first is Data Engineering,
which uses Apache Spark and Hive to run a four hour ETL process,
gathering data from various sources,
cleaning it, transforming it and then loading it into the data warehouse.
That ETL job runs once per day very early in the morning.
The second workload is a data mark that business analysts query with Apache Impala
running ad hoc queries that help them to identify new opportunities.
They get into the office at nine a.m.
Several hours after the ETL job is finished
and they run these queries until they leave for the day.
Although those two workloads aren't happening concurrently,
they still compete for the finite resources of the machines where they're running.
This is because the resources are allocated on a service by service basis,
not based on which individual service happens to have the highest demand
at a given point in time.
In other words,
it's possible for one service to experience performance problems
due to a lack of memory,
even though another service on the same machine has plenty of unused memory.