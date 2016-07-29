
---
layout: page
title: Introduction to Hadoop
subtitle: Integrating Python Mapper and Reducer in Hadoop
minutes: 15
---
> ## Learning Objectives {.objectives}
>
> *   Run the combination of Python-based mapper and reducer on the Hadoop
>     infrastructure
> *   Customize reducer for questions that require global access to KEYS

With the mapper and reducer created and tested, the final step is to run this
combination on the Hadoop infrastructure.


```python
!ssh dsciu001 yarn jar /usr/hdp/current/hadoop-mapreduce-client/hadoop-streaming.jar \
    -input /user/lngo/intro-to-hadoop/ml-10M100K/ratings.dat  \
    -output ratings \
    -file /home/lngo/intro-to-hadoop/mapper02.py \
    -mapper mapper02.py \
    -file /home/lngo/intro-to-hadoop/reducer01.py \
    -reducer reducer01.py \
    -file /home/lngo/intro-to-hadoop/movies.dat
```

    16/07/25 15:31:35 WARN streaming.StreamJob: -file option is deprecated, please use generic option -files instead.
    packageJobJar: [/home/lngo/intro-to-hadoop/mapper02.py, /home/lngo/intro-to-hadoop/reducer01.py, /home/lngo/intro-to-hadoop/movies.dat] [/usr/hdp/2.4.2.0-258/hadoop-mapreduce/hadoop-streaming-2.7.1.2.4.2.0-258.jar] /var/lib/ambari-agent/tmp/hadoop_java_io_tmpdir/streamjob8030563500250963142.jar tmpDir=null
    16/07/25 15:31:37 INFO impl.TimelineClientImpl: Timeline service address: http://dscim003.palmetto.clemson.edu:8188/ws/v1/timeline/
    16/07/25 15:31:37 INFO impl.TimelineClientImpl: Timeline service address: http://dscim003.palmetto.clemson.edu:8188/ws/v1/timeline/
    16/07/25 15:31:37 INFO hdfs.DFSClient: Created HDFS_DELEGATION_TOKEN token 860 for lngo on ha-hdfs:dsci
    16/07/25 15:31:37 INFO security.TokenCache: Got dt for hdfs://dsci; Kind: HDFS_DELEGATION_TOKEN, Service: ha-hdfs:dsci, Ident: (HDFS_DELEGATION_TOKEN token 860 for lngo)
    16/07/25 15:31:38 INFO mapred.FileInputFormat: Total input paths to process : 1
    16/07/25 15:31:38 INFO net.NetworkTopology: Adding a new node: /default-rack/10.125.8.217:1019
    16/07/25 15:31:38 INFO net.NetworkTopology: Adding a new node: /default-rack/10.125.8.204:1019
    16/07/25 15:31:38 INFO net.NetworkTopology: Adding a new node: /default-rack/10.125.8.218:1019
    16/07/25 15:31:38 INFO net.NetworkTopology: Adding a new node: /default-rack/10.125.8.222:1019
    16/07/25 15:31:38 INFO mapreduce.JobSubmitter: number of splits:2
    16/07/25 15:31:38 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1469462752582_0010
    16/07/25 15:31:38 INFO mapreduce.JobSubmitter: Kind: HDFS_DELEGATION_TOKEN, Service: ha-hdfs:dsci, Ident: (HDFS_DELEGATION_TOKEN token 860 for lngo)
    16/07/25 15:31:39 INFO impl.YarnClientImpl: Submitted application application_1469462752582_0010
    16/07/25 15:31:39 INFO mapreduce.Job: The url to track the job: http://dscim001.palmetto.clemson.edu:8088/proxy/application_1469462752582_0010/
    16/07/25 15:31:39 INFO mapreduce.Job: Running job: job_1469462752582_0010
    16/07/25 15:31:54 INFO mapreduce.Job: Job job_1469462752582_0010 running in uber mode : false
    16/07/25 15:31:54 INFO mapreduce.Job:  map 0% reduce 0%
    16/07/25 15:32:13 INFO mapreduce.Job:  map 4% reduce 0%
    16/07/25 15:32:16 INFO mapreduce.Job:  map 8% reduce 0%
    16/07/25 15:32:19 INFO mapreduce.Job:  map 12% reduce 0%
    16/07/25 15:32:22 INFO mapreduce.Job:  map 16% reduce 0%
    16/07/25 15:32:25 INFO mapreduce.Job:  map 21% reduce 0%
    16/07/25 15:32:28 INFO mapreduce.Job:  map 25% reduce 0%
    16/07/25 15:32:31 INFO mapreduce.Job:  map 27% reduce 0%
    16/07/25 15:32:32 INFO mapreduce.Job:  map 29% reduce 0%
    16/07/25 15:32:36 INFO mapreduce.Job:  map 33% reduce 0%
    16/07/25 15:32:39 INFO mapreduce.Job:  map 37% reduce 0%
    16/07/25 15:32:42 INFO mapreduce.Job:  map 41% reduce 0%
    16/07/25 15:32:45 INFO mapreduce.Job:  map 45% reduce 0%
    16/07/25 15:32:48 INFO mapreduce.Job:  map 48% reduce 0%
    16/07/25 15:32:51 INFO mapreduce.Job:  map 52% reduce 0%
    16/07/25 15:32:54 INFO mapreduce.Job:  map 54% reduce 0%
    16/07/25 15:32:55 INFO mapreduce.Job:  map 56% reduce 0%
    16/07/25 15:32:58 INFO mapreduce.Job:  map 62% reduce 0%
    16/07/25 15:33:01 INFO mapreduce.Job:  map 66% reduce 0%
    16/07/25 15:33:04 INFO mapreduce.Job:  map 67% reduce 0%
    16/07/25 15:33:13 INFO mapreduce.Job:  map 83% reduce 0%
    16/07/25 15:33:19 INFO mapreduce.Job:  map 100% reduce 0%
    16/07/25 15:33:30 INFO mapreduce.Job:  map 100% reduce 46%
    16/07/25 15:33:33 INFO mapreduce.Job:  map 100% reduce 56%
    16/07/25 15:33:36 INFO mapreduce.Job:  map 100% reduce 67%
    16/07/25 15:33:39 INFO mapreduce.Job:  map 100% reduce 69%
    16/07/25 15:33:42 INFO mapreduce.Job:  map 100% reduce 71%
    16/07/25 15:33:45 INFO mapreduce.Job:  map 100% reduce 74%
    16/07/25 15:33:49 INFO mapreduce.Job:  map 100% reduce 76%
    16/07/25 15:33:52 INFO mapreduce.Job:  map 100% reduce 78%
    16/07/25 15:33:55 INFO mapreduce.Job:  map 100% reduce 81%
    16/07/25 15:33:58 INFO mapreduce.Job:  map 100% reduce 85%
    16/07/25 15:34:01 INFO mapreduce.Job:  map 100% reduce 88%
    16/07/25 15:34:04 INFO mapreduce.Job:  map 100% reduce 91%
    16/07/25 15:34:07 INFO mapreduce.Job:  map 100% reduce 94%
    16/07/25 15:34:10 INFO mapreduce.Job:  map 100% reduce 98%
    16/07/25 15:34:12 INFO mapreduce.Job:  map 100% reduce 100%
    16/07/25 15:34:13 INFO mapreduce.Job: Job job_1469462752582_0010 completed successfully
    16/07/25 15:34:13 INFO mapreduce.Job: Counters: 50
    	File System Counters
    		FILE: Number of bytes read=315119692
    		FILE: Number of bytes written=630684946
    		FILE: Number of read operations=0
    		FILE: Number of large read operations=0
    		FILE: Number of write operations=0
    		HDFS: Number of bytes read=265236931
    		HDFS: Number of bytes written=422298
    		HDFS: Number of read operations=9
    		HDFS: Number of large read operations=0
    		HDFS: Number of write operations=2
    	Job Counters 
    		Launched map tasks=2
    		Launched reduce tasks=1
    		Data-local map tasks=1
    		Rack-local map tasks=1
    		Total time spent by all maps in occupied slots (ms)=158762
    		Total time spent by all reduces in occupied slots (ms)=114720
    		Total time spent by all map tasks (ms)=158762
    		Total time spent by all reduce tasks (ms)=57360
    		Total vcore-seconds taken by all map tasks=158762
    		Total vcore-seconds taken by all reduce tasks=57360
    		Total megabyte-seconds taken by all map tasks=1300578304
    		Total megabyte-seconds taken by all reduce tasks=939786240
    	Map-Reduce Framework
    		Map input records=10000054
    		Map output records=10000054
    		Map output bytes=295119333
    		Map output materialized bytes=315119698
    		Input split bytes=224
    		Combine input records=0
    		Combine output records=0
    		Reduce input groups=10676
    		Reduce shuffle bytes=315119698
    		Reduce input records=10000054
    		Reduce output records=10676
    		Spilled Records=20000108
    		Shuffled Maps =2
    		Failed Shuffles=0
    		Merged Map outputs=2
    		GC time elapsed (ms)=1832
    		CPU time spent (ms)=252730
    		Physical memory (bytes) snapshot=6152097792
    		Virtual memory (bytes) snapshot=34582532096
    		Total committed heap usage (bytes)=7099383808
    	Shuffle Errors
    		BAD_ID=0
    		CONNECTION=0
    		IO_ERROR=0
    		WRONG_LENGTH=0
    		WRONG_MAP=0
    		WRONG_REDUCE=0
    	File Input Format Counters 
    		Bytes Read=265236707
    	File Output Format Counters 
    		Bytes Written=422298
    16/07/25 15:34:13 INFO streaming.StreamJob: Output directory: ratings


The content of the ratings directory includes an empty file serves as a flag to
indicate whether the operation was successful or not, and the output files. The
number of output files depends on how many reducers we use.


```python
!ssh dsciu001 hdfs dfs -ls ratings 2>/dev/null
```

    Found 2 items
    -rw-r--r--   2 lngo hdfs          0 2016-07-25 15:34 ratings/_SUCCESS
    -rw-r--r--   2 lngo hdfs     422298 2016-07-25 15:34 ratings/part-00000


We can **cat** for the content of the output file


```python
!ssh dsciu001 hdfs dfs -cat ratings/part-00000 2>/dev/null | head
```

    "Great Performances" Cats (1998)	3.58333333333
    'Round Midnight (1986)	3.72
    'Til There Was You (1997)	2.83774834437
    'burbs, The (1989)	2.96941489362
    'night Mother (1986)	3.45023696682
    *batteries not included (1987)	3.15314401623
    ...All the Marbles (a.k.a. The California Dolls) (1981)	2.21739130435
    ...And God Created Woman (Et Dieu... créa la femme) (1956)	3.08552631579
    ...And God Spoke (1993)	3.28260869565
    ...And Justice for All (1979)	3.65270935961


It is also possible to increase number of reducers


```python
!ssh dsciu001 yarn jar /usr/hdp/current/hadoop-mapreduce-client/hadoop-streaming.jar \
    -D mapreduce.job.reduces=4 \
    -input /user/lngo/intro-to-hadoop/ml-10M100K/ratings.dat  \
    -output ratings4R \
    -file /home/lngo/intro-to-hadoop/mapper02.py \
    -mapper mapper02.py \
    -file /home/lngo/intro-to-hadoop/reducer01.py \
    -reducer reducer01.py \
    -file /home/lngo/intro-to-hadoop/movies.dat
```

    16/07/25 15:36:57 WARN streaming.StreamJob: -file option is deprecated, please use generic option -files instead.
    packageJobJar: [/home/lngo/intro-to-hadoop/mapper02.py, /home/lngo/intro-to-hadoop/reducer01.py, /home/lngo/intro-to-hadoop/movies.dat] [/usr/hdp/2.4.2.0-258/hadoop-mapreduce/hadoop-streaming-2.7.1.2.4.2.0-258.jar] /var/lib/ambari-agent/tmp/hadoop_java_io_tmpdir/streamjob4268970964328268399.jar tmpDir=null
    16/07/25 15:36:58 INFO impl.TimelineClientImpl: Timeline service address: http://dscim003.palmetto.clemson.edu:8188/ws/v1/timeline/
    16/07/25 15:36:59 INFO impl.TimelineClientImpl: Timeline service address: http://dscim003.palmetto.clemson.edu:8188/ws/v1/timeline/
    16/07/25 15:36:59 INFO hdfs.DFSClient: Created HDFS_DELEGATION_TOKEN token 861 for lngo on ha-hdfs:dsci
    16/07/25 15:36:59 INFO security.TokenCache: Got dt for hdfs://dsci; Kind: HDFS_DELEGATION_TOKEN, Service: ha-hdfs:dsci, Ident: (HDFS_DELEGATION_TOKEN token 861 for lngo)
    16/07/25 15:37:00 INFO mapred.FileInputFormat: Total input paths to process : 1
    16/07/25 15:37:00 INFO net.NetworkTopology: Adding a new node: /default-rack/10.125.8.204:1019
    16/07/25 15:37:00 INFO net.NetworkTopology: Adding a new node: /default-rack/10.125.8.217:1019
    16/07/25 15:37:00 INFO net.NetworkTopology: Adding a new node: /default-rack/10.125.8.222:1019
    16/07/25 15:37:00 INFO net.NetworkTopology: Adding a new node: /default-rack/10.125.8.218:1019
    16/07/25 15:37:00 INFO mapreduce.JobSubmitter: number of splits:2
    16/07/25 15:37:00 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1469462752582_0011
    16/07/25 15:37:00 INFO mapreduce.JobSubmitter: Kind: HDFS_DELEGATION_TOKEN, Service: ha-hdfs:dsci, Ident: (HDFS_DELEGATION_TOKEN token 861 for lngo)
    16/07/25 15:37:01 INFO impl.YarnClientImpl: Submitted application application_1469462752582_0011
    16/07/25 15:37:01 INFO mapreduce.Job: The url to track the job: http://dscim001.palmetto.clemson.edu:8088/proxy/application_1469462752582_0011/
    16/07/25 15:37:01 INFO mapreduce.Job: Running job: job_1469462752582_0011
    16/07/25 15:37:16 INFO mapreduce.Job: Job job_1469462752582_0011 running in uber mode : false
    16/07/25 15:37:16 INFO mapreduce.Job:  map 0% reduce 0%
    16/07/25 15:37:34 INFO mapreduce.Job:  map 4% reduce 0%
    16/07/25 15:37:37 INFO mapreduce.Job:  map 9% reduce 0%
    16/07/25 15:37:40 INFO mapreduce.Job:  map 13% reduce 0%
    16/07/25 15:37:43 INFO mapreduce.Job:  map 17% reduce 0%
    16/07/25 15:37:46 INFO mapreduce.Job:  map 21% reduce 0%
    16/07/25 15:37:49 INFO mapreduce.Job:  map 23% reduce 0%
    16/07/25 15:37:50 INFO mapreduce.Job:  map 25% reduce 0%
    16/07/25 15:37:52 INFO mapreduce.Job:  map 26% reduce 0%
    16/07/25 15:37:53 INFO mapreduce.Job:  map 28% reduce 0%
    16/07/25 15:37:56 INFO mapreduce.Job:  map 32% reduce 0%
    16/07/25 15:37:59 INFO mapreduce.Job:  map 36% reduce 0%
    16/07/25 15:38:02 INFO mapreduce.Job:  map 40% reduce 0%
    16/07/25 15:38:05 INFO mapreduce.Job:  map 44% reduce 0%
    16/07/25 15:38:08 INFO mapreduce.Job:  map 48% reduce 0%
    16/07/25 15:38:11 INFO mapreduce.Job:  map 53% reduce 0%
    16/07/25 15:38:14 INFO mapreduce.Job:  map 59% reduce 0%
    16/07/25 15:38:17 INFO mapreduce.Job:  map 62% reduce 0%
    16/07/25 15:38:18 INFO mapreduce.Job:  map 64% reduce 0%
    16/07/25 15:38:21 INFO mapreduce.Job:  map 65% reduce 0%
    16/07/25 15:38:24 INFO mapreduce.Job:  map 67% reduce 0%
    16/07/25 15:38:32 INFO mapreduce.Job:  map 83% reduce 0%
    16/07/25 15:38:39 INFO mapreduce.Job:  map 100% reduce 0%
    16/07/25 15:38:50 INFO mapreduce.Job:  map 100% reduce 73%
    16/07/25 15:38:53 INFO mapreduce.Job:  map 100% reduce 78%
    16/07/25 15:38:54 INFO mapreduce.Job:  map 100% reduce 84%
    16/07/25 15:38:55 INFO mapreduce.Job:  map 100% reduce 85%
    16/07/25 15:38:56 INFO mapreduce.Job:  map 100% reduce 91%
    16/07/25 15:38:57 INFO mapreduce.Job:  map 100% reduce 93%
    16/07/25 15:38:59 INFO mapreduce.Job:  map 100% reduce 98%
    16/07/25 15:39:00 INFO mapreduce.Job:  map 100% reduce 100%
    16/07/25 15:39:01 INFO mapreduce.Job: Job job_1469462752582_0011 completed successfully
    16/07/25 15:39:01 INFO mapreduce.Job: Counters: 49
    	File System Counters
    		FILE: Number of bytes read=315119710
    		FILE: Number of bytes written=631130596
    		FILE: Number of read operations=0
    		FILE: Number of large read operations=0
    		FILE: Number of write operations=0
    		HDFS: Number of bytes read=265197906
    		HDFS: Number of bytes written=422298
    		HDFS: Number of read operations=18
    		HDFS: Number of large read operations=0
    		HDFS: Number of write operations=8
    	Job Counters 
    		Launched map tasks=2
    		Launched reduce tasks=4
    		Rack-local map tasks=2
    		Total time spent by all maps in occupied slots (ms)=154519
    		Total time spent by all reduces in occupied slots (ms)=188586
    		Total time spent by all map tasks (ms)=154519
    		Total time spent by all reduce tasks (ms)=94293
    		Total vcore-seconds taken by all map tasks=154519
    		Total vcore-seconds taken by all reduce tasks=94293
    		Total megabyte-seconds taken by all map tasks=1265819648
    		Total megabyte-seconds taken by all reduce tasks=1544896512
    	Map-Reduce Framework
    		Map input records=10000054
    		Map output records=10000054
    		Map output bytes=295119333
    		Map output materialized bytes=315119734
    		Input split bytes=224
    		Combine input records=0
    		Combine output records=0
    		Reduce input groups=10676
    		Reduce shuffle bytes=315119734
    		Reduce input records=10000054
    		Reduce output records=10676
    		Spilled Records=20000108
    		Shuffled Maps =8
    		Failed Shuffles=0
    		Merged Map outputs=8
    		GC time elapsed (ms)=2064
    		CPU time spent (ms)=271690
    		Physical memory (bytes) snapshot=7317250048
    		Virtual memory (bytes) snapshot=83353436160
    		Total committed heap usage (bytes)=8577351680
    	Shuffle Errors
    		BAD_ID=0
    		CONNECTION=0
    		IO_ERROR=0
    		WRONG_LENGTH=0
    		WRONG_MAP=0
    		WRONG_REDUCE=0
    	File Input Format Counters 
    		Bytes Read=265197682
    	File Output Format Counters 
    		Bytes Written=422298
    16/07/25 15:39:01 INFO streaming.StreamJob: Output directory: ratings4R



```python
!ssh dsciu001 hdfs dfs -ls ratings4R 2>/dev/null
```

    Found 5 items
    -rw-r--r--   2 lngo hdfs          0 2016-07-25 15:38 ratings4R/_SUCCESS
    -rw-r--r--   2 lngo hdfs     106498 2016-07-25 15:38 ratings4R/part-00000
    -rw-r--r--   2 lngo hdfs     103491 2016-07-25 15:38 ratings4R/part-00001
    -rw-r--r--   2 lngo hdfs     104521 2016-07-25 15:38 ratings4R/part-00002
    -rw-r--r--   2 lngo hdfs     107788 2016-07-25 15:38 ratings4R/part-00003


Aside from performance implication, an important difference between using one
and many reducers is demonstrated in cases where we want to perform operations
that require a global examination of the data. Let's say the movie company
wishes to identify the movie with highest rating average.

Create a file called **reduce03.py** with the following content

~~~ {.output}
#!/usr/bin/env python
import sys

current_movie = None
current_rating_sum = 0
current_rating_count = 0

max_movie = ""
max_average = 0

for line in sys.stdin:
  line = line.strip()
  movie, rating = line.split("\t", 1)
  try:
    rating = float(rating)
  except ValueError:
    continue

  if current_movie == movie:
    current_rating_sum += rating
    current_rating_count += 1
  else:
    if current_movie:
      rating_average = current_rating_sum / current_rating_count
      if rating_average > max_average:
        max_movie = current_movie
        max_average = rating_average
    current_movie = movie
    current_rating_sum = rating
    current_rating_count = 1

if current_movie == movie:
  rating_average = current_rating_sum / current_rating_count
  if rating_average > max_average:
    max_movie = current_movie
    max_average = rating_average

print ("%s\t%s" % (max_movie, max_average))
~~~

Rerun the Hadoop program using one and four reducers, respectively:


```python
!ssh dsciu001 yarn jar /usr/hdp/current/hadoop-mapreduce-client/hadoop-streaming.jar \
    -D mapreduce.job.reduces=4 \
    -input /user/lngo/intro-to-hadoop/ml-10M100K/ratings.dat  \
    -output ratingsMax \
    -file /home/lngo/intro-to-hadoop/mapper02.py \
    -mapper mapper02.py \
    -file /home/lngo/intro-to-hadoop/reducer03.py \
    -reducer reducer03.py \
    -file /home/lngo/intro-to-hadoop/movies.dat
```

    16/07/25 15:46:22 WARN streaming.StreamJob: -file option is deprecated, please use generic option -files instead.
    packageJobJar: [/home/lngo/intro-to-hadoop/mapper02.py, /home/lngo/intro-to-hadoop/reducer03.py, /home/lngo/intro-to-hadoop/movies.dat] [/usr/hdp/2.4.2.0-258/hadoop-mapreduce/hadoop-streaming-2.7.1.2.4.2.0-258.jar] /var/lib/ambari-agent/tmp/hadoop_java_io_tmpdir/streamjob4500088075814474419.jar tmpDir=null
    16/07/25 15:46:23 INFO impl.TimelineClientImpl: Timeline service address: http://dscim003.palmetto.clemson.edu:8188/ws/v1/timeline/
    16/07/25 15:46:24 INFO impl.TimelineClientImpl: Timeline service address: http://dscim003.palmetto.clemson.edu:8188/ws/v1/timeline/
    16/07/25 15:46:24 INFO hdfs.DFSClient: Created HDFS_DELEGATION_TOKEN token 862 for lngo on ha-hdfs:dsci
    16/07/25 15:46:24 INFO security.TokenCache: Got dt for hdfs://dsci; Kind: HDFS_DELEGATION_TOKEN, Service: ha-hdfs:dsci, Ident: (HDFS_DELEGATION_TOKEN token 862 for lngo)
    16/07/25 15:46:25 INFO mapred.FileInputFormat: Total input paths to process : 1
    16/07/25 15:46:25 INFO net.NetworkTopology: Adding a new node: /default-rack/10.125.8.204:1019
    16/07/25 15:46:25 INFO net.NetworkTopology: Adding a new node: /default-rack/10.125.8.217:1019
    16/07/25 15:46:25 INFO net.NetworkTopology: Adding a new node: /default-rack/10.125.8.218:1019
    16/07/25 15:46:25 INFO net.NetworkTopology: Adding a new node: /default-rack/10.125.8.222:1019
    16/07/25 15:46:25 INFO mapreduce.JobSubmitter: number of splits:2
    16/07/25 15:46:25 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1469462752582_0012
    16/07/25 15:46:25 INFO mapreduce.JobSubmitter: Kind: HDFS_DELEGATION_TOKEN, Service: ha-hdfs:dsci, Ident: (HDFS_DELEGATION_TOKEN token 862 for lngo)
    16/07/25 15:46:26 INFO impl.YarnClientImpl: Submitted application application_1469462752582_0012
    16/07/25 15:46:26 INFO mapreduce.Job: The url to track the job: http://dscim001.palmetto.clemson.edu:8088/proxy/application_1469462752582_0012/
    16/07/25 15:46:26 INFO mapreduce.Job: Running job: job_1469462752582_0012
    16/07/25 15:46:40 INFO mapreduce.Job: Job job_1469462752582_0012 running in uber mode : false
    16/07/25 15:46:40 INFO mapreduce.Job:  map 0% reduce 0%
    16/07/25 15:46:57 INFO mapreduce.Job:  map 2% reduce 0%
    16/07/25 15:46:58 INFO mapreduce.Job:  map 4% reduce 0%
    16/07/25 15:47:00 INFO mapreduce.Job:  map 6% reduce 0%
    16/07/25 15:47:01 INFO mapreduce.Job:  map 8% reduce 0%
    16/07/25 15:47:03 INFO mapreduce.Job:  map 10% reduce 0%
    16/07/25 15:47:04 INFO mapreduce.Job:  map 12% reduce 0%
    16/07/25 15:47:07 INFO mapreduce.Job:  map 16% reduce 0%
    16/07/25 15:47:10 INFO mapreduce.Job:  map 19% reduce 0%
    16/07/25 15:47:11 INFO mapreduce.Job:  map 21% reduce 0%
    16/07/25 15:47:13 INFO mapreduce.Job:  map 24% reduce 0%
    16/07/25 15:47:14 INFO mapreduce.Job:  map 26% reduce 0%
    16/07/25 15:47:16 INFO mapreduce.Job:  map 29% reduce 0%
    16/07/25 15:47:17 INFO mapreduce.Job:  map 31% reduce 0%
    16/07/25 15:47:20 INFO mapreduce.Job:  map 38% reduce 0%
    16/07/25 15:47:23 INFO mapreduce.Job:  map 44% reduce 0%
    16/07/25 15:47:26 INFO mapreduce.Job:  map 50% reduce 0%
    16/07/25 15:47:29 INFO mapreduce.Job:  map 56% reduce 0%
    16/07/25 15:47:32 INFO mapreduce.Job:  map 61% reduce 0%
    16/07/25 15:47:35 INFO mapreduce.Job:  map 66% reduce 0%
    16/07/25 15:47:40 INFO mapreduce.Job:  map 67% reduce 0%
    16/07/25 15:47:52 INFO mapreduce.Job:  map 100% reduce 0%
    16/07/25 15:48:09 INFO mapreduce.Job:  map 100% reduce 80%
    16/07/25 15:48:12 INFO mapreduce.Job:  map 100% reduce 91%
    16/07/25 15:48:13 INFO mapreduce.Job:  map 100% reduce 94%
    16/07/25 15:48:14 INFO mapreduce.Job:  map 100% reduce 95%
    16/07/25 15:48:15 INFO mapreduce.Job:  map 100% reduce 97%
    16/07/25 15:48:16 INFO mapreduce.Job:  map 100% reduce 100%
    16/07/25 15:48:17 INFO mapreduce.Job: Job job_1469462752582_0012 completed successfully
    16/07/25 15:48:17 INFO mapreduce.Job: Counters: 49
    	File System Counters
    		FILE: Number of bytes read=315119710
    		FILE: Number of bytes written=631130602
    		FILE: Number of read operations=0
    		FILE: Number of large read operations=0
    		FILE: Number of write operations=0
    		HDFS: Number of bytes read=265197906
    		HDFS: Number of bytes written=180
    		HDFS: Number of read operations=18
    		HDFS: Number of large read operations=0
    		HDFS: Number of write operations=8
    	Job Counters 
    		Launched map tasks=2
    		Launched reduce tasks=4
    		Rack-local map tasks=2
    		Total time spent by all maps in occupied slots (ms)=138245
    		Total time spent by all reduces in occupied slots (ms)=166412
    		Total time spent by all map tasks (ms)=138245
    		Total time spent by all reduce tasks (ms)=83206
    		Total vcore-seconds taken by all map tasks=138245
    		Total vcore-seconds taken by all reduce tasks=83206
    		Total megabyte-seconds taken by all map tasks=1132503040
    		Total megabyte-seconds taken by all reduce tasks=1363247104
    	Map-Reduce Framework
    		Map input records=10000054
    		Map output records=10000054
    		Map output bytes=295119333
    		Map output materialized bytes=315119734
    		Input split bytes=224
    		Combine input records=0
    		Combine output records=0
    		Reduce input groups=10676
    		Reduce shuffle bytes=315119734
    		Reduce input records=10000054
    		Reduce output records=4
    		Spilled Records=20000108
    		Shuffled Maps =8
    		Failed Shuffles=0
    		Merged Map outputs=8
    		GC time elapsed (ms)=2006
    		CPU time spent (ms)=240550
    		Physical memory (bytes) snapshot=7421755392
    		Virtual memory (bytes) snapshot=83398647808
    		Total committed heap usage (bytes)=8729395200
    	Shuffle Errors
    		BAD_ID=0
    		CONNECTION=0
    		IO_ERROR=0
    		WRONG_LENGTH=0
    		WRONG_MAP=0
    		WRONG_REDUCE=0
    	File Input Format Counters 
    		Bytes Read=265197682
    	File Output Format Counters 
    		Bytes Written=180
    16/07/25 15:48:17 INFO streaming.StreamJob: Output directory: ratingsMax



```python
!ssh dsciu001 yarn jar /usr/hdp/current/hadoop-mapreduce-client/hadoop-streaming.jar \
    -D mapreduce.job.reduces=4 \
    -input /user/lngo/intro-to-hadoop/ml-10M100K/ratings.dat  \
    -output ratingsMax4R \
    -file /home/lngo/intro-to-hadoop/mapper02.py \
    -mapper mapper02.py \
    -file /home/lngo/intro-to-hadoop/reducer03.py \
    -reducer reducer03.py \
    -file /home/lngo/intro-to-hadoop/movies.dat
```

    16/07/25 15:53:18 WARN streaming.StreamJob: -file option is deprecated, please use generic option -files instead.
    packageJobJar: [/home/lngo/intro-to-hadoop/mapper02.py, /home/lngo/intro-to-hadoop/reducer03.py, /home/lngo/intro-to-hadoop/movies.dat] [/usr/hdp/2.4.2.0-258/hadoop-mapreduce/hadoop-streaming-2.7.1.2.4.2.0-258.jar] /var/lib/ambari-agent/tmp/hadoop_java_io_tmpdir/streamjob3588979903194305897.jar tmpDir=null
    16/07/25 15:53:19 INFO impl.TimelineClientImpl: Timeline service address: http://dscim003.palmetto.clemson.edu:8188/ws/v1/timeline/
    16/07/25 15:53:20 INFO impl.TimelineClientImpl: Timeline service address: http://dscim003.palmetto.clemson.edu:8188/ws/v1/timeline/
    16/07/25 15:53:20 INFO hdfs.DFSClient: Created HDFS_DELEGATION_TOKEN token 864 for lngo on ha-hdfs:dsci
    16/07/25 15:53:20 INFO security.TokenCache: Got dt for hdfs://dsci; Kind: HDFS_DELEGATION_TOKEN, Service: ha-hdfs:dsci, Ident: (HDFS_DELEGATION_TOKEN token 864 for lngo)
    16/07/25 15:53:20 INFO mapred.FileInputFormat: Total input paths to process : 1
    16/07/25 15:53:20 INFO net.NetworkTopology: Adding a new node: /default-rack/10.125.8.217:1019
    16/07/25 15:53:20 INFO net.NetworkTopology: Adding a new node: /default-rack/10.125.8.204:1019
    16/07/25 15:53:20 INFO net.NetworkTopology: Adding a new node: /default-rack/10.125.8.218:1019
    16/07/25 15:53:20 INFO net.NetworkTopology: Adding a new node: /default-rack/10.125.8.222:1019
    16/07/25 15:53:21 INFO mapreduce.JobSubmitter: number of splits:2
    16/07/25 15:53:21 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1469462752582_0014
    16/07/25 15:53:21 INFO mapreduce.JobSubmitter: Kind: HDFS_DELEGATION_TOKEN, Service: ha-hdfs:dsci, Ident: (HDFS_DELEGATION_TOKEN token 864 for lngo)
    16/07/25 15:53:21 INFO impl.YarnClientImpl: Submitted application application_1469462752582_0014
    16/07/25 15:53:22 INFO mapreduce.Job: The url to track the job: http://dscim001.palmetto.clemson.edu:8088/proxy/application_1469462752582_0014/
    16/07/25 15:53:22 INFO mapreduce.Job: Running job: job_1469462752582_0014
    16/07/25 15:53:36 INFO mapreduce.Job: Job job_1469462752582_0014 running in uber mode : false
    16/07/25 15:53:36 INFO mapreduce.Job:  map 0% reduce 0%
    16/07/25 15:53:53 INFO mapreduce.Job:  map 4% reduce 0%
    16/07/25 15:53:56 INFO mapreduce.Job:  map 8% reduce 0%
    16/07/25 15:53:59 INFO mapreduce.Job:  map 12% reduce 0%
    16/07/25 15:54:02 INFO mapreduce.Job:  map 16% reduce 0%
    16/07/25 15:54:05 INFO mapreduce.Job:  map 21% reduce 0%
    16/07/25 15:54:08 INFO mapreduce.Job:  map 23% reduce 0%
    16/07/25 15:54:09 INFO mapreduce.Job:  map 25% reduce 0%
    16/07/25 15:54:12 INFO mapreduce.Job:  map 29% reduce 0%
    16/07/25 15:54:15 INFO mapreduce.Job:  map 33% reduce 0%
    16/07/25 15:54:18 INFO mapreduce.Job:  map 38% reduce 0%
    16/07/25 15:54:21 INFO mapreduce.Job:  map 42% reduce 0%
    16/07/25 15:54:24 INFO mapreduce.Job:  map 46% reduce 0%
    16/07/25 15:54:27 INFO mapreduce.Job:  map 50% reduce 0%
    16/07/25 15:54:30 INFO mapreduce.Job:  map 55% reduce 0%
    16/07/25 15:54:34 INFO mapreduce.Job:  map 60% reduce 0%
    16/07/25 15:54:37 INFO mapreduce.Job:  map 65% reduce 0%
    16/07/25 15:54:40 INFO mapreduce.Job:  map 67% reduce 0%
    16/07/25 15:54:52 INFO mapreduce.Job:  map 83% reduce 0%
    16/07/25 15:54:57 INFO mapreduce.Job:  map 100% reduce 0%
    16/07/25 15:55:09 INFO mapreduce.Job:  map 100% reduce 38%
    16/07/25 15:55:10 INFO mapreduce.Job:  map 100% reduce 78%
    16/07/25 15:55:13 INFO mapreduce.Job:  map 100% reduce 89%
    16/07/25 15:55:16 INFO mapreduce.Job:  map 100% reduce 98%
    16/07/25 15:55:18 INFO mapreduce.Job:  map 100% reduce 100%
    16/07/25 15:55:19 INFO mapreduce.Job: Job job_1469462752582_0014 completed successfully
    16/07/25 15:55:19 INFO mapreduce.Job: Counters: 49
    	File System Counters
    		FILE: Number of bytes read=315119710
    		FILE: Number of bytes written=631130614
    		FILE: Number of read operations=0
    		FILE: Number of large read operations=0
    		FILE: Number of write operations=0
    		HDFS: Number of bytes read=265197906
    		HDFS: Number of bytes written=180
    		HDFS: Number of read operations=18
    		HDFS: Number of large read operations=0
    		HDFS: Number of write operations=8
    	Job Counters 
    		Launched map tasks=2
    		Launched reduce tasks=4
    		Rack-local map tasks=2
    		Total time spent by all maps in occupied slots (ms)=154378
    		Total time spent by all reduces in occupied slots (ms)=174446
    		Total time spent by all map tasks (ms)=154378
    		Total time spent by all reduce tasks (ms)=87223
    		Total vcore-seconds taken by all map tasks=154378
    		Total vcore-seconds taken by all reduce tasks=87223
    		Total megabyte-seconds taken by all map tasks=1264664576
    		Total megabyte-seconds taken by all reduce tasks=1429061632
    	Map-Reduce Framework
    		Map input records=10000054
    		Map output records=10000054
    		Map output bytes=295119333
    		Map output materialized bytes=315119734
    		Input split bytes=224
    		Combine input records=0
    		Combine output records=0
    		Reduce input groups=10676
    		Reduce shuffle bytes=315119734
    		Reduce input records=10000054
    		Reduce output records=4
    		Spilled Records=20000108
    		Shuffled Maps =8
    		Failed Shuffles=0
    		Merged Map outputs=8
    		GC time elapsed (ms)=2074
    		CPU time spent (ms)=271730
    		Physical memory (bytes) snapshot=7329378304
    		Virtual memory (bytes) snapshot=83325136896
    		Total committed heap usage (bytes)=8554283008
    	Shuffle Errors
    		BAD_ID=0
    		CONNECTION=0
    		IO_ERROR=0
    		WRONG_LENGTH=0
    		WRONG_MAP=0
    		WRONG_REDUCE=0
    	File Input Format Counters 
    		Bytes Read=265197682
    	File Output Format Counters 
    		Bytes Written=180
    16/07/25 15:55:19 INFO streaming.StreamJob: Output directory: ratingsMax4R


In the case of one reducer, there is only a single answer for the movie with
highest rating average. With four reducers, we have four possible answers. On
the other hand, it is quite feasible to infer the final single answer from a
set of four possible choices.


```python
!ssh dsciu001 hdfs dfs -cat ratingsMax/part-00000 2>/dev/null
```

    Blue Light, The (Das Blaue Licht) (1932)	5.0



```python
!ssh dsciu001 hdfs dfs -cat ratingsMax4R/part-00000 2>/dev/null
```

    Blue Light, The (Das Blaue Licht) (1932)	5.0



```python
!ssh dsciu001 hdfs dfs -cat ratingsMax4R/part-00001 2>/dev/null
```

    Satan's Tango (Sátántangó) (1994)	5.0



```python
!ssh dsciu001 hdfs dfs -cat ratingsMax4R/part-00002 2>/dev/null
```

    End of Summer, The (Kohayagawa-ke no aki) (1961)	4.5



```python
!ssh dsciu001 hdfs dfs -cat ratingsMax4R/part-00003 2>/dev/null
```

    Fighting Elegy (Kenka erejii) (1966)	5.0


## Check your understanding: Additional conditions on the reduce side {.challenge}
The previous results do not make sense intuitively, as these movies are not
well known. It is possible that our results are skewed by movies having too
few reviews. Modify the reducer so that we only consider movies that have more
than one thousand ratings totally. Name this reducer reducer03.py. Run the
Hadoop MapReduce program again with mapper03.py and reducer03.py using one and
four reducers respectively. Report the outcome.



## Check your understanding: User Study {.challenge}
User feedback plays an important role in marketing strategies. Implement a
Hadoop MapReduce program that identifies the user that rates the most movies
over time. Identify the genre that this user rates most favorably.