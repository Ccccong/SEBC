# 1. Create a precious directory in HDFS; copy the ZIP course file into it.
```
su - gang1998
hdfs dfs -mkdir precious 
[gang1998@ip-172-31-6-7 ~]$ hadoop fs -copyFromLocal SEBC-Shanghai.zip /user/gang1998/precious/SEBC-Shanghai.zip 
```
# 2. Enable snapshots for precious
  
```
[root@ip-172-31-6-7 ~]# su - hdfs
[hdfs@ip-172-31-6-7 ~]$ hdfs dfsadmin -allowSnapshot /user/gang1998/precious
Allowing snaphot on /user/gang1998/precious succeeded
  
```
# 3. Create a snapshot called sebc-hdfs-test
  
```
[hdfs@ip-172-31-6-7 ~]$ hdfs dfs -createSnapshot /user/gang1998/precious sebc-hdfs-test
Created snapshot /user/gang1998/precious/.snapshot/sebc-hdfs-test  
```
# 4. Delete the directory
  
```
[hdfs@ip-172-31-6-7 ~]$ hadoop fs -rm /user/gang1998/precious/SEBC-Shanghai.zip
17/05/09 18:13:23 INFO fs.TrashPolicyDefault: Moved: 'hdfs://ip-172-31-11-232.ec2.internal:8020/user/gang1998/precious/SEBC-Shanghai.zip' to trash at: hdfs://ip-172-31-11-232.ec2.internal:8020/user/hdfs/.Trash/Current/user/gang1998/precious/SEBC-Shanghai.zip  
```

  
# 5. Delete the ZIP file
  
```
[hdfs@ip-172-31-6-7 ~]$ hadoop fs -rm -r /user/gang1998/precious
rm: Failed to move to trash: hdfs://ip-172-31-11-232.ec2.internal:8020/user/gang1998/precious: The directory /user/gang1998/precious cannot be deleted since /user/gang1998/precious is snapshottable and already has snapshots
```
  
# 6. Restore the deleted file
  
```
[hdfs@ip-172-31-6-7 ~]$ hdfs dfs -cp /user/gang1998/precious/.snapshot/sebc-hdfs-test/SEBC-Shanghai.zip /user/gang1998/precious
[hdfs@ip-172-31-6-7 ~]$ hadoop fs -ls /user/gang1998/precious/
Found 1 items
-rw-r--r--   3 hdfs gang1998     474957 2017-05-09 18:15 /user/gang1998/precious/SEBC-Shanghai.zip  
```



