


#Dag_scheduling

- **Parameters**:
	- ###### Start_date: 
		- The time timestamp from from witch the scheduler will attempt to  execute 
	- Schedule_interval: 
		- How often a DAG runs in cron expression 
	- End_date: 
		- The tiemstap from witch a DAG ends  in cron expression 



- **Code Example**

```python
with DAG('user_processing', start_date=datetime(2023,11,29),
         schedule_interval='@daily', catchup=False)as dag:
	         some_awesome_stuff
```



#### Multiple DAGS with schedule interval every 1 minutes 

![[Pasted image 20231130100229.png]]



- Is task1 >> task2 >> task3 >> task4 equals to task4 << task3 << task2 << task1 ?
	R = Yes is the same is the requirements to be executed the dependency tree 


- Let's assume a DAG `start_date` to the 28/10/2021:10:00:00 PM UTC and the DAG is turned on at 10:30:00 PM UTC with a `schedule_interval` of */10 * * * * (After every 10 minutes). How many DagRuns are going to be executed?

	#### R: 2 times
	You right! The first one is executed at 10:10 for the execution_date 10:00, then 10:20 for the execution_date 10:20. DAG Run 3 is not yet executed since a DAG Run runs once the schedule_interval (10 minutes here) is passed.


#### Subdags (link dags in other dag)

#subdags_in_airflow  

The downloads row, contains multiple task is like linking dags (workflows)
call one dag from other dag 

![[Pasted image 20231130204426.png]]

##### Downloads dag 

![[Pasted image 20231130204524.png]]


**Code example***
dags
	subdags 
		|
		------- subdags_dowloads.py
		
	group_dag.py 

 - subdags_dowloads.py ( children )
 ````python
from airflow import DAG
from airflow.operators.bash import BashOperator

def subdag_downloads(parent_dag_id, child_dag_id, args): #define subdags function

	with DAG(f"{parent_dag_id}.{child_dag_id}",
		#Recive parameters from group_dag who is the Father
		start_date=args['start_date'],
		schedule_interval=args['schedule_interval'],
		catchup=args['catchup']) as dag:
		
		download_a = BashOperator(
			task_id='download_a',
			bash_command='sleep 10'
		)

		download_b = BashOperator(
		task_id='download_b',
		bash_command='sleep 10'

		)

		download_c = BashOperator(
		task_id='download_c',
		bash_command='sleep 10'

		)

		return dag





```

``````
```
```


- group_dag.py ( Father )
```python
from airflow import DAG
from airflow.operators.bash import BashOperator
from airflow.operators.subdag import SubDagOperator
from subdags.subdags_dowloads import subdag_downloads
from datetime import datetime

with DAG('group_dag', start_date=datetime(2022, 1, 1), 
    schedule_interval='@daily', catchup=False) as dag:
	args = {'start_date':dag.start_date, 'schedule_interval': dag.schedule_interval, 'catchup':dag.catchup}  
	#Calls to children def 
	downloads = SubDagOperator(
            task_id = 'downloads',
            subdag=subdag_downloads(dag.dag_id, 'downloads', args)
            
	)

	check_files = BashOperator(
		task_id='check_files',
		bash_command='sleep 10'
	)

	transform_a = BashOperator(
		task_id='transform_a',
		bash_command='sleep 10'
	)

	transform_b = BashOperator(
		task_id='transform_b',
		bash_command='sleep 10'
	)

	transform_c = BashOperator(
		task_id='transform_c',
		bash_command='sleep 10'
	)

	downloads >> check_files >> [transform_a, transform_b, transform_c]

```



### GROUP DAGS
Is the new way to do sub dags should be in groups folder 

![[Pasted image 20231201125124.png]]

Children = [ Group_downloads.py, group_transforms.py ]
Father = [ group_dag.py ]

