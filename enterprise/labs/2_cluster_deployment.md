# command
[root@ip-172-31-6-7 ~]# curl -u admin:admin 'http://172.31.6.7:7180/api/v2/cm/deployment ' >2_cluster_deployment.md 
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 26920    0 26920    0     0   481k      0 --:--:-- --:--:-- --:--:--  486k
# output
```
{
  "timestamp" : "2017-05-10T03:27:04.324Z",
  "clusters" : [ {
    "name" : "gang1998",
    "version" : "CDH5",
    "services" : [ {
      "name" : "hive",
      "type" : "HIVE",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "HIVEMETASTORE",
          "items" : [ {
            "name" : "hive_metastore_java_heapsize",
            "value" : "612368384"
          } ]
        }, {
          "roleType" : "HIVESERVER2",
          "items" : [ {
            "name" : "hiveserver2_java_heapsize",
            "value" : "612368384"
          }, {
            "name" : "hiveserver2_spark_driver_memory",
            "value" : "966367641"
          }, {
            "name" : "hiveserver2_spark_executor_cores",
            "value" : "4"
          }, {
            "name" : "hiveserver2_spark_executor_memory",
            "value" : "4679270400"
          }, {
            "name" : "hiveserver2_spark_yarn_driver_memory_overhead",
            "value" : "102"
          }, {
            "name" : "hiveserver2_spark_yarn_executor_memory_overhead",
            "value" : "787"
          } ]
        } ],
        "items" : [ {
          "name" : "hive_metastore_database_host",
          "value" : "ip-172-31-6-7.ec2.internal"
        }, {
          "name" : "hive_metastore_database_name",
          "value" : "hivedb"
        }, {
          "name" : "hive_metastore_database_password",
          "value" : "Gmcc1234"
        }, {
          "name" : "hive_metastore_database_user",
          "value" : "root"
        }, {
          "name" : "mapreduce_yarn_service",
          "value" : "yarn"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hive-GATEWAY-013cccf53a0238e142c7bec4fce0d01b",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "f3e9f4aa-9549-4226-b9c5-353c03a9f593"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-GATEWAY-06396069889e4f7b61776cf40bb2d597",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "601d3135-1b20-4a30-95be-3a91f2681de1"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-GATEWAY-50b84f9ceb55aa15be9ae821cb75f05b",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "6e4c9707-6b26-465a-b3e0-d4d51f1c56de"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-GATEWAY-cd35ba2a0cb89ab58290e9cd095bf28e",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "fa32d7d6-0ce4-41da-97f9-ebb10317fc5f"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-GATEWAY-f24391512884ddf7a7c8b95da66ce1ee",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "i-01151823cfdaa6a5e"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-HIVEMETASTORE-013cccf53a0238e142c7bec4fce0d01b",
        "type" : "HIVEMETASTORE",
        "hostRef" : {
          "hostId" : "f3e9f4aa-9549-4226-b9c5-353c03a9f593"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "9suawbuxiyt2klnn7x25jt9sw"
          } ]
        }
      }, {
        "name" : "hive-HIVESERVER2-013cccf53a0238e142c7bec4fce0d01b",
        "type" : "HIVESERVER2",
        "hostRef" : {
          "hostId" : "f3e9f4aa-9549-4226-b9c5-353c03a9f593"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "c9p3apkspascaixeq5x1daqw5"
          } ]
        }
      } ],
      "displayName" : "Hive"
    }, {
      "name" : "zookeeper",
      "type" : "ZOOKEEPER",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "SERVER",
          "items" : [ {
            "name" : "zookeeper_server_java_heapsize",
            "value" : "612368384"
          } ]
        } ],
        "items" : [ ]
      },
      "roles" : [ {
        "name" : "zookeeper-SERVER-013cccf53a0238e142c7bec4fce0d01b",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "f3e9f4aa-9549-4226-b9c5-353c03a9f593"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "d045jf8larpjccey1sf6dvoqo"
          }, {
            "name" : "serverId",
            "value" : "1"
          } ]
        }
      }, {
        "name" : "zookeeper-SERVER-06396069889e4f7b61776cf40bb2d597",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "601d3135-1b20-4a30-95be-3a91f2681de1"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "4lian2asyign2ivwhy6sybuv"
          }, {
            "name" : "serverId",
            "value" : "2"
          } ]
        }
      }, {
        "name" : "zookeeper-SERVER-50b84f9ceb55aa15be9ae821cb75f05b",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "6e4c9707-6b26-465a-b3e0-d4d51f1c56de"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "7mhcj8p7ozic73e3p47mnrkhj"
          }, {
            "name" : "serverId",
            "value" : "3"
          } ]
        }
      } ],
      "displayName" : "ZooKeeper"
    }, {
      "name" : "hue",
      "type" : "HUE",
      "config" : {
        "roleTypeConfigs" : [ ],
        "items" : [ {
          "name" : "database_host",
          "value" : "ip-172-31-6-7.ec2.internal"
        }, {
          "name" : "database_name",
          "value" : "huedb"
        }, {
          "name" : "database_password",
          "value" : "Gmcc1234"
        }, {
          "name" : "database_type",
          "value" : "mysql"
        }, {
          "name" : "database_user",
          "value" : "root"
        }, {
          "name" : "hive_service",
          "value" : "hive"
        }, {
          "name" : "hue_webhdfs",
          "value" : "hdfs-NAMENODE-013cccf53a0238e142c7bec4fce0d01b"
        }, {
          "name" : "oozie_service",
          "value" : "oozie"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hue-HUE_SERVER-013cccf53a0238e142c7bec4fce0d01b",
        "type" : "HUE_SERVER",
        "hostRef" : {
          "hostId" : "f3e9f4aa-9549-4226-b9c5-353c03a9f593"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "cy30hqj1hbpbk6xr1kkteh98g"
          }, {
            "name" : "secret_key",
            "value" : "hSLB6o2aRKdMPji8gyvTHdyWKIE6Eb"
          } ]
        }
      } ],
      "displayName" : "Hue"
    }, {
      "name" : "oozie",
      "type" : "OOZIE",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "OOZIE_SERVER",
          "items" : [ {
            "name" : "oozie_database_host",
            "value" : "ip-172-31-6-7.ec2.internal"
          }, {
            "name" : "oozie_database_name",
            "value" : "OOdb"
          }, {
            "name" : "oozie_database_password",
            "value" : "Gmcc1234"
          }, {
            "name" : "oozie_database_type",
            "value" : "mysql"
          }, {
            "name" : "oozie_database_user",
            "value" : "root"
          }, {
            "name" : "oozie_java_heapsize",
            "value" : "612368384"
          } ]
        } ],
        "items" : [ {
          "name" : "hive_service",
          "value" : "hive"
        }, {
          "name" : "mapreduce_yarn_service",
          "value" : "yarn"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "oozie-OOZIE_SERVER-013cccf53a0238e142c7bec4fce0d01b",
        "type" : "OOZIE_SERVER",
        "hostRef" : {
          "hostId" : "f3e9f4aa-9549-4226-b9c5-353c03a9f593"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "ajt2gwikrhuk6x8q3ant4nrr"
          } ]
        }
      } ],
      "displayName" : "Oozie"
    }, {
      "name" : "yarn",
      "type" : "YARN",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "GATEWAY",
          "items" : [ {
            "name" : "mapred_reduce_tasks",
            "value" : "8"
          }, {
            "name" : "mapred_submit_replication",
            "value" : "2"
          } ]
        }, {
          "roleType" : "JOBHISTORY",
          "items" : [ {
            "name" : "mr2_jobhistory_java_heapsize",
            "value" : "612368384"
          } ]
        }, {
          "roleType" : "NODEMANAGER",
          "items" : [ {
            "name" : "yarn_nodemanager_heartbeat_interval_ms",
            "value" : "100"
          }, {
            "name" : "yarn_nodemanager_local_dirs",
            "value" : "/yarn/nm"
          }, {
            "name" : "yarn_nodemanager_log_dirs",
            "value" : "/yarn/container-logs"
          }, {
            "name" : "yarn_nodemanager_resource_cpu_vcores",
            "value" : "4"
          }, {
            "name" : "yarn_nodemanager_resource_memory_mb",
            "value" : "5250"
          } ]
        }, {
          "roleType" : "RESOURCEMANAGER",
          "items" : [ {
            "name" : "resource_manager_java_heapsize",
            "value" : "612368384"
          }, {
            "name" : "yarn_scheduler_maximum_allocation_mb",
            "value" : "5250"
          }, {
            "name" : "yarn_scheduler_maximum_allocation_vcores",
            "value" : "4"
          } ]
        } ],
        "items" : [ {
          "name" : "hdfs_service",
          "value" : "hdfs"
        }, {
          "name" : "rm_dirty",
          "value" : "true"
        }, {
          "name" : "zk_authorization_secret_key",
          "value" : "1ZunJOTiWJ2nF5R1IvBmrDafgNIt1T"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "yarn-JOBHISTORY-013cccf53a0238e142c7bec4fce0d01b",
        "type" : "JOBHISTORY",
        "hostRef" : {
          "hostId" : "f3e9f4aa-9549-4226-b9c5-353c03a9f593"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "9cnkkbxnaag2zctbwvuk2xu88"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-06396069889e4f7b61776cf40bb2d597",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "601d3135-1b20-4a30-95be-3a91f2681de1"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "7o0kfcmgu9utgnt5vr1m9ipnk"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-50b84f9ceb55aa15be9ae821cb75f05b",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "6e4c9707-6b26-465a-b3e0-d4d51f1c56de"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "5iurlmg03mvhuwtl7ztbhoxtt"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-cd35ba2a0cb89ab58290e9cd095bf28e",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "fa32d7d6-0ce4-41da-97f9-ebb10317fc5f"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "7agr2s2odlp8g7ang7piha3to"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-f24391512884ddf7a7c8b95da66ce1ee",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "i-01151823cfdaa6a5e"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "70l8h4w99xq9sy5mm2c39k162"
          } ]
        }
      }, {
        "name" : "yarn-RESOURCEMANAGER-013cccf53a0238e142c7bec4fce0d01b",
        "type" : "RESOURCEMANAGER",
        "hostRef" : {
          "hostId" : "f3e9f4aa-9549-4226-b9c5-353c03a9f593"
        },
        "config" : {
          "items" : [ {
            "name" : "rm_id",
            "value" : "49"
          }, {
            "name" : "role_jceks_password",
            "value" : "ddym6cll2wjaxvlkd4sg7rhmj"
          } ]
        }
      } ],
      "displayName" : "YARN (MR2 Included)"
    }, {
      "name" : "hdfs",
      "type" : "HDFS",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "BALANCER",
          "items" : [ {
            "name" : "balancer_java_heapsize",
            "value" : "612368384"
          } ]
        }, {
          "roleType" : "DATANODE",
          "items" : [ {
            "name" : "dfs_data_dir_list",
            "value" : "/dfs/dn"
          }, {
            "name" : "dfs_datanode_du_reserved",
            "value" : "3170683699"
          } ]
        }, {
          "roleType" : "GATEWAY",
          "items" : [ {
            "name" : "dfs_client_use_trash",
            "value" : "true"
          } ]
        }, {
          "roleType" : "JOURNALNODE",
          "items" : [ {
            "name" : "dfs_journalnode_edits_dir",
            "value" : "/dfs/jn"
          } ]
        }, {
          "roleType" : "NAMENODE",
          "items" : [ {
            "name" : "dfs_name_dir_list",
            "value" : "/dfs/nn"
          }, {
            "name" : "dfs_namenode_servicerpc_address",
            "value" : "8022"
          }, {
            "name" : "namenode_java_heapsize",
            "value" : "612368384"
          } ]
        }, {
          "roleType" : "SECONDARYNAMENODE",
          "items" : [ {
            "name" : "fs_checkpoint_dir_list",
            "value" : "/dfs/snn"
          }, {
            "name" : "secondary_namenode_java_heapsize",
            "value" : "612368384"
          } ]
        } ],
        "items" : [ {
          "name" : "dfs_ha_fencing_cloudera_manager_secret_key",
          "value" : "GJlPbpQFCw9Jn22Sznz0FYi3vl5XWm"
        }, {
          "name" : "dfs_ha_fencing_methods",
          "value" : "shell(true)"
        }, {
          "name" : "fc_authorization_secret_key",
          "value" : "jnJ9ckbkC3yISQ80aHmzjwADQWCB4q"
        }, {
          "name" : "http_auth_signature_secret",
          "value" : "AEOgefcqBjGRAHdGgJOKonBHSHNzTf"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hdfs-BALANCER-013cccf53a0238e142c7bec4fce0d01b",
        "type" : "BALANCER",
        "hostRef" : {
          "hostId" : "f3e9f4aa-9549-4226-b9c5-353c03a9f593"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hdfs-DATANODE-06396069889e4f7b61776cf40bb2d597",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "601d3135-1b20-4a30-95be-3a91f2681de1"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "6zinfiszkpdv4li6ok2lv5omw"
          } ]
        }
      }, {
        "name" : "hdfs-DATANODE-50b84f9ceb55aa15be9ae821cb75f05b",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "6e4c9707-6b26-465a-b3e0-d4d51f1c56de"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "a2rzcocl4proaff8ncv7qvpon"
          } ]
        }
      }, {
        "name" : "hdfs-DATANODE-cd35ba2a0cb89ab58290e9cd095bf28e",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "fa32d7d6-0ce4-41da-97f9-ebb10317fc5f"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "2y7egz2u6acah4bbjw2jo7z0"
          } ]
        }
      }, {
        "name" : "hdfs-DATANODE-f24391512884ddf7a7c8b95da66ce1ee",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "i-01151823cfdaa6a5e"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "2azsyp9iljmh4y89zh5aw4lly"
          } ]
        }
      }, {
        "name" : "hdfs-FAILOVERCONTROLLER-013cccf53a0238e142c7bec4fce0d01b",
        "type" : "FAILOVERCONTROLLER",
        "hostRef" : {
          "hostId" : "f3e9f4aa-9549-4226-b9c5-353c03a9f593"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "cvcciqakvgbk57j4ek9mapjyb"
          } ]
        }
      }, {
        "name" : "hdfs-FAILOVERCONTROLLER-cd35ba2a0cb89ab58290e9cd095bf28e",
        "type" : "FAILOVERCONTROLLER",
        "hostRef" : {
          "hostId" : "fa32d7d6-0ce4-41da-97f9-ebb10317fc5f"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "akkwkk0o98ulb36wmmmwyw98b"
          } ]
        }
      }, {
        "name" : "hdfs-JOURNALNODE-013cccf53a0238e142c7bec4fce0d01b",
        "type" : "JOURNALNODE",
        "hostRef" : {
          "hostId" : "f3e9f4aa-9549-4226-b9c5-353c03a9f593"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "41lqeo0mek83iioy4lrph21br"
          } ]
        }
      }, {
        "name" : "hdfs-JOURNALNODE-50b84f9ceb55aa15be9ae821cb75f05b",
        "type" : "JOURNALNODE",
        "hostRef" : {
          "hostId" : "6e4c9707-6b26-465a-b3e0-d4d51f1c56de"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "gmlat52pv581oi2c7iqf03ul"
          } ]
        }
      }, {
        "name" : "hdfs-JOURNALNODE-cd35ba2a0cb89ab58290e9cd095bf28e",
        "type" : "JOURNALNODE",
        "hostRef" : {
          "hostId" : "fa32d7d6-0ce4-41da-97f9-ebb10317fc5f"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "vc3tx0evz2puvuyd2qrmu0ao"
          } ]
        }
      }, {
        "name" : "hdfs-NAMENODE-013cccf53a0238e142c7bec4fce0d01b",
        "type" : "NAMENODE",
        "hostRef" : {
          "hostId" : "f3e9f4aa-9549-4226-b9c5-353c03a9f593"
        },
        "config" : {
          "items" : [ {
            "name" : "autofailover_enabled",
            "value" : "true"
          }, {
            "name" : "dfs_federation_namenode_nameservice",
            "value" : "nameservice1"
          }, {
            "name" : "dfs_namenode_quorum_journal_name",
            "value" : "nameservice1"
          }, {
            "name" : "namenode_id",
            "value" : "51"
          }, {
            "name" : "role_jceks_password",
            "value" : "9t7rhezjuwroyy2g7ln24ih3m"
          } ]
        }
      }, {
        "name" : "hdfs-NAMENODE-cd35ba2a0cb89ab58290e9cd095bf28e",
        "type" : "NAMENODE",
        "hostRef" : {
          "hostId" : "fa32d7d6-0ce4-41da-97f9-ebb10317fc5f"
        },
        "config" : {
          "items" : [ {
            "name" : "autofailover_enabled",
            "value" : "true"
          }, {
            "name" : "dfs_federation_namenode_nameservice",
            "value" : "nameservice1"
          }, {
            "name" : "dfs_namenode_quorum_journal_name",
            "value" : "nameservice1"
          }, {
            "name" : "namenode_id",
            "value" : "59"
          }, {
            "name" : "role_jceks_password",
            "value" : "b1vzeom2cs8j6hecutv1pu2sn"
          } ]
        }
      } ],
      "displayName" : "HDFS"
    } ]
  } ],
  "hosts" : [ {
    "hostId" : "f3e9f4aa-9549-4226-b9c5-353c03a9f593",
    "ipAddress" : "172.31.11.232",
    "hostname" : "ip-172-31-11-232.ec2.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "fa32d7d6-0ce4-41da-97f9-ebb10317fc5f",
    "ipAddress" : "172.31.15.40",
    "hostname" : "ip-172-31-15-40.ec2.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "6e4c9707-6b26-465a-b3e0-d4d51f1c56de",
    "ipAddress" : "172.31.5.148",
    "hostname" : "ip-172-31-5-148.ec2.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "601d3135-1b20-4a30-95be-3a91f2681de1",
    "ipAddress" : "172.31.6.212",
    "hostname" : "ip-172-31-6-212.ec2.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "i-01151823cfdaa6a5e",
    "ipAddress" : "172.31.6.7",
    "hostname" : "ip-172-31-6-7.ec2.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  } ],
  "users" : [ {
    "name" : " minotaur ",
    "roles" : [ "ROLE_CONFIGURATOR" ],
    "pwHash" : "00d6a5a160ed54e757447123d57cea7df8edc8a4a5a955c056af9428d57709ea",
    "pwSalt" : 8753567311391251196,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-EVENTSERVER-013cccf53a0238e142c7bec4fce0d01b",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "01a4bb49fd7216ba84bb7be0a0ad3c47bbddcf960c9868f1d71513a4b48a5356",
    "pwSalt" : -6315968570105043101,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-HOSTMONITOR-013cccf53a0238e142c7bec4fce0d01b",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "9d0c074389448c30d862426a9b64e8427323c17d097839d9527bbbe504ad242e",
    "pwSalt" : -5858185308406675419,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-REPORTSMANAGER-013cccf53a0238e142c7bec4fce0d01b",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "2e6d99a1d4391ab8dfb5984b37debd5d4b9729373b5592fcaf0c7a3288100bfc",
    "pwSalt" : 5823113900747297546,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-SERVICEMONITOR-013cccf53a0238e142c7bec4fce0d01b",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "13d6d67429f861015e5f96f0a73e6dbd53085c618f8246cb1737c411a471a15f",
    "pwSalt" : -5737216344500187743,
    "pwLogin" : true
  }, {
    "name" : "admin",
    "roles" : [ "ROLE_ADMIN" ],
    "pwHash" : "2645280866f18239fa49ca9074b8aff1eac9e646c52fd23594d353c089943efd",
    "pwSalt" : -4427131628473139987,
    "pwLogin" : true
  }, {
    "name" : "gang1998",
    "roles" : [ "ROLE_ADMIN" ],
    "pwHash" : "f6b7bf4f72f2948bb1b9bfafaf2448d3ec99a06753134ef104e43fc7d293bf4e",
    "pwSalt" : 1478515963221833557,
    "pwLogin" : true
  }, {
    "name" : "minotaur",
    "roles" : [ "ROLE_CONFIGURATOR" ],
    "pwHash" : "586a7a5b2b50e51c3daad6363435801b04bd13e0b6bbc735f9cbc57198d3b440",
    "pwSalt" : -5516504859582671412,
    "pwLogin" : true
  } ],
  "versionInfo" : {
    "version" : "5.9.2",
    "buildUser" : "jenkins",
    "buildTimestamp" : "20170330-1814",
    "gitHash" : "822da28bff818f57fc1bfc3eafe3a550300ef1b0",
    "snapshot" : false
  },
  "managementService" : {
    "name" : "mgmt",
    "type" : "MGMT",
    "config" : {
      "roleTypeConfigs" : [ {
        "roleType" : "EVENTSERVER",
        "items" : [ {
          "name" : "event_server_heapsize",
          "value" : "612368384"
        } ]
      }, {
        "roleType" : "HOSTMONITOR",
        "items" : [ {
          "name" : "firehose_heapsize",
          "value" : "612368384"
        }, {
          "name" : "firehose_non_java_memory_bytes",
          "value" : "805306368"
        } ]
      }, {
        "roleType" : "REPORTSMANAGER",
        "items" : [ {
          "name" : "headlamp_database_host",
          "value" : "ip-172-31-6-7.ec2.internal"
        }, {
          "name" : "headlamp_database_name",
          "value" : "RptDB"
        }, {
          "name" : "headlamp_database_password",
          "value" : "Gmcc1234"
        }, {
          "name" : "headlamp_database_user",
          "value" : "root"
        }, {
          "name" : "headlamp_heapsize",
          "value" : "612368384"
        } ]
      }, {
        "roleType" : "SERVICEMONITOR",
        "items" : [ {
          "name" : "firehose_heapsize",
          "value" : "612368384"
        }, {
          "name" : "firehose_non_java_memory_bytes",
          "value" : "805306368"
        } ]
      } ],
      "items" : [ ]
    },
    "roles" : [ {
      "name" : "mgmt-ALERTPUBLISHER-013cccf53a0238e142c7bec4fce0d01b",
      "type" : "ALERTPUBLISHER",
      "hostRef" : {
        "hostId" : "f3e9f4aa-9549-4226-b9c5-353c03a9f593"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "9e47v0m9hny6hk7r1yzzrujy6"
        } ]
      }
    }, {
      "name" : "mgmt-EVENTSERVER-013cccf53a0238e142c7bec4fce0d01b",
      "type" : "EVENTSERVER",
      "hostRef" : {
        "hostId" : "f3e9f4aa-9549-4226-b9c5-353c03a9f593"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "73rsyh6c9jzk5cnkgbixfppv"
        } ]
      }
    }, {
      "name" : "mgmt-HOSTMONITOR-013cccf53a0238e142c7bec4fce0d01b",
      "type" : "HOSTMONITOR",
      "hostRef" : {
        "hostId" : "f3e9f4aa-9549-4226-b9c5-353c03a9f593"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "f42ysdrl9m5892zgdl6q4iwrk"
        } ]
      }
    }, {
      "name" : "mgmt-REPORTSMANAGER-013cccf53a0238e142c7bec4fce0d01b",
      "type" : "REPORTSMANAGER",
      "hostRef" : {
        "hostId" : "f3e9f4aa-9549-4226-b9c5-353c03a9f593"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "zntgu3hgf1hfh2qfeuf1qr3t"
        } ]
      }
    }, {
      "name" : "mgmt-SERVICEMONITOR-013cccf53a0238e142c7bec4fce0d01b",
      "type" : "SERVICEMONITOR",
      "hostRef" : {
        "hostId" : "f3e9f4aa-9549-4226-b9c5-353c03a9f593"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "dqfy8owvxiwwkn3xcynmw9eri"
        } ]
      }
    } ],
    "displayName" : "Cloudera Management Service"
  },
  "managerSettings" : {
    "items" : [ {
      "name" : "CLUSTER_STATS_START",
      "value" : "10/26/2012 20:20"
    }, {
      "name" : "PUBLIC_CLOUD_STATUS",
      "value" : "ON_PUBLIC_CLOUD"
    }, {
      "name" : "REMOTE_PARCEL_REPO_URLS",
      "value" : "https://archive.cloudera.com/cdh5/parcels/{latest_supported}/,https://archive.cloudera.com/cdh4/parcels/latest/,https://archive.cloudera.com/impala/parcels/latest/,https://archive.cloudera.com/search/parcels/latest/,https://archive.cloudera.com/accumulo/parcels/1.4/,https://archive.cloudera.com/accumulo-c5/parcels/latest/,https://archive.cloudera.com/kafka/parcels/latest/,https://archive.cloudera.com/navigator-keytrustee5/parcels/latest/,https://archive.cloudera.com/spark/parcels/latest/,https://archive.cloudera.com/sqoop-connectors/parcels/latest/"
    } ]
  }
}
```
