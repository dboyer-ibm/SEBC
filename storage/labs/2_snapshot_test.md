List the commands and output for each step below in `storage/labs/2_snapshot_test.md`.

* Create a `precious` directory in HDFS; copy the ZIP course file into it.
```
[dboyer-ibm@ip-172-31-34-71 ~]$ hdfs dfs -mkdir /user/dboyer-ibm/precious
```

```
[dboyer-ibm@ip-172-31-34-71 ~]$ hdfs dfs -put SEBC-master.zip /user/dboyer-ibm/precious/
[dboyer-ibm@ip-172-31-34-71 ~]$ hdfs dfs -ls /user/dboyer-ibm/precious/
Found 1 items
-rw-r--r--   3 dboyer-ibm dboyer-ibm     450893 2017-10-17 16:49 /user/dboyer-ibm/precious/SEBC-master.zip
```

* Enable snapshots for `precious`
[hdfs@ip-172-31-34-71 ~]$ hdfs dfsadmin -allowSnapshot /user/dboyer-ibm/precious
Allowing snaphot on /user/dboyer-ibm/precious succeeded

* Create a snapshot called `sebc-hdfs-test`
```
[dboyer-ibm@ip-172-31-34-71 ~]$ hdfs dfs -createSnapshot /user/dboyer-ibm/precious sebc-hdfs-test
Created snapshot /user/dboyer-ibm/precious/.snapshot/sebc-hdfs-test
```

* Delete the directory
Deleting the directory is impossible because there already is a snapshot in use
```
[dboyer-ibm@ip-172-31-34-71 ~]$ hdfs dfs -rm -r -f -skipTrash /user/dboyer-ibm/precious
rm: The directory /user/dboyer-ibm/precious cannot be deleted since /user/dboyer-ibm/precious is snapshottable and already has snapshots
```
* Delete the ZIP file

```
[dboyer-ibm@ip-172-31-34-71 ~]$ hdfs dfs -rm -f -skipTrash /user/dboyer-ibm/precious/SEBC-master.zip
Deleted /user/dboyer-ibm/precious/SEBC-master.zip
```
* Restore the deleted file
```
hdfs@ip-172-31-34-71 ~]$ hdfs dfs -cp /user/dboyer-ibm/precious/.snapshot/sebc-hdfs-test/SEBC-master.zip /user/dboyer-ibm/precious/
```
* Capture the NameNode web UI screen that lists snapshots in `storage/labs/2_snapshot_list.png`.
