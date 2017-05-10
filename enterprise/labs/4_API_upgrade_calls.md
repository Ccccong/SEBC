# Use the API on the command line to: 
# 1.Report the latest available version of the API
```
[root@ip-172-31-6-7 ~]# curl -u admin:admin 'http://172.31.6.7:7180/api/version'
v14
```
# 2. Report the CM version
```
[root@ip-172-31-6-7 ~]# curl -u admin:admin 'http://172.31.6.7:7180/api/v14/cm/version'
{
  "version" : "5.9.2",
  "buildUser" : "jenkins",
  "buildTimestamp" : "20170330-1814",
  "gitHash" : "822da28bff818f57fc1bfc3eafe3a550300ef1b0",
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