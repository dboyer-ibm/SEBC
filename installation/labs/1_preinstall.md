1.vm.swappiness

```
[root@ip-172-31-42-52 ~]# sysctl vm.swappiness
vm.swappiness = 1
```

---------------------------------------------------------------------
2.Show the mount attributes of all volumes


```
SUMMARY :
/dev/mapper/centos-root on / type xfs (rw,noatime,attr2,inode64,noquota)
/dev/xvda1 on /boot type xfs (rw,noatime,attr2,inode64,noquota)
/dev/xvdb1 on /data1 type xfs (rw,noatime,attr2,inode64,noquota)
```


```
ALL : 
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
devtmpfs on /dev type devtmpfs (rw,nosuid,size=7607544k,nr_inodes=1901886,mode=755)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,nodev,mode=755)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/usr/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpuacct,cpu)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/net_cls type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
configfs on /sys/kernel/config type configfs (rw,relatime)
/dev/mapper/centos-root on / type xfs (rw,noatime,attr2,inode64,noquota)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=32,pgrp=1,timeout=300,minproto=5,maxproto=5,direct)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
mqueue on /dev/mqueue type mqueue (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
/dev/xvda1 on /boot type xfs (rw,noatime,attr2,inode64,noquota)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=1497312k,mode=700,uid=1000,gid=1000)
/dev/xvdb1 on /data1 type xfs (rw,noatime,attr2,inode64,noquota)
```

---------------------------------------------------------------------

3.Show the reserve space of any non-root, ext-based volumes 

```
XFS was used, so there is no such attributes
```

---------------------------------------------------------------------
4.Disable transparent hugepage support

```
[root@ip-172-31-42-52 ~]# cat /sys/kernel/mm/transparent_hugepage/enabled 
always madvise [never]
[root@ip-172-31-42-52 ~]# cat /sys/kernel/mm/transparent_hugepage/defrag
always madvise [never]
[root@ip-172-31-42-52 ~]# sysctl -a | grep hugepage
vm.hugepages_treat_as_movable = 0
vm.nr_hugepages = 0
vm.nr_hugepages_mempolicy = 0
vm.nr_overcommit_hugepages = 0
```

5. List your network interface configuration

```
[root@ip-172-31-42-52 ~]# ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 9001 qdisc pfifo_fast state UP qlen 1000
    link/ether 0a:c7:83:f8:0b:ec brd ff:ff:ff:ff:ff:ff
    inet 172.31.42.52/20 brd 172.31.47.255 scope global dynamic eth0
       valid_lft 3142sec preferred_lft 3142sec
[root@ip-172-31-42-52 ~]# 
```

6. List forward and reverse host lookups using getent or nslookup

```
[root@ip-172-31-42-52 ~]# nslookup ip-172-31-42-52
Server:         172.31.0.2
Address:        172.31.0.2#53

Non-authoritative answer:
Name:   ip-172-31-42-52.eu-west-1.compute.internal
Address: 172.31.42.52
```

7. Show the nscd service is running

```
root@ip-172-31-42-52 ~]# systemctl status nscd
● nscd.service - Name Service Cache Daemon
   Loaded: loaded (/usr/lib/systemd/system/nscd.service; enabled; vendor preset: disabled)
   Active: active (running) since Mon 2017-10-16 15:49:27 CEST; 1s ago
  Process: 2633 ExecStart=/usr/sbin/nscd $NSCD_OPTIONS (code=exited, status=0/SUCCESS)
 Main PID: 2634 (nscd)
   CGroup: /system.slice/nscd.service
           └─2634 /usr/sbin/nscd
```


8. Show the ntpd service is running

```
[root@ip-172-31-42-52 ~]# systemctl status ntpd
● ntpd.service - Network Time Service
   Loaded: loaded (/usr/lib/systemd/system/ntpd.service; enabled; vendor preset: disabled)
   Active: active (running) since Mon 2017-10-16 15:30:14 CEST; 20min ago
 Main PID: 664 (ntpd)
   CGroup: /system.slice/ntpd.service
           └─664 /usr/sbin/ntpd -u ntp:ntp -g
```
