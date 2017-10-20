```
[ernest@ip-172-31-44-121 ~]$ time hadoop jar /opt/cloudera/parcels/CDH/jars/hadoop-mapreduce-examples-2.6.0-cdh5.9.3.jar teragen -Dmapred.map.tasks=6 -Ddfs.block.size=33554432 51200000 /user/ernest/tgen512
17/10/20 11:48:11 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-39-82.eu-west-1.compute.internal/172.31.39.82:8032
17/10/20 11:48:12 INFO terasort.TeraSort: Generating 51200000 using 6
17/10/20 11:48:12 INFO mapreduce.JobSubmitter: number of splits:6
17/10/20 11:48:12 INFO Configuration.deprecation: mapred.map.tasks is deprecated. Instead, use mapreduce.job.maps
17/10/20 11:48:12 INFO Configuration.deprecation: dfs.block.size is deprecated. Instead, use dfs.blocksize
17/10/20 11:48:12 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1508491853318_0003
17/10/20 11:48:12 INFO impl.YarnClientImpl: Submitted application application_1508491853318_0003
17/10/20 11:48:12 INFO mapreduce.Job: The url to track the job: http://ip-172-31-39-82.eu-west-1.compute.internal:8088/proxy/application_1508491853318_0003/
17/10/20 11:48:12 INFO mapreduce.Job: Running job: job_1508491853318_0003
17/10/20 11:48:20 INFO mapreduce.Job: Job job_1508491853318_0003 running in uber mode : false
17/10/20 11:48:20 INFO mapreduce.Job:  map 0% reduce 0%
17/10/20 11:48:35 INFO mapreduce.Job:  map 1% reduce 0%
17/10/20 11:48:38 INFO mapreduce.Job:  map 2% reduce 0%
17/10/20 11:48:41 INFO mapreduce.Job:  map 3% reduce 0%
17/10/20 11:48:47 INFO mapreduce.Job:  map 4% reduce 0%
17/10/20 11:48:50 INFO mapreduce.Job:  map 5% reduce 0%
17/10/20 11:48:57 INFO mapreduce.Job:  map 6% reduce 0%
17/10/20 11:48:58 INFO mapreduce.Job:  map 8% reduce 0%
17/10/20 11:49:00 INFO mapreduce.Job:  map 9% reduce 0%
17/10/20 11:49:01 INFO mapreduce.Job:  map 12% reduce 0%
17/10/20 11:49:02 INFO mapreduce.Job:  map 13% reduce 0%
17/10/20 11:49:04 INFO mapreduce.Job:  map 15% reduce 0%
17/10/20 11:49:06 INFO mapreduce.Job:  map 16% reduce 0%
17/10/20 11:49:07 INFO mapreduce.Job:  map 18% reduce 0%
17/10/20 11:49:10 INFO mapreduce.Job:  map 20% reduce 0%
17/10/20 11:49:13 INFO mapreduce.Job:  map 21% reduce 0%
17/10/20 11:49:17 INFO mapreduce.Job:  map 22% reduce 0%
17/10/20 11:49:19 INFO mapreduce.Job:  map 23% reduce 0%
17/10/20 11:49:20 INFO mapreduce.Job:  map 25% reduce 0%
17/10/20 11:49:21 INFO mapreduce.Job:  map 27% reduce 0%
17/10/20 11:49:22 INFO mapreduce.Job:  map 30% reduce 0%
17/10/20 11:49:23 INFO mapreduce.Job:  map 36% reduce 0%
17/10/20 11:49:25 INFO mapreduce.Job:  map 38% reduce 0%
17/10/20 11:49:26 INFO mapreduce.Job:  map 40% reduce 0%
17/10/20 11:49:27 INFO mapreduce.Job:  map 41% reduce 0%
17/10/20 11:49:28 INFO mapreduce.Job:  map 42% reduce 0%
17/10/20 11:49:29 INFO mapreduce.Job:  map 44% reduce 0%
17/10/20 11:49:30 INFO mapreduce.Job:  map 45% reduce 0%
17/10/20 11:49:31 INFO mapreduce.Job:  map 47% reduce 0%
17/10/20 11:49:32 INFO mapreduce.Job:  map 49% reduce 0%
17/10/20 11:49:34 INFO mapreduce.Job:  map 51% reduce 0%
17/10/20 11:49:35 INFO mapreduce.Job:  map 53% reduce 0%
17/10/20 11:49:36 INFO mapreduce.Job:  map 54% reduce 0%
17/10/20 11:49:37 INFO mapreduce.Job:  map 55% reduce 0%
17/10/20 11:49:38 INFO mapreduce.Job:  map 57% reduce 0%
17/10/20 11:49:40 INFO mapreduce.Job:  map 59% reduce 0%
17/10/20 11:49:41 INFO mapreduce.Job:  map 62% reduce 0%
17/10/20 11:49:42 INFO mapreduce.Job:  map 63% reduce 0%
17/10/20 11:49:43 INFO mapreduce.Job:  map 64% reduce 0%
17/10/20 11:49:44 INFO mapreduce.Job:  map 67% reduce 0%
17/10/20 11:49:45 INFO mapreduce.Job:  map 68% reduce 0%
17/10/20 11:49:47 INFO mapreduce.Job:  map 71% reduce 0%
17/10/20 11:49:48 INFO mapreduce.Job:  map 72% reduce 0%
17/10/20 11:49:49 INFO mapreduce.Job:  map 73% reduce 0%
17/10/20 11:49:50 INFO mapreduce.Job:  map 75% reduce 0%
17/10/20 11:49:51 INFO mapreduce.Job:  map 76% reduce 0%
17/10/20 11:49:52 INFO mapreduce.Job:  map 77% reduce 0%
17/10/20 11:49:53 INFO mapreduce.Job:  map 79% reduce 0%
17/10/20 11:49:54 INFO mapreduce.Job:  map 80% reduce 0%
17/10/20 11:49:55 INFO mapreduce.Job:  map 82% reduce 0%
17/10/20 11:49:56 INFO mapreduce.Job:  map 83% reduce 0%
17/10/20 11:49:58 INFO mapreduce.Job:  map 85% reduce 0%
17/10/20 11:49:59 INFO mapreduce.Job:  map 88% reduce 0%
17/10/20 11:50:01 INFO mapreduce.Job:  map 89% reduce 0%
17/10/20 11:50:02 INFO mapreduce.Job:  map 91% reduce 0%
17/10/20 11:50:04 INFO mapreduce.Job:  map 92% reduce 0%
17/10/20 11:50:05 INFO mapreduce.Job:  map 95% reduce 0%
17/10/20 11:50:07 INFO mapreduce.Job:  map 96% reduce 0%
17/10/20 11:50:08 INFO mapreduce.Job:  map 98% reduce 0%
17/10/20 11:50:09 INFO mapreduce.Job:  map 99% reduce 0%
17/10/20 11:50:11 INFO mapreduce.Job:  map 100% reduce 0%
17/10/20 11:50:11 INFO mapreduce.Job: Job job_1508491853318_0003 completed successfully
17/10/20 11:50:11 INFO mapreduce.Job: Counters: 31
        File System Counters
                FILE: Number of bytes read=0
                FILE: Number of bytes written=741294
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=511
                HDFS: Number of bytes written=5120000000
                HDFS: Number of read operations=24
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=12
        Job Counters 
                Launched map tasks=6
                Other local map tasks=6
                Total time spent by all maps in occupied slots (ms)=426086
                Total time spent by all reduces in occupied slots (ms)=0
                Total time spent by all map tasks (ms)=426086
                Total vcore-seconds taken by all map tasks=426086
                Total megabyte-seconds taken by all map tasks=436312064
        Map-Reduce Framework
                Map input records=51200000
                Map output records=51200000
                Input split bytes=511
                Spilled Records=0
                Failed Shuffles=0
                Merged Map outputs=0
                GC time elapsed (ms)=1359
                CPU time spent (ms)=109460
                Physical memory (bytes) snapshot=1767018496
                Virtual memory (bytes) snapshot=9511907328
                Total committed heap usage (bytes)=1857028096
        org.apache.hadoop.examples.terasort.TeraGen$Counters
                CHECKSUM=109963291816450258
        File Input Format Counters 
                Bytes Read=0
        File Output Format Counters 
                Bytes Written=5120000000

real    2m3.977s
user    0m7.039s
sys     0m0.480s
```
```
hdfs dfs -ls /user/ernest/tgen512m
Found 7 items
-rw-r--r--   3 ernest ernest          0 2017-10-20 11:49 /user/ernest/tgen512m/_SUCCESS
-rw-r--r--   3 ernest ernest  853333400 2017-10-20 11:48 /user/ernest/tgen512m/part-m-00000
-rw-r--r--   3 ernest ernest  853333300 2017-10-20 11:48 /user/ernest/tgen512m/part-m-00001
-rw-r--r--   3 ernest ernest  853333300 2017-10-20 11:48 /user/ernest/tgen512m/part-m-00002
-rw-r--r--   3 ernest ernest  853333400 2017-10-20 11:48 /user/ernest/tgen512m/part-m-00003
-rw-r--r--   3 ernest ernest  853333300 2017-10-20 11:48 /user/ernest/tgen512m/part-m-00004
-rw-r--r--   3 ernest ernest  853333300 2017-10-20 11:49 /user/ernest/tgen512m/part-m-00005
```

```
[ernest@ip-172-31-44-121 ~]$ hdfs fsck  /user/ernest/tgen512 -blocks
Connecting to namenode via http://ip-172-31-44-231.eu-west-1.compute.internal:50070
FSCK started by ernest (auth:SIMPLE) from /172.31.44.121 for path /user/ernest/tgen512 at Fri Oct 20 11:54:04 CEST 2017
.......Status: HEALTHY
 Total size:    5120000000 B
 Total dirs:    1
 Total files:   7
 Total symlinks:                0
 Total blocks (validated):      156 (avg. block size 32820512 B)
 Minimally replicated blocks:   156 (100.0 %)
 Over-replicated blocks:        0 (0.0 %)
 Under-replicated blocks:       0 (0.0 %)
 Mis-replicated blocks:         0 (0.0 %)
 Default replication factor:    3
 Average block replication:     3.0
 Corrupt blocks:                0
 Missing replicas:              0 (0.0 %)
 Number of data-nodes:          3
 Number of racks:               1
FSCK ended at Fri Oct 20 11:54:04 CEST 2017 in 6 milliseconds


The filesystem under path '/user/ernest/tgen512' is HEALTHY
```
