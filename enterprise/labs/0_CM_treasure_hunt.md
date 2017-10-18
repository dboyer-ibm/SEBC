* What is ubertask optimization?
```
Whether to enable ubertask optimization, which runs "sufficiently small" jobs sequentially within a single JVM. "Small" is defined by the mapreduce.job.ubertask.maxmaps, mapreduce.job.ubertask.maxreduces, and mapreduce.job.ubertask.maxbytes settings.
```
* Where in CM is the Kerberos Security Realm value displayed?
```
Administration -> Security -> Kerberos Credentials Configuration -> Settings -> kerberos -> Kerberos Security Realm
```
* Which CDH service(s) host a property for enabling Kerberos authentication?
```
I may have misunderstood the question, but in my opinion the answer is all, because they all have a "Kerberos Principal" option allowing them to authenticate through kerberos.

```
* How do you upgrade the CM agents?
```
They can be upgraded through cm manager ( by using "re-run upgrade wizard" in the hosts section
```
* Give the `tsquery` statement used to chart Hue's CPU utilization?
```
Opening in chart builder the chart "cpu cores used" chart of hue gives:
select cpu_system_rate + cpu_user_rate where category=ROLE and serviceName=$SERVICENAME

$SERVICENAME being replaced by "hue"
```
* Name all the roles that make up the Hive service
```
They are :
- Hive Metastore Server
- WebHCat Server
- HiveServer2 
- Gateway
```

* What steps must be completed before integrating Cloudera Manager with Kerberos?
```
launching the wizard show these steps :
- Set up a working KDC. Cloudera Manager supports MIT KDC and Active Directory.
- The KDC should be configured to have non-zero ticket lifetime and renewal lifetime. CDH will not work properly if tickets are not renewable.
- OpenLdap client libraries should be installed on the Cloudera Manager Server host if you want to use Active Directory. Also, Kerberos client libraries should be installed on ALL hosts.
- Cloudera Manager needs an account that has permissions to create other accounts in the KDC.
```
