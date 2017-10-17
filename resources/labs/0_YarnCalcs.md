Do the following:
1. Plug the hardware numbers for your cluster into the spreadsheet
2. Inspect the derived/default values. Adjust as necessary.

```
The documentation reads:

- As with any system, the more memory and CPU resources available, the faster the cluster can process large amounts of data
- Start with at least 8 GB for your operating system, and 1 GB for Cloudera Manager. If services outside of CDH require additional resources, add those numbers under Other Services.
- The HDFS DataNode uses a minimum of 1 core and about 1 GB of memory. The same requirements apply to the YARN NodeManager.

Plus, I did not affect memory or CPU to Impala, HBASE and Solar are they are not installed on the cluster.

I then compared to the values of the documentation to the ones in the sheet.
Most of them were already OK, and i focused on the OS allocated values.
Setting 1 vcore to the OS allows 16 jobs  ( versus 15 with 2 vcores ) to work at the same time, so i changed this value.
Setting 8 GB to the OS did not improve that much the memory allocation of the jobs, but offers 4GB more to the OS, which could be of help for it to face occasional problems. 

I set the value of "workload factor" to 2 as it allows more jobs to run at the same time, while does not improve anything.
In a real cluster, this choice would depend of the intensivity of the jobs to run.
```

3. What criteria affects workload factor? What does a value of 1, 2, or 4 signify?
  * Put your answers in the same file as step 2.

```
The workload factor affect both the number of maps and reduces jobs
It corresponds to the number of jobs which can run at the same time on one workernode.
A value of 1 would allow a job to use every CPU available for yarn resources (so 16 CPUs). But only 10 jobs would run at the same time on the cluster. This is for the case of intensive jobs.
A value of 2 would allow 2 jobs to run at the same time on the same host, but in the limit of "yarn.nodemanager.resource.cpu-vcores" value. 
A value of 4 would would allow 4 jobs but we would still reach the limit of "yarn.nodemanager.resource.cpu-vcores", so there would be no gain. 
```


