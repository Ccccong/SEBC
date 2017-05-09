# 1.Choose a partner in class
```
	Due to the use of internal hostname in my cluster, the nodes can't connect to other cluster, so I copy the file to local cluster instead of remote cluster.
```	
# 2.Name a source directory after your GitHub handle
```
su - hdfs
hdfs dfs -mkdir /labs
hdfs dfs -mkdir /labs/gang1998
```
# 3.Name a target directory after your partner's GitHub handle
	Use /labs/dest as target directory as this will copy to local cluster for testing.
```
hdfs dfs -mkdir /labs/dest

[hdfs@ip-172-31-6-7 ~]$ hdfs dfs -ls /labs
Found 2 items
drwxr-xr-x   - hdfs supergroup          0 2017-05-09 17:01 /labs/dest
drwxr-xr-x   - hdfs supergroup          0 2017-05-09 17:01 /labs/gang1998
```

# 4.Use teragen to create a 500 MB file
```
[hdfs@ip-172-31-6-7 ~]$ hadoop jar /opt/cloudera/parcels/CDH/jars/hadoop-examples.jar teragen -Dmapred.map.tasks=4 5242880 /labs/gang1998/teragen500MB  
17/05/09 17:05:27 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-11-232.ec2.internal/172.31.11.232:8032
17/05/09 17:05:28 INFO terasort.TeraSort: Generating 5242880 using 4
17/05/09 17:05:28 INFO mapreduce.JobSubmitter: number of splits:4
17/05/09 17:05:28 INFO Configuration.deprecation: mapred.map.tasks is deprecated. Instead, use mapreduce.job.maps
17/05/09 17:05:28 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1494346839702_0001
17/05/09 17:05:29 INFO impl.YarnClientImpl: Submitted application application_1494346839702_0001
17/05/09 17:05:29 INFO mapreduce.Job: The url to track the job: http://ip-172-31-11-232.ec2.internal:8088/proxy/application_1494346839702_0001/
17/05/09 17:05:29 INFO mapreduce.Job: Running job: job_1494346839702_0001
17/05/09 17:05:36 INFO mapreduce.Job: Job job_1494346839702_0001 running in uber mode : false
17/05/09 17:05:36 INFO mapreduce.Job:  map 0% reduce 0%
17/05/09 17:05:47 INFO mapreduce.Job:  map 25% reduce 0%
17/05/09 17:05:48 INFO mapreduce.Job:  map 100% reduce 0%
17/05/09 17:05:49 INFO mapreduce.Job: Job job_1494346839702_0001 completed successfully
17/05/09 17:05:50 INFO mapreduce.Job: Counters: 31
        File System Counters
                FILE: Number of bytes read=0
                FILE: Number of bytes written=493152
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=337
                HDFS: Number of bytes written=524288000
                HDFS: Number of read operations=16
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=8
        Job Counters 
                Launched map tasks=4
                Other local map tasks=4
                Total time spent by all maps in occupied slots (ms)=37884
                Total time spent by all reduces in occupied slots (ms)=0
                Total time spent by all map tasks (ms)=37884
                Total vcore-seconds taken by all map tasks=37884
                Total megabyte-seconds taken by all map tasks=38793216
        Map-Reduce Framework
                Map input records=5242880
                Map output records=5242880
                Input split bytes=337
                Spilled Records=0
                Failed Shuffles=0
                Merged Map outputs=0
                GC time elapsed (ms)=492
                CPU time spent (ms)=21580
                Physical memory (bytes) snapshot=1446354944
                Virtual memory (bytes) snapshot=6265413632
                Total committed heap usage (bytes)=1691877376
        org.apache.hadoop.examples.terasort.TeraGen$Counters
                CHECKSUM=11257830824958050
        File Input Format Counters 
                Bytes Read=0
        File Output Format Counters 
                Bytes Written=524288000
```
```
[hdfs@ip-172-31-6-7 ~]$ hdfs dfs -ls /labs/gang1998/teragen500MB
Found 5 items
-rw-r--r--   3 hdfs supergroup          0 2017-05-09 17:05 /labs/gang1998/teragen500MB/_SUCCESS
-rw-r--r--   3 hdfs supergroup  131072000 2017-05-09 17:05 /labs/gang1998/teragen500MB/part-m-00000
-rw-r--r--   3 hdfs supergroup  131072000 2017-05-09 17:05 /labs/gang1998/teragen500MB/part-m-00001
-rw-r--r--   3 hdfs supergroup  131072000 2017-05-09 17:05 /labs/gang1998/teragen500MB/part-m-00002
-rw-r--r--   3 hdfs supergroup  131072000 2017-05-09 17:05 /labs/gang1998/teragen500MB/part-m-00003

```
# 5.Copy your partner's file to your target directory
	Let one partner use distCp on the command line
```
[hdfs@ip-172-31-6-7 conf]$ hadoop distcp hdfs://ip-172-31-11-232.ec2.internal:8020/labs/gang1998/teragen500MB hdfs://ip-172-31-11-232.ec2.internal:8020/labs/dest/teragen500MB_distcp

17/05/09 17:17:58 INFO tools.DistCp: Input Options: DistCpOptions{atomicCommit=false, syncFolder=false, deleteMissing=false, ignoreFailures=false, overwrite=false, append=false, useDiff=false, useRdiff=false, fromSnapshot=null, toSnapshot=null, skipCRC=false, blocking=true, numListstatusThreads=0, maxMaps=20, mapBandwidth=100, sslConfigurationFile='null', copyStrategy='uniformsize', preserveStatus=[], preserveRawXattrs=false, atomicWorkPath=null, logPath=null, sourceFileListing=null, sourcePaths=[hdfs://ip-172-31-11-232.ec2.internal:8020/labs/gang1998/teragen500MB], targetPath=hdfs://ip-172-31-11-232.ec2.internal:8020/labs/dest/teragen500MB_distcp, targetPathExists=false, filtersFile='null'}
17/05/09 17:17:58 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-11-232.ec2.internal/172.31.11.232:8032
17/05/09 17:17:59 INFO tools.SimpleCopyListing: Paths (files+dirs) cnt = 6; dirCnt = 1
17/05/09 17:17:59 INFO tools.SimpleCopyListing: Build file listing completed.
17/05/09 17:17:59 INFO Configuration.deprecation: io.sort.mb is deprecated. Instead, use mapreduce.task.io.sort.mb
17/05/09 17:17:59 INFO Configuration.deprecation: io.sort.factor is deprecated. Instead, use mapreduce.task.io.sort.factor
17/05/09 17:17:59 INFO tools.DistCp: Number of paths in the copy list: 6
17/05/09 17:17:59 INFO tools.DistCp: Number of paths in the copy list: 6
17/05/09 17:17:59 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-11-232.ec2.internal/172.31.11.232:8032
17/05/09 17:17:59 INFO mapreduce.JobSubmitter: number of splits:5
17/05/09 17:18:00 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1494346839702_0002
17/05/09 17:18:00 INFO impl.YarnClientImpl: Submitted application application_1494346839702_0002
17/05/09 17:18:00 INFO mapreduce.Job: The url to track the job: http://ip-172-31-11-232.ec2.internal:8088/proxy/application_1494346839702_0002/
17/05/09 17:18:00 INFO tools.DistCp: DistCp job-id: job_1494346839702_0002
17/05/09 17:18:00 INFO mapreduce.Job: Running job: job_1494346839702_0002
17/05/09 17:18:06 INFO mapreduce.Job: Job job_1494346839702_0002 running in uber mode : false
17/05/09 17:18:06 INFO mapreduce.Job:  map 0% reduce 0%
17/05/09 17:18:14 INFO mapreduce.Job:  map 20% reduce 0%
17/05/09 17:18:17 INFO mapreduce.Job:  map 40% reduce 0%
17/05/09 17:18:20 INFO mapreduce.Job:  map 60% reduce 0%
17/05/09 17:18:21 INFO mapreduce.Job:  map 100% reduce 0%
17/05/09 17:18:21 INFO mapreduce.Job: Job job_1494346839702_0002 completed successfully
17/05/09 17:18:21 INFO mapreduce.Job: Counters: 33
        File System Counters
                FILE: Number of bytes read=0
                FILE: Number of bytes written=631540
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=524290920
                HDFS: Number of bytes written=524288000
                HDFS: Number of read operations=94
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=21
        Job Counters 
                Launched map tasks=5
                Other local map tasks=5
                Total time spent by all maps in occupied slots (ms)=50514
                Total time spent by all reduces in occupied slots (ms)=0
                Total time spent by all map tasks (ms)=50514
                Total vcore-seconds taken by all map tasks=50514
                Total megabyte-seconds taken by all map tasks=51726336
        Map-Reduce Framework
                Map input records=6
                Map output records=0
                Input split bytes=570
                Spilled Records=0
                Failed Shuffles=0
                Merged Map outputs=0
                GC time elapsed (ms)=530
                CPU time spent (ms)=20050
                Physical memory (bytes) snapshot=1116917760
                Virtual memory (bytes) snapshot=7835168768
                Total committed heap usage (bytes)=1429209088
        File Input Format Counters 
                Bytes Read=2350
        File Output Format Counters 
                Bytes Written=0
        org.apache.hadoop.tools.mapred.CopyMapper$Counter
                BYTESCOPIED=524288000
                BYTESEXPECTED=524288000
                COPY=6
```	
	Let the other use BDR
	Schedule backup schedule to replicate.
```
[hdfs@ip-172-31-6-7 conf]$ hdfs dfs -ls /labs/BDR
Found 1 items
drwxr-xr-x   - hdfs supergroup          0 2017-05-09 17:22 /labs/BDR/gang1998
[hdfs@ip-172-31-6-7 conf]$ hdfs dfs -ls /labs/BDR/gang1998
Found 1 items
drwxr-xr-x   - hdfs supergroup          0 2017-05-09 17:22 /labs/BDR/gang1998/teragen500MB
```

# 6.Browse the results
	Use hdfs fsck <path> -files -blocks on your source and target directories
Source:	
```
[hdfs@ip-172-31-6-7 conf]$ hdfs fsck /labs/gang1998 -files -blocks 
Connecting to namenode via http://ip-172-31-11-232.ec2.internal:50070
FSCK started by hdfs (auth:SIMPLE) from /172.31.6.7 for path /labs/gang1998 at Tue May 09 17:26:59 UTC 2017
/labs/gang1998 <dir>
/labs/gang1998/teragen500MB <dir>
/labs/gang1998/teragen500MB/_SUCCESS 0 bytes, 0 block(s):  OK

/labs/gang1998/teragen500MB/part-m-00000 131072000 bytes, 1 block(s):  OK
0. BP-1120856374-172.31.11.232-1494333329973:blk_1073742794_1970 len=131072000 Live_repl=3

/labs/gang1998/teragen500MB/part-m-00001 131072000 bytes, 1 block(s):  OK
0. BP-1120856374-172.31.11.232-1494333329973:blk_1073742793_1969 len=131072000 Live_repl=3

/labs/gang1998/teragen500MB/part-m-00002 131072000 bytes, 1 block(s):  OK
0. BP-1120856374-172.31.11.232-1494333329973:blk_1073742796_1972 len=131072000 Live_repl=3

/labs/gang1998/teragen500MB/part-m-00003 131072000 bytes, 1 block(s):  OK
0. BP-1120856374-172.31.11.232-1494333329973:blk_1073742797_1973 len=131072000 Live_repl=3

Status: HEALTHY
 Total size:    524288000 B
 Total dirs:    2
 Total files:   5
 Total symlinks:                0
 Total blocks (validated):      4 (avg. block size 131072000 B)
 Minimally replicated blocks:   4 (100.0 %)
 Over-replicated blocks:        0 (0.0 %)
 Under-replicated blocks:       0 (0.0 %)
 Mis-replicated blocks:         0 (0.0 %)
 Default replication factor:    3
 Average block replication:     3.0
 Corrupt blocks:                0
 Missing replicas:              0 (0.0 %)
 Number of data-nodes:          4
 Number of racks:               1
FSCK ended at Tue May 09 17:26:59 UTC 2017 in 4 milliseconds


The filesystem under path '/labs/gang1998' is HEALTHY
```
Target of distcp:
```
[hdfs@ip-172-31-6-7 conf]$ hdfs fsck /labs/dest -files -blocks 
Connecting to namenode via http://ip-172-31-11-232.ec2.internal:50070
FSCK started by hdfs (auth:SIMPLE) from /172.31.6.7 for path /labs/dest at Tue May 09 17:27:03 UTC 2017
/labs/dest <dir>
/labs/dest/teragen500MB_distcp <dir>
/labs/dest/teragen500MB_distcp/_SUCCESS 0 bytes, 0 block(s):  OK

/labs/dest/teragen500MB_distcp/part-m-00000 131072000 bytes, 1 block(s):  OK
0. BP-1120856374-172.31.11.232-1494333329973:blk_1073742825_2001 len=131072000 Live_repl=3

/labs/dest/teragen500MB_distcp/part-m-00001 131072000 bytes, 1 block(s):  OK
0. BP-1120856374-172.31.11.232-1494333329973:blk_1073742829_2005 len=131072000 Live_repl=3

/labs/dest/teragen500MB_distcp/part-m-00002 131072000 bytes, 1 block(s):  OK
0. BP-1120856374-172.31.11.232-1494333329973:blk_1073742828_2004 len=131072000 Live_repl=3

/labs/dest/teragen500MB_distcp/part-m-00003 131072000 bytes, 1 block(s):  OK
0. BP-1120856374-172.31.11.232-1494333329973:blk_1073742827_2003 len=131072000 Live_repl=3

Status: HEALTHY
 Total size:    524288000 B
 Total dirs:    2
 Total files:   5
 Total symlinks:                0
 Total blocks (validated):      4 (avg. block size 131072000 B)
 Minimally replicated blocks:   4 (100.0 %)
 Over-replicated blocks:        0 (0.0 %)
 Under-replicated blocks:       0 (0.0 %)
 Mis-replicated blocks:         0 (0.0 %)
 Default replication factor:    3
 Average block replication:     3.0
 Corrupt blocks:                0
 Missing replicas:              0 (0.0 %)
 Number of data-nodes:          4
 Number of racks:               1
FSCK ended at Tue May 09 17:27:03 UTC 2017 in 2 milliseconds


The filesystem under path '/labs/dest' is HEALTHY
```
Target of BDR:
```
[hdfs@ip-172-31-6-7 conf]$ hdfs fsck /labs/BDR -files -blocks 
Connecting to namenode via http://ip-172-31-11-232.ec2.internal:50070
FSCK started by hdfs (auth:SIMPLE) from /172.31.6.7 for path /labs/BDR at Tue May 09 17:27:09 UTC 2017
/labs/BDR <dir>
/labs/BDR/gang1998 <dir>
/labs/BDR/gang1998/teragen500MB <dir>
/labs/BDR/gang1998/teragen500MB/_SUCCESS 0 bytes, 0 block(s):  OK

/labs/BDR/gang1998/teragen500MB/part-m-00000 131072000 bytes, 1 block(s):  OK
0. BP-1120856374-172.31.11.232-1494333329973:blk_1073742856_2032 len=131072000 Live_repl=3

/labs/BDR/gang1998/teragen500MB/part-m-00001 131072000 bytes, 1 block(s):  OK
0. BP-1120856374-172.31.11.232-1494333329973:blk_1073742857_2033 len=131072000 Live_repl=3

/labs/BDR/gang1998/teragen500MB/part-m-00002 131072000 bytes, 1 block(s):  OK
0. BP-1120856374-172.31.11.232-1494333329973:blk_1073742855_2031 len=131072000 Live_repl=3

/labs/BDR/gang1998/teragen500MB/part-m-00003 131072000 bytes, 1 block(s):  OK
0. BP-1120856374-172.31.11.232-1494333329973:blk_1073742858_2034 len=131072000 Live_repl=3

Status: HEALTHY
 Total size:    524288000 B
 Total dirs:    3
 Total files:   5
 Total symlinks:                0
 Total blocks (validated):      4 (avg. block size 131072000 B)
 Minimally replicated blocks:   4 (100.0 %)
 Over-replicated blocks:        0 (0.0 %)
 Under-replicated blocks:       0 (0.0 %)
 Mis-replicated blocks:         0 (0.0 %)
 Default replication factor:    3
 Average block replication:     3.0
 Corrupt blocks:                0
 Missing replicas:              0 (0.0 %)
 Number of data-nodes:          4
 Number of racks:               1
FSCK ended at Tue May 09 17:27:09 UTC 2017 in 2 milliseconds


The filesystem under path '/labs/BDR' is HEALTHY

```	
