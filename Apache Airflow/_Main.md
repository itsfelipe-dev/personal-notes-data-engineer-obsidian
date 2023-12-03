- Airflow is an orchestrator, not a processing framework. Process your gigabytes of data outside of Airflow (i.e. You have a Spark cluster, you use an operator to execute a Spark job, and the data is processed in Spark).
    
- A DAG is a data pipeline, an Operator is a task.
    
- An Executor defines how your tasks are executed, whereas a worker is a process executing your task
    
- The Scheduler schedules your tasks, the web server serves the UI, and the database stores the metadata of Airflow.

### Table of contents 

- #### What is an [[operator in apache airflow ]]
- #### What is an [[provider in apache airflow]]
- #### What is [[ the sensors in apache airflow]]
- #### What is a [[hook in apache airflow]]
- #### What is a [[DAG in apache airflow]]
- #### What is [[Backfilling in apache airflow]]
- #### What is [[ dataset in apache airflow]]
- #### What is [[ executor in apache airflow]]
- What is a [[queue in apache airflow]]
- What is [[xcom in apache  airlfow]]
- [[What is Elasticsearch]]


------------------------


Commands 
	Start flower dashboard ( Workers status )
		docker-compose down && docker-compose --profile flower up -d
