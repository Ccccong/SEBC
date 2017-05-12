# The command and output for  hdfs dfs -ls /user 
```
[hdfs@ip-172-31-12-204 ~]$ hdfs dfs -ls /user
Found 7 items
drwxr-xr-x   - chen   chen            0 2017-05-12 02:29 /user/chen
drwxrwxrwx   - mapred hadoop          0 2017-05-12 02:23 /user/history
drwxrwxr-t   - hive   hive            0 2017-05-12 02:24 /user/hive
drwxrwxr-x   - hue    hue             0 2017-05-12 02:25 /user/hue
drwxrwxr-x   - impala impala          0 2017-05-12 02:25 /user/impala
drwxrwxr-x   - oozie  oozie           0 2017-05-12 02:25 /user/oozie
drwxr-xr-x   - zhou   zhou            0 2017-05-12 02:29 /user/zhou
```

# The command and output from the CM API call  ../api/v14/hosts 

```
[root@ip-172-31-12-204 ~]# curl -X GET -u admin:admin 'http://ip-172-31-12-204.ec2.internal:7180/api/v14/hosts'
{
  "items" : [ {
    "hostId" : "1a3ac9e4-6be1-4990-982b-4bb46c6fbcf7",
    "ipAddress" : "172.31.1.9",
    "hostname" : "ip-172-31-1-9.ec2.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-172-31-12-204.ec2.internal:7180/cmf/hostRedirect/1a3ac9e4-6be1-4990-982b-4bb46c6fbcf7",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 4,
    "totalPhysMemBytes" : 15740305408
  }, {
    "hostId" : "af7e0ec0-0699-4ed4-95c8-68b32f20a236",
    "ipAddress" : "172.31.1.94",
    "hostname" : "ip-172-31-1-94.ec2.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-172-31-12-204.ec2.internal:7180/cmf/hostRedirect/af7e0ec0-0699-4ed4-95c8-68b32f20a236",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 4,
    "totalPhysMemBytes" : 15740305408
  }, {
    "hostId" : "6099ad6b-2991-410a-baab-9696be0193c7",
    "ipAddress" : "172.31.12.204",
    "hostname" : "ip-172-31-12-204.ec2.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-172-31-12-204.ec2.internal:7180/cmf/hostRedirect/6099ad6b-2991-410a-baab-9696be0193c7",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 4,
    "totalPhysMemBytes" : 15740305408
  }, {
    "hostId" : "ae14d0de-cf00-4d3c-af58-5dd5887e74f5",
    "ipAddress" : "172.31.6.145",
    "hostname" : "ip-172-31-6-145.ec2.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-172-31-12-204.ec2.internal:7180/cmf/hostRedirect/ae14d0de-cf00-4d3c-af58-5dd5887e74f5",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 4,
    "totalPhysMemBytes" : 15740305408
  }, {
    "hostId" : "94b9c724-0282-4eb0-83a0-86ac9bf681b0",
    "ipAddress" : "172.31.6.28",
    "hostname" : "ip-172-31-6-28.ec2.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-172-31-12-204.ec2.internal:7180/cmf/hostRedirect/94b9c724-0282-4eb0-83a0-86ac9bf681b0",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 4,
    "totalPhysMemBytes" : 15740305408
  } ]
}
```

# The command and output from the CM API call  ../api/v6/clusters/<githubName>/services 
```
[root@ip-172-31-12-204 ~]# curl -X GET -u admin:admin 'http://ip-172-31-12-204.ec2.internal:7180/api/v6/clusters/gang1998/services'
{
  "items" : [ {
    "name" : "hive",
    "type" : "HIVE",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://ip-172-31-12-204.ec2.internal:7180/cmf/serviceRedirect/hive",
    "serviceState" : "STARTED",
    "healthSummary" : "GOOD",
    "healthChecks" : [ {
      "name" : "HIVE_HIVEMETASTORES_HEALTHY",
      "summary" : "GOOD"
    }, {
      "name" : "HIVE_HIVESERVER2S_HEALTHY",
      "summary" : "GOOD"
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "Hive"
  }, {
    "name" : "zookeeper",
    "type" : "ZOOKEEPER",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://ip-172-31-12-204.ec2.internal:7180/cmf/serviceRedirect/zookeeper",
    "serviceState" : "STARTED",
    "healthSummary" : "GOOD",
    "healthChecks" : [ {
      "name" : "ZOOKEEPER_CANARY_HEALTH",
      "summary" : "GOOD"
    }, {
      "name" : "ZOOKEEPER_SERVERS_HEALTHY",
      "summary" : "GOOD"
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "ZooKeeper"
  }, {
    "name" : "hue",
    "type" : "HUE",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://ip-172-31-12-204.ec2.internal:7180/cmf/serviceRedirect/hue",
    "serviceState" : "STARTED",
    "healthSummary" : "GOOD",
    "healthChecks" : [ {
      "name" : "HUE_HUE_SERVERS_HEALTHY",
      "summary" : "GOOD"
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "Hue"
  }, {
    "name" : "oozie",
    "type" : "OOZIE",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://ip-172-31-12-204.ec2.internal:7180/cmf/serviceRedirect/oozie",
    "serviceState" : "STARTED",
    "healthSummary" : "GOOD",
    "healthChecks" : [ {
      "name" : "OOZIE_OOZIE_SERVERS_HEALTHY",
      "summary" : "GOOD"
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "Oozie"
  }, {
    "name" : "impala",
    "type" : "IMPALA",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://ip-172-31-12-204.ec2.internal:7180/cmf/serviceRedirect/impala",
    "serviceState" : "STARTED",
    "healthSummary" : "GOOD",
    "healthChecks" : [ {
      "name" : "IMPALA_ASSIGNMENT_LOCALITY",
      "summary" : "DISABLED"
    }, {
      "name" : "IMPALA_CATALOGSERVER_HEALTH",
      "summary" : "GOOD"
    }, {
      "name" : "IMPALA_IMPALADS_HEALTHY",
      "summary" : "GOOD"
    }, {
      "name" : "IMPALA_STATESTORE_HEALTH",
      "summary" : "GOOD"
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "Impala"
  }, {
    "name" : "yarn",
    "type" : "YARN",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://ip-172-31-12-204.ec2.internal:7180/cmf/serviceRedirect/yarn",
    "serviceState" : "STARTED",
    "healthSummary" : "GOOD",
    "healthChecks" : [ {
      "name" : "YARN_JOBHISTORY_HEALTH",
      "summary" : "GOOD"
    }, {
      "name" : "YARN_NODE_MANAGERS_HEALTHY",
      "summary" : "GOOD"
    }, {
      "name" : "YARN_RESOURCEMANAGERS_HEALTH",
      "summary" : "GOOD"
    }, {
      "name" : "YARN_USAGE_AGGREGATION_HEALTH",
      "summary" : "DISABLED"
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "YARN (MR2 Included)"
  }, {
    "name" : "hdfs",
    "type" : "HDFS",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://ip-172-31-12-204.ec2.internal:7180/cmf/serviceRedirect/hdfs",
    "serviceState" : "STARTED",
    "healthSummary" : "GOOD",
    "healthChecks" : [ {
      "name" : "HDFS_BLOCKS_WITH_CORRUPT_REPLICAS",
      "summary" : "GOOD"
    }, {
      "name" : "HDFS_CANARY_HEALTH",
      "summary" : "GOOD"
    }, {
      "name" : "HDFS_DATA_NODES_HEALTHY",
      "summary" : "GOOD"
    }, {
      "name" : "HDFS_FREE_SPACE_REMAINING",
      "summary" : "GOOD"
    }, {
      "name" : "HDFS_HA_NAMENODE_HEALTH",
      "summary" : "GOOD"
    }, {
      "name" : "HDFS_MISSING_BLOCKS",
      "summary" : "GOOD"
    }, {
      "name" : "HDFS_UNDER_REPLICATED_BLOCKS",
      "summary" : "GOOD"
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "HDFS"
  } ]
}
```

