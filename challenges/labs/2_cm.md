# List the command and output for  ls /etc/yum.repos.d  in  challenges/labs/2_cm.md 
```
[root@ip-172-31-12-204 sysadm]#  ls /etc/yum.repos.d 
CentOS-Base.repo  CentOS-Debuginfo.repo  CentOS-Media.repo  CentOS-Vault.repo  cloudera-manager.repo  mysql-community.repo  mysql-community-source.repo
```
# Use the  scm_prepare_database.sh  script to write your  db.properties  file 
  List the full command and result 
```
[root@ip-172-31-12-204 ~]# /usr/share/cmf/schema/scm_prepare_database.sh -h ip-172-31-1-9.ec2.internal mysql  scm root 123456
JAVA_HOME=/usr/java/jdk1.7.0_67-cloudera
Verifying that we can write to /etc/cloudera-scm-server
Creating SCM configuration file in /etc/cloudera-scm-server
Executing:  /usr/java/jdk1.7.0_67-cloudera/bin/java -cp /usr/share/java/mysql-connector-java.jar:/usr/share/java/oracle-connector-java.jar:/usr/share/cmf/schema/../lib/* com.cloudera.enterprise.dbutil.DbCommandExecutor /etc/cloudera-scm-server/db.properties com.cloudera.cmf.db.
[                          main] DbCommandExecutor              INFO  Successfully connected to database.
All done, your SCM database is configured correctly!

```