**HDFS Arquitecture**

 ![[Pasted image 20220401140153.png]]



**Name Nood**
[[Name nood]]

**How works**

**Reading a file in HDFS**
![[Pasted image 20220401140824.png]]

1. Client Node call to #Name_nood  and Name Node devuelve la informacion de donde esta ubicado esos #Blocks  de archivos
2. Client Node consulta la informacion en los data nodes



**Writing a file in HDFS**
![[Pasted image 20220401141254.png]]


1. Client Node call to Name Node y name Node asigna una entrada para ese archivo
2. Client Node go to create file and replicate information in Each Data node
3. Finalmente se va el mapeo de donde quedo la informacion a Name node

