# HDFS

## HDFS是什么

GFS的开源实现

作为Hadoop 生态系统的主要组件，HDFS **是一个分布式文件系统，可提供对应用数据的高吞吐量访问，而无需预先定义架构**。

## 设计思路

### Assumption

HDFS的设计大量借鉴了GFS的设计

- Cheap, commodity machines
- A “modest” number of very *large* files
- Batch processing（ **write-once**, **mostly appended to** ）
- 高持续吞吐量优于低延迟

### Design

- NameNode: 管家，管理filesystem data
- DataNode(chunk server)：存储和检索data
- SecondaryNameNode（shadow master）：checkpoint
- **Single namespace for the entire cluster**
- Data coherency: 写一次多次读取
- 文件分块：blocks，128MB 一个block
- intelligent client: 可以找到block locations, 直接从DataNode获取data
  



## 架构

![image-20240411151511372](assets\image-20240411151511372.png)

![image-20240411151555006](assets\image-20240411151555006.png)

## 工作原理

### NameNode(master)

- 管理file system namespace
- 映射filename到a set of blocks
- 将块映射到它所在的datanode
- 集群配置管理
- block 复制

#### NameNode metadata

存在memory

type

- list of files
- list of blocks for each file
- file attribute
- list of DataNode for each block

### DataNode

- 在本地存储data
- 存储metadata的block
- 把data和metadata发给client
- 给NameNode周期性发送心跳包（3s)
- Block report（一个小时，周期性检查）
- Facilitates pipelining of data 

## 工作流程

### Closest block

![image-20240411152056008](assets\image-20240411152056008.png)

![image-20240411152119574](assets\image-20240411152119574.png)

![image-20240411152138242](assets\image-20240411152138242.png)

### Block placement

当前策略（可用自定义策略替换）

- One replica on local node 

- 2nd and 3rd replica on two nodes of same *remote* rack 

- Additional replicas are randomly placed

一旦选择了复制位置，就建立一条管道

![image-20240411152343072](assets\image-20240411152343072.png)

### 文件读取

![image-20240411152030837](assets\image-20240411152030837.png)

### 文件写入

![image-20240411152158878](assets\image-20240411152158878.png)



## 错误处理

### 心跳包heartbeat

### Replication engine

upon detecting a DataNode failure

### Data corrections

checksum

### NameNode failure

单点故障

解决方法：Add a **secondary NameNode**

#### Secondary NameNode

- Not Standby/Backup NameNode

  - only for checkpointing

- Copies NameNode’s FSImage & Transaction Log 

- Merges them to a new FSImage 

- Uploads new FSImage to the NameNode and purges 

  Transaction Log

## Limitations

Low-latency data access

Lots of small files 