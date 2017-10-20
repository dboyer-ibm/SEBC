
* Install a MySQL 5.5.x server on the node you listed first
    * Use the YUM repository available at `dev.mysql.com`
    * Copy `/etc/yum.repos.d/mysql-community.repo` to `challenges/labs/1_mysql-community.repo.md`
* On all cluster nodes
    * Install the MySQL client package and JDBC connector jar
* Start the `mysqld` service
* Create the following databases
    * `scm`
    * `rman`
    * `hive`
    * `oozie`
    * `hue`
    * `sentry`
* Put the following in the file `challenges/labs/1_mysql.md`
    * The hostname of your MySQL node 
```
ip-172-31-46-143.eu-west-1.compute.internal
```
    * The command and output for `mysql --version`
```
[root@ip-172-31-46-143 ~]# mysql --version
mysql  Ver 14.14 Distrib 5.5.58, for Linux (x86_64) using readline 5.1
```
    * The command and output for listing MySQL databases 
```
[root@ip-172-31-46-143 ~]# mysql -u root -pcloudera -e "show databases"
+--------------------+
| Database           |
+--------------------+
| information_schema |
| hive               |
| hue                |
| mysql              |
| oozie              |
| performance_schema |
| rman               |
| scm                |
| sentry             |
+--------------------+

```
* Push this work to your GitHub repo
* Label the Issue 'submitted` and assign it to both instructors
