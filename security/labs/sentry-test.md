## <center> A Quick Sentry Tutorial </center>

* This tutorial assumes:
  * Your cluster has been Kerberized
  * You're familiar with [HiveQL syntax for Sentry](https://www.cloudera.com/documentation/enterprise/latest/topics/sg_hive_sql.html)

### Configure Sentry to recognize this account as an administrator
* Add your test user's primary  group to the `sentry.service.admin.group` list in CM
* Restart Sentry, Hue, Hive, and Impala services
    * It should not be necessary to restart HDFS or YARN

### Verify user privileges
* Authenticate your user as a Kerberos principal 
* Use `beeline` to confirm your principal sees no tables
    * `!connect jdbc:hive2://localhost:10000/default;principal=hive/fdqn@REALM.COM`
        * Replace `fqdn` with your host's fully-qualified domain name 
    * Use your Linux account/password to authenticate when prompted
    * Enter `SHOW TABLES;`
    * The statement should return an empty set because no authorizations are in place
* Copy the transcript of this section to `security/labs/sentry-test.md`

```
[dboyer-ibm@ip-172-31-39-197 ~]$ beeline
Beeline version 1.1.0-cdh5.9.3 by Apache Hive
beeline> !connect jdbc:hive2://ip-172-31-39-197.eu-west-1.compute.internal:10000/default;principal=hive/ip-172-31-39-197.eu-west-1.compute.internal@DBO.IBM
scan complete in 2ms
Connecting to jdbc:hive2://ip-172-31-39-197.eu-west-1.compute.internal:10000/default;principal=hive/ip-172-31-39-197.eu-west-1.compute.internal@DBO.IBM
Connected to: Apache Hive (version 1.1.0-cdh5.9.3)
Driver: Hive JDBC (version 1.1.0-cdh5.9.3)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://ip-172-31-39-197.eu-west-1.co> show tables;
INFO  : Compiling command(queryId=hive_20171019133838_34de88c5-72a8-4b50-af0e-eccc8fa1733a): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20171019133838_34de88c5-72a8-4b50-af0e-eccc8fa1733a); Time taken: 0.056 seconds
INFO  : Executing command(queryId=hive_20171019133838_34de88c5-72a8-4b50-af0e-eccc8fa1733a): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171019133838_34de88c5-72a8-4b50-af0e-eccc8fa1733a); Time taken: 0.152 seconds
INFO  : OK
+-----------+--+
| tab_name  |
+-----------+--+
+-----------+--+
No rows selected (0.311 seconds)

```

### Create a Sentry role with full authorization 
* In `beeline`:
    * `CREATE ROLE sentry_admin;`
    * `GRANT ALL ON SERVER server1 TO ROLE sentry_admin;`
    * `GRANT ROLE sentry_admin TO GROUP {your_primary};`
    * `SHOW TABLES;`
* The statement should now return all tables
```
0: jdbc:hive2://ip-172-31-39-197.eu-west-1.co> CREATE ROLE sentry_admin;
INFO  : Compiling command(queryId=hive_20171019134242_98828ca2-1f98-4c38-9f52-f600d2ac9613): CREATE ROLE sentry_admin
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20171019134242_98828ca2-1f98-4c38-9f52-f600d2ac9613); Time taken: 0.067 seconds
INFO  : Executing command(queryId=hive_20171019134242_98828ca2-1f98-4c38-9f52-f600d2ac9613): CREATE ROLE sentry_admin
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171019134242_98828ca2-1f98-4c38-9f52-f600d2ac9613); Time taken: 0.537 seconds
INFO  : OK
No rows affected (0.622 seconds)
0: jdbc:hive2://ip-172-31-39-197.eu-west-1.co> GRANT ALL ON SERVER server1 TO ROLE sentry_admin;
INFO  : Compiling command(queryId=hive_20171019134242_057a209f-4567-45f6-80f4-8efc7740cff6): GRANT ALL ON SERVER server1 TO ROLE sentry_admin
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20171019134242_057a209f-4567-45f6-80f4-8efc7740cff6); Time taken: 0.079 seconds
INFO  : Executing command(queryId=hive_20171019134242_057a209f-4567-45f6-80f4-8efc7740cff6): GRANT ALL ON SERVER server1 TO ROLE sentry_admin
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171019134242_057a209f-4567-45f6-80f4-8efc7740cff6); Time taken: 0.077 seconds
INFO  : OK
No rows affected (0.169 seconds)
0: jdbc:hive2://ip-172-31-39-197.eu-west-1.co> GRANT ROLE sentry_admin TO GROUP dboyer-ibm;
Error: Error while compiling statement: FAILED: ParseException line 1:39 missing EOF at '-' near 'dboyer' (state=42000,code=40000)

```

As there was a problem with the hyphen, I created a "dboyer" group, and added my user in it. I could not find easily the reason or how to solve it and did not want to lose toom much time on this, while others did not encounter this issue ( no hyphen in their users ).
I then continued.
```
0: jdbc:hive2://ip-172-31-39-197.eu-west-1.co> GRANT ROLE sentry_admin TO GROUP dboyer;
INFO  : Compiling command(queryId=hive_20171019134444_fcfb254f-2c85-48f2-8365-cbc31578666a): GRANT ROLE sentry_admin TO GROUP dboyer
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20171019134444_fcfb254f-2c85-48f2-8365-cbc31578666a); Time taken: 0.085 seconds
INFO  : Executing command(queryId=hive_20171019134444_fcfb254f-2c85-48f2-8365-cbc31578666a): GRANT ROLE sentry_admin TO GROUP dboyer
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171019134444_fcfb254f-2c85-48f2-8365-cbc31578666a); Time taken: 0.07 seconds
INFO  : OK

0: jdbc:hive2://ip-172-31-39-197.eu-west-1.co> SHOW TABLES;                                                                                                                                          
INFO  : Compiling command(queryId=hive_20171019135656_8f2dcd16-316c-4309-9e09-33a723882fd7): SHOW TABLES                                                                                             
INFO  : Semantic Analysis Completed                                                                                                                                                                  
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)                                                            
INFO  : Completed compiling command(queryId=hive_20171019135656_8f2dcd16-316c-4309-9e09-33a723882fd7); Time taken: 0.061 seconds                                                                     
INFO  : Executing command(queryId=hive_20171019135656_8f2dcd16-316c-4309-9e09-33a723882fd7): SHOW TABLES                                                                                             
INFO  : Starting task [Stage-0:DDL] in serial mode                                                                                                                                                   
INFO  : Completed executing command(queryId=hive_20171019135656_8f2dcd16-316c-4309-9e09-33a723882fd7); Time taken: 0.136 seconds                                                                     
INFO  : OK                                                                                                                                                                                           
+------------+--+                                                                                                                                                                                    
|  tab_name  |                                                                                                                                                                                       
+------------+--+                                                                                                                                                                                    
| customers  |                                                                                                                                                                                       
| sample_07  |
| sample_08  |
| web_logs   |
+------------+--+
4 rows selected (0.32 seconds)

```


### Create additional test users
* Add new users to all cluster nodes
    * `$ sudo groupadd selector`
    * `$ sudo groupadd inserters`
    * `$ sudo useradd -u 1100 -g selector george`
    * `$ sudo useradd -u 1200 -g inserters ferdinand`
    * `$ kadmin.local: add_principal george`
    * `$ kadmin.local: add_principal ferdinand`
```
Users created on all machines :
[root@ip-172-31-42-52 ~]# id george;id ferdinand                                                                                                                                                     
uid=1100(george) gid=1982(selector) groups=1982(selector)                                                                                                                                            
uid=1200(ferdinand) gid=1983(inserters) groups=1983(inserters)



```
### Create test roles
* Login to `beeline` as your admin user
    * `CREATE ROLE reads;`
    * `CREATE ROLE writes;`
```
0: jdbc:hive2://ip-172-31-39-197.eu-west-1.co> CREATE ROLE reads;
INFO  : Compiling command(queryId=hive_20171019140202_05e4d9ee-3f8f-45f7-8315-eb9ebcd0dd37): CREATE ROLE reads
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20171019140202_05e4d9ee-3f8f-45f7-8315-eb9ebcd0dd37); Time taken: 0.058 seconds
INFO  : Executing command(queryId=hive_20171019140202_05e4d9ee-3f8f-45f7-8315-eb9ebcd0dd37): CREATE ROLE reads
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171019140202_05e4d9ee-3f8f-45f7-8315-eb9ebcd0dd37); Time taken: 0.04 seconds
INFO  : OK
No rows affected (0.112 seconds)
0: jdbc:hive2://ip-172-31-39-197.eu-west-1.co> CREATE ROLE writes;
INFO  : Compiling command(queryId=hive_20171019140202_c399b775-4a8b-4d10-b3ed-31476efc19ee): CREATE ROLE writes
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20171019140202_c399b775-4a8b-4d10-b3ed-31476efc19ee); Time taken: 0.053 seconds
INFO  : Executing command(queryId=hive_20171019140202_c399b775-4a8b-4d10-b3ed-31476efc19ee): CREATE ROLE writes
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171019140202_c399b775-4a8b-4d10-b3ed-31476efc19ee); Time taken: 0.023 seconds
INFO  : OK
No rows affected (0.09 seconds)

```
### Grant read privilege for all tables to `reads`
* `GRANT SELECT ON DATABASE default TO ROLE reads;`
* `GRANT ROLE reads TO GROUP selector;`
```
0: jdbc:hive2://ip-172-31-39-197.eu-west-1.co> GRANT SELECT ON DATABASE default TO ROLE reads;
INFO  : Compiling command(queryId=hive_20171019140909_bfcdffc5-8706-499c-9f23-baa37d30a35e): GRANT SELECT ON DATABASE default TO ROLE reads
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20171019140909_bfcdffc5-8706-499c-9f23-baa37d30a35e); Time taken: 0.064 seconds
INFO  : Executing command(queryId=hive_20171019140909_bfcdffc5-8706-499c-9f23-baa37d30a35e): GRANT SELECT ON DATABASE default TO ROLE reads
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171019140909_bfcdffc5-8706-499c-9f23-baa37d30a35e); Time taken: 0.038 seconds
INFO  : OK
No rows affected (0.113 seconds)
0: jdbc:hive2://ip-172-31-39-197.eu-west-1.co> GRANT ROLE reads TO GROUP selector;
INFO  : Compiling command(queryId=hive_20171019140909_e8527b69-af9a-4919-abdb-7a79ae3ea7a0): GRANT ROLE reads TO GROUP selector
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20171019140909_e8527b69-af9a-4919-abdb-7a79ae3ea7a0); Time taken: 0.053 seconds
INFO  : Executing command(queryId=hive_20171019140909_e8527b69-af9a-4919-abdb-7a79ae3ea7a0): GRANT ROLE reads TO GROUP selector
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171019140909_e8527b69-af9a-4919-abdb-7a79ae3ea7a0); Time taken: 0.027 seconds
INFO  : OK
No rows affected (0.093 seconds)
```

### Grant read privilege for `default.sample07` only to 'writes':
* `REVOKE ALL ON DATABASE default FROM ROLE writes;`
* `GRANT SELECT ON default.sample_07 TO ROLE writes;`
* `GRANT ROLE writes TO GROUP inserters;`
```
0: jdbc:hive2://ip-172-31-39-197.eu-west-1.co> REVOKE ALL ON DATABASE default FROM ROLE writes;
INFO  : Compiling command(queryId=hive_20171019141010_04009863-63b2-406a-b8e9-1eb5be3ed20e): REVOKE ALL ON DATABASE default FROM ROLE writes
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20171019141010_04009863-63b2-406a-b8e9-1eb5be3ed20e); Time taken: 0.054 seconds
INFO  : Executing command(queryId=hive_20171019141010_04009863-63b2-406a-b8e9-1eb5be3ed20e): REVOKE ALL ON DATABASE default FROM ROLE writes
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171019141010_04009863-63b2-406a-b8e9-1eb5be3ed20e); Time taken: 0.081 seconds
INFO  : OK
No rows affected (0.147 seconds)
0: jdbc:hive2://ip-172-31-39-197.eu-west-1.co> GRANT SELECT ON default.sample_07 TO ROLE writes;
INFO  : Compiling command(queryId=hive_20171019141010_2c4dce76-2e4e-4475-b0d7-cbd76ae6e80d): GRANT SELECT ON default.sample_07 TO ROLE writes
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20171019141010_2c4dce76-2e4e-4475-b0d7-cbd76ae6e80d); Time taken: 0.057 seconds
INFO  : Executing command(queryId=hive_20171019141010_2c4dce76-2e4e-4475-b0d7-cbd76ae6e80d): GRANT SELECT ON default.sample_07 TO ROLE writes
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171019141010_2c4dce76-2e4e-4475-b0d7-cbd76ae6e80d); Time taken: 0.035 seconds
INFO  : OK
No rows affected (0.103 seconds)
0: jdbc:hive2://ip-172-31-39-197.eu-west-1.co> GRANT ROLE writes TO GROUP inserters;
INFO  : Compiling command(queryId=hive_20171019141010_4e8f2659-68f0-4a6b-9a00-127be0907742): GRANT ROLE writes TO GROUP inserters
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20171019141010_4e8f2659-68f0-4a6b-9a00-127be0907742); Time taken: 0.053 seconds
INFO  : Executing command(queryId=hive_20171019141010_4e8f2659-68f0-4a6b-9a00-127be0907742): GRANT ROLE writes TO GROUP inserters
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171019141010_4e8f2659-68f0-4a6b-9a00-127be0907742); Time taken: 0.028 seconds
INFO  : OK
No rows affected (0.092 seconds)

```

### `kinit` as george, then login to beeline
* `kinit` as `george`, login to beeline, and use `SHOW TABLES;`
    * `george` should be able to see all tables

```
[george@ip-172-31-34-71 ~]$ kinit                                                                                                                                                                    
Password for george@DBO.IBM:                                                                                                                                                                         
[george@ip-172-31-34-71 ~]$ 
```
```
[george@ip-172-31-34-71 ~]$ beeline                                                                                                                                                                  
Beeline version 1.1.0-cdh5.9.3 by Apache Hive                                                                                                                                                        
beeline> !connect jdbc:hive2://ip-172-31-39-197.eu-west-1.compute.internal:10000/default;principal=hive/ip-172-31-39-197.eu-west-1.compute.internal@DBO.IBM                                          
scan complete in 2ms                                                                                                                                                                                 
Connecting to jdbc:hive2://ip-172-31-39-197.eu-west-1.compute.internal:10000/default;principal=hive/ip-172-31-39-197.eu-west-1.compute.internal@DBO.IBM                                              
Connected to: Apache Hive (version 1.1.0-cdh5.9.3)                                                                                                                                                   
Driver: Hive JDBC (version 1.1.0-cdh5.9.3)                                                                                                                                                           
Transaction isolation: TRANSACTION_REPEATABLE_READ                                                                                                                                                   
0: jdbc:hive2://ip-172-31-39-197.eu-west-1.co> SHOW TABLES;                                                                                                                                          
INFO  : Compiling command(queryId=hive_20171019141212_4af0d92f-2d4e-4ec2-ba59-9e58564d2df3): SHOW TABLES                                                                                             
INFO  : Semantic Analysis Completed                                                                                                                                                                  
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)                                                            
INFO  : Completed compiling command(queryId=hive_20171019141212_4af0d92f-2d4e-4ec2-ba59-9e58564d2df3); Time taken: 0.062 seconds                                                                     
INFO  : Executing command(queryId=hive_20171019141212_4af0d92f-2d4e-4ec2-ba59-9e58564d2df3): SHOW TABLES                                                                                             
INFO  : Starting task [Stage-0:DDL] in serial mode                                                                                                                                                   
INFO  : Completed executing command(queryId=hive_20171019141212_4af0d92f-2d4e-4ec2-ba59-9e58564d2df3); Time taken: 0.134 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| customers  |
| sample_07  |
| sample_08  |
| web_logs   |
+------------+--+
4 rows selected (0.286 seconds)

```

* Repeat the process as `ferdinand`
    * `ferdinand` should see `sample_07` 
```
[ferdinand@ip-172-31-34-71 ~]$ beeline
Beeline version 1.1.0-cdh5.9.3 by Apache Hive
beeline> !connect jdbc:hive2://ip-172-31-39-197.eu-west-1.compute.internal:10000/default;principal=hive/ip-172-31-39-197.eu-west-1.compute.internal@DBO.IBM
scan complete in 1ms
Connecting to jdbc:hive2://ip-172-31-39-197.eu-west-1.compute.internal:10000/default;principal=hive/ip-172-31-39-197.eu-west-1.compute.internal@DBO.IBM
Connected to: Apache Hive (version 1.1.0-cdh5.9.3)
Driver: Hive JDBC (version 1.1.0-cdh5.9.3)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://ip-172-31-39-197.eu-west-1.co> show tables;
INFO  : Compiling command(queryId=hive_20171019141414_4a7d5bfa-0976-4bdd-a2dc-58fdcb26fb98): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20171019141414_4a7d5bfa-0976-4bdd-a2dc-58fdcb26fb98); Time taken: 0.06 seconds
INFO  : Executing command(queryId=hive_20171019141414_4a7d5bfa-0976-4bdd-a2dc-58fdcb26fb98): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171019141414_4a7d5bfa-0976-4bdd-a2dc-58fdcb26fb98); Time taken: 0.125 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| sample_07  |
+------------+--+
1 row selected (0.274 seconds)

```
* Add the transcripts of these sessions to `security/labs/sentry-test.md`
