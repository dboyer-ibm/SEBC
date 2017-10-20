* Create the Issue `Install CM`
* Install a supported version of Java 8 on all machines
* Assign yourself to the Issue and label it `started`
* Install Cloudera Manager on a different node from MySQL
* Configure the CM repo to install the 5.9 release
  * List the command and output of `ls /etc/yum.repos.d` in `challenges/labs/2_cm.md`
```
[root@ip-172-31-44-231 yum.repos.d]# ls /etc/yum.repos.d
CentOS-Base.repo  CentOS-Debuginfo.repo  CentOS-Media.repo    CentOS-Vault.repo      mysql-community.repo
CentOS-CR.repo    CentOS-fasttrack.repo  CentOS-Sources.repo  cloudera-manager.repo  mysql-community-source.repo

```
  * Copy the `cloudera-manager.repo` file to `challenges/labs/2_cloudera-manager.repo.md`
* Configure Cloudera Manager
  * Use the `scm_prepare_database.sh` script to write your `db.properties` file 
    * List the full command line in `2_cm.md`
```
root@ip-172-31-44-231 UnlimitedJCEPolicyJDK8]# /usr/share/cmf/schema/scm_prepare_database.sh -h ip-172-31-46-143.eu-west-1.compute.internal mysql scm scm scm
JAVA_HOME=/usr/java/jdk1.8.0_131
Verifying that we can write to /etc/cloudera-scm-server
Creating SCM configuration file in /etc/cloudera-scm-server
Executing:  /usr/java/jdk1.8.0_131/bin/java -cp /usr/share/java/mysql-connector-java.jar:/usr/share/java/oracle-connector-java.jar:/usr/share/cmf/schema/../lib/* com.cloudera.enterprise.dbutil.DbCommandExecutor /etc/cloudera-scm-server/db.properties com.cloudera.cmf.db.
[                          main] DbCommandExecutor              INFO  Successfully connected to database.
All done, your SCM database is configured correctly!
```
* Start the Cloudera Manager server. Then in `challenges/labs/2_db.properties.md`:
  * Add the first line from your server log
  * Add the log line that contains the phrase "Started Jetty server"
  * Copy your `db.properties` file to `challenges/labs/2_db.properties.md`
* Push to your GitHub repo and label the Issue 'submitted`
* Assign the issue to both instructors

