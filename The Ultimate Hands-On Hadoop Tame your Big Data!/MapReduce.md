**MapReduce** ([[Mappers]] and [[reducers]])
Programming model to procces data the entire cluster

**Why MapReduce**
- Divides data into partitions thath are MAPPED (transofrmed  ) and REDUCE ( Agregated ) by [[Mappers]] and [[reducers]] fuctions you define
-
- Distrubutes the processing of data in the [[cluster]] 

- Resilent to failure - an application master monitors your [[Mappers]] and [[reducers]] on each partiton

**Steps to working MapReduce**
1. Mappers
2. Suffle and Short (Normalizacion de datos, unir y acortar la mayoria de datos posibles) (Start with the smaller user ID )
		(Nodos  pueden trabajar en paralelo, cada nodo se puede encargar de reducir individualemnte y al final juntarlos en el siguiente paso)
3. Reducer (USER ID: (Lengt array item)(cuantos elementos contiene un item y solo pone el numero))
![[Pasted image 20220404111951.png]]



![[Pasted image 20220404113323.png]]


**How are mappers and reducers written**
	- MapReduce is natively Java code
	- STREAMING allows interfacig to other lenguages (ie python)
	- ![[Pasted image 20220404115424.png]]


**Handling Failure MapReduce**

![[Pasted image 20220404115410.png]]




**Python MapReduce Script**
**![[Pasted image 20220404132655.png]]**


