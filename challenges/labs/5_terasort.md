[ernest@ip-172-31-44-231 ~]$ time hadoop jar /opt/cloudera/parcels/CDH-5.9.3-1.cdh5.9.3.p0.4/jars/hadoop-mapreduce-examples-2.6.0-cdh5.9.3.jar terasort /user/ernest/tgen512 /user/ernest/tsort512
17/10/20 06:22:53 INFO terasort.TeraSort: starting
17/10/20 06:22:54 INFO hdfs.DFSClient: Created token for ernest: HDFS_DELEGATION_TOKEN owner=ernest@DBOYER.CO.UK, renewer=yarn, realUser=, issueDate=1508493774890, maxDate=1509098574890, sequenceNumber=1, masterKeyId=2 on 172.31.44.231:8020
17/10/20 06:22:54 INFO security.TokenCache: Got dt for hdfs://ip-172-31-44-231.eu-west-1.compute.internal:8020; Kind: HDFS_DELEGATION_TOKEN, Service: 172.31.44.231:8020, Ident: (token for ernest: HDFS_DELEGATION_TOKEN owner=ernest@DBOYER.CO.UK, renewer=yarn, realUser=, issueDate=1508493774890, maxDate=1509098574890, sequenceNumber=1, masterKeyId=2)
17/10/20 06:22:55 INFO input.FileInputFormat: Total input paths to process : 2
Spent 359ms computing base-splits.
Spent 4ms computing TeraScheduler splits.
Computing input splits took 363ms
Sampling 10 splits of 154
Making 6 from 100000 sampled records
Computing parititions took 891ms
Spent 1256ms computing partitions.
17/10/20 06:22:56 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-44-231.eu-west-1.compute.internal/172.31.44.231:8032
17/10/20 06:22:56 INFO mapreduce.JobSubmitter: number of splits:154
17/10/20 06:22:57 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1508493661574_0001
17/10/20 06:22:57 INFO mapreduce.JobSubmitter: Kind: HDFS_DELEGATION_TOKEN, Service: 172.31.44.231:8020, Ident: (token for ernest: HDFS_DELEGATION_TOKEN owner=ernest@DBOYER.CO.UK, renewer=yarn, realUser=, issueDate=1508493774890, maxDate=1509098574890, sequenceNumber=1, masterKeyId=2)
17/10/20 06:22:58 INFO impl.YarnClientImpl: Submitted application application_1508493661574_0001
17/10/20 06:22:58 INFO mapreduce.Job: The url to track the job: http://ip-172-31-44-231.eu-west-1.compute.internal:8088/proxy/application_1508493661574_0001/
17/10/20 06:23:07 INFO mapreduce.Job:  map 0% reduce 0%
17/10/20 06:26:27 INFO mapreduce.Job: Counters: 49
	File System Counters
		FILE: Number of bytes read=2270863632
		FILE: Number of bytes written=4514422193
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=5120023562
		HDFS: Number of bytes written=5120000000
		HDFS: Number of read operations=480
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=12
	Job Counters 
		Launched map tasks=154
		Launched reduce tasks=6
		Data-local map tasks=154
		Total time spent by all maps in occupied slots (ms)=1376497
		Total time spent by all reduces in occupied slots (ms)=302123
		Total time spent by all map tasks (ms)=1376497
		Total time spent by all reduce tasks (ms)=302123
		Total vcore-seconds taken by all map tasks=1376497
		Total vcore-seconds taken by all reduce tasks=302123
		Total megabyte-seconds taken by all map tasks=1409532928
		Total megabyte-seconds taken by all reduce tasks=309373952
	Map-Reduce Framework
		Map input records=51200000
		Map output records=51200000
		Map output bytes=5222400000
		Map output materialized bytes=2223429323
		Input split bytes=23562
		Combine input records=0
		Combine output records=0
		Reduce input groups=51200000
		Reduce shuffle bytes=2223429323
		Reduce input records=51200000
		Reduce output records=51200000
		Spilled Records=102400000
		Shuffled Maps =924
		Failed Shuffles=0
		Merged Map outputs=924
		GC time elapsed (ms)=36204
		CPU time spent (ms)=833570
		Physical memory (bytes) snapshot=79226880000
		Virtual memory (bytes) snapshot=445559390208
		Total committed heap usage (bytes)=83626557440
	Shuffle Errors
		BAD_ID=0
		CONNECTION=0
		IO_ERROR=0
		WRONG_LENGTH=0
		WRONG_MAP=0
		WRONG_REDUCE=0
	File Input Format Counters 
		Bytes Read=5120000000
	File Output Format Counters 
		Bytes Written=5120000000
17/10/20 06:26:27 INFO terasort.TeraSort: done

real	3m34.942s
user	0m10.735s
sys	0m0.470s

real	3m54.702s
user	0m30.512s
sys	0m0.470s
