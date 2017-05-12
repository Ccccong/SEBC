# The hostname of your db server node
```
[root@ip-172-31-1-9 ~]# hostname
ip-172-31-1-9
[root@ip-172-31-1-9 ~]# hostname -f
ip-172-31-1-9.ec2.internal

```
# The command and output for display your database server's version
```
[root@ip-172-31-1-9 ~]# mysql -uroot -p123456
Warning: Using a password on the command line interface can be insecure.
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 3
Server version: 5.6.36 MySQL Community Server (GPL)

Copyright (c) 2000, 2017, Oracle and/or its affiliates. All rights reserved.

```
# The command and output for listing your created databases
```
mysql> show databases;
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
9 rows in set (0.00 sec)
```
