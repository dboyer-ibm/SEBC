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
