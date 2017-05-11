# Initial test
```
[root@ip-172-31-6-7 ~]# kinit sentry_test@SEBC.COM
Password for sentry_test@SEBC.COM: 
[root@ip-172-31-6-7 ~]# beeline
Beeline version 1.1.0-cdh5.9.2 by Apache Hive
beeline>  !connect jdbc:hive2://ip-172-31-11-232.ec2.internal:10000/default;principal=hive/ip-172-31-11-232.ec2.internal@SEBC.COM 
scan complete in 2ms
Connecting to jdbc:hive2://ip-172-31-11-232.ec2.internal:10000/default;principal=hive/ip-172-31-11-232.ec2.internal@SEBC.COM
Connected to: Apache Hive (version 1.1.0-cdh5.9.2)
Driver: Hive JDBC (version 1.1.0-cdh5.9.2)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://ip-172-31-11-232.ec2.internal> show tables
. . . . . . . . . . . . . . . . . . . . . . .> ;
INFO  : Compiling command(queryId=hive_20170511054747_0e1d9811-9a95-4a27-95ac-67207d93de3b): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20170511054747_0e1d9811-9a95-4a27-95ac-67207d93de3b); Time taken: 0.078 seconds
INFO  : Executing command(queryId=hive_20170511054747_0e1d9811-9a95-4a27-95ac-67207d93de3b): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170511054747_0e1d9811-9a95-4a27-95ac-67207d93de3b); Time taken: 0.141 seconds
INFO  : OK
+-----------+--+
| tab_name  |
+-----------+--+
+-----------+--+
No rows selected (0.319 seconds)
```

# After grant permission

```
0: jdbc:hive2://ip-172-31-11-232.ec2.internal>  CREATE ROLE sentry_admin; 
INFO  : Compiling command(queryId=hive_20170511054747_4b450e90-c67e-4870-8028-2450cedd40f4): CREATE ROLE sentry_admin
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170511054747_4b450e90-c67e-4870-8028-2450cedd40f4); Time taken: 0.06 seconds
INFO  : Executing command(queryId=hive_20170511054747_4b450e90-c67e-4870-8028-2450cedd40f4): CREATE ROLE sentry_admin
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170511054747_4b450e90-c67e-4870-8028-2450cedd40f4); Time taken: 0.14 seconds
INFO  : OK
No rows affected (0.216 seconds)
0: jdbc:hive2://ip-172-31-11-232.ec2.internal> GRANT ALL ON SERVER server1 TO ROLE sentry_admin; 
INFO  : Compiling command(queryId=hive_20170511054747_33d3591c-2308-496f-81f2-16c24bc3794b): GRANT ALL ON SERVER server1 TO ROLE sentry_admin
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170511054747_33d3591c-2308-496f-81f2-16c24bc3794b); Time taken: 0.083 seconds
INFO  : Executing command(queryId=hive_20170511054747_33d3591c-2308-496f-81f2-16c24bc3794b): GRANT ALL ON SERVER server1 TO ROLE sentry_admin
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170511054747_33d3591c-2308-496f-81f2-16c24bc3794b); Time taken: 0.099 seconds
INFO  : OK
No rows affected (0.198 seconds)
0: jdbc:hive2://ip-172-31-11-232.ec2.internal>  GRANT ROLE sentry_admin TO GROUP sentry_test; 
INFO  : Compiling command(queryId=hive_20170511054747_84287448-7881-42d5-bdb4-7e4742d39e52): GRANT ROLE sentry_admin TO GROUP sentry_test
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170511054747_84287448-7881-42d5-bdb4-7e4742d39e52); Time taken: 0.059 seconds
INFO  : Executing command(queryId=hive_20170511054747_84287448-7881-42d5-bdb4-7e4742d39e52): GRANT ROLE sentry_admin TO GROUP sentry_test
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170511054747_84287448-7881-42d5-bdb4-7e4742d39e52); Time taken: 0.093 seconds
INFO  : OK
No rows affected (0.166 seconds)
0: jdbc:hive2://ip-172-31-11-232.ec2.internal> SHOW TABLES; 
INFO  : Compiling command(queryId=hive_20170511054747_1d8fee8f-577e-4eb5-9af7-32b30066f483): SHOW TABLES
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20170511054747_1d8fee8f-577e-4eb5-9af7-32b30066f483); Time taken: 0.064 seconds
INFO  : Executing command(queryId=hive_20170511054747_1d8fee8f-577e-4eb5-9af7-32b30066f483): SHOW TABLES
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170511054747_1d8fee8f-577e-4eb5-9af7-32b30066f483); Time taken: 0.137 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| customers  |
| sample_07  |
| sample_08  |
| web_logs   |
+------------+--+
4 rows selected (0.226 seconds)
0: jdbc:hive2://ip-172-31-11-232.ec2.internal> 
```
# for user george
```
[root@ip-172-31-6-7 ~]# kinit george
Password for george@SEBC.COM: 
[root@ip-172-31-6-7 ~]# beeline
Beeline version 1.1.0-cdh5.9.2 by Apache Hive
beeline>   !connect jdbc:hive2://ip-172-31-11-232.ec2.internal:10000/default;principal=hive/ip-172-31-11-232.ec2.internal@SEBC.COM 
scan complete in 2ms
Connecting to jdbc:hive2://ip-172-31-11-232.ec2.internal:10000/default;principal=hive/ip-172-31-11-232.ec2.internal@SEBC.COM
Connected to: Apache Hive (version 1.1.0-cdh5.9.2)
Driver: Hive JDBC (version 1.1.0-cdh5.9.2)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://ip-172-31-11-232.ec2.internal> show tables;
INFO  : Compiling command(queryId=hive_20170511065959_7ef03409-18b7-4cba-b925-f645c8d34e9d): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20170511065959_7ef03409-18b7-4cba-b925-f645c8d34e9d); Time taken: 0.055 seconds
INFO  : Executing command(queryId=hive_20170511065959_7ef03409-18b7-4cba-b925-f645c8d34e9d): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170511065959_7ef03409-18b7-4cba-b925-f645c8d34e9d); Time taken: 0.138 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| customers  |
| sample_07  |
| sample_08  |
| web_logs   |
+------------+--+
4 rows selected (0.296 seconds)
```
# For user ferdinand
```
[root@ip-172-31-6-7 ~]# kinit ferdinand
Password for ferdinand@SEBC.COM: 
[root@ip-172-31-6-7 ~]# klist
Ticket cache: FILE:/tmp/krb5cc_0
Default principal: ferdinand@SEBC.COM

Valid starting     Expires            Service principal
05/11/17 07:00:18  05/12/17 07:00:18  krbtgt/SEBC.COM@SEBC.COM
        renew until 05/18/17 07:00:18
[root@ip-172-31-6-7 ~]# beeline
Beeline version 1.1.0-cdh5.9.2 by Apache Hive
beeline> !connect jdbc:hive2://ip-172-31-11-232.ec2.internal:10000/default;principal=hive/ip-172-31-11-232.ec2.internal@SEBC.COM 
scan complete in 2ms
Connecting to jdbc:hive2://ip-172-31-11-232.ec2.internal:10000/default;principal=hive/ip-172-31-11-232.ec2.internal@SEBC.COM
Connected to: Apache Hive (version 1.1.0-cdh5.9.2)
Driver: Hive JDBC (version 1.1.0-cdh5.9.2)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://ip-172-31-11-232.ec2.internal> show tables;
INFO  : Compiling command(queryId=hive_20170511070000_1b515cb4-0d74-423c-ba00-c64ee748f17d): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20170511070000_1b515cb4-0d74-423c-ba00-c64ee748f17d); Time taken: 0.07 seconds
INFO  : Executing command(queryId=hive_20170511070000_1b515cb4-0d74-423c-ba00-c64ee748f17d): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170511070000_1b515cb4-0d74-423c-ba00-c64ee748f17d); Time taken: 0.129 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| sample_07  |
+------------+--+
1 row selected (0.3 seconds)
```