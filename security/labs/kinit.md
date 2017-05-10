# `The  kinit  command you use to authenticate your test user
```
[root@ip-172-31-6-7 ~]# kinit hdfs
Password for hdfs@SEBC.COM: 
[root@ip-172-31-6-7 ~]# 
```
# 2The output from a  klist  command listing your credentials and ticket lifetime
```
[root@ip-172-31-6-7 ~]# klist
Ticket cache: FILE:/tmp/krb5cc_0
Default principal: hdfs@SEBC.COM

Valid starting     Expires            Service principal
05/10/17 11:49:40  05/11/17 11:49:40  krbtgt/SEBC.COM@SEBC.COM
        renew until 05/17/17 11:49:40
```