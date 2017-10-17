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
[dboyer-ibm@ip-172-31-34-71 ~]$ hadoop jar /opt/cloudera/parcels/CDH/jars/hadoop-mapreduce-examples-2.6.0-cdh5.8.3.jar teragen 50000000 /user/dboyer-ibm/512M
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
[dboyer-ibm@ip-172-31-34-71 ~]$ hadoop distcp hdfs:///user/dboyer-ibm/512M/ /user/dboyer-ibm/512M2
17/10/17 16:39:46 INFO tools.DistCp: Input Options: DistCpOptions{atomicCommit=false, syncFolder=false, deleteMissing=false, ignoreFailures=false, overwrite=false, skipCRC=false, blocking=true, numListstatusThreads=0, maxMaps=20, mapBandwidth=100, sslConfigurationFile='null', copyStrategy='uniformsize', preserveStatus=[], preserveRawXattrs=false, atomicWorkPath=null, logPath=null, sourceFileListing=null, sourcePaths=[hdfs:/user/dboyer-ibm/512M], targetPath=/user/dboyer-ibm/512M2, targetPathExists=false, filtersFile='null'}
17/10/17 16:39:46 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-34-71.eu-west-1.compute.internal/172.31.34.71:8032
17/10/17 16:39:47 INFO tools.SimpleCopyListing: Paths (files+dirs) cnt = 4; dirCnt = 1
17/10/17 16:39:47 INFO tools.SimpleCopyListing: Build file listing completed.
17/10/17 16:39:47 INFO Configuration.deprecation: io.sort.mb is deprecated. Instead, use mapreduce.task.io.sort.mb
17/10/17 16:39:47 INFO Configuration.deprecation: io.sort.factor is deprecated. Instead, use mapreduce.task.io.sort.factor
17/10/17 16:39:47 INFO tools.DistCp: Number of paths in the copy list: 4
17/10/17 16:39:47 INFO tools.DistCp: Number of paths in the copy list: 4
17/10/17 16:39:47 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-34-71.eu-west-1.compute.internal/172.31.34.71:8032
17/10/17 16:39:47 INFO mapreduce.JobSubmitter: number of splits:3
17/10/17 16:39:48 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1508238440226_0021
17/10/17 16:39:48 INFO impl.YarnClientImpl: Submitted application application_1508238440226_0021
17/10/17 16:39:48 INFO mapreduce.Job: The url to track the job: http://ip-172-31-34-71.eu-west-1.compute.internal:8088/proxy/application_1508238440226_0021/
17/10/17 16:39:48 INFO tools.DistCp: DistCp job-id: job_1508238440226_0021
17/10/17 16:39:48 INFO mapreduce.Job: Running job: job_1508238440226_0021
17/10/17 16:39:54 INFO mapreduce.Job: Job job_1508238440226_0021 running in uber mode : false
17/10/17 16:39:54 INFO mapreduce.Job:  map 0% reduce 0%
17/10/17 16:39:59 INFO mapreduce.Job:  map 33% reduce 0%
17/10/17 16:40:04 INFO mapreduce.Job:  map 67% reduce 0%
17/10/17 16:40:05 INFO mapreduce.Job:  map 100% reduce 0%
17/10/17 16:41:13 INFO mapreduce.Job: Job job_1508238440226_0021 completed successfully
17/10/17 16:41:13 INFO mapreduce.Job: Counters: 33
        File System Counters
                FILE: Number of bytes read=0
                FILE: Number of bytes written=375183
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=5000001834
                HDFS: Number of bytes written=5000000000
                HDFS: Number of read operations=56
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=13
        Job Counters 
                Launched map tasks=3
                Other local map tasks=3
                Total time spent by all maps in occupied slots (ms)=152134
                Total time spent by all reduces in occupied slots (ms)=0
                Total time spent by all map tasks (ms)=152134
                Total vcore-seconds taken by all map tasks=152134
                Total megabyte-seconds taken by all map tasks=155785216
        Map-Reduce Framework
                Map input records=4
                Map output records=0
                Input split bytes=366
                Spilled Records=0
                Failed Shuffles=0
                Merged Map outputs=0
                GC time elapsed (ms)=269
                CPU time spent (ms)=38510
                Physical memory (bytes) snapshot=792207360
                Virtual memory (bytes) snapshot=4750909440
                Total committed heap usage (bytes)=856162304
        File Input Format Counters 
                Bytes Read=1468
        File Output Format Counters 
                Bytes Written=0
        org.apache.hadoop.tools.mapred.CopyMapper$Counter
                BYTESCOPIED=5000000000
                BYTESEXPECTED=5000000000
                COPY=4
```

    * Let the other use BDR
      Romain used BDR

* Browse the results 
    * Use `hdfs fsck <path> -files -blocks` on your source and target directories

```
[dboyer-ibm@ip-172-31-34-71 ~]$ hdfs fsck /user/dboyer-ibm/512M -files -blocks                    
Connecting to namenode via http://ip-172-31-42-52.eu-west-1.compute.internal:50070
FSCK started by dboyer-ibm (auth:SIMPLE) from /172.31.34.71 for path /user/dboyer-ibm/512M at Tue Oct 17 16:44:10 CEST 2017
/user/dboyer-ibm/512M <dir>
/user/dboyer-ibm/512M/_SUCCESS 0 bytes, 0 block(s):  OK

/user/dboyer-ibm/512M/part-m-00000 2500000000 bytes, 19 block(s):  OK
0. BP-1226871346-172.31.42.52-1508234690456:blk_1073744239_3415 len=134217728 Live_repl=3
1. BP-1226871346-172.31.42.52-1508234690456:blk_1073744240_3416 len=134217728 Live_repl=3
2. BP-1226871346-172.31.42.52-1508234690456:blk_1073744242_3418 len=134217728 Live_repl=3
3. BP-1226871346-172.31.42.52-1508234690456:blk_1073744244_3420 len=134217728 Live_repl=3
4. BP-1226871346-172.31.42.52-1508234690456:blk_1073744246_3422 len=134217728 Live_repl=3
5. BP-1226871346-172.31.42.52-1508234690456:blk_1073744248_3424 len=134217728 Live_repl=3
6. BP-1226871346-172.31.42.52-1508234690456:blk_1073744250_3426 len=134217728 Live_repl=3
7. BP-1226871346-172.31.42.52-1508234690456:blk_1073744252_3428 len=134217728 Live_repl=3
8. BP-1226871346-172.31.42.52-1508234690456:blk_1073744254_3430 len=134217728 Live_repl=3
9. BP-1226871346-172.31.42.52-1508234690456:blk_1073744256_3432 len=134217728 Live_repl=3
10. BP-1226871346-172.31.42.52-1508234690456:blk_1073744258_3434 len=134217728 Live_repl=3
11. BP-1226871346-172.31.42.52-1508234690456:blk_1073744261_3437 len=134217728 Live_repl=3
12. BP-1226871346-172.31.42.52-1508234690456:blk_1073744263_3439 len=134217728 Live_repl=3
13. BP-1226871346-172.31.42.52-1508234690456:blk_1073744265_3441 len=134217728 Live_repl=3
14. BP-1226871346-172.31.42.52-1508234690456:blk_1073744267_3443 len=134217728 Live_repl=3
15. BP-1226871346-172.31.42.52-1508234690456:blk_1073744269_3445 len=134217728 Live_repl=3
16. BP-1226871346-172.31.42.52-1508234690456:blk_1073744271_3447 len=134217728 Live_repl=3
17. BP-1226871346-172.31.42.52-1508234690456:blk_1073744273_3449 len=134217728 Live_repl=3
18. BP-1226871346-172.31.42.52-1508234690456:blk_1073744275_3451 len=84080896 Live_repl=3

/user/dboyer-ibm/512M/part-m-00001 2500000000 bytes, 19 block(s):  OK
0. BP-1226871346-172.31.42.52-1508234690456:blk_1073744238_3414 len=134217728 Live_repl=3
1. BP-1226871346-172.31.42.52-1508234690456:blk_1073744241_3417 len=134217728 Live_repl=3
2. BP-1226871346-172.31.42.52-1508234690456:blk_1073744243_3419 len=134217728 Live_repl=3
3. BP-1226871346-172.31.42.52-1508234690456:blk_1073744245_3421 len=134217728 Live_repl=3
4. BP-1226871346-172.31.42.52-1508234690456:blk_1073744247_3423 len=134217728 Live_repl=3
5. BP-1226871346-172.31.42.52-1508234690456:blk_1073744249_3425 len=134217728 Live_repl=3
6. BP-1226871346-172.31.42.52-1508234690456:blk_1073744251_3427 len=134217728 Live_repl=3
7. BP-1226871346-172.31.42.52-1508234690456:blk_1073744253_3429 len=134217728 Live_repl=3
8. BP-1226871346-172.31.42.52-1508234690456:blk_1073744255_3431 len=134217728 Live_repl=3
9. BP-1226871346-172.31.42.52-1508234690456:blk_1073744257_3433 len=134217728 Live_repl=3
10. BP-1226871346-172.31.42.52-1508234690456:blk_1073744260_3436 len=134217728 Live_repl=3
11. BP-1226871346-172.31.42.52-1508234690456:blk_1073744262_3438 len=134217728 Live_repl=3
12. BP-1226871346-172.31.42.52-1508234690456:blk_1073744264_3440 len=134217728 Live_repl=3
13. BP-1226871346-172.31.42.52-1508234690456:blk_1073744266_3442 len=134217728 Live_repl=3
14. BP-1226871346-172.31.42.52-1508234690456:blk_1073744268_3444 len=134217728 Live_repl=3
15. BP-1226871346-172.31.42.52-1508234690456:blk_1073744270_3446 len=134217728 Live_repl=3
16. BP-1226871346-172.31.42.52-1508234690456:blk_1073744272_3448 len=134217728 Live_repl=3
17. BP-1226871346-172.31.42.52-1508234690456:blk_1073744274_3450 len=134217728 Live_repl=3
18. BP-1226871346-172.31.42.52-1508234690456:blk_1073744276_3452 len=84080896 Live_repl=3

Status: HEALTHY
 Total size:    5000000000 B
 Total dirs:    1
 Total files:   3
 Total symlinks:                0
 Total blocks (validated):      38 (avg. block size 131578947 B)
 Minimally replicated blocks:   38 (100.0 %)
 Over-replicated blocks:        0 (0.0 %)
 Under-replicated blocks:       0 (0.0 %)
 Mis-replicated blocks:         0 (0.0 %)
 Default replication factor:    3
 Average block replication:     3.0
 Corrupt blocks:                0
 Missing replicas:              0 (0.0 %)
 Number of data-nodes:          3
 Number of racks:               1
FSCK ended at Tue Oct 17 16:44:10 CEST 2017 in 2 milliseconds


The filesystem under path '/user/dboyer-ibm/512M' is HEALTHY
```

```
[dboyer-ibm@ip-172-31-34-71 ~]$ hdfs fsck /user/dboyer-ibm/512M2 -files -blocks
Connecting to namenode via http://ip-172-31-42-52.eu-west-1.compute.internal:50070
FSCK started by dboyer-ibm (auth:SIMPLE) from /172.31.34.71 for path /user/dboyer-ibm/512M2 at Tue Oct 17 16:44:37 CEST 2017
/user/dboyer-ibm/512M2 <dir>
/user/dboyer-ibm/512M2/_SUCCESS 0 bytes, 0 block(s):  OK

/user/dboyer-ibm/512M2/part-m-00000 2500000000 bytes, 19 block(s):  OK
0. BP-1226871346-172.31.42.52-1508234690456:blk_1073744295_3471 len=134217728 Live_repl=3
1. BP-1226871346-172.31.42.52-1508234690456:blk_1073744298_3474 len=134217728 Live_repl=3
2. BP-1226871346-172.31.42.52-1508234690456:blk_1073744300_3476 len=134217728 Live_repl=3
3. BP-1226871346-172.31.42.52-1508234690456:blk_1073744302_3478 len=134217728 Live_repl=3
4. BP-1226871346-172.31.42.52-1508234690456:blk_1073744304_3480 len=134217728 Live_repl=3
5. BP-1226871346-172.31.42.52-1508234690456:blk_1073744306_3482 len=134217728 Live_repl=3
6. BP-1226871346-172.31.42.52-1508234690456:blk_1073744308_3484 len=134217728 Live_repl=3
7. BP-1226871346-172.31.42.52-1508234690456:blk_1073744310_3486 len=134217728 Live_repl=3
8. BP-1226871346-172.31.42.52-1508234690456:blk_1073744312_3488 len=134217728 Live_repl=3
9. BP-1226871346-172.31.42.52-1508234690456:blk_1073744314_3490 len=134217728 Live_repl=3
10. BP-1226871346-172.31.42.52-1508234690456:blk_1073744316_3492 len=134217728 Live_repl=3
11. BP-1226871346-172.31.42.52-1508234690456:blk_1073744319_3495 len=134217728 Live_repl=3
12. BP-1226871346-172.31.42.52-1508234690456:blk_1073744321_3497 len=134217728 Live_repl=3
13. BP-1226871346-172.31.42.52-1508234690456:blk_1073744323_3499 len=134217728 Live_repl=3
14. BP-1226871346-172.31.42.52-1508234690456:blk_1073744326_3502 len=134217728 Live_repl=3
15. BP-1226871346-172.31.42.52-1508234690456:blk_1073744328_3504 len=134217728 Live_repl=3
16. BP-1226871346-172.31.42.52-1508234690456:blk_1073744330_3506 len=134217728 Live_repl=3
17. BP-1226871346-172.31.42.52-1508234690456:blk_1073744332_3508 len=134217728 Live_repl=3
18. BP-1226871346-172.31.42.52-1508234690456:blk_1073744333_3509 len=84080896 Live_repl=3

/user/dboyer-ibm/512M2/part-m-00001 2500000000 bytes, 19 block(s):  OK
0. BP-1226871346-172.31.42.52-1508234690456:blk_1073744294_3470 len=134217728 Live_repl=3
1. BP-1226871346-172.31.42.52-1508234690456:blk_1073744297_3473 len=134217728 Live_repl=3
2. BP-1226871346-172.31.42.52-1508234690456:blk_1073744299_3475 len=134217728 Live_repl=3
3. BP-1226871346-172.31.42.52-1508234690456:blk_1073744301_3477 len=134217728 Live_repl=3
4. BP-1226871346-172.31.42.52-1508234690456:blk_1073744303_3479 len=134217728 Live_repl=3
5. BP-1226871346-172.31.42.52-1508234690456:blk_1073744305_3481 len=134217728 Live_repl=3
6. BP-1226871346-172.31.42.52-1508234690456:blk_1073744307_3483 len=134217728 Live_repl=3
7. BP-1226871346-172.31.42.52-1508234690456:blk_1073744309_3485 len=134217728 Live_repl=3
8. BP-1226871346-172.31.42.52-1508234690456:blk_1073744311_3487 len=134217728 Live_repl=3
9. BP-1226871346-172.31.42.52-1508234690456:blk_1073744313_3489 len=134217728 Live_repl=3
10. BP-1226871346-172.31.42.52-1508234690456:blk_1073744315_3491 len=134217728 Live_repl=3
11. BP-1226871346-172.31.42.52-1508234690456:blk_1073744317_3493 len=134217728 Live_repl=3
12. BP-1226871346-172.31.42.52-1508234690456:blk_1073744320_3496 len=134217728 Live_repl=3
13. BP-1226871346-172.31.42.52-1508234690456:blk_1073744322_3498 len=134217728 Live_repl=3
14. BP-1226871346-172.31.42.52-1508234690456:blk_1073744324_3500 len=134217728 Live_repl=3
15. BP-1226871346-172.31.42.52-1508234690456:blk_1073744325_3501 len=134217728 Live_repl=3
16. BP-1226871346-172.31.42.52-1508234690456:blk_1073744327_3503 len=134217728 Live_repl=3
17. BP-1226871346-172.31.42.52-1508234690456:blk_1073744329_3505 len=134217728 Live_repl=3
18. BP-1226871346-172.31.42.52-1508234690456:blk_1073744331_3507 len=84080896 Live_repl=3

Status: HEALTHY
 Total size:    5000000000 B
 Total dirs:    1
 Total files:   3
 Total symlinks:                0
 Total blocks (validated):      38 (avg. block size 131578947 B)
 Minimally replicated blocks:   38 (100.0 %)
 Over-replicated blocks:        0 (0.0 %)
 Under-replicated blocks:       0 (0.0 %)
 Mis-replicated blocks:         0 (0.0 %)
 Default replication factor:    3
 Average block replication:     3.0
 Corrupt blocks:                0
 Missing replicas:              0 (0.0 %)
 Number of data-nodes:          3
 Number of racks:               1
FSCK ended at Tue Oct 17 16:44:37 CEST 2017 in 2 milliseconds


The filesystem under path '/user/dboyer-ibm/512M2' is HEALTHY
```
