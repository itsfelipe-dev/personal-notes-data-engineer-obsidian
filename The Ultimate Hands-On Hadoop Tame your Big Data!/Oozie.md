**Oozie**
	used to schedule Apache Hadoop jobs

Is usefull when have a task that invovles many diferents steps and maybe many different systems, in the [[Core Hadoop Ecosystem]]


There are two basic types of Oozie jobs:

-   **Oozie Workflow** jobs are Directed Acyclical Graphs (DAGs), specifying a sequence of actions to execute. The Workflow job has to wait.
-   **Oozie Coordinator** jobs are recurrent Oozie Workflow jobs that are triggered by time and data availability.

**Oozie Bundle** provides a way to package multiple coordinator and workflow jobs and to manage the lifecycle of those jobs.