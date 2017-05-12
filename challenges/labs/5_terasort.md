# Run the  terasort  program as  zhou  using the output target  /user/zhou/tsort  
Copy the command and full output to  challenges/labs/5_terasort.md 
```
[zhou@ip-172-31-12-204 ~]$ kinit zhou
Password for zhou@GANG1998.CN: 
[zhou@ip-172-31-12-204 ~]$ klist
Ticket cache: FILE:/tmp/krb5cc_2800
Default principal: zhou@GANG1998.CN

Valid starting     Expires            Service principal
05/12/17 03:17:22  05/13/17 03:17:22  krbtgt/GANG1998.CN@GANG1998.CN
        renew until 05/19/17 03:17:22
```
```
[zhou@ip-172-31-12-204 ~]$ time hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar terasort -Dmapred.reduce.tasks=6 /user/zhou/tgen /user/zhou/tsort640m
```
```
17/05/12 03:18:36 INFO terasort.TeraSort: starting
17/05/12 03:18:38 INFO hdfs.DFSClient: Created token for zhou: HDFS_DELEGATION_TOKEN owner=zhou@GANG1998.CN, renewer=yarn, realUser=, issueDate=1494559118494, maxDate=1495163918494, sequenceNumber=1, masterKeyId=2 on 172.31.1.9:8020
17/05/12 03:18:38 INFO security.TokenCache: Got dt for hdfs://ip-172-31-1-9.ec2.internal:8020; Kind: HDFS_DELEGATION_TOKEN, Service: 172.31.1.9:8020, Ident: (token for zhou: HDFS_DELEGATION_TOKEN owner=zhou@GANG1998.CN, renewer=yarn, realUser=, issueDate=1494559118494, maxDate=1495163918494, sequenceNumber=1, masterKeyId=2)
17/05/12 03:18:38 INFO input.FileInputFormat: Total input paths to process : 6
Spent 351ms computing base-splits.
Spent 5ms computing TeraScheduler splits.
Computing input splits took 357ms
Sampling 10 splits of 102
Making 6 from 100000 sampled records
Computing parititions took 863ms
Spent 1223ms computing partitions.
17/05/12 03:18:39 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-1-9.ec2.internal/172.31.1.9:8032
17/05/12 03:18:40 INFO mapreduce.JobSubmitter: number of splits:102
17/05/12 03:18:40 INFO Configuration.deprecation: mapred.reduce.tasks is deprecated. Instead, use mapreduce.job.reduces
17/05/12 03:18:40 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1494558582875_0001
17/05/12 03:18:40 INFO mapreduce.JobSubmitter: Kind: HDFS_DELEGATION_TOKEN, Service: 172.31.1.9:8020, Ident: (token for zhou: HDFS_DELEGATION_TOKEN owner=zhou@GANG1998.CN, renewer=yarn, realUser=, issueDate=1494559118494, maxDate=1495163918494, sequenceNumber=1, masterKeyId=2)
17/05/12 03:18:41 INFO impl.YarnClientImpl: Submitted application application_1494558582875_0001
17/05/12 03:18:41 INFO mapreduce.Job: The url to track the job: http://ip-172-31-1-9.ec2.internal:8088/proxy/application_1494558582875_0001/
17/05/12 03:18:41 INFO mapreduce.Job: Running job: job_1494558582875_0001
17/05/12 03:18:51 INFO mapreduce.Job: Job job_1494558582875_0001 running in uber mode : false
17/05/12 03:18:51 INFO mapreduce.Job:  map 0% reduce 0%
17/05/12 03:18:59 INFO mapreduce.Job:  map 1% reduce 0%
17/05/12 03:19:06 INFO mapreduce.Job:  map 3% reduce 0%
17/05/12 03:19:07 INFO mapreduce.Job:  map 4% reduce 0%
17/05/12 03:19:11 INFO mapreduce.Job:  map 7% reduce 0%
17/05/12 03:19:12 INFO mapreduce.Job:  map 10% reduce 0%
17/05/12 03:19:15 INFO mapreduce.Job:  map 12% reduce 0%
17/05/12 03:19:16 INFO mapreduce.Job:  map 13% reduce 0%
17/05/12 03:19:23 INFO mapreduce.Job:  map 14% reduce 0%
17/05/12 03:19:24 INFO mapreduce.Job:  map 15% reduce 0%
17/05/12 03:19:25 INFO mapreduce.Job:  map 18% reduce 0%
17/05/12 03:19:26 INFO mapreduce.Job:  map 19% reduce 0%
17/05/12 03:19:27 INFO mapreduce.Job:  map 22% reduce 0%
17/05/12 03:19:31 INFO mapreduce.Job:  map 23% reduce 0%
17/05/12 03:19:35 INFO mapreduce.Job:  map 24% reduce 0%
17/05/12 03:19:36 INFO mapreduce.Job:  map 25% reduce 0%
17/05/12 03:19:37 INFO mapreduce.Job:  map 27% reduce 0%
17/05/12 03:19:39 INFO mapreduce.Job:  map 28% reduce 0%
17/05/12 03:19:40 INFO mapreduce.Job:  map 31% reduce 0%
17/05/12 03:19:45 INFO mapreduce.Job:  map 33% reduce 0%
17/05/12 03:19:46 INFO mapreduce.Job:  map 34% reduce 0%
17/05/12 03:19:49 INFO mapreduce.Job:  map 36% reduce 0%
17/05/12 03:19:50 INFO mapreduce.Job:  map 37% reduce 0%
17/05/12 03:19:53 INFO mapreduce.Job:  map 38% reduce 0%
17/05/12 03:19:54 INFO mapreduce.Job:  map 42% reduce 0%
17/05/12 03:19:55 INFO mapreduce.Job:  map 43% reduce 0%
17/05/12 03:20:01 INFO mapreduce.Job:  map 45% reduce 0%
17/05/12 03:20:02 INFO mapreduce.Job:  map 47% reduce 0%
17/05/12 03:20:04 INFO mapreduce.Job:  map 49% reduce 0%
17/05/12 03:20:07 INFO mapreduce.Job:  map 50% reduce 0%
17/05/12 03:20:08 INFO mapreduce.Job:  map 53% reduce 0%
17/05/12 03:20:14 INFO mapreduce.Job:  map 56% reduce 0%
17/05/12 03:20:15 INFO mapreduce.Job:  map 57% reduce 0%
17/05/12 03:20:16 INFO mapreduce.Job:  map 59% reduce 0%
17/05/12 03:20:20 INFO mapreduce.Job:  map 60% reduce 0%
17/05/12 03:20:21 INFO mapreduce.Job:  map 61% reduce 0%
17/05/12 03:20:22 INFO mapreduce.Job:  map 63% reduce 0%
17/05/12 03:20:24 INFO mapreduce.Job:  map 64% reduce 0%
17/05/12 03:20:27 INFO mapreduce.Job:  map 65% reduce 0%
17/05/12 03:20:28 INFO mapreduce.Job:  map 67% reduce 0%
17/05/12 03:20:29 INFO mapreduce.Job:  map 68% reduce 0%
17/05/12 03:20:32 INFO mapreduce.Job:  map 69% reduce 0%
17/05/12 03:20:33 INFO mapreduce.Job:  map 71% reduce 0%
17/05/12 03:20:34 INFO mapreduce.Job:  map 72% reduce 0%
17/05/12 03:20:37 INFO mapreduce.Job:  map 73% reduce 0%
17/05/12 03:20:40 INFO mapreduce.Job:  map 74% reduce 0%
17/05/12 03:20:46 INFO mapreduce.Job:  map 75% reduce 0%
17/05/12 03:20:50 INFO mapreduce.Job:  map 76% reduce 0%
17/05/12 03:20:51 INFO mapreduce.Job:  map 77% reduce 0%
17/05/12 03:20:54 INFO mapreduce.Job:  map 79% reduce 0%
17/05/12 03:20:57 INFO mapreduce.Job:  map 80% reduce 0%
17/05/12 03:20:58 INFO mapreduce.Job:  map 81% reduce 0%
17/05/12 03:20:59 INFO mapreduce.Job:  map 82% reduce 0%
17/05/12 03:21:04 INFO mapreduce.Job:  map 83% reduce 0%
17/05/12 03:21:05 INFO mapreduce.Job:  map 84% reduce 0%
17/05/12 03:21:06 INFO mapreduce.Job:  map 87% reduce 0%
17/05/12 03:21:07 INFO mapreduce.Job:  map 88% reduce 0%
17/05/12 03:21:09 INFO mapreduce.Job:  map 89% reduce 0%
17/05/12 03:21:12 INFO mapreduce.Job:  map 90% reduce 0%
17/05/12 03:21:15 INFO mapreduce.Job:  map 90% reduce 4%
17/05/12 03:21:16 INFO mapreduce.Job:  map 91% reduce 4%
17/05/12 03:21:18 INFO mapreduce.Job:  map 91% reduce 5%
17/05/12 03:21:19 INFO mapreduce.Job:  map 92% reduce 8%
17/05/12 03:21:20 INFO mapreduce.Job:  map 94% reduce 13%
17/05/12 03:21:22 INFO mapreduce.Job:  map 95% reduce 14%
17/05/12 03:21:23 INFO mapreduce.Job:  map 95% reduce 18%
17/05/12 03:21:26 INFO mapreduce.Job:  map 95% reduce 19%
17/05/12 03:21:27 INFO mapreduce.Job:  map 96% reduce 19%
17/05/12 03:21:28 INFO mapreduce.Job:  map 97% reduce 19%
17/05/12 03:21:29 INFO mapreduce.Job:  map 98% reduce 21%
17/05/12 03:21:30 INFO mapreduce.Job:  map 99% reduce 22%
17/05/12 03:21:33 INFO mapreduce.Job:  map 99% reduce 26%
17/05/12 03:21:34 INFO mapreduce.Job:  map 100% reduce 26%
17/05/12 03:21:35 INFO mapreduce.Job:  map 100% reduce 33%
17/05/12 03:21:36 INFO mapreduce.Job:  map 100% reduce 39%
17/05/12 03:21:38 INFO mapreduce.Job:  map 100% reduce 51%
17/05/12 03:21:39 INFO mapreduce.Job:  map 100% reduce 52%
17/05/12 03:21:40 INFO mapreduce.Job:  map 100% reduce 56%
17/05/12 03:21:41 INFO mapreduce.Job:  map 100% reduce 59%
17/05/12 03:21:42 INFO mapreduce.Job:  map 100% reduce 66%
17/05/12 03:21:43 INFO mapreduce.Job:  map 100% reduce 67%
17/05/12 03:21:44 INFO mapreduce.Job:  map 100% reduce 70%
17/05/12 03:21:45 INFO mapreduce.Job:  map 100% reduce 72%
17/05/12 03:21:46 INFO mapreduce.Job:  map 100% reduce 77%
17/05/12 03:21:47 INFO mapreduce.Job:  map 100% reduce 78%
17/05/12 03:21:48 INFO mapreduce.Job:  map 100% reduce 83%
17/05/12 03:21:49 INFO mapreduce.Job:  map 100% reduce 84%
17/05/12 03:21:50 INFO mapreduce.Job:  map 100% reduce 85%
17/05/12 03:21:51 INFO mapreduce.Job:  map 100% reduce 87%
17/05/12 03:21:52 INFO mapreduce.Job:  map 100% reduce 88%
17/05/12 03:21:53 INFO mapreduce.Job:  map 100% reduce 89%
17/05/12 03:21:54 INFO mapreduce.Job:  map 100% reduce 92%
17/05/12 03:21:56 INFO mapreduce.Job:  map 100% reduce 95%
17/05/12 03:21:57 INFO mapreduce.Job:  map 100% reduce 98%
17/05/12 03:21:58 INFO mapreduce.Job:  map 100% reduce 100%
17/05/12 03:21:59 INFO mapreduce.Job: Job job_1494558582875_0001 completed successfully
17/05/12 03:21:59 INFO mapreduce.Job: Counters: 49
        File System Counters
                FILE: Number of bytes read=2933933943
                FILE: Number of bytes written=5820533824
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=6553613362
                HDFS: Number of bytes written=6553600000
                HDFS: Number of read operations=324
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=12
        Job Counters 
                Launched map tasks=102
                Launched reduce tasks=6
                Data-local map tasks=102
                Total time spent by all maps in occupied slots (ms)=1044941
                Total time spent by all reduces in occupied slots (ms)=255969
                Total time spent by all map tasks (ms)=1044941
                Total time spent by all reduce tasks (ms)=255969
                Total vcore-seconds taken by all map tasks=1044941
                Total vcore-seconds taken by all reduce tasks=255969
                Total megabyte-seconds taken by all map tasks=1070019584
                Total megabyte-seconds taken by all reduce tasks=262112256
        Map-Reduce Framework
                Map input records=65536000
                Map output records=65536000
                Map output bytes=6684672000
                Map output materialized bytes=2873051907
                Input split bytes=13362
                Combine input records=0
                Combine output records=0
                Reduce input groups=65536000
                Reduce shuffle bytes=2873051907
                Reduce input records=65536000
                Reduce output records=65536000
                Spilled Records=131072000
                Shuffled Maps =612
                Failed Shuffles=0
                Merged Map outputs=612
                GC time elapsed (ms)=16019
                CPU time spent (ms)=743520
                Physical memory (bytes) snapshot=56733708288
                Virtual memory (bytes) snapshot=169041629184
                Total committed heap usage (bytes)=66669510656
        Shuffle Errors
                BAD_ID=0
                CONNECTION=0
                IO_ERROR=0
                WRONG_LENGTH=0
                WRONG_MAP=0
                WRONG_REDUCE=0
        File Input Format Counters 
                Bytes Read=6553600000
        File Output Format Counters 
                Bytes Written=6553600000
17/05/12 03:21:59 INFO terasort.TeraSort: done

real    3m24.091s
user    0m8.797s
sys     0m0.897s

```