* Write `curl` statements that stop,
```
curl -X POST -u dboyer-ibm:cloudera "http://ec2-52-212-24-11.eu-west-1.compute.amazonaws.com:7180/api/v12/clusters/cluster/services/hive/commands/stop"
```

 start, 
```
curl -X POST -u dboyer-ibm:cloudera "http://ec2-52-212-24-11.eu-west-1.compute.amazonaws.com:7180/api/v12/clusters/cluster/services/hive/commands/start"
```

and check the current state of your Hive service.
```
curl -u dboyer-ibm:cloudera "http://ec2-52-212-24-11.eu-west-1.compute.amazonaws.com:7180/api/v12/clusters/cluster/services/hive"
```




  * Add these statements and their output to `enterprise/labs/3_api_hive_state.md`

Ouput of stop :
```

{
  "id" : 583,
  "name" : "Stop",
  "startTime" : "2017-10-18T09:53:19.178Z",
  "active" : true,
  "serviceRef" : {
    "clusterName" : "cluster",
    "serviceName" : "hive"
  }
}
```

Output of start :
```

{
  "id" : 588,
  "name" : "Start",
  "startTime" : "2017-10-18T09:54:46.452Z",
  "active" : true,
  "serviceRef" : {
    "clusterName" : "cluster",
    "serviceName" : "hive"
  }
}
```

Output of status :
```

{
  "name" : "hive",
  "type" : "HIVE",
  "clusterRef" : {
    "clusterName" : "cluster"
  },
  "serviceUrl" : "http://ip-172-31-42-52.eu-west-1.compute.internal:7180/cmf/serviceRedirect/hive",
  "roleInstancesUrl" : "http://ip-172-31-42-52.eu-west-1.compute.internal:7180/cmf/serviceRedirect/hive/instances",
  "serviceState" : "STARTED",
  "healthSummary" : "GOOD",
  "healthChecks" : [ {
    "name" : "HIVE_HIVEMETASTORES_HEALTHY",
    "summary" : "GOOD",
    "suppressed" : false
  }, {
    "name" : "HIVE_HIVESERVER2S_HEALTHY",
    "summary" : "GOOD",
    "suppressed" : false
  } ],
  "configStalenessStatus" : "FRESH",
  "clientConfigStalenessStatus" : "FRESH",
  "maintenanceMode" : false,
  "maintenanceOwners" : [ ],
  "displayName" : "Hive",
  "entityStatus" : "GOOD_HEALTH"
}