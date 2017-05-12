# Run the Hadoop  pi  program as the user  chen  
Copy the command and full output to  challenges/labs/5_pi.md 
```
[root@ip-172-31-12-204 ~]# su - chen
[chen@ip-172-31-12-204 ~]$ kinit chen
Password for chen@GANG1998.CN: 
```
```
[chen@ip-172-31-12-204 ~]$ time hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar pi 10 10
```
```Number of Maps  = 10
Samples per Map = 10
Wrote input for Map #0
Wrote input for Map #1
Wrote input for Map #2
Wrote input for Map #3
Wrote input for Map #4
Wrote input for Map #5
Wrote input for Map #6
Wrote input for Map #7
Wrote input for Map #8
Wrote input for Map #9
Starting Job
17/05/12 03:20:05 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-1-9.ec2.internal/172.31.1.9:8032
17/05/12 03:20:05 INFO hdfs.DFSClient: Created token for chen: HDFS_DELEGATION_TOKEN owner=chen@GANG1998.CN, renewer=yarn, realUser=, issueDate=1494559205754, maxDate=1495164005754, sequenceNumber=2, masterKeyId=2 on 172.31.1.9:8020
17/05/12 03:20:05 INFO security.TokenCache: Got dt for hdfs://ip-172-31-1-9.ec2.internal:8020; Kind: HDFS_DELEGATION_TOKEN, Service: 172.31.1.9:8020, Ident: (token for chen: HDFS_DELEGATION_TOKEN owner=chen@GANG1998.CN, renewer=yarn, realUser=, issueDate=1494559205754, maxDate=1495164005754, sequenceNumber=2, masterKeyId=2)
17/05/12 03:20:06 INFO input.FileInputFormat: Total input paths to process : 10
17/05/12 03:20:06 INFO mapreduce.JobSubmitter: number of splits:10
17/05/12 03:20:07 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1494558582875_0002
17/05/12 03:20:07 INFO mapreduce.JobSubmitter: Kind: HDFS_DELEGATION_TOKEN, Service: 172.31.1.9:8020, Ident: (token for chen: HDFS_DELEGATION_TOKEN owner=chen@GANG1998.CN, renewer=yarn, realUser=, issueDate=1494559205754, maxDate=1495164005754, sequenceNumber=2, masterKeyId=2)
17/05/12 03:20:08 INFO impl.YarnClientImpl: Submitted application application_1494558582875_0002
17/05/12 03:20:08 INFO mapreduce.Job: The url to track the job: http://ip-172-31-1-9.ec2.internal:8088/proxy/application_1494558582875_0002/
17/05/12 03:20:08 INFO mapreduce.Job: Running job: job_1494558582875_0002
17/05/12 03:20:25 INFO mapreduce.Job: Job job_1494558582875_0002 running in uber mode : false
17/05/12 03:20:25 INFO mapreduce.Job:  map 0% reduce 0%
17/05/12 03:20:37 INFO mapreduce.Job:  map 10% reduce 0%
17/05/12 03:20:42 INFO mapreduce.Job:  map 40% reduce 0%
17/05/12 03:20:44 INFO mapreduce.Job:  map 50% reduce 0%
17/05/12 03:20:46 INFO mapreduce.Job:  map 60% reduce 0%
17/05/12 03:20:48 INFO mapreduce.Job:  map 70% reduce 0%
17/05/12 03:20:54 INFO mapreduce.Job:  map 80% reduce 0%
17/05/12 03:20:55 INFO mapreduce.Job:  map 100% reduce 0%
17/05/12 03:21:04 INFO mapreduce.Job:  map 100% reduce 100%
17/05/12 03:21:05 INFO mapreduce.Job: Job job_1494558582875_0002 completed successfully
17/05/12 03:21:06 INFO mapreduce.Job: Counters: 49
        File System Counters
                FILE: Number of bytes read=79
                FILE: Number of bytes written=1371678
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=2810
                HDFS: Number of bytes written=215
                HDFS: Number of read operations=43
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=3
        Job Counters 
                Launched map tasks=10
                Launched reduce tasks=1
                Data-local map tasks=10
                Total time spent by all maps in occupied slots (ms)=78935
                Total time spent by all reduces in occupied slots (ms)=7975
                Total time spent by all map tasks (ms)=78935
                Total time spent by all reduce tasks (ms)=7975
                Total vcore-seconds taken by all map tasks=78935
                Total vcore-seconds taken by all reduce tasks=7975
                Total megabyte-seconds taken by all map tasks=80829440
                Total megabyte-seconds taken by all reduce tasks=8166400
        Map-Reduce Framework
                Map input records=10
                Map output records=20
                Map output bytes=180
                Map output materialized bytes=339
                Input split bytes=1630
                Combine input records=0
                Combine output records=0
                Reduce input groups=2
                Reduce shuffle bytes=339
                Reduce input records=20
                Reduce output records=0
                Spilled Records=40
                Shuffled Maps =10
                Failed Shuffles=0
                Merged Map outputs=10
                GC time elapsed (ms)=386
                CPU time spent (ms)=9280
                Physical memory (bytes) snapshot=4693377024
                Virtual memory (bytes) snapshot=17201156096
                Total committed heap usage (bytes)=5471993856
        Shuffle Errors
                BAD_ID=0
                CONNECTION=0
                IO_ERROR=0
                WRONG_LENGTH=0
                WRONG_MAP=0
                WRONG_REDUCE=0
        File Input Format Counters 
                Bytes Read=1180
        File Output Format Counters 
                Bytes Written=97
Job Finished in 61.179 seconds
Estimated value of Pi is 3.20000000000000000000
```
```
real    1m7.755s
user    0m7.730s
sys     0m0.971s

```
