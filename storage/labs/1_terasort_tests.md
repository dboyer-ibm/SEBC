* Create an end-user Linux account named with your GitHub handle
```
    useradd dboyer-ibm
    passwd dboyer-ibm
```
* Create a home HDFS directory for this user as well
```
[hdfs@ip-172-31-43-28 ~]$ hdfs dfs -mkdir /users/dboyer2-ibm
[hdfs@ip-172-31-43-28 ~]$ hdfs dfs -mkdir /user/dboyer-ibm
[hdfs@ip-172-31-43-28 ~]$ hdfs dfs -chown -R dboyer-ibm:dboyer-ibm /user/dboyer-ibm
```
* Run the following exercises as this user
* Create a 10 GB file using `teragen`
    * Set the number of mappers to four
    * Limit the block size to 32 MB
    * Land the result under your user's home directory
    * Use the `time` command to report the job's duration
```
[dboyer-ibm@ip-172-31-34-71 ~]$ time hadoop jar /opt/cloudera/parcels/CDH/jars/hadoop-mapreduce-examples-2.6.0-cdh5.8.3.jar teragen -Dmapred.map.tasks=4 -Ddfs.block.size=33554432 100000000 /user/dboyer-ibm/10gb
17/10/17 16:10:52 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-34-71.eu-west-1.compute.internal/172.31.34.71:8032
17/10/17 16:10:53 INFO terasort.TeraSort: Generating 100000000 using 4
17/10/17 16:10:53 INFO mapreduce.JobSubmitter: number of splits:4
17/10/17 16:10:53 INFO Configuration.deprecation: mapred.map.tasks is deprecated. Instead, use mapreduce.job.maps
17/10/17 16:10:53 INFO Configuration.deprecation: dfs.block.size is deprecated. Instead, use dfs.blocksize
17/10/17 16:10:53 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1508238440226_0018
17/10/17 16:10:53 INFO impl.YarnClientImpl: Submitted application application_1508238440226_0018
17/10/17 16:10:53 INFO mapreduce.Job: The url to track the job: http://ip-172-31-34-71.eu-west-1.compute.internal:8088/proxy/application_1508238440226_0018/
17/10/17 16:10:53 INFO mapreduce.Job: Running job: job_1508238440226_0018
17/10/17 16:10:59 INFO mapreduce.Job: Job job_1508238440226_0018 running in uber mode : false
17/10/17 16:10:59 INFO mapreduce.Job:  map 0% reduce 0%
...
17/10/17 16:13:35 INFO mapreduce.Job:  map 100% reduce 0%
17/10/17 16:13:36 INFO mapreduce.Job: Job job_1508238440226_0018 completed successfully
17/10/17 16:13:36 INFO mapreduce.Job: Counters: 31
        File System Counters
                FILE: Number of bytes read=0
                FILE: Number of bytes written=488516
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=344
                HDFS: Number of bytes written=10000000000
                HDFS: Number of read operations=16
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=8
        Job Counters 
                Launched map tasks=4
                Other local map tasks=4
                Total time spent by all maps in occupied slots (ms)=609033
                Total time spent by all reduces in occupied slots (ms)=0
                Total time spent by all map tasks (ms)=609033
                Total vcore-seconds taken by all map tasks=609033
                Total megabyte-seconds taken by all map tasks=623649792
        Map-Reduce Framework
                Map input records=100000000
                Map output records=100000000
                Input split bytes=344
                Spilled Records=0
                Failed Shuffles=0
                Merged Map outputs=0
                GC time elapsed (ms)=1394
                CPU time spent (ms)=164270
                Physical memory (bytes) snapshot=877428736
                Virtual memory (bytes) snapshot=6334480384
                Total committed heap usage (bytes)=869269504
        org.apache.hadoop.examples.terasort.TeraGen$Counters
                CHECKSUM=214760662691937609
        File Input Format Counters 
                Bytes Read=0
        File Output Format Counters 
                Bytes Written=10000000000

real    2m45.748s
user    0m6.661s
sys     0m0.331s
```
* Run the `terasort` command on this file
    * Use the `time` command to report the job's duration
    * Land the result under your user's home directory
```
[dboyer-ibm@ip-172-31-34-71 ~]$ time hadoop jar /opt/cloudera/parcels/CDH/jars/hadoop-mapreduce-examples-2.6.0-cdh5.8.3.jar terasort /user/dboyer-ibm/10gb /user/dboyer-ibm/10gb-sort                17/10/17 16:19:48 INFO terasort.TeraSort: starting
17/10/17 16:19:50 INFO input.FileInputFormat: Total input paths to process : 4
Spent 255ms computing base-splits.
Spent 6ms computing TeraScheduler splits.
Computing input splits took 262ms
Sampling 10 splits of 300
Making 6 from 100000 sampled records
Computing parititions took 909ms
Spent 1173ms computing partitions.
17/10/17 16:19:51 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-34-71.eu-west-1.compute.internal/172.31.34.71:8032
17/10/17 16:19:51 INFO mapreduce.JobSubmitter: number of splits:300
17/10/17 16:19:51 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1508238440226_0019
17/10/17 16:19:51 INFO impl.YarnClientImpl: Submitted application application_1508238440226_0019
17/10/17 16:19:51 INFO mapreduce.Job: The url to track the job: http://ip-172-31-34-71.eu-west-1.compute.internal:8088/proxy/application_1508238440226_0019/
17/10/17 16:19:51 INFO mapreduce.Job: Running job: job_1508238440226_0019
17/10/17 16:19:58 INFO mapreduce.Job: Job job_1508238440226_0019 running in uber mode : false
17/10/17 16:19:58 INFO mapreduce.Job:  map 0% reduce 0%
17/10/17 16:20:06 INFO mapreduce.Job:  map 1% reduce 0%
...
17/10/17 16:28:12 INFO mapreduce.Job: Job job_1508238440226_0019 completed successfully
17/10/17 16:28:12 INFO mapreduce.Job: Counters: 49
        File System Counters
                FILE: Number of bytes read=4444338556
                FILE: Number of bytes written=8824955019
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=10000045900
                HDFS: Number of bytes written=10000000000
                HDFS: Number of read operations=918
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=12
        Job Counters 
                Launched map tasks=300
                Launched reduce tasks=6
                Data-local map tasks=300
                Total time spent by all maps in occupied slots (ms)=2867554
                Total time spent by all reduces in occupied slots (ms)=1062213
                Total time spent by all map tasks (ms)=2867554
                Total time spent by all reduce tasks (ms)=1062213
                Total vcore-seconds taken by all map tasks=2867554
                Total vcore-seconds taken by all reduce tasks=1062213
                Total megabyte-seconds taken by all map tasks=2936375296
                Total megabyte-seconds taken by all reduce tasks=1087706112
        Map-Reduce Framework
                Map input records=100000000
                Map output records=100000000
                Map output bytes=10200000000
                Map output materialized bytes=4342784689
                Input split bytes=45900
                Combine input records=0
                Combine output records=0
                Reduce input groups=100000000
                Reduce shuffle bytes=4342784689
                Reduce input records=100000000
                Reduce output records=100000000
                Spilled Records=200000000
                Shuffled Maps =1800
                Failed Shuffles=0
                Merged Map outputs=1800
                GC time elapsed (ms)=37207
                CPU time spent (ms)=1459870
                Physical memory (bytes) snapshot=148488183808
                Virtual memory (bytes) snapshot=484590813184
                Total committed heap usage (bytes)=171946541056
        Shuffle Errors
                BAD_ID=0
                CONNECTION=0
                IO_ERROR=0
                WRONG_LENGTH=0
                WRONG_MAP=0
                WRONG_REDUCE=0
        File Input Format Counters 
                Bytes Read=10000000000
        File Output Format Counters 
                Bytes Written=10000000000
17/10/17 16:28:12 INFO terasort.TeraSort: done

real    8m24.835s
user    0m10.233s
sys     0m0.418s

```

