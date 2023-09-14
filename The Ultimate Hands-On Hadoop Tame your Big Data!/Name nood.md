**Name Nood**
#Name_nood
	keeps trak of where all those blocks live. (Nodo maestro, mapea la ubicacion los #Blocks  de archivos). Haciendo el traking de los Data Nodes
- Mantiene los logs de what is created and what is modfied . Keep all track of where everythigs is as thigs get moved


**Como se protege un Name Nood en caso de fallo?** (Porque es el mas importante donde esta el mapeo de toda la informacion)

![[Pasted image 20220401154447.png]]

**- Back up metadata** 
	Name Nodes writes to local disk and [[NFS]] and backup this data in other rack or in other data center.
	And later restore backup to other node 

- **Secondey NameNode** (Mirror node, espejo)
	- Maintain merged copy of logs (mapeo) what can be restore 

**HDFS Federation**
	- Each name node manages a specific namespace volume

**HDFS Higt Avatilibily **

- Hot standby namenode using shared edit log
- Zookepper tracks active name node
-  Uses extreme mesures to ensure only one namenode is used at time, Because use more the system goings down 