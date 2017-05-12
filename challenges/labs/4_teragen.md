# The full  teragen  command and job output
```
Command:
[zhou@ip-172-31-12-204 ~]$ time hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar teragen -Dmapreduce.map.memory.mb=1024 -Dmapred.map.tasks=6 -Ddfs.block.size=67108864 65536000 /user/zhou/tgen
```
```
17/05/12 02:42:08 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-1-9.ec2.internal/172.31.1.9:8032

17/05/12 02:42:08 INFO terasort.TeraSort: Generating 65536000 using 6
17/05/12 02:42:08 INFO mapreduce.JobSubmitter: number of splits:6
17/05/12 02:42:08 INFO Configuration.deprecation: mapred.map.tasks is deprecated. Instead, use mapreduce.job.maps
17/05/12 02:42:08 INFO Configuration.deprecation: dfs.block.size is deprecated. Instead, use dfs.blocksize
17/05/12 02:42:09 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1494555828853_0001
17/05/12 02:42:09 INFO impl.YarnClientImpl: Submitted application application_1494555828853_0001
17/05/12 02:42:09 INFO mapreduce.Job: The url to track the job: http://ip-172-31-1-9.ec2.internal:8088/proxy/application_1494555828853_0001/
17/05/12 02:42:09 INFO mapreduce.Job: Running job: job_1494555828853_0001
17/05/12 02:42:16 INFO mapreduce.Job: Job job_1494555828853_0001 running in uber mode : false
17/05/12 02:42:16 INFO mapreduce.Job:  map 0% reduce 0%
17/05/12 02:42:29 INFO mapreduce.Job:  map 5% reduce 0%
17/05/12 02:42:30 INFO mapreduce.Job:  map 9% reduce 0%
17/05/12 02:42:32 INFO mapreduce.Job:  map 19% reduce 0%
17/05/12 02:42:33 INFO mapreduce.Job:  map 20% reduce 0%
17/05/12 02:42:35 INFO mapreduce.Job:  map 26% reduce 0%
17/05/12 02:42:38 INFO mapreduce.Job:  map 30% reduce 0%
17/05/12 02:42:39 INFO mapreduce.Job:  map 31% reduce 0%
17/05/12 02:42:41 INFO mapreduce.Job:  map 35% reduce 0%
17/05/12 02:42:42 INFO mapreduce.Job:  map 36% reduce 0%
17/05/12 02:42:44 INFO mapreduce.Job:  map 40% reduce 0%
17/05/12 02:42:45 INFO mapreduce.Job:  map 41% reduce 0%
17/05/12 02:42:47 INFO mapreduce.Job:  map 45% reduce 0%
17/05/12 02:42:48 INFO mapreduce.Job:  map 46% reduce 0%
17/05/12 02:42:50 INFO mapreduce.Job:  map 49% reduce 0%
17/05/12 02:42:51 INFO mapreduce.Job:  map 50% reduce 0%
17/05/12 02:42:53 INFO mapreduce.Job:  map 54% reduce 0%
17/05/12 02:42:56 INFO mapreduce.Job:  map 57% reduce 0%
17/05/12 02:42:57 INFO mapreduce.Job:  map 58% reduce 0%
17/05/12 02:42:59 INFO mapreduce.Job:  map 61% reduce 0%
17/05/12 02:43:00 INFO mapreduce.Job:  map 62% reduce 0%
17/05/12 02:43:01 INFO mapreduce.Job:  map 63% reduce 0%
17/05/12 02:43:02 INFO mapreduce.Job:  map 66% reduce 0%
17/05/12 02:43:03 INFO mapreduce.Job:  map 67% reduce 0%
17/05/12 02:43:04 INFO mapreduce.Job:  map 69% reduce 0%
17/05/12 02:43:05 INFO mapreduce.Job:  map 70% reduce 0%
17/05/12 02:43:06 INFO mapreduce.Job:  map 71% reduce 0%
17/05/12 02:43:07 INFO mapreduce.Job:  map 73% reduce 0%
17/05/12 02:43:08 INFO mapreduce.Job:  map 75% reduce 0%
17/05/12 02:43:09 INFO mapreduce.Job:  map 76% reduce 0%
17/05/12 02:43:10 INFO mapreduce.Job:  map 77% reduce 0%
17/05/12 02:43:11 INFO mapreduce.Job:  map 80% reduce 0%
17/05/12 02:43:13 INFO mapreduce.Job:  map 81% reduce 0%
17/05/12 02:43:14 INFO mapreduce.Job:  map 82% reduce 0%
17/05/12 02:43:15 INFO mapreduce.Job:  map 83% reduce 0%
17/05/12 02:43:16 INFO mapreduce.Job:  map 84% reduce 0%
17/05/12 02:43:17 INFO mapreduce.Job:  map 86% reduce 0%
17/05/12 02:43:19 INFO mapreduce.Job:  map 87% reduce 0%
17/05/12 02:43:20 INFO mapreduce.Job:  map 90% reduce 0%
17/05/12 02:43:21 INFO mapreduce.Job:  map 91% reduce 0%
17/05/12 02:43:22 INFO mapreduce.Job:  map 93% reduce 0%
17/05/12 02:43:23 INFO mapreduce.Job:  map 95% reduce 0%
17/05/12 02:43:26 INFO mapreduce.Job:  map 98% reduce 0%
17/05/12 02:43:27 INFO mapreduce.Job:  map 99% reduce 0%
17/05/12 02:43:28 INFO mapreduce.Job:  map 100% reduce 0%
17/05/12 02:43:28 INFO mapreduce.Job: Job job_1494555828853_0001 completed successfully
17/05/12 02:43:29 INFO mapreduce.Job: Counters: 31
        File System Counters
                FILE: Number of bytes read=0
                FILE: Number of bytes written=739434
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=511
                HDFS: Number of bytes written=6553600000
                HDFS: Number of read operations=24
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=12
        Job Counters 
                Launched map tasks=6
                Other local map tasks=6
                Total time spent by all maps in occupied slots (ms)=379973
                Total time spent by all reduces in occupied slots (ms)=0
                Total time spent by all map tasks (ms)=379973
                Total vcore-seconds taken by all map tasks=379973
                Total megabyte-seconds taken by all map tasks=389092352
        Map-Reduce Framework
                Map input records=65536000
                Map output records=65536000
                Input split bytes=511
                Spilled Records=0
                Failed Shuffles=0
                Merged Map outputs=0
                GC time elapsed (ms)=1182
                CPU time spent (ms)=124390
                Physical memory (bytes) snapshot=1999278080
                Virtual memory (bytes) snapshot=9398927360
                Total committed heap usage (bytes)=1960312832
        org.apache.hadoop.examples.terasort.TeraGen$Counters
                CHECKSUM=140750829423462787
        File Input Format Counters 
                Bytes Read=0
        File Output Format Counters 
                Bytes Written=6553600000
```
# The result of the  time  command
```
real    1m23.627s
user    0m5.776s
sys     0m0.692s
```
# The command and output of  hdfs dfs -ls /user/zhou/tgen 
```
[zhou@ip-172-31-12-204 ~]$ hdfs dfs -ls /user/zhou/tgen
Found 7 items
-rw-r--r--   3 zhou zhou          0 2017-05-12 02:43 /user/zhou/tgen/_SUCCESS
-rw-r--r--   3 zhou zhou 1092266700 2017-05-12 02:43 /user/zhou/tgen/part-m-00000
-rw-r--r--   3 zhou zhou 1092266700 2017-05-12 02:43 /user/zhou/tgen/part-m-00001
-rw-r--r--   3 zhou zhou 1092266600 2017-05-12 02:43 /user/zhou/tgen/part-m-00002
-rw-r--r--   3 zhou zhou 1092266700 2017-05-12 02:43 /user/zhou/tgen/part-m-00003
-rw-r--r--   3 zhou zhou 1092266700 2017-05-12 02:43 /user/zhou/tgen/part-m-00004
-rw-r--r--   3 zhou zhou 1092266600 2017-05-12 02:43 /user/zhou/tgen/part-m-00005
```