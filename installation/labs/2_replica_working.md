# 1 Download mysql and install
```
1. Master node ( vm1) and slave node (vm2):
	yum install mysql-server
2. All nodes:
	yum install mysql
     yum -y install mysql-connector-java
```
# 2 Modify /etc/my.cnf to support replication
<div>
Master node:
```
server-id=1
log-bin=mysql-bin
binlog-format=row
```
Slave node:
```
server-id=2
log-bin=mysql-bin
binlog-format=row
```
</div>
# 3 Start the mysqld service.
	Start mysql on master and slave
```
Service mysqld start
```
# 4 Secure mysql installation
```
[root@ip-172-31-6-7 ~]#  /usr/bin/mysql_secure_installation 
```
# 5 Grant replication privileges 

Create replication user
```
CREATE USER 'repl'@'172.31.%.%' IDENTIFIED BY 'slavepass';
GRANT REPLICATION SLAVE ON *.* TO 'repl'@'172.31.%.%';
SET GLOBAL binlog_format = 'ROW';
FLUSH TABLES WITH READ LOCK;
```
# 6 Log into the MySQL master and show its status
	Master node:
```
mysql> show master status;
+------------------+----------+--------------+------------------+
| File             | Position | Binlog_Do_DB | Binlog_Ignore_DB |
+------------------+----------+--------------+------------------+
| mysql-bin.000003 |     2251 |              |                  |
+------------------+----------+--------------+------------------+
1 row in set (0.00 sec)
```
# 7  Configure a connection to the master from slave:
```
mysql> CHANGE MASTER TO MASTER_HOST='vm1', MASTER_USER='repl', MASTER_PASSWORD='slavepass', MASTER_LOG_FILE='mysql-bin.000003', MASTER_LOG_POS=2251 ; 
Query OK, 0 rows affected (0.02 sec)
```
# 8 Initiate slave operations on the replica
```
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
 ```

# 9 Grant user logon from remote
```
grant all on *.* to 'root'@'%' identified by 'Gmcc1234' with grant option;
flush privileges;
```