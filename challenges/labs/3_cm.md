* Create the Issue `Install CDH`
* Assign the issue to yourself and label it `started`
* Install the CDH 5.9 release; deploy coreset services only
  * Rename your cluster after your GitHub handle
* Create user directories in HDFS for `ernest` and `siwicki`
* Add the following to `3_cm.md`:
    * Command and output for `hdfs dfs -ls /user`
```
[hdfs@ip-172-31-44-121 ~]$ hdfs dfs -ls /user
Found 6 items
drwxr-xr-x   - ernest  ernest           0 2017-10-20 11:34 /user/ernest
drwxrwxrwx   - mapred  hadoop           0 2017-10-20 11:30 /user/history
drwxrwxr-t   - hive    hive             0 2017-10-20 11:31 /user/hive
drwxrwxr-x   - hue     hue              0 2017-10-20 11:32 /user/hue
drwxrwxr-x   - oozie   oozie            0 2017-10-20 11:32 /user/oozie
drwxr-xr-x   - siwicki siwicki          0 2017-10-20 11:34 /user/siwicki

```
    * The output from the CM API call `../api/v14/hosts`
```
{
  "items" : [ {
    "hostId" : "6c48f134-53df-4662-9289-5aa065b9bbad",
    "ipAddress" : "172.31.39.82",
    "hostname" : "ip-172-31-39-82.eu-west-1.compute.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-172-31-44-231.eu-west-1.compute.internal:7180/cmf/hostRedirect/6c48f134-53df-4662-9289-5aa065b9bbad",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 15332438016
  }, {
    "hostId" : "154590f9-e7e4-4296-8c42-333566781f2a",
    "ipAddress" : "172.31.44.121",
    "hostname" : "ip-172-31-44-121.eu-west-1.compute.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-172-31-44-231.eu-west-1.compute.internal:7180/cmf/hostRedirect/154590f9-e7e4-4296-8c42-333566781f2a",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 15332438016
  }, {
    "hostId" : "i-012ccb0cd8b735f18",
    "ipAddress" : "172.31.44.231",
    "hostname" : "ip-172-31-44-231.eu-west-1.compute.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-172-31-44-231.eu-west-1.compute.internal:7180/cmf/hostRedirect/i-012ccb0cd8b735f18",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 15332438016
  }, {
    "hostId" : "8fe6c044-3182-48bf-a2f4-e6704437fae4",
    "ipAddress" : "172.31.44.94",
    "hostname" : "ip-172-31-44-94.eu-west-1.compute.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-172-31-44-231.eu-west-1.compute.internal:7180/cmf/hostRedirect/8fe6c044-3182-48bf-a2f4-e6704437fae4",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 15332438016
  }, {
    "hostId" : "i-0384388576e662060",
    "ipAddress" : "172.31.46.143",
    "hostname" : "ip-172-31-46-143.eu-west-1.compute.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-172-31-44-231.eu-west-1.compute.internal:7180/cmf/hostRedirect/i-0384388576e662060",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 15332438016
  } ]

```
* Login to Hue and install the Hive sample data
    * Capture the Hue home page to `challenges/labs/3_hue_installed.png`
* Push this work to your GitHub repo and label the Issue `submitted`
* Assign the issue to both instructors
* Capture output of java -version and add it to `3_jv.md`
