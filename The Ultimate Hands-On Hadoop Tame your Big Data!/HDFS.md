**HDFS** 
Hadoop Distrubuted file system
File system what do they have the hard drive
(Allows your big data to be stored across an entire cluster in a distributed manner, allows the applications to analyze that data to access that data)

- Optimized to Manage big files, very large to distrube across the entire [[cluster]], 128 (Megabytes default size of each block) 
- (Spilt large files into blocks)
![[Pasted image 20220401124126.png]]


#Blocks
-  Breaking data into blocks and save each part in multiples hardive 
	- Each blocks have default size to (128MB)  
	-  Diferentes computadores puede acceder a cada parte simultaneamente, ya que no es solo un archivo si no varios. Accediendo de manera mas eficiente
	![[Pasted image 20220401124526.png]]
	- each part (block blue square ), can be store across several computers.
	 - Save several copy's of each block. In order to handle failure (Para manejar caidas)
		 - Varios backups en varias computadores, espejos

[[HDFS Arquitecture]]
![[Pasted image 20220401124954.png]]



#Api_for_accessing_storage_CDP
![[Pasted image 20220607103823.png]]