# 1. Check vm.swappiness on all your nodes Set the value to 1 if necessary
```
[root@ip-172-31-6-7 ~]# ./rallsh.sh "sysctl vm.swappiness"
cmd=- sysctl vm.swappiness -
Connect to vm1
ssh -i  AWS-SEBC-TRAINING.pem root@vm1 "sysctl vm.swappiness" 
vm.swappiness = 60
Connect to vm2
ssh -i  AWS-SEBC-TRAINING.pem root@vm2 "sysctl vm.swappiness" 
vm.swappiness = 60
Connect to vm3
ssh -i  AWS-SEBC-TRAINING.pem root@vm3 "sysctl vm.swappiness" 
vm.swappiness = 60
Connect to vm4
ssh -i  AWS-SEBC-TRAINING.pem root@vm4 "sysctl vm.swappiness" 
vm.swappiness = 60
Connect to vm5
ssh -i  AWS-SEBC-TRAINING.pem root@vm5 "sysctl vm.swappiness" 
vm.swappiness = 60
[root@ip-172-31-6-7 ~]# ./rallsh.sh "sysctl vm.swappiness=1"
cmd=- sysctl vm.swappiness=1 -
Connect to vm1
ssh -i  AWS-SEBC-TRAINING.pem root@vm1 "sysctl vm.swappiness=1" 
vm.swappiness = 1
Connect to vm2
ssh -i  AWS-SEBC-TRAINING.pem root@vm2 "sysctl vm.swappiness=1" 
vm.swappiness = 1
Connect to vm3
ssh -i  AWS-SEBC-TRAINING.pem root@vm3 "sysctl vm.swappiness=1" 
vm.swappiness = 1
Connect to vm4
ssh -i  AWS-SEBC-TRAINING.pem root@vm4 "sysctl vm.swappiness=1" 
vm.swappiness = 1
Connect to vm5
ssh -i  AWS-SEBC-TRAINING.pem root@vm5 "sysctl vm.swappiness=1" 
vm.swappiness = 1
```

# 2.Show the mount attributes of your volume(s)

Resize2fs /dev/xvde

[root@ip-172-31-6-7 ~]# mount -v|grep "on / "
```
/dev/xvde on / type ext4 (rw)

ssh -i  AWS-SEBC-TRAINING.pem root@vm1 "df -v -m" 
Filesystem     1M-blocks  Used Available Use% Mounted on
/dev/xvde          30238   655     28049   3% /
tmpfs               7506     0      7506   0% /dev/shm
```
# 3.If you have ext-based volumes, list the reserve space setting 
``` 
[root@ip-172-31-6-7 ~]# dumpe2fs /dev/xvde |more
dumpe2fs 1.41.12 (17-May-2010)
Filesystem volume name:   centos_root
Last mounted on:          /
Filesystem UUID:          44d27f92-d3df-4207-80ea-22830afccf03
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              1966080
Block count:              7864320
Reserved block count:     393145
Free blocks:              5800759
Free inodes:              1882305
```
# 4.Disable transparent hugepage support
```
[root@ip-172-31-3-160 ~]#  cat /sys/kernel/mm/transparent_hugepage/enabled 
cat: /sys/kernel/mm/transparent_hugepage/enabled: No such file or directory
[root@ip-172-31-3-160 ~]# ls -l /sys/kernel/mm/
total 0
drwxr-xr-x. 3 root root 0 May  8 13:31 hugepages
drwxr-xr-x. 2 root root 0 May  8 13:31 ksm

[root@ip-172-31-3-160 ~]# cat /proc/meminfo | grep HugePages 
AnonHugePages:         0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
```
# 5.List your network interface configuration
```
[root@ip-172-31-6-7 ~]# ifconfig
eth0      Link encap:Ethernet  HWaddr 0A:76:D3:09:26:92  
          inet addr:172.31.6.7  Bcast:172.31.15.255  Mask:255.255.240.0
          inet6 addr: fe80::876:d3ff:fe09:2692/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:9001  Metric:1
          RX packets:459 errors:0 dropped:0 overruns:0 frame:0
          TX packets:432 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:62346 (60.8 KiB)  TX bytes:64882 (63.3 KiB)
          Interrupt:24 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13092 (12.7 KiB)  TX bytes:13092 (12.7 KiB)
```
# 6.Show that forward and reverse host lookups are correctly resolved
```
[root@ip-172-31-6-7 ~]# getent hosts
127.0.0.1       localhost.localdomain localhost
127.0.0.1       localhost6.localdomain6 localhost6
172.31.6.7       ip-172-31-6-7.ec2.internal	vm1
172.31.5.148    ip-172-31-5-148.ec2.internal  vm2
172.31.15.40    ip-172-31-15-40.ec2.internal	vm3
172.31.11.232   ip-172-31-11-232.ec2.internal vm4
172.31.6.212    ip-172-31-6-212.ec2.internal vm5

[root@ip-172-31-6-7 ~]# nslookup `hostname`
Server:         172.31.0.2
Address:        172.31.0.2#53

Non-authoritative answer:
Name:   ip-172-31-6-7.ec2.internal
Address: 172.31.6.7

```
# 7.Show the nscd service is running
```
[root@ip-172-31-6-7 ~]# rash "service nscd status"
Connect to vm1
ssh -i  AWS-SEBC-TRAINING.pem root@vm1 "service nscd status" 
nscd (pid 4456) is running...
Connect to vm2
ssh -i  AWS-SEBC-TRAINING.pem root@vm2 "service nscd status" 
nscd (pid 1038) is running...
Connect to vm3
ssh -i  AWS-SEBC-TRAINING.pem root@vm3 "service nscd status" 
nscd (pid 4275) is running...
Connect to vm4
ssh -i  AWS-SEBC-TRAINING.pem root@vm4 "service nscd status" 
nscd (pid 1036) is running...
Connect to vm5
ssh -i  AWS-SEBC-TRAINING.pem root@vm5 "service nscd status" 
nscd (pid 1038) is running... 
```
# 8.Show the  ntpd  service is running
```
rash "yum -y install ntp"
rash "chkconfig ntpd on"
```
```
[root@ip-172-31-6-7 ~]# rash "service ntpd status"
Connect to vm1
ssh -i  AWS-SEBC-TRAINING.pem root@vm1 "service ntpd status" 
ntpd (pid  4581) is running...
Connect to vm2
ssh -i  AWS-SEBC-TRAINING.pem root@vm2 "service ntpd status" 
ntpd (pid  1114) is running...
Connect to vm3
ssh -i  AWS-SEBC-TRAINING.pem root@vm3 "service ntpd status" 
ntpd (pid  4351) is running...
Connect to vm4
ssh -i  AWS-SEBC-TRAINING.pem root@vm4 "service ntpd status" 
ntpd (pid  1112) is running...
Connect to vm5
ssh -i  AWS-SEBC-TRAINING.pem root@vm5 "service ntpd status" 
ntpd (pid  1114) is running...
```
# 9. misc
1 stop selinux
```
ssh -i  AWS-SEBC-TRAINING.pem root@vm1 "cat /etc/selinux/config|grep ^SELINUX" 
SELINUX=disabled
ssh -i  AWS-SEBC-TRAINING.pem root@vm2 "cat /etc/selinux/config|grep ^SELINUX" 
SELINUX=disabled
ssh -i  AWS-SEBC-TRAINING.pem root@vm3 "cat /etc/selinux/config|grep ^SELINUX" 
SELINUX=disabled
ssh -i  AWS-SEBC-TRAINING.pem root@vm4 "cat /etc/selinux/config|grep ^SELINUX" 
SELINUX=disabled
ssh -i  AWS-SEBC-TRAINING.pem root@vm5 "cat /etc/selinux/config|grep ^SELINUX" 
SELINUX=disabled
```
[root@ip-172-31-6-7 ~]# rash getenforce
ssh -i  AWS-SEBC-TRAINING.pem root@vm1 "getenforce" 
Disabled
ssh -i  AWS-SEBC-TRAINING.pem root@vm2 "getenforce" 
Disabled
ssh -i  AWS-SEBC-TRAINING.pem root@vm3 "getenforce" 
Disabled
ssh -i  AWS-SEBC-TRAINING.pem root@vm4 "getenforce" 
Disabled
ssh -i  AWS-SEBC-TRAINING.pem root@vm5 "getenforce" 
Disabled
```
2 stop iptables
```
[root@ip-172-31-6-7 ~]# ./rallsh.sh "chkconfig iptables off"
ssh -i  AWS-SEBC-TRAINING.pem root@vm1 "chkconfig iptables off" 
ssh -i  AWS-SEBC-TRAINING.pem root@vm2 "chkconfig iptables off" 
ssh -i  AWS-SEBC-TRAINING.pem root@vm3 "chkconfig iptables off" 
ssh -i  AWS-SEBC-TRAINING.pem root@vm4 "chkconfig iptables off" 
ssh -i  AWS-SEBC-TRAINING.pem root@vm5 "chkconfig iptables off" 

[root@ip-172-31-6-7 ~]# ./rallsh.sh "service iptables stop"
ssh -i  AWS-SEBC-TRAINING.pem root@vm1 "service iptables stop" 
iptables: Setting chains to policy ACCEPT: filter [  OK  ]
iptables: Flushing firewall rules: [  OK  ]
iptables: Unloading modules: [  OK  ]
ssh -i  AWS-SEBC-TRAINING.pem root@vm2 "service iptables stop" 
iptables: Setting chains to policy ACCEPT: filter [  OK  ]
iptables: Flushing firewall rules: [  OK  ]
iptables: Unloading modules: [  OK  ]
ssh -i  AWS-SEBC-TRAINING.pem root@vm3 "service iptables stop" 
iptables: Setting chains to policy ACCEPT: filter [  OK  ]
iptables: Flushing firewall rules: [  OK  ]
iptables: Unloading modules: [  OK  ]
ssh -i  AWS-SEBC-TRAINING.pem root@vm4 "service iptables stop" 
iptables: Setting chains to policy ACCEPT: filter [  OK  ]
iptables: Flushing firewall rules: [  OK  ]
iptables: Unloading modules: [  OK  ]
ssh -i  AWS-SEBC-TRAINING.pem root@vm5 "service iptables stop" 
iptables: Setting chains to policy ACCEPT: filter [  OK  ]
iptables: Flushing firewall rules: [  OK  ]
iptables: Unloading modules: [  OK  ]
```









安装MYSQL
Vm1 master
Vm2 slave
Vm3-vm5 install mysql
All nodes:
Rash “yum -y install mysql”

Master & slave:
Yum -y install mysql-server

Vi /etc/my.cnf
Master:
server-id=1
log-bin=mysql-bin
binlog-format=row


slave:
server-id=2
log-bin=mysql-bin
binlog-format=row


Start mysql on master and slave
Service mysqld start
[root@ip-172-31-6-7 ~]#  /usr/bin/mysql_secure_installation 




NOTE: RUNNING ALL PARTS OF THIS SCRIPT IS RECOMMENDED FOR ALL MySQL
      SERVERS IN PRODUCTION USE!  PLEASE READ EACH STEP CAREFULLY!


In order to log into MySQL to secure it, we'll need the current
password for the root user.  If you've just installed MySQL, and
you haven't set the root password yet, the password will be blank,
so you should just press enter here.

Enter current password for root (enter for none): 
OK, successfully used password, moving on...

Setting the root password ensures that nobody can log into the MySQL
root user without the proper authorisation.

Set root password? [Y/n] y
New password: 
Re-enter new password: 
Password updated successfully!
Reloading privilege tables..
 ... Success!


By default, a MySQL installation has an anonymous user, allowing anyone
to log into MySQL without having to have a user account created for
them.  This is intended only for testing, and to make the installation
go a bit smoother.  You should remove them before moving into a
production environment.

Remove anonymous users? [Y/n] y
 ... Success!

Normally, root should only be allowed to connect from 'localhost'.  This
ensures that someone cannot guess at the root password from the network.

Disallow root login remotely? [Y/n] n
 ... skipping.

By default, MySQL comes with a database named 'test' that anyone can
access.  This is also intended only for testing, and should be removed
before moving into a production environment.

Remove test database and access to it? [Y/n] y
 - Dropping test database...
 ... Success!
 - Removing privileges on test database...
 ... Success!

Reloading the privilege tables will ensure that all changes made so far
will take effect immediately.

Reload privilege tables now? [Y/n] y
 ... Success!

Cleaning up...



All done!  If you've completed all of the above steps, your MySQL
installation should now be secure.

Thanks for using MySQL!

Create replication user
CREATE USER 'repl'@'172.31.%.%' IDENTIFIED BY 'slavepass';
GRANT REPLICATION SLAVE ON *.* TO 'repl'@'172.31.%.%';


Opt：
SET GLOBAL binlog_format = 'ROW';
FLUSH TABLES WITH READ LOCK;


At master:
mysql> show master status;
+------------------+----------+--------------+------------------+
| File             | Position | Binlog_Do_DB | Binlog_Ignore_DB |
+------------------+----------+--------------+------------------+
| mysql-bin.000003 |     2251 |              |                  |
+------------------+----------+--------------+------------------+
1 row in set (0.00 sec)
 
At slave:
CHANGE MASTER TO MASTER_HOST='vm1', MASTER_USER='repl', MASTER_PASSWORD='slavepass', MASTER_LOG_FILE='mysql-bin.000003', MASTER_LOG_POS=2251 ;

mysql> CHANGE MASTER TO MASTER_HOST='vm1', MASTER_USER='repl', MASTER_PASSWORD='slavepass', MASTER_LOG_FILE='mysql-bin.000003', MASTER_LOG_POS=2251 ; 
Query OK, 0 rows affected (0.02 sec)
 
mysql> START SLAVE;
Query OK, 0 rows affected (0.00 sec)

mysql> SHOW SLAVE STATUS \G 
*************************** 1. row ***************************
               Slave_IO_State: Waiting for master to send event
                  Master_Host: vm1
                  Master_User: repl
                  Master_Port: 3306
                Connect_Retry: 60
              Master_Log_File: mysql-bin.000003
          Read_Master_Log_Pos: 2251
               Relay_Log_File: mysqld-relay-bin.000002
                Relay_Log_Pos: 251
        Relay_Master_Log_File: mysql-bin.000003
             Slave_IO_Running: Yes
            Slave_SQL_Running: Yes
              Replicate_Do_DB: 
          Replicate_Ignore_DB: 
           Replicate_Do_Table: 
       Replicate_Ignore_Table: 
      Replicate_Wild_Do_Table: 
  Replicate_Wild_Ignore_Table: 
                   Last_Errno: 0
                   Last_Error: 
                 Skip_Counter: 0
          Exec_Master_Log_Pos: 2251
              Relay_Log_Space: 407
              Until_Condition: None
               Until_Log_File: 
                Until_Log_Pos: 0
           Master_SSL_Allowed: No
           Master_SSL_CA_File: 
           Master_SSL_CA_Path: 
              Master_SSL_Cert: 
            Master_SSL_Cipher: 
               Master_SSL_Key: 
        Seconds_Behind_Master: 0
Master_SSL_Verify_Server_Cert: No
                Last_IO_Errno: 0
                Last_IO_Error: 
               Last_SQL_Errno: 0
               Last_SQL_Error: 
1 row in set (0.00 sec) 
 

Grant user logon from remote
grant all on *.* to 'root'@'%' identified by 'Gmcc1234' with grant option;
flush privileges;
install connector
rash "yum -y install mysql-connector-java"
下载cloudera repo并修改为CM 5.9
[root@ip-172-31-6-7 ~]# more cloudera-manager.repo 

[cloudera-manager]
# Packages for Cloudera Manager, Version 5, on RedHat or CentOS 6 x86_64                  
name=Cloudera Manager
baseurl=https://archive.cloudera.com/cm5/redhat/6/x86_64/cm/5.9/
gpgkey =https://archive.cloudera.com/cm5/redhat/6/x86_64/cm/RPM-GPG-KEY-cloudera    
gpgcheck = 1

安装JAVA JDK
yum install oracle-j2sdk1.7
配置CM DB
/usr/share/cmf/schema/scm_prepare_database.sh  -h vm1 mysql cmdb root Gmcc1234
启动服务
service cloudera-scm-server start

通过CM安装
http://ec2-34-224-8-199.compute-1.amazonaws.com:7180/

需要重新检查"sysctl vm.swappiness=1"
