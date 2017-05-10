# Use the API on the command line to: 
# 1.Report the latest available version of the API
```
[root@ip-172-31-6-7 cloudera-scm-server]# curl -u admin:admin 'http://172.31.6.7:7180/api/version'
v16
```
# 2. Report the CM version
```
[root@ip-172-31-6-7 cloudera-scm-server]# curl -u admin:admin 'http://172.31.6.7:7180/api/v14/cm/version'
{
  "version" : "5.11.0",
  "buildUser" : "jenkins",
  "buildTimestamp" : "20170412-1249",
  "gitHash" : "70cb1442626406432a6e7af5bdf206a384ca3f98",
  "snapshot" : false
}
```
# 3. List all CM users
```
[root@ip-172-31-6-7 ~]# curl -u admin:admin 'http://172.31.6.7:7180/api/v14/users'
{
  "items" : [ {
    "name" : " minotaur ",
    "roles" : [ "ROLE_CONFIGURATOR" ]
  }, {
    "name" : "admin",
    "roles" : [ "ROLE_ADMIN" ]
  }, {
    "name" : "gang1998",
    "roles" : [ "ROLE_ADMIN" ]
  }, {
    "name" : "minotaur",
    "roles" : [ "ROLE_CONFIGURATOR" ]
  } ]
}
```
# 4. Report the database server in use by CM
```
}[root@ip-172-31-6-7 ~]# curl -u admin:admin 'http://172.31.6.7:7180/api/v14/cm/scmDbInfo'
{
  "scmDbType" : "MYSQL",
  "embeddedDbUsed" : false
}
```