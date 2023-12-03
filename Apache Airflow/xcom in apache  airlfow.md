Xcom is the way of share data between two task 
" Cross communication allows to exchange **SMALL** amount of data "

Limits of data:
	-MYSQL: 64 KB
	-Postgrest: 1GB 
	-SQLite : 2GB 

##### Case of use 

![[Pasted image 20231202131037.png]]

**First way** 
For the example bellow, you can use the traditional way of push to database and later retrain from this one, for gb and tb is worth it.

**Second way** 
The native way is using xcom a native tool of Apache airflow, who is in charge of store data, and retrieve from other task
![[Pasted image 20231202131209.png]]

#### Code example 
_Task 1 
```python
def _t1(ti):
    ti.xcom_push(key='my_key',value=42) #using ti parameter 
    #return 35  # one way to return values to airflow
```

_Task 2_
```python
def _t2(ti):
    #Pull the return values 
    ti.xcom_pull(key='my_key',task_ids='t1')
    None
```
