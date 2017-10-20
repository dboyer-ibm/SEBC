* In the file `challenges/labs/0_setup.md`:
    * List the cloud provider you are using (AWS, GCE, Azure, other)
```
AWS
```
    * List the Linux release you have chosen

```
[root@ip-172-31-44-231 ~]# cat /etc/redhat-release 
CentOS Linux release 7.2.1511 (Core)
```
    * Show that the disk space on each node is at least 30 GB
```
[root@ip-172-31-44-231 ~]# df -h -t xfs  |grep -v boot
Filesystem               Size  Used Avail Use% Mounted on
/dev/mapper/centos-root   35G  1.1G   34G   3% /
/dev/xvdb1                40G   33M   40G   1% /data
```

    * List the command and output for `yum repolist enabled`
```
[root@ip-172-31-44-231 ~]# yum repolist enabled
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: ftp.heanet.ie
 * extras: ftp.heanet.ie
 * updates: ftp.heanet.ie
repo id                                                                                       repo name                                                                                        status
base/7/x86_64                                                                                 CentOS-7 - Base                                                                                  9,591
extras/7/x86_64                                                                               CentOS-7 - Extras                                                                                  227
updates/7/x86_64                                                                              CentOS-7 - Updates                                                                                 741
repolist: 10,559

```
* Add the following Linux accounts to all nodes
    * User `ernest` with a UID of `2000`
```
useradd -u 2000 ernest
```
    * User `siwicki` with a UID of `3000`
```
useradd -u 3000 siwicki
```
    * Create the group `usa` and add `ernest` to it
```
groupadd usa 
usermod -a -G usa ernest
```
    * Create the group `emea` and add `siwicki` to it
```
groupadd emea
usermod -a -G emea siwicki
```
* List the `/etc/passwd` entries for `ernest` and `siwicki` in your setup file
[root@ip-172-31-44-231 ~]# grep -E '(ernest|siwicki)' /etc/passwd
ernest:x:2000:2000::/home/ernest:/bin/bash
siwicki:x:3000:3000::/home/siwicki:/bin/bash
* List the `/etc/group` entries for `usa` and `emea` in your setup file
[root@ip-172-31-44-231 ~]# grep -E '(usa|emea)' /etc/group
usa:x:3001:ernest
emea:x:3002:siwicki
* Push to your GitHub repo
* Label your Issue `submitted`
* Assign the Issue to both instructors
