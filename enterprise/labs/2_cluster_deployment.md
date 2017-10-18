curl -u dboyer-ibm:cloudera "http://ec2-52-212-24-11.eu-west-1.compute.amazonaws.com:7180/api/v12/cm/deployment" > config.json
```

{
  "timestamp" : "2017-10-18T09:35:08.908Z",
  "clusters" : [ {
    "name" : "cluster",
    "displayName" : "dboyer-ibm",
    "version" : "CDH5",
    "fullVersion" : "5.8.3",
    "services" : [ {
      "name" : "hive",
      "type" : "HIVE",
      "config" : {
        "items" : [ {
          "name" : "hive_metastore_database_host",
          "value" : "ip-172-31-42-52.eu-west-1.compute.internal"
        }, {
          "name" : "hive_metastore_database_name",
          "value" : "hive"
        }, {
          "name" : "hive_metastore_database_password",
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
        "name" : "hive-GATEWAY-46191c4a3b9201e78a09201414a94cb7",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "c3c73582-d857-4a12-8e45-8f646f17d3ba"
        },
        "config" : {
          "items" : [ ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hive-GATEWAY-BASE"
        }
      }, {
        "name" : "hive-GATEWAY-50ff51cf01113b52d952b12d54c48c27",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "i-0264fd9f8c75202e0"
        },
        "config" : {
          "items" : [ ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hive-GATEWAY-BASE"
        }
      }, {
        "name" : "hive-GATEWAY-86a3d7df20849e59d2b48456acfcd343",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "6646d6b8-c8bb-4286-ac90-d7321a053a47"
        },
        "config" : {
          "items" : [ ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hive-GATEWAY-BASE"
        }
      }, {
        "name" : "hive-GATEWAY-9e8c893bc6a6a6b6912886a671c11e56",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "a07483a2-5c42-4914-a12c-707ad98ebc86"
        },
        "config" : {
          "items" : [ ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hive-GATEWAY-BASE"
        }
      }, {
        "name" : "hive-GATEWAY-c5b95ddf27a5bacfdac031005a2440d3",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "ba5cf9be-dfe3-4e13-b829-0c97a31e0979"
        },
        "config" : {
          "items" : [ ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hive-GATEWAY-BASE"
        }
      }, {
        "name" : "hive-HIVEMETASTORE-50ff51cf01113b52d952b12d54c48c27",
        "type" : "HIVEMETASTORE",
        "hostRef" : {
          "hostId" : "i-0264fd9f8c75202e0"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "e4736qnn64a8fiarcqih044hs"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hive-HIVEMETASTORE-BASE"
        }
      }, {
        "name" : "hive-HIVESERVER2-50ff51cf01113b52d952b12d54c48c27",
        "type" : "HIVESERVER2",
        "hostRef" : {
          "hostId" : "i-0264fd9f8c75202e0"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "ee6qs64pzkhkmir165til6hfc"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hive-HIVESERVER2-1"
        }
      }, {
        "name" : "hive-HIVESERVER2-86a3d7df20849e59d2b48456acfcd343",
        "type" : "HIVESERVER2",
        "hostRef" : {
          "hostId" : "6646d6b8-c8bb-4286-ac90-d7321a053a47"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "7m23ksbwetyt9p12z2emd2u38"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hive-HIVESERVER2-BASE"
        }
      } ],
      "displayName" : "Hive",
      "roleConfigGroups" : [ {
        "name" : "hive-GATEWAY-BASE",
        "displayName" : "Gateway Default Group",
        "roleType" : "GATEWAY",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hive"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-HIVEMETASTORE-BASE",
        "displayName" : "Hive Metastore Server Default Group",
        "roleType" : "HIVEMETASTORE",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hive"
        },
        "config" : {
          "items" : [ {
            "name" : "hive_metastore_java_heapsize",
            "value" : "789577728"
          } ]
        }
      }, {
        "name" : "hive-HIVESERVER2-1",
        "displayName" : "HiveServer2 Group 1",
        "roleType" : "HIVESERVER2",
        "base" : false,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hive"
        },
        "config" : {
          "items" : [ {
            "name" : "hiveserver2_java_heapsize",
            "value" : "789577728"
          }, {
            "name" : "hiveserver2_spark_driver_memory",
            "value" : "966367641"
          }, {
            "name" : "hiveserver2_spark_executor_cores",
            "value" : "4"
          }, {
            "name" : "hiveserver2_spark_executor_memory",
            "value" : "2246049792"
          }, {
            "name" : "hiveserver2_spark_yarn_driver_memory_overhead",
            "value" : "102"
          }, {
            "name" : "hiveserver2_spark_yarn_executor_memory_overhead",
            "value" : "378"
          } ]
        }
      }, {
        "name" : "hive-HIVESERVER2-BASE",
        "displayName" : "HiveServer2 Default Group",
        "roleType" : "HIVESERVER2",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hive"
        },
        "config" : {
          "items" : [ {
            "name" : "hiveserver2_java_heapsize",
            "value" : "3643801600"
          }, {
            "name" : "hiveserver2_spark_driver_memory",
            "value" : "966367641"
          }, {
            "name" : "hiveserver2_spark_executor_cores",
            "value" : "4"
          }, {
            "name" : "hiveserver2_spark_executor_memory",
            "value" : "2246049792"
          }, {
            "name" : "hiveserver2_spark_yarn_driver_memory_overhead",
            "value" : "102"
          }, {
            "name" : "hiveserver2_spark_yarn_executor_memory_overhead",
            "value" : "378"
          } ]
        }
      }, {
        "name" : "hive-WEBHCAT-BASE",
        "displayName" : "WebHCat Server Default Group",
        "roleType" : "WEBHCAT",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hive"
        },
        "config" : {
          "items" : [ ]
        }
      } ],
      "replicationSchedules" : [ ]
    }, {
      "name" : "zookeeper",
      "type" : "ZOOKEEPER",
      "config" : {
        "items" : [ ]
      },
      "roles" : [ {
        "name" : "zookeeper-SERVER-50ff51cf01113b52d952b12d54c48c27",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "i-0264fd9f8c75202e0"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "8fj0i24etxfjwgsxdnau7yv8t"
          }, {
            "name" : "serverId",
            "value" : "3"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "zookeeper-SERVER-BASE"
        }
      }, {
        "name" : "zookeeper-SERVER-86a3d7df20849e59d2b48456acfcd343",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "6646d6b8-c8bb-4286-ac90-d7321a053a47"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "9mmo9glwednkcxekert3679zf"
          }, {
            "name" : "serverId",
            "value" : "2"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "zookeeper-SERVER-BASE"
        }
      }, {
        "name" : "zookeeper-SERVER-9e8c893bc6a6a6b6912886a671c11e56",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "a07483a2-5c42-4914-a12c-707ad98ebc86"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "50d0ehbdpncvsmbm20p94d8j5"
          }, {
            "name" : "serverId",
            "value" : "1"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "zookeeper-SERVER-BASE"
        }
      } ],
      "displayName" : "ZooKeeper",
      "roleConfigGroups" : [ {
        "name" : "zookeeper-SERVER-BASE",
        "displayName" : "Server Default Group",
        "roleType" : "SERVER",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "zookeeper"
        },
        "config" : {
          "items" : [ {
            "name" : "dataDir",
            "value" : "/data1/zookeeper"
          }, {
            "name" : "dataLogDir",
            "value" : "/data1/zookeeper"
          }, {
            "name" : "zookeeper_server_java_heapsize",
            "value" : "789577728"
          } ]
        }
      } ]
    }, {
      "name" : "hue",
      "type" : "HUE",
      "config" : {
        "items" : [ {
          "name" : "database_host",
          "value" : "ip-172-31-42-52.eu-west-1.compute.internal"
        }, {
          "name" : "database_password",
          "value" : "hue"
        }, {
          "name" : "database_type",
          "value" : "mysql"
        }, {
          "name" : "hive_service",
          "value" : "hive"
        }, {
          "name" : "hue_webhdfs",
          "value" : "hdfs-HTTPFS-50ff51cf01113b52d952b12d54c48c27"
        }, {
          "name" : "oozie_service",
          "value" : "oozie"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hue-HUE_SERVER-50ff51cf01113b52d952b12d54c48c27",
        "type" : "HUE_SERVER",
        "hostRef" : {
          "hostId" : "i-0264fd9f8c75202e0"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "5yzex1rmxgzlins6ogboatqxd"
          }, {
            "name" : "secret_key",
            "value" : "6qHTRxJjRH9T89iHrcFfgBieoa0mJF"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hue-HUE_SERVER-BASE"
        }
      } ],
      "displayName" : "Hue",
      "roleConfigGroups" : [ {
        "name" : "hue-HUE_LOAD_BALANCER-BASE",
        "displayName" : "Load Balancer Default Group",
        "roleType" : "HUE_LOAD_BALANCER",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hue"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hue-HUE_SERVER-BASE",
        "displayName" : "Hue Server Default Group",
        "roleType" : "HUE_SERVER",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hue"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hue-KT_RENEWER-BASE",
        "displayName" : "Kerberos Ticket Renewer Default Group",
        "roleType" : "KT_RENEWER",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hue"
        },
        "config" : {
          "items" : [ ]
        }
      } ]
    }, {
      "name" : "oozie",
      "type" : "OOZIE",
      "config" : {
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
        "name" : "oozie-OOZIE_SERVER-50ff51cf01113b52d952b12d54c48c27",
        "type" : "OOZIE_SERVER",
        "hostRef" : {
          "hostId" : "i-0264fd9f8c75202e0"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "728e16ez8xgkh8gz7s5hude0x"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "oozie-OOZIE_SERVER-BASE"
        }
      } ],
      "displayName" : "Oozie",
      "roleConfigGroups" : [ {
        "name" : "oozie-OOZIE_SERVER-BASE",
        "displayName" : "Oozie Server Default Group",
        "roleType" : "OOZIE_SERVER",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "oozie"
        },
        "config" : {
          "items" : [ {
            "name" : "oozie_database_host",
            "value" : "ip-172-31-42-52.eu-west-1.compute.internal"
          }, {
            "name" : "oozie_database_password",
            "value" : "oozie"
          }, {
            "name" : "oozie_database_type",
            "value" : "mysql"
          }, {
            "name" : "oozie_database_user",
            "value" : "oozie"
          }, {
            "name" : "oozie_java_heapsize",
            "value" : "789577728"
          } ]
        }
      } ]
    }, {
      "name" : "yarn",
      "type" : "YARN",
      "config" : {
        "items" : [ {
          "name" : "hdfs_service",
          "value" : "hdfs"
        }, {
          "name" : "rm_dirty",
          "value" : "false"
        }, {
          "name" : "rm_last_allocation_percentage",
          "value" : "90"
        }, {
          "name" : "yarn_service_cgroups",
          "value" : "false"
        }, {
          "name" : "yarn_service_lce_always",
          "value" : "false"
        }, {
          "name" : "zk_authorization_secret_key",
          "value" : "ns8LG6iYTY7yxPkjXrPrlDCdQQdgOC"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "yarn-JOBHISTORY-9e8c893bc6a6a6b6912886a671c11e56",
        "type" : "JOBHISTORY",
        "hostRef" : {
          "hostId" : "a07483a2-5c42-4914-a12c-707ad98ebc86"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "alokl3hfkzm7tfi6q0e8du5p1"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "yarn-JOBHISTORY-BASE"
        }
      }, {
        "name" : "yarn-NODEMANAGER-46191c4a3b9201e78a09201414a94cb7",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "c3c73582-d857-4a12-8e45-8f646f17d3ba"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "av0zho9xdwlm85qh2r2eg1zdz"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "yarn-NODEMANAGER-BASE"
        }
      }, {
        "name" : "yarn-NODEMANAGER-9e8c893bc6a6a6b6912886a671c11e56",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "a07483a2-5c42-4914-a12c-707ad98ebc86"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "7t6vk1zoq53d4w53g63upgzl6"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "yarn-NODEMANAGER-1"
        }
      }, {
        "name" : "yarn-NODEMANAGER-c5b95ddf27a5bacfdac031005a2440d3",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "ba5cf9be-dfe3-4e13-b829-0c97a31e0979"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "6mix5ltgy5fd5xx8l7fuinzxh"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "yarn-NODEMANAGER-BASE"
        }
      }, {
        "name" : "yarn-RESOURCEMANAGER-9e8c893bc6a6a6b6912886a671c11e56",
        "type" : "RESOURCEMANAGER",
        "hostRef" : {
          "hostId" : "a07483a2-5c42-4914-a12c-707ad98ebc86"
        },
        "config" : {
          "items" : [ {
            "name" : "rm_id",
            "value" : "83"
          }, {
            "name" : "role_jceks_password",
            "value" : "1abe9lqbgqsxnja7g2zxr09q0"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "yarn-RESOURCEMANAGER-BASE"
        }
      } ],
      "displayName" : "YARN (MR2 Included)",
      "roleConfigGroups" : [ {
        "name" : "yarn-GATEWAY-BASE",
        "displayName" : "Gateway Default Group",
        "roleType" : "GATEWAY",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "yarn"
        },
        "config" : {
          "items" : [ {
            "name" : "mapred_reduce_tasks",
            "value" : "6"
          }, {
            "name" : "mapred_submit_replication",
            "value" : "1"
          } ]
        }
      }, {
        "name" : "yarn-JOBHISTORY-BASE",
        "displayName" : "JobHistory Server Default Group",
        "roleType" : "JOBHISTORY",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "yarn"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-1",
        "displayName" : "NodeManager Group 1",
        "roleType" : "NODEMANAGER",
        "base" : false,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "yarn"
        },
        "config" : {
          "items" : [ {
            "name" : "yarn_nodemanager_heartbeat_interval_ms",
            "value" : "100"
          }, {
            "name" : "yarn_nodemanager_local_dirs",
            "value" : "/data1/yarn/nm"
          }, {
            "name" : "yarn_nodemanager_log_dirs",
            "value" : "/data1/yarn/container-logs"
          }, {
            "name" : "yarn_nodemanager_resource_cpu_vcores",
            "value" : "4"
          }, {
            "name" : "yarn_nodemanager_resource_memory_mb",
            "value" : "1024"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-BASE",
        "displayName" : "NodeManager Default Group",
        "roleType" : "NODEMANAGER",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "yarn"
        },
        "config" : {
          "items" : [ {
            "name" : "rm_cpu_shares",
            "value" : "1800"
          }, {
            "name" : "rm_io_weight",
            "value" : "900"
          }, {
            "name" : "yarn_nodemanager_heartbeat_interval_ms",
            "value" : "100"
          }, {
            "name" : "yarn_nodemanager_local_dirs",
            "value" : "/data1/yarn/nm"
          }, {
            "name" : "yarn_nodemanager_log_dirs",
            "value" : "/data1/yarn/container-logs"
          }, {
            "name" : "yarn_nodemanager_resource_cpu_vcores",
            "value" : "3"
          }, {
            "name" : "yarn_nodemanager_resource_memory_mb",
            "value" : "4939"
          } ]
        }
      }, {
        "name" : "yarn-RESOURCEMANAGER-BASE",
        "displayName" : "ResourceManager Default Group",
        "roleType" : "RESOURCEMANAGER",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "yarn"
        },
        "config" : {
          "items" : [ {
            "name" : "yarn_scheduler_maximum_allocation_mb",
            "value" : "4939"
          }, {
            "name" : "yarn_scheduler_maximum_allocation_vcores",
            "value" : "3"
          } ]
        }
      } ]
    }, {
      "name" : "hdfs",
      "type" : "HDFS",
      "config" : {
        "items" : [ {
          "name" : "dfs_ha_fencing_cloudera_manager_secret_key",
          "value" : "AURFUFvPa23fT4fz1TPY6XS53ZBiLE"
        }, {
          "name" : "dfs_ha_fencing_methods",
          "value" : "shell(true)"
        }, {
          "name" : "fc_authorization_secret_key",
          "value" : "yE9QWx2s5FSu7TwejDvuuLl0enQs55"
        }, {
          "name" : "http_auth_signature_secret",
          "value" : "ARZ5ufsjFyI9DVDvelbCUgh3qUBS9A"
        }, {
          "name" : "rm_dirty",
          "value" : "false"
        }, {
          "name" : "rm_last_allocation_percentage",
          "value" : "10"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hdfs-BALANCER-86a3d7df20849e59d2b48456acfcd343",
        "type" : "BALANCER",
        "hostRef" : {
          "hostId" : "6646d6b8-c8bb-4286-ac90-d7321a053a47"
        },
        "config" : {
          "items" : [ ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hdfs-BALANCER-BASE"
        }
      }, {
        "name" : "hdfs-DATANODE-46191c4a3b9201e78a09201414a94cb7",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "c3c73582-d857-4a12-8e45-8f646f17d3ba"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "esykd5i694nw2e39tpojvmg2b"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hdfs-DATANODE-BASE"
        }
      }, {
        "name" : "hdfs-DATANODE-9e8c893bc6a6a6b6912886a671c11e56",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "a07483a2-5c42-4914-a12c-707ad98ebc86"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "czj8m1qiau98xg8ykelx9zgbt"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hdfs-DATANODE-1"
        }
      }, {
        "name" : "hdfs-DATANODE-c5b95ddf27a5bacfdac031005a2440d3",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "ba5cf9be-dfe3-4e13-b829-0c97a31e0979"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "7pr694dm10bwtyvy16e1o5dti"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hdfs-DATANODE-BASE"
        }
      }, {
        "name" : "hdfs-FAILOVERCONTROLLER-50ff51cf01113b52d952b12d54c48c27",
        "type" : "FAILOVERCONTROLLER",
        "hostRef" : {
          "hostId" : "i-0264fd9f8c75202e0"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "8byuuzbwotialb5zd0f8r2fvd"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hdfs-FAILOVERCONTROLLER-BASE"
        }
      }, {
        "name" : "hdfs-FAILOVERCONTROLLER-86a3d7df20849e59d2b48456acfcd343",
        "type" : "FAILOVERCONTROLLER",
        "hostRef" : {
          "hostId" : "6646d6b8-c8bb-4286-ac90-d7321a053a47"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "8dp8jl303kh9flmcedur7hpjm"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hdfs-FAILOVERCONTROLLER-BASE"
        }
      }, {
        "name" : "hdfs-GATEWAY-46191c4a3b9201e78a09201414a94cb7",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "c3c73582-d857-4a12-8e45-8f646f17d3ba"
        },
        "config" : {
          "items" : [ ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hdfs-GATEWAY-BASE"
        }
      }, {
        "name" : "hdfs-GATEWAY-50ff51cf01113b52d952b12d54c48c27",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "i-0264fd9f8c75202e0"
        },
        "config" : {
          "items" : [ ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hdfs-GATEWAY-BASE"
        }
      }, {
        "name" : "hdfs-GATEWAY-86a3d7df20849e59d2b48456acfcd343",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "6646d6b8-c8bb-4286-ac90-d7321a053a47"
        },
        "config" : {
          "items" : [ ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hdfs-GATEWAY-BASE"
        }
      }, {
        "name" : "hdfs-GATEWAY-9e8c893bc6a6a6b6912886a671c11e56",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "a07483a2-5c42-4914-a12c-707ad98ebc86"
        },
        "config" : {
          "items" : [ ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hdfs-GATEWAY-BASE"
        }
      }, {
        "name" : "hdfs-GATEWAY-c5b95ddf27a5bacfdac031005a2440d3",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "ba5cf9be-dfe3-4e13-b829-0c97a31e0979"
        },
        "config" : {
          "items" : [ ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hdfs-GATEWAY-BASE"
        }
      }, {
        "name" : "hdfs-HTTPFS-50ff51cf01113b52d952b12d54c48c27",
        "type" : "HTTPFS",
        "hostRef" : {
          "hostId" : "i-0264fd9f8c75202e0"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "ek1imobb9u7hvm2e4lohg06kv"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hdfs-HTTPFS-BASE"
        }
      }, {
        "name" : "hdfs-JOURNALNODE-50ff51cf01113b52d952b12d54c48c27",
        "type" : "JOURNALNODE",
        "hostRef" : {
          "hostId" : "i-0264fd9f8c75202e0"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "d5egbcof0pm65qqlut51h9vsx"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hdfs-JOURNALNODE-BASE"
        }
      }, {
        "name" : "hdfs-JOURNALNODE-86a3d7df20849e59d2b48456acfcd343",
        "type" : "JOURNALNODE",
        "hostRef" : {
          "hostId" : "6646d6b8-c8bb-4286-ac90-d7321a053a47"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "az1sca1qi6frms1zul7yqzkk7"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hdfs-JOURNALNODE-BASE"
        }
      }, {
        "name" : "hdfs-JOURNALNODE-9e8c893bc6a6a6b6912886a671c11e56",
        "type" : "JOURNALNODE",
        "hostRef" : {
          "hostId" : "a07483a2-5c42-4914-a12c-707ad98ebc86"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "68ltu4ssajj9utultadmru3uw"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hdfs-JOURNALNODE-BASE"
        }
      }, {
        "name" : "hdfs-NAMENODE-50ff51cf01113b52d952b12d54c48c27",
        "type" : "NAMENODE",
        "hostRef" : {
          "hostId" : "i-0264fd9f8c75202e0"
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
            "value" : "86"
          }, {
            "name" : "role_jceks_password",
            "value" : "wr1yixflsg6nwzlwwxqlojk6"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hdfs-NAMENODE-BASE"
        }
      }, {
        "name" : "hdfs-NAMENODE-86a3d7df20849e59d2b48456acfcd343",
        "type" : "NAMENODE",
        "hostRef" : {
          "hostId" : "6646d6b8-c8bb-4286-ac90-d7321a053a47"
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
            "value" : "96"
          }, {
            "name" : "role_jceks_password",
            "value" : "ailm8go9ec9wl8whxbo0mqain"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hdfs-NAMENODE-BASE"
        }
      } ],
      "displayName" : "HDFS",
      "roleConfigGroups" : [ {
        "name" : "hdfs-BALANCER-BASE",
        "displayName" : "Balancer Default Group",
        "roleType" : "BALANCER",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hdfs"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hdfs-DATANODE-1",
        "displayName" : "DataNode Group 1",
        "roleType" : "DATANODE",
        "base" : false,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hdfs"
        },
        "config" : {
          "items" : [ {
            "name" : "dfs_data_dir_list",
            "value" : "/data1/dfs/dn"
          }, {
            "name" : "dfs_datanode_du_reserved",
            "value" : "4292765696"
          }, {
            "name" : "dfs_datanode_max_locked_memory",
            "value" : "4294967296"
          } ]
        }
      }, {
        "name" : "hdfs-DATANODE-BASE",
        "displayName" : "DataNode Default Group",
        "roleType" : "DATANODE",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hdfs"
        },
        "config" : {
          "items" : [ {
            "name" : "datanode_java_heapsize",
            "value" : "1073741824"
          }, {
            "name" : "dfs_data_dir_list",
            "value" : "/data1/dfs/dn"
          }, {
            "name" : "dfs_datanode_du_reserved",
            "value" : "4292765696"
          }, {
            "name" : "dfs_datanode_max_locked_memory",
            "value" : "4294967296"
          }, {
            "name" : "rm_cpu_shares",
            "value" : "200"
          }, {
            "name" : "rm_io_weight",
            "value" : "100"
          } ]
        }
      }, {
        "name" : "hdfs-FAILOVERCONTROLLER-BASE",
        "displayName" : "Failover Controller Default Group",
        "roleType" : "FAILOVERCONTROLLER",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hdfs"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hdfs-GATEWAY-BASE",
        "displayName" : "Gateway Default Group",
        "roleType" : "GATEWAY",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hdfs"
        },
        "config" : {
          "items" : [ {
            "name" : "dfs_client_use_trash",
            "value" : "true"
          } ]
        }
      }, {
        "name" : "hdfs-HTTPFS-BASE",
        "displayName" : "HttpFS Default Group",
        "roleType" : "HTTPFS",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hdfs"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hdfs-JOURNALNODE-BASE",
        "displayName" : "JournalNode Default Group",
        "roleType" : "JOURNALNODE",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hdfs"
        },
        "config" : {
          "items" : [ {
            "name" : "dfs_journalnode_edits_dir",
            "value" : "/data1/dfs/jn"
          }, {
            "name" : "journalnode_fsync_latency_thresholds",
            "value" : "{\"warning\":1200,\"critical\":3000}"
          } ]
        }
      }, {
        "name" : "hdfs-NAMENODE-BASE",
        "displayName" : "NameNode Default Group",
        "roleType" : "NAMENODE",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hdfs"
        },
        "config" : {
          "items" : [ {
            "name" : "dfs_name_dir_list",
            "value" : "/data1/dfs/nn"
          }, {
            "name" : "dfs_namenode_servicerpc_address",
            "value" : "8022"
          } ]
        }
      }, {
        "name" : "hdfs-NFSGATEWAY-BASE",
        "displayName" : "NFS Gateway Default Group",
        "roleType" : "NFSGATEWAY",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hdfs"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hdfs-SECONDARYNAMENODE-BASE",
        "displayName" : "SecondaryNameNode Default Group",
        "roleType" : "SECONDARYNAMENODE",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hdfs"
        },
        "config" : {
          "items" : [ {
            "name" : "fs_checkpoint_dir_list",
            "value" : "/data1/dfs/snn"
          } ]
        }
      } ],
      "replicationSchedules" : [ ],
      "snapshotPolicies" : [ ]
    } ],
    "parcels" : [ {
      "product" : "CDH",
      "version" : "5.8.3-1.cdh5.8.3.p0.2",
      "stage" : "DISTRIBUTED",
      "clusterRef" : {
        "clusterName" : "cluster"
      }
    }, {
      "product" : "CDH",
      "version" : "5.8.3-1.cdh5.8.3.p0.2",
      "stage" : "ACTIVATED",
      "clusterRef" : {
        "clusterName" : "cluster"
      }
    } ]
  } ],
  "hosts" : [ {
    "hostId" : "a07483a2-5c42-4914-a12c-707ad98ebc86",
    "ipAddress" : "172.31.34.71",
    "hostname" : "ip-172-31-34-71.eu-west-1.compute.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ {
        "name" : "memory_overcommit_threshold",
        "value" : "0.9"
      } ]
    }
  }, {
    "hostId" : "6646d6b8-c8bb-4286-ac90-d7321a053a47",
    "ipAddress" : "172.31.39.197",
    "hostname" : "ip-172-31-39-197.eu-west-1.compute.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ {
        "name" : "memory_overcommit_threshold",
        "value" : "0.99"
      } ]
    }
  }, {
    "hostId" : "i-0264fd9f8c75202e0",
    "ipAddress" : "172.31.42.52",
    "hostname" : "ip-172-31-42-52.eu-west-1.compute.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ {
        "name" : "host_config_suppression_memory_overcommitted_validator",
        "value" : "true"
      } ]
    }
  }, {
    "hostId" : "ba5cf9be-dfe3-4e13-b829-0c97a31e0979",
    "ipAddress" : "172.31.43.28",
    "hostname" : "ip-172-31-43-28.eu-west-1.compute.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "c3c73582-d857-4a12-8e45-8f646f17d3ba",
    "ipAddress" : "172.31.45.199",
    "hostname" : "ip-172-31-45-199.eu-west-1.compute.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  } ],
  "users" : [ {
    "name" : "__cloudera_internal_user__a2852ff7-5c8a-446d-9f1a-ca6dd87ff0d0",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "47eb9e0db80b0f3e92ae4f4f7e8fcff0a27452b7e1c68658c9a730765c2f4250",
    "pwSalt" : 1721520031204075590,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-EVENTSERVER-50ff51cf01113b52d952b12d54c48c27",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "b8ffc0740396a2d4a4da4784f7c46405b61a649f9b6b603162dc5b16607117e9",
    "pwSalt" : 6804630686372551109,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-HOSTMONITOR-50ff51cf01113b52d952b12d54c48c27",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "bd3e103f76b4c05c8f7d730994a39cfca429f378351ee682f4a304b5e82d337e",
    "pwSalt" : 7957377678986640712,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-REPORTSMANAGER-50ff51cf01113b52d952b12d54c48c27",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "ca52d8fb2c53b0637baff9115491c529d204ea6337b95d0a54608f3c6d51403d",
    "pwSalt" : 8953722570460257770,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-SERVICEMONITOR-50ff51cf01113b52d952b12d54c48c27",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "bac4ad362cea603e14c681c3ef4e121f20139c4b1f1422694a4a1b373fb49617",
    "pwSalt" : 5231371847541156039,
    "pwLogin" : true
  }, {
    "name" : "admin",
    "roles" : [ "ROLE_LIMITED" ],
    "pwHash" : "d89322bd90493e62349858d769efa1efb5be958d912212702d50e75891782973",
    "pwSalt" : -5790095450987018719,
    "pwLogin" : true
  }, {
    "name" : "dboyer-ibm",
    "roles" : [ "ROLE_ADMIN" ],
    "pwHash" : "6bc99e7993feabeac44c33191aebd781102bafe267468af9d6eb87cae32bb34e",
    "pwSalt" : -8957258987126021437,
    "pwLogin" : true
  }, {
    "name" : "minotaur",
    "roles" : [ "ROLE_CONFIGURATOR" ],
    "pwHash" : "b741a5ab009aca8ae27168634f0bd46c554dd19856fc5d9ede7cd114b4d23cd4",
    "pwSalt" : 5941404765081375896,
    "pwLogin" : true
  } ],
  "versionInfo" : {
    "version" : "5.8.3",
    "buildUser" : "jenkins",
    "buildTimestamp" : "20161019-1013",
    "gitHash" : "518f0d6d44abc87bc392646e4369a20c8192b7cf",
    "snapshot" : false
  },
  "managementService" : {
    "name" : "mgmt",
    "type" : "MGMT",
    "config" : {
      "items" : [ ]
    },
    "roles" : [ {
      "name" : "mgmt-ALERTPUBLISHER-50ff51cf01113b52d952b12d54c48c27",
      "type" : "ALERTPUBLISHER",
      "hostRef" : {
        "hostId" : "i-0264fd9f8c75202e0"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "ahmyizw0ekzsdkzyrxg9nnrmy"
        } ]
      },
      "roleConfigGroupRef" : {
        "roleConfigGroupName" : "mgmt-ALERTPUBLISHER-BASE"
      }
    }, {
      "name" : "mgmt-EVENTSERVER-50ff51cf01113b52d952b12d54c48c27",
      "type" : "EVENTSERVER",
      "hostRef" : {
        "hostId" : "i-0264fd9f8c75202e0"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "75s47pgc9l8tgtjin05anmpyp"
        } ]
      },
      "roleConfigGroupRef" : {
        "roleConfigGroupName" : "mgmt-EVENTSERVER-BASE"
      }
    }, {
      "name" : "mgmt-HOSTMONITOR-50ff51cf01113b52d952b12d54c48c27",
      "type" : "HOSTMONITOR",
      "hostRef" : {
        "hostId" : "i-0264fd9f8c75202e0"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "edvbsfhs6631byihr5vj3sz34"
        } ]
      },
      "roleConfigGroupRef" : {
        "roleConfigGroupName" : "mgmt-HOSTMONITOR-BASE"
      }
    }, {
      "name" : "mgmt-REPORTSMANAGER-50ff51cf01113b52d952b12d54c48c27",
      "type" : "REPORTSMANAGER",
      "hostRef" : {
        "hostId" : "i-0264fd9f8c75202e0"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "erm30t95jxle4a0e9kpv17zt6"
        } ]
      },
      "roleConfigGroupRef" : {
        "roleConfigGroupName" : "mgmt-REPORTSMANAGER-BASE"
      }
    }, {
      "name" : "mgmt-SERVICEMONITOR-50ff51cf01113b52d952b12d54c48c27",
      "type" : "SERVICEMONITOR",
      "hostRef" : {
        "hostId" : "i-0264fd9f8c75202e0"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "8f6o23iicvc3f7is6l1hi0c83"
        } ]
      },
      "roleConfigGroupRef" : {
        "roleConfigGroupName" : "mgmt-SERVICEMONITOR-BASE"
      }
    } ],
    "displayName" : "Cloudera Management Service",
    "roleConfigGroups" : [ {
      "name" : "mgmt-ACTIVITYMONITOR-BASE",
      "displayName" : "Activity Monitor Default Group",
      "roleType" : "ACTIVITYMONITOR",
      "base" : true,
      "serviceRef" : {
        "serviceName" : "mgmt"
      },
      "config" : {
        "items" : [ ]
      }
    }, {
      "name" : "mgmt-ALERTPUBLISHER-BASE",
      "displayName" : "Alert Publisher Default Group",
      "roleType" : "ALERTPUBLISHER",
      "base" : true,
      "serviceRef" : {
        "serviceName" : "mgmt"
      },
      "config" : {
        "items" : [ ]
      }
    }, {
      "name" : "mgmt-EVENTSERVER-BASE",
      "displayName" : "Event Server Default Group",
      "roleType" : "EVENTSERVER",
      "base" : true,
      "serviceRef" : {
        "serviceName" : "mgmt"
      },
      "config" : {
        "items" : [ {
          "name" : "event_server_heapsize",
          "value" : "789577728"
        } ]
      }
    }, {
      "name" : "mgmt-HOSTMONITOR-BASE",
      "displayName" : "Host Monitor Default Group",
      "roleType" : "HOSTMONITOR",
      "base" : true,
      "serviceRef" : {
        "serviceName" : "mgmt"
      },
      "config" : {
        "items" : [ {
          "name" : "firehose_non_java_memory_bytes",
          "value" : "1610612736"
        } ]
      }
    }, {
      "name" : "mgmt-NAVIGATOR-BASE",
      "displayName" : "Navigator Audit Server Default Group",
      "roleType" : "NAVIGATOR",
      "base" : true,
      "serviceRef" : {
        "serviceName" : "mgmt"
      },
      "config" : {
        "items" : [ ]
      }
    }, {
      "name" : "mgmt-NAVIGATORMETASERVER-BASE",
      "displayName" : "Navigator Metadata Server Default Group",
      "roleType" : "NAVIGATORMETASERVER",
      "base" : true,
      "serviceRef" : {
        "serviceName" : "mgmt"
      },
      "config" : {
        "items" : [ ]
      }
    }, {
      "name" : "mgmt-REPORTSMANAGER-BASE",
      "displayName" : "Reports Manager Default Group",
      "roleType" : "REPORTSMANAGER",
      "base" : true,
      "serviceRef" : {
        "serviceName" : "mgmt"
      },
      "config" : {
        "items" : [ {
          "name" : "headlamp_database_host",
          "value" : "ip-172-31-42-52.eu-west-1.compute.internal"
        }, {
          "name" : "headlamp_database_name",
          "value" : "rman"
        }, {
          "name" : "headlamp_database_password",
          "value" : "rman"
        }, {
          "name" : "headlamp_database_user",
          "value" : "rman"
        }, {
          "name" : "headlamp_heapsize",
          "value" : "789577728"
        } ]
      }
    }, {
      "name" : "mgmt-SERVICEMONITOR-BASE",
      "displayName" : "Service Monitor Default Group",
      "roleType" : "SERVICEMONITOR",
      "base" : true,
      "serviceRef" : {
        "serviceName" : "mgmt"
      },
      "config" : {
        "items" : [ {
          "name" : "firehose_non_java_memory_bytes",
          "value" : "1610612736"
        } ]
      }
    } ]
  },
  "managerSettings" : {
    "items" : [ {
      "name" : "CLUSTER_STATS_START",
      "value" : "10/23/2012 13:30"
    }, {
      "name" : "PUBLIC_CLOUD_STATUS",
      "value" : "ON_PUBLIC_CLOUD"
    }, {
      "name" : "REMOTE_PARCEL_REPO_URLS",
      "value" : "https://archive.cloudera.com/cdh5/parcels/{latest_supported}/,https://archive.cloudera.com/cdh5/parcels/5.8.3/,https://archive.cloudera.com/cdh4/parcels/latest/,https://archive.cloudera.com/impala/parcels/latest/,https://archive.cloudera.com/search/parcels/latest/,https://archive.cloudera.com/accumulo/parcels/1.4/,https://archive.cloudera.com/accumulo-c5/parcels/latest/,https://archive.cloudera.com/kafka/parcels/latest/,https://archive.cloudera.com/navigator-keytrustee5/parcels/latest/,https://archive.cloudera.com/spark/parcels/latest/,https://archive.cloudera.com/sqoop-connectors/parcels/latest/"
    } ]
  },
  "allHostsConfig" : {
    "items" : [ {
      "name" : "rm_enabled",
      "value" : "true"
    } ]
  },
  "peers" : [ ],
  "hostTemplates" : {
    "items" : [ ]
  }
}
```
