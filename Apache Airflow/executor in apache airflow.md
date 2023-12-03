Apache airflow DON'T execute your task only define HOW run your task where

#### Executors example  

![[Pasted image 20231130115211.png]]

- Sequential Executor (Runs one by one No parallel )
- Local (Runs parallel with our local resources )
- Remote 
	- [[Celery Executor airflow ]] (Is the default in docker start Up)
	- K8s (Kubernetes)

