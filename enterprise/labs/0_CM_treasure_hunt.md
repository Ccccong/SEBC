# 1.What is ubertask optimization?
```
Ubertask optimization, which runs "sufficiently small" jobs sequentially within a single JVM. "Small" is defined by the mapreduce.job.ubertask.maxmaps, mapreduce.job.ubertask.maxreduces, and mapreduce.job.ubertask.maxbytes settings
```
# 2.Where in CM is the Kerberos Security Realm value displayed?
```
Administration->Setting->Kerberos->Kerberos Security Realm
```
# 3.Which CDH service(s) host a property for enabling Kerberos authentication?
```
Zookeeper, YARN, HDFS have configuration properties for enabling Kerberos authentication.
```
# 4.How do you upgrade the CM agents?
```
Host->All hosts->Select all hosts. Then run the 'Re-run Upgrade Wizard'.
```
# 5.Give the  tsquery  statement used to chart Hue's CPU utilization?
Get from Hue->Charts Library->'CPU Cores Used' chart
```
SELECT cpu_system_rate + cpu_user_rate WHERE entityName = "hue-HUE_SERVER-013cccf53a0238e142c7bec4fce0d01b" AND category = ROLE
```
# 6.Name all the roles that make up the Hive service
```
HiveServer2, Hive Metastore Server, Gateway, WebHCat Server
```
# 7.What steps must be completed before integrating Cloudera Manager with Kerberos?
```
# Before Enable Kerberos:
1.Set up a working KDC. Cloudera Manager supports authentication with MIT KDC and Active Directory.
2.Configure the KDC to allow renewable tickets with non-zero ticket lifetimes. 
3.If you are using Active Directory, make sure LDAP over TLS/SSL (LDAPS) is enabled for the Domain Controllers.
4.Install the OS-specific packages for your cluster. 
5.Create an account for Cloudera Manager that has the permissions to create other accounts in the KDC.
```
