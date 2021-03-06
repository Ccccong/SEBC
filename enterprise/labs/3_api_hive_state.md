# Write  curl  statements that stop, start, and check the current state of your Hive service.

1. Check Hive status
```
[root@ip-172-31-6-7 ~]# curl -u admin:admin 'http://172.31.6.7:7180/api/v2/clusters/gang1998/services/hive'
{
  "name" : "hive",
  "type" : "HIVE",
  "clusterRef" : {
    "clusterName" : "cluster"
  },
  "serviceUrl" : "http://ip-172-31-6-7.ec2.internal:7180/cmf/serviceRedirect/hive",
  "serviceState" : "STARTED",
  "healthSummary" : "GOOD",
  "healthChecks" : [ {
    "name" : "HIVE_HIVEMETASTORES_HEALTHY",
    "summary" : "GOOD"
  }, {
    "name" : "HIVE_HIVESERVER2S_HEALTHY",
    "summary" : "GOOD"
  } ],
  "configStale" : false,
  "maintenanceMode" : false,
  "maintenanceOwners" : [ ],
  "displayName" : "Hive"

```
2. Stop Hive service
```
[root@ip-172-31-6-7 ~]# curl -X POST -u admin:admin 'http://172.31.6.7:7180/api/v2/clusters/gang1998/services/hive/commands/stop'
{
  "id" : 269,
  "name" : "Stop",
  "startTime" : "2017-05-10T03:39:22.924Z",
  "active" : true,
  "serviceRef" : {
    "clusterName" : "cluster",
    "serviceName" : "hive"
  }
}[root@ip-172-31-6-7 ~]# 
```
3. Start Hive service
```
[root@ip-172-31-6-7 ~]# curl -X POST -u admin:admin 'http://172.31.6.7:7180/api/v2/clusters/gang1998/services/hive/commands/start'
{
  "id" : 273,
  "name" : "Start",
  "startTime" : "2017-05-10T03:40:11.432Z",
  "active" : true,
  "serviceRef" : {
    "clusterName" : "cluster",
    "serviceName" : "hive"
  }
}[root@ip-172-31-6-7 ~]# 
```
4.Verify the Hive status
```
[root@ip-172-31-6-7 ~]# curl -u admin:admin 'http://172.31.6.7:7180/api/v2/clusters/gang1998/services/hive'
{
  "name" : "hive",
  "type" : "HIVE",
  "clusterRef" : {
    "clusterName" : "cluster"
  },
  "serviceUrl" : "http://ip-172-31-6-7.ec2.internal:7180/cmf/serviceRedirect/hive",
  "serviceState" : "STARTED",
  "healthSummary" : "GOOD",
  "healthChecks" : [ {
    "name" : "HIVE_HIVEMETASTORES_HEALTHY",
    "summary" : "GOOD"
  }, {
    "name" : "HIVE_HIVESERVER2S_HEALTHY",
    "summary" : "GOOD"
  } ],
  "configStale" : false,
  "maintenanceMode" : false,
  "maintenanceOwners" : [ ],
  "displayName" : "Hive"
}
```

