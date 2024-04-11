# Hadoop

## 什么是Hadoop

An open-source implementation of MapReduce in Java

## Hadoop terminology

- Job: 用于提交到集群的打包的Hadoop程序
- Task: an execution of a mapper or a reducer on a slice of data
- Task attempt: a particular task will be attempted at least once, possibly more times if it crashes

eg. 

对20个文件执行WordCount是一个job

20个文件mapped to 20个map task+一些reduce tasks

最少20map task attempts wii be performed

## Data types

![image-20240411160911208](assets\image-20240411160911208.png)

## Complex data types

![image-20240411161220869](assets\image-20240411161220869.png)

## WordCount

![image-20240411160951264](assets\image-20240411160951264.png)

![image-20240411161008589](assets\image-20240411161008589.png)

![image-20240411161057649](assets\image-20240411161057649.png)

![image-20240411161112444](assets\image-20240411161112444.png)

## Anatomy of Hadoop

Hadoop = HDFS + MapReduce

单个cluster

- NameNode
- JobTracker

set of each per slave machine

- DataNode
- TaskTracker



## Hadoop I/O



## Workflow

![image-20240411162038007](assets\image-20240411162038007.png)