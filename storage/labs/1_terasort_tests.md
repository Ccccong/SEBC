# 1. Create an end-user Linux account named with your GitHub handle  
1.1 Make sure this Linux account is added to all cluster nodes  
```
[root@ip-172-31-6-7 ~]# rash useradd   gang1998
cmd=- useradd gang1998 -
Connect to ip-172-31-6-7.ec2.internal
ssh -i  AWS-SEBC-TRAINING.pem root@ip-172-31-6-7.ec2.internal "useradd gang1998" 
Connect to ip-172-31-5-148.ec2.internal
ssh -i  AWS-SEBC-TRAINING.pem root@ip-172-31-5-148.ec2.internal "useradd gang1998" 
Connect to ip-172-31-15-40.ec2.internal
ssh -i  AWS-SEBC-TRAINING.pem root@ip-172-31-15-40.ec2.internal "useradd gang1998" 
Connect to ip-172-31-11-232.ec2.internal
ssh -i  AWS-SEBC-TRAINING.pem root@ip-172-31-11-232.ec2.internal "useradd gang1998" 
Connect to ip-172-31-6-212.ec2.internal
ssh -i  AWS-SEBC-TRAINING.pem root@ip-172-31-6-212.ec2.internal "useradd gang1998" 
 ```
  
1.2 Create an HDFS directory under /user  
```
su - hdfs  
hdfs dfs -mkdir /user/gang1998 
hdfs dfs -chown gang1998:gang1998 /user/gang1998 
```
  
1.3 Run the following exercises under this user account  
  
2. Create a 10 GB file using teragen  
2.1 Set the number of mappers to four  
2.2 Limit the block size to 32 MB  
2.3 Land the output in your user's home directory  
2.4 Use the time command to report the job's duration  
```
 su - gang1998 
[gang1998@ip-172-31-6-7 ~]$ time hadoop jar /opt/cloudera/parcels/CDH/jars/hadoop-examples.jar teragen -Dmapred.map.tasks=4 -D dfs.blocksize=33554432 107374180 /user/gang1998/teragen10GB
17/05/09 17:47:19 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-11-232.ec2.internal/172.31.11.232:8032
17/05/09 17:47:19 INFO terasort.TeraSort: Generating 107374180 using 4
17/05/09 17:47:20 INFO mapreduce.JobSubmitter: number of splits:4
17/05/09 17:47:20 INFO Configuration.deprecation: mapred.map.tasks is deprecated. Instead, use mapreduce.job.maps
17/05/09 17:47:20 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1494346839702_0005
17/05/09 17:47:20 INFO impl.YarnClientImpl: Submitted application application_1494346839702_0005
17/05/09 17:47:20 INFO mapreduce.Job: The url to track the job: http://ip-172-31-11-232.ec2.internal:8088/proxy/application_1494346839702_0005/
17/05/09 17:47:20 INFO mapreduce.Job: Running job: job_1494346839702_0005
17/05/09 17:47:26 INFO mapreduce.Job: Job job_1494346839702_0005 running in uber mode : false
17/05/09 17:47:26 INFO mapreduce.Job:  map 0% reduce 0%
17/05/09 17:47:38 INFO mapreduce.Job:  map 3% reduce 0%
17/05/09 17:47:41 INFO mapreduce.Job:  map 10% reduce 0%
17/05/09 17:47:44 INFO mapreduce.Job:  map 14% reduce 0%
17/05/09 17:47:45 INFO mapreduce.Job:  map 15% reduce 0%
17/05/09 17:47:47 INFO mapreduce.Job:  map 17% reduce 0%
17/05/09 17:47:48 INFO mapreduce.Job:  map 18% reduce 0%
17/05/09 17:47:50 INFO mapreduce.Job:  map 19% reduce 0%
17/05/09 17:47:51 INFO mapreduce.Job:  map 20% reduce 0%
17/05/09 17:47:53 INFO mapreduce.Job:  map 22% reduce 0%
17/05/09 17:47:54 INFO mapreduce.Job:  map 23% reduce 0%
17/05/09 17:47:56 INFO mapreduce.Job:  map 24% reduce 0%
17/05/09 17:47:57 INFO mapreduce.Job:  map 25% reduce 0%
17/05/09 17:47:59 INFO mapreduce.Job:  map 26% reduce 0%
17/05/09 17:48:00 INFO mapreduce.Job:  map 27% reduce 0%
17/05/09 17:48:02 INFO mapreduce.Job:  map 28% reduce 0%
17/05/09 17:48:04 INFO mapreduce.Job:  map 29% reduce 0%
17/05/09 17:48:06 INFO mapreduce.Job:  map 30% reduce 0%
17/05/09 17:48:07 INFO mapreduce.Job:  map 31% reduce 0%
17/05/09 17:48:09 INFO mapreduce.Job:  map 33% reduce 0%
17/05/09 17:48:10 INFO mapreduce.Job:  map 34% reduce 0%
17/05/09 17:48:12 INFO mapreduce.Job:  map 36% reduce 0%
17/05/09 17:48:15 INFO mapreduce.Job:  map 38% reduce 0%
17/05/09 17:48:18 INFO mapreduce.Job:  map 40% reduce 0%
17/05/09 17:48:21 INFO mapreduce.Job:  map 42% reduce 0%
17/05/09 17:48:24 INFO mapreduce.Job:  map 44% reduce 0%
17/05/09 17:48:27 INFO mapreduce.Job:  map 46% reduce 0%
17/05/09 17:48:30 INFO mapreduce.Job:  map 47% reduce 0%
17/05/09 17:48:31 INFO mapreduce.Job:  map 48% reduce 0%
17/05/09 17:48:33 INFO mapreduce.Job:  map 49% reduce 0%
17/05/09 17:48:34 INFO mapreduce.Job:  map 50% reduce 0%
17/05/09 17:48:36 INFO mapreduce.Job:  map 51% reduce 0%
17/05/09 17:48:37 INFO mapreduce.Job:  map 52% reduce 0%
17/05/09 17:48:39 INFO mapreduce.Job:  map 53% reduce 0%
17/05/09 17:48:40 INFO mapreduce.Job:  map 54% reduce 0%
17/05/09 17:48:43 INFO mapreduce.Job:  map 56% reduce 0%
17/05/09 17:48:45 INFO mapreduce.Job:  map 57% reduce 0%
17/05/09 17:48:46 INFO mapreduce.Job:  map 58% reduce 0%
17/05/09 17:48:48 INFO mapreduce.Job:  map 59% reduce 0%
17/05/09 17:48:49 INFO mapreduce.Job:  map 61% reduce 0%
17/05/09 17:48:52 INFO mapreduce.Job:  map 63% reduce 0%
17/05/09 17:48:54 INFO mapreduce.Job:  map 64% reduce 0%
17/05/09 17:48:55 INFO mapreduce.Job:  map 65% reduce 0%
17/05/09 17:48:58 INFO mapreduce.Job:  map 67% reduce 0%
17/05/09 17:49:00 INFO mapreduce.Job:  map 68% reduce 0%
17/05/09 17:49:01 INFO mapreduce.Job:  map 69% reduce 0%
17/05/09 17:49:03 INFO mapreduce.Job:  map 70% reduce 0%
17/05/09 17:49:04 INFO mapreduce.Job:  map 71% reduce 0%
17/05/09 17:49:06 INFO mapreduce.Job:  map 72% reduce 0%
17/05/09 17:49:07 INFO mapreduce.Job:  map 73% reduce 0%
17/05/09 17:49:09 INFO mapreduce.Job:  map 74% reduce 0%
17/05/09 17:49:10 INFO mapreduce.Job:  map 75% reduce 0%
17/05/09 17:49:11 INFO mapreduce.Job:  map 76% reduce 0%
17/05/09 17:49:13 INFO mapreduce.Job:  map 77% reduce 0%
17/05/09 17:49:14 INFO mapreduce.Job:  map 78% reduce 0%
17/05/09 17:49:16 INFO mapreduce.Job:  map 79% reduce 0%
17/05/09 17:49:17 INFO mapreduce.Job:  map 80% reduce 0%
17/05/09 17:49:19 INFO mapreduce.Job:  map 81% reduce 0%
17/05/09 17:49:22 INFO mapreduce.Job:  map 83% reduce 0%
17/05/09 17:49:25 INFO mapreduce.Job:  map 84% reduce 0%
17/05/09 17:49:26 INFO mapreduce.Job:  map 85% reduce 0%
17/05/09 17:49:28 INFO mapreduce.Job:  map 86% reduce 0%
17/05/09 17:49:29 INFO mapreduce.Job:  map 87% reduce 0%
17/05/09 17:49:31 INFO mapreduce.Job:  map 88% reduce 0%
17/05/09 17:49:32 INFO mapreduce.Job:  map 89% reduce 0%
17/05/09 17:49:34 INFO mapreduce.Job:  map 90% reduce 0%
17/05/09 17:49:37 INFO mapreduce.Job:  map 92% reduce 0%
17/05/09 17:49:40 INFO mapreduce.Job:  map 93% reduce 0%
17/05/09 17:49:41 INFO mapreduce.Job:  map 94% reduce 0%
17/05/09 17:49:43 INFO mapreduce.Job:  map 95% reduce 0%
17/05/09 17:49:44 INFO mapreduce.Job:  map 96% reduce 0%
17/05/09 17:49:46 INFO mapreduce.Job:  map 97% reduce 0%
17/05/09 17:49:47 INFO mapreduce.Job:  map 98% reduce 0%
17/05/09 17:49:49 INFO mapreduce.Job:  map 99% reduce 0%
17/05/09 17:49:51 INFO mapreduce.Job:  map 100% reduce 0%
17/05/09 17:49:51 INFO mapreduce.Job: Job job_1494346839702_0005 completed successfully
17/05/09 17:49:51 INFO mapreduce.Job: Counters: 31
        File System Counters
                FILE: Number of bytes read=0
                FILE: Number of bytes written=493264
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=344
                HDFS: Number of bytes written=10737418000
                HDFS: Number of read operations=16
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=8
        Job Counters 
                Launched map tasks=4
                Other local map tasks=4
                Total time spent by all maps in occupied slots (ms)=530113
                Total time spent by all reduces in occupied slots (ms)=0
                Total time spent by all map tasks (ms)=530113
                Total vcore-seconds taken by all map tasks=530113
                Total megabyte-seconds taken by all map tasks=542835712
        Map-Reduce Framework
                Map input records=107374180
                Map output records=107374180
                Input split bytes=344
                Spilled Records=0
                Failed Shuffles=0
                Merged Map outputs=0
                GC time elapsed (ms)=1846
                CPU time spent (ms)=169980
                Physical memory (bytes) snapshot=894115840
                Virtual memory (bytes) snapshot=6245224448
                Total committed heap usage (bytes)=832045056
        org.apache.hadoop.examples.terasort.TeraGen$Counters
                CHECKSUM=230593858507236407
        File Input Format Counters 
                Bytes Read=0
        File Output Format Counters 
                Bytes Written=10737418000
```
```
real    2m35.204s
user    0m5.920s
sys     0m0.759s

```
  
3. Run the terasort command on this file  
3.1 Use the time command to report the job's duration  
3.2 Land the result under your user's home directory  
```

[gang1998@ip-172-31-6-7 ~]$ time hadoop jar /opt/cloudera/parcels/CDH/jars/hadoop-examples.jar terasort /user/gang1998/teragen10GB /user/gang1998/teragen10GB_terasort  
17/05/09 17:50:29 INFO terasort.TeraSort: starting
17/05/09 17:50:31 INFO input.FileInputFormat: Total input paths to process : 4
Spent 295ms computing base-splits.
Spent 5ms computing TeraScheduler splits.
Computing input splits took 302ms
Sampling 10 splits of 320
Making 8 from 100000 sampled records
Computing parititions took 983ms
Spent 1288ms computing partitions.
17/05/09 17:50:32 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-11-232.ec2.internal/172.31.11.232:8032
17/05/09 17:50:32 INFO mapreduce.JobSubmitter: number of splits:320
17/05/09 17:50:32 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1494346839702_0006
17/05/09 17:50:33 INFO impl.YarnClientImpl: Submitted application application_1494346839702_0006
17/05/09 17:50:33 INFO mapreduce.Job: The url to track the job: http://ip-172-31-11-232.ec2.internal:8088/proxy/application_1494346839702_0006/
17/05/09 17:50:33 INFO mapreduce.Job: Running job: job_1494346839702_0006
17/05/09 17:50:39 INFO mapreduce.Job: Job job_1494346839702_0006 running in uber mode : false
17/05/09 17:50:39 INFO mapreduce.Job:  map 0% reduce 0%
17/05/09 17:50:51 INFO mapreduce.Job:  map 1% reduce 0%
17/05/09 17:50:53 INFO mapreduce.Job:  map 2% reduce 0%
17/05/09 17:50:54 INFO mapreduce.Job:  map 5% reduce 0%
17/05/09 17:51:03 INFO mapreduce.Job:  map 6% reduce 0%
17/05/09 17:51:07 INFO mapreduce.Job:  map 8% reduce 0%
17/05/09 17:51:08 INFO mapreduce.Job:  map 9% reduce 0%
17/05/09 17:51:12 INFO mapreduce.Job:  map 10% reduce 0%
17/05/09 17:51:19 INFO mapreduce.Job:  map 11% reduce 0%
17/05/09 17:51:20 INFO mapreduce.Job:  map 12% reduce 0%
17/05/09 17:51:21 INFO mapreduce.Job:  map 13% reduce 0%
17/05/09 17:51:22 INFO mapreduce.Job:  map 14% reduce 0%
17/05/09 17:51:24 INFO mapreduce.Job:  map 15% reduce 0%
17/05/09 17:51:32 INFO mapreduce.Job:  map 17% reduce 0%
17/05/09 17:51:34 INFO mapreduce.Job:  map 18% reduce 0%
17/05/09 17:51:35 INFO mapreduce.Job:  map 20% reduce 0%
17/05/09 17:51:46 INFO mapreduce.Job:  map 22% reduce 0%
17/05/09 17:51:48 INFO mapreduce.Job:  map 23% reduce 0%
17/05/09 17:51:49 INFO mapreduce.Job:  map 24% reduce 0%
17/05/09 17:51:53 INFO mapreduce.Job:  map 25% reduce 0%
17/05/09 17:51:58 INFO mapreduce.Job:  map 26% reduce 0%
17/05/09 17:51:59 INFO mapreduce.Job:  map 27% reduce 0%
17/05/09 17:52:01 INFO mapreduce.Job:  map 28% reduce 0%
17/05/09 17:52:03 INFO mapreduce.Job:  map 29% reduce 0%
17/05/09 17:52:06 INFO mapreduce.Job:  map 30% reduce 0%
17/05/09 17:52:12 INFO mapreduce.Job:  map 31% reduce 0%
17/05/09 17:52:13 INFO mapreduce.Job:  map 32% reduce 0%
17/05/09 17:52:15 INFO mapreduce.Job:  map 33% reduce 0%
17/05/09 17:52:16 INFO mapreduce.Job:  map 34% reduce 0%
17/05/09 17:52:17 INFO mapreduce.Job:  map 35% reduce 0%
17/05/09 17:52:24 INFO mapreduce.Job:  map 36% reduce 0%
17/05/09 17:52:25 INFO mapreduce.Job:  map 37% reduce 0%
17/05/09 17:52:27 INFO mapreduce.Job:  map 38% reduce 0%
17/05/09 17:52:29 INFO mapreduce.Job:  map 39% reduce 0%
17/05/09 17:52:33 INFO mapreduce.Job:  map 40% reduce 0%
17/05/09 17:52:37 INFO mapreduce.Job:  map 41% reduce 0%
17/05/09 17:52:38 INFO mapreduce.Job:  map 42% reduce 0%
17/05/09 17:52:40 INFO mapreduce.Job:  map 43% reduce 0%
17/05/09 17:52:42 INFO mapreduce.Job:  map 44% reduce 0%
17/05/09 17:52:46 INFO mapreduce.Job:  map 45% reduce 0%
17/05/09 17:52:50 INFO mapreduce.Job:  map 46% reduce 0%
17/05/09 17:52:51 INFO mapreduce.Job:  map 47% reduce 0%
17/05/09 17:52:54 INFO mapreduce.Job:  map 48% reduce 0%
17/05/09 17:52:55 INFO mapreduce.Job:  map 49% reduce 0%
17/05/09 17:52:57 INFO mapreduce.Job:  map 50% reduce 0%
17/05/09 17:53:04 INFO mapreduce.Job:  map 52% reduce 0%
17/05/09 17:53:06 INFO mapreduce.Job:  map 53% reduce 0%
17/05/09 17:53:08 INFO mapreduce.Job:  map 54% reduce 0%
17/05/09 17:53:14 INFO mapreduce.Job:  map 55% reduce 0%
17/05/09 17:53:16 INFO mapreduce.Job:  map 56% reduce 0%
17/05/09 17:53:17 INFO mapreduce.Job:  map 57% reduce 0%
17/05/09 17:53:19 INFO mapreduce.Job:  map 58% reduce 0%
17/05/09 17:53:22 INFO mapreduce.Job:  map 59% reduce 0%
17/05/09 17:53:25 INFO mapreduce.Job:  map 60% reduce 0%
17/05/09 17:53:29 INFO mapreduce.Job:  map 61% reduce 0%
17/05/09 17:53:32 INFO mapreduce.Job:  map 62% reduce 0%
17/05/09 17:53:33 INFO mapreduce.Job:  map 63% reduce 0%
17/05/09 17:53:35 INFO mapreduce.Job:  map 64% reduce 0%
17/05/09 17:53:36 INFO mapreduce.Job:  map 65% reduce 0%
17/05/09 17:53:43 INFO mapreduce.Job:  map 66% reduce 0%
17/05/09 17:53:45 INFO mapreduce.Job:  map 67% reduce 0%
17/05/09 17:53:46 INFO mapreduce.Job:  map 68% reduce 0%
17/05/09 17:53:48 INFO mapreduce.Job:  map 69% reduce 0%
17/05/09 17:53:54 INFO mapreduce.Job:  map 70% reduce 0%
17/05/09 17:53:57 INFO mapreduce.Job:  map 72% reduce 0%
17/05/09 17:54:01 INFO mapreduce.Job:  map 73% reduce 0%
17/05/09 17:54:02 INFO mapreduce.Job:  map 74% reduce 0%
17/05/09 17:54:07 INFO mapreduce.Job:  map 75% reduce 0%
17/05/09 17:54:10 INFO mapreduce.Job:  map 76% reduce 0%
17/05/09 17:54:12 INFO mapreduce.Job:  map 77% reduce 0%
17/05/09 17:54:14 INFO mapreduce.Job:  map 78% reduce 0%
17/05/09 17:54:16 INFO mapreduce.Job:  map 79% reduce 0%
17/05/09 17:54:18 INFO mapreduce.Job:  map 80% reduce 0%
17/05/09 17:54:23 INFO mapreduce.Job:  map 81% reduce 0%
17/05/09 17:54:25 INFO mapreduce.Job:  map 82% reduce 0%
17/05/09 17:54:27 INFO mapreduce.Job:  map 83% reduce 0%
17/05/09 17:54:28 INFO mapreduce.Job:  map 84% reduce 0%
17/05/09 17:54:35 INFO mapreduce.Job:  map 85% reduce 0%
17/05/09 17:54:38 INFO mapreduce.Job:  map 85% reduce 3%
17/05/09 17:54:39 INFO mapreduce.Job:  map 86% reduce 5%
17/05/09 17:54:41 INFO mapreduce.Job:  map 86% reduce 9%
17/05/09 17:54:42 INFO mapreduce.Job:  map 87% reduce 10%
17/05/09 17:54:44 INFO mapreduce.Job:  map 87% reduce 14%
17/05/09 17:54:47 INFO mapreduce.Job:  map 87% reduce 16%
17/05/09 17:54:48 INFO mapreduce.Job:  map 87% reduce 18%
17/05/09 17:54:50 INFO mapreduce.Job:  map 88% reduce 22%
17/05/09 17:54:54 INFO mapreduce.Job:  map 89% reduce 24%
17/05/09 17:54:56 INFO mapreduce.Job:  map 90% reduce 25%
17/05/09 17:54:57 INFO mapreduce.Job:  map 90% reduce 26%
17/05/09 17:54:59 INFO mapreduce.Job:  map 91% reduce 26%
17/05/09 17:55:03 INFO mapreduce.Job:  map 91% reduce 27%
17/05/09 17:55:05 INFO mapreduce.Job:  map 92% reduce 27%
17/05/09 17:55:07 INFO mapreduce.Job:  map 93% reduce 27%
17/05/09 17:55:09 INFO mapreduce.Job:  map 94% reduce 27%
17/05/09 17:55:15 INFO mapreduce.Job:  map 95% reduce 27%
17/05/09 17:55:16 INFO mapreduce.Job:  map 96% reduce 27%
17/05/09 17:55:17 INFO mapreduce.Job:  map 96% reduce 28%
17/05/09 17:55:22 INFO mapreduce.Job:  map 97% reduce 28%
17/05/09 17:55:24 INFO mapreduce.Job:  map 98% reduce 28%
17/05/09 17:55:27 INFO mapreduce.Job:  map 99% reduce 29%
17/05/09 17:55:31 INFO mapreduce.Job:  map 100% reduce 29%
17/05/09 17:55:33 INFO mapreduce.Job:  map 100% reduce 33%
17/05/09 17:55:35 INFO mapreduce.Job:  map 100% reduce 39%
17/05/09 17:55:36 INFO mapreduce.Job:  map 100% reduce 55%
17/05/09 17:55:38 INFO mapreduce.Job:  map 100% reduce 57%
17/05/09 17:55:39 INFO mapreduce.Job:  map 100% reduce 63%
17/05/09 17:55:41 INFO mapreduce.Job:  map 100% reduce 64%
17/05/09 17:55:42 INFO mapreduce.Job:  map 100% reduce 68%
17/05/09 17:55:45 INFO mapreduce.Job:  map 100% reduce 69%
17/05/09 17:55:46 INFO mapreduce.Job:  map 100% reduce 73%
17/05/09 17:55:48 INFO mapreduce.Job:  map 100% reduce 74%
17/05/09 17:55:49 INFO mapreduce.Job:  map 100% reduce 80%
17/05/09 17:55:51 INFO mapreduce.Job:  map 100% reduce 82%
17/05/09 17:55:52 INFO mapreduce.Job:  map 100% reduce 84%
17/05/09 17:55:54 INFO mapreduce.Job:  map 100% reduce 86%
17/05/09 17:55:55 INFO mapreduce.Job:  map 100% reduce 88%
17/05/09 17:55:57 INFO mapreduce.Job:  map 100% reduce 89%
17/05/09 17:55:58 INFO mapreduce.Job:  map 100% reduce 92%
17/05/09 17:56:01 INFO mapreduce.Job:  map 100% reduce 95%
17/05/09 17:56:04 INFO mapreduce.Job:  map 100% reduce 97%
17/05/09 17:56:06 INFO mapreduce.Job:  map 100% reduce 98%
17/05/09 17:56:07 INFO mapreduce.Job:  map 100% reduce 99%
17/05/09 17:56:08 INFO mapreduce.Job:  map 100% reduce 100%
17/05/09 17:56:09 INFO mapreduce.Job: Job job_1494346839702_0006 completed successfully
17/05/09 17:56:09 INFO mapreduce.Job: Counters: 49
        File System Counters
                FILE: Number of bytes read=4806286575
                FILE: Number of bytes written=9544826414
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=10737464400
                HDFS: Number of bytes written=10737418000
                HDFS: Number of read operations=984
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=16
        Job Counters 
                Launched map tasks=320
                Launched reduce tasks=8
                Data-local map tasks=320
                Total time spent by all maps in occupied slots (ms)=3523623
                Total time spent by all reduces in occupied slots (ms)=701645
                Total time spent by all map tasks (ms)=3523623
                Total time spent by all reduce tasks (ms)=701645
                Total vcore-seconds taken by all map tasks=3523623
                Total vcore-seconds taken by all reduce tasks=701645
                Total megabyte-seconds taken by all map tasks=3608189952
                Total megabyte-seconds taken by all reduce tasks=718484480
        Map-Reduce Framework
                Map input records=107374180
                Map output records=107374180
                Map output bytes=10952166360
                Map output materialized bytes=4697592957
                Input split bytes=46400
                Combine input records=0
                Combine output records=0
                Reduce input groups=107374180
                Reduce shuffle bytes=4697592957
                Reduce input records=107374180
                Reduce output records=107374180
                Spilled Records=214748360
                Shuffled Maps =2560
                Failed Shuffles=0
                Merged Map outputs=2560
                GC time elapsed (ms)=46181
                CPU time spent (ms)=1676460
                Physical memory (bytes) snapshot=155980120064
                Virtual memory (bytes) snapshot=512909889536
                Total committed heap usage (bytes)=186536427520
        Shuffle Errors
                BAD_ID=0
                CONNECTION=0
                IO_ERROR=0
                WRONG_LENGTH=0
                WRONG_MAP=0
                WRONG_REDUCE=0
        File Input Format Counters 
                Bytes Read=10737418000
        File Output Format Counters 
                Bytes Written=10737418000
17/05/09 17:56:09 INFO terasort.TeraSort: done
```
```
real    5m41.079s
user    0m9.559s
sys     0m1.002s
```
 

