* Choose a partner in class
==> Romain CASSIAU : github=rcassiau
* Name a source directory after your GitHub handle
```
hdfs dfs -mkdir /user/dboyer-ibm
```
* Name a target directory after your partner's GitHub handle
```
hdfs dfs -mkdir /user/rcassiau
```
* Use `teragen` to create a 500 MB file
```
yarn jar /opt/cloudera/parcels/CDH/jars/hadoop-mapreduce-examples-2.6.0-cdh5.8.3.jar teragen -Dmapred.map.tasks=6 5120000 /user/dboyer-ibm/test
```
* Copy your partner's file to your target directory 
    * Let one partner use `distCp` on the command line
```
The command looked like hadoop distcp hdfs://34.253.82.44/user/rcassiau /user/dboyer
Using internal IPs, this part did not work because of the lack of communication between internal addresses at AMAZON.
Using external IPS, the mapper part worked in local, while the reduce one failed
We think a solution could be to use Amazon VPC, but this will have to be tried later if we have time.	
Locally, the distcp worked as expected:
```

```
hdfs dfs -ls /user/dboyer-ibm/test
Found 7 items
-rw-r--r--   3 dboyer-ibm dboyer-ibm          0 2017-10-17 13:58 /user/dboyer-ibm/test/_SUCCESS
-rw-r--r--   3 dboyer-ibm dboyer-ibm   85333400 2017-10-17 13:58 /user/dboyer-ibm/test/part-m-00000
-rw-r--r--   3 dboyer-ibm dboyer-ibm   85333300 2017-10-17 13:58 /user/dboyer-ibm/test/part-m-00001
-rw-r--r--   3 dboyer-ibm dboyer-ibm   85333300 2017-10-17 13:58 /user/dboyer-ibm/test/part-m-00002
-rw-r--r--   3 dboyer-ibm dboyer-ibm   85333400 2017-10-17 13:58 /user/dboyer-ibm/test/part-m-00003
-rw-r--r--   3 dboyer-ibm dboyer-ibm   85333300 2017-10-17 13:58 /user/dboyer-ibm/test/part-m-00004
-rw-r--r--   3 dboyer-ibm dboyer-ibm   85333300 2017-10-17 13:58 /user/dboyer-ibm/test/part-m-00005
```

```
hadoop distcp hdfs:///user/dboyer-ibm/test/ /user/dboyer-ibm/test2
```

```
hdfs dfs -ls /user/dboyer-ibm/test2/
Found 7 items
-rw-r--r--   3 dboyer-ibm dboyer-ibm          0 2017-10-17 15:36 /user/dboyer-ibm/test2/_SUCCESS
-rw-r--r--   3 dboyer-ibm dboyer-ibm   85333400 2017-10-17 15:36 /user/dboyer-ibm/test2/part-m-00000
-rw-r--r--   3 dboyer-ibm dboyer-ibm   85333300 2017-10-17 15:36 /user/dboyer-ibm/test2/part-m-00001
-rw-r--r--   3 dboyer-ibm dboyer-ibm   85333300 2017-10-17 15:36 /user/dboyer-ibm/test2/part-m-00002
-rw-r--r--   3 dboyer-ibm dboyer-ibm   85333400 2017-10-17 15:36 /user/dboyer-ibm/test2/part-m-00003
-rw-r--r--   3 dboyer-ibm dboyer-ibm   85333300 2017-10-17 15:36 /user/dboyer-ibm/test2/part-m-00004
-rw-r--r--   3 dboyer-ibm dboyer-ibm   85333300 2017-10-17 15:36 /user/dboyer-ibm/test2/part-m-00005
```

    * Let the other use BDR
Romain used BDR

* Browse the results 
    * Use `hdfs fsck <path> -files -blocks` on your source and target directories

