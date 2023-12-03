
Gives the option to wait data to execute the next step, second DAG are gonna to be only executed when the dataset is ready, can wait multiple data

![[Pasted image 20231130114210.png]]

The producer generate two datasets and consumer waits until booth requirements are meet 

**Producer code***
```python
from airflow import DAG, Dataset
from airflow.decorators import task
from datetime import datetime

my_file = Dataset("/tmp/my_file.txt")
my_file_2 = Dataset("/tmp/my_file_2.txt")

with DAG(
    dag_id="producer",
    schedule="@daily",
    start_date=datetime(2023, 11, 30),
    catchup=False,
):
    # as soon this task finished triggers the consumer dag
    @task(outlets=[my_file])
    def update_dataset():
        with open(my_file.uri, "a+") as f:
            f.write("producer update")


    @task(outlets=[my_file_2])
    def update_dataset_2():
        with open(my_file_2.uri, "a+") as f:
            f.write("producer update 2")

    update_dataset() >> update_dataset_2()
```

**Consumer code***
```PYTHON 
from airflow import DAG, Dataset
from airflow.decorators import task
from datetime import datetime

my_file = Dataset("/tmp/my_file.txt")
my_file_2 = Dataset("/tmp/my_file_2.txt")

with DAG(
    dag_id="consumer",
    schedule=[my_file,my_file_2], # Wait to datasets
    start_date=datetime(2023, 11, 30),
    catchup=False,

):
    @task
    def read_dataset():
        with open(my_file.uri, "r") as f:
            print(f.read())
    read_dataset()
```

**Parameters**
	- URI : Unique identifier of your data  | Path of your data | only accepts ASCII characters | case sensitive  
```python
from airflow import Dataset 

#Valid Datasets
schemeless = Dataset("/path/file.txt")
csv_file = Dataset("file.csv")
```
- EXTRA :
```python 
from airflow import Dataaset 

my_file = Dataset(
				  "s3://dataset/file.csv",
				  extra={'owner'='james'}, # you can put whatever, is public row
				  
)
```

![[Pasted image 20231130105012.png]]


#### Datasets limitations
Datasets are amazing, but they have limitations as well:

  

- DAGs can only use Datasets in the same Airflow instance. A DAG cannot wait for a Dataset defined in another Airflow instance.
    
- Consumer DAGs are triggered every time a task that updates datasets completes successfully. **Airflow doesn't check whether the data has been effectively updated.**
    
- You can't combine different schedules like datasets with cron expressions.
    
- If two tasks update the same dataset, as soon as one is done, that triggers the Consumer DAG immediately without waiting for the second task to complete.
    
- Airflow monitors datasets only within the context of DAGs and Tasks. If an external tool updates the actual data represented by a Dataset, Airflow has no way of knowing that.