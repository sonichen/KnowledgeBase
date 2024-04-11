## GFS是什么

The Google File System

Google文件系统（英语：Google File System，缩写为GFS或GoogleFS），**一种专有分布式文件系统**

一个建立在高度不可靠的硬件之上的高度可靠的存储系统



## 适用场景

- 成千上万计算机
- 分布式
- 容错性强
- 超大文件（huge，not many)
- 写一次，读取多次
  - 改变通过appending
  - once written, files are typically only read
  - 批处理，流读取，随机读取
- I/O带宽比延迟更重要，适用于批处理和日志分析





## 工作原理

### 分块存储

Large chunk size: 64 MB 

为什么large chunks？

- minimizes the cost of disk seeks 
- pushes up file transfer rate to the disk transfer rate

### 通过复制实现可靠性

Each chunk replicated across 3+ chunkservers 

- 一次复制在同一个rack
- 另外两次复制存在不同的rack

如图

![image-20240411144342268](assets\image-20240411144342268.png)

### Single master to coordinate access

metadata元数据会记录文件信息，*filename, permissions, **chunk index**, folder hierarchy, etc*

data存在chunkservers

### Add record append operations 

Support concurrent appends

## 整体架构

### 设计1-Single master Multiple chunkservers

![image-20240411144618636](assets\image-20240411144618636.png)

client向GFS master发送要查询的文件名和chunk index

GFS master返回chunk handle和locations给client

client根据locations等信息找到GFS chunk server，发送chunk handle和range

GFS chunk server返回client chunk data

### 存在的问题是什么

单点故障

Scalability bottleneck：如果overloaded怎么办

![image-20240411144948794](assets\image-20240411144948794.png)

### 解决方案

单点故障--》增加shadow master

Scalability bottleneck--》master can be overloaded

- 最小化master的参与来解决scalability issue
- 永远不要将数据移动，只用于大块大小的元数据
- 最小化查找/索引时间块租赁
- master权限委托给数据突变中的primary 

#### Metadata

三种metadata，存在memory

- fine and chunk namespaces
- 映射，mappings from files to chunks (each chunk has a unique ID) 
- chunk 副本的locations

前两种类型是通过操作日志进行持久化的

Chunk replica locations learned by polling chunkservers at startup 

Chunkserver is final arbiter of what chunks it holds

#### Master’s responsibilities

- metadata存储
- namespace管理和locking
- 周期性地检查chunkserver-give instructions, collect state, track cluster health 
- chunk的插件，复制和rebalancing
- 垃圾回收
- stale replica delection

#### Chunkserver

- 在本地磁盘上存储64 MB的文件块，每个文件块都有version number和checksum
- 读/写请求指定chunk handle和byte range
- Chunks replicated 
- no file data caching

### Client

-  control *(metadata)* requests to master 
- data requests directly to chunkservers
- caching metadata

## 文件读写

### 读取文件

![image-20240411145903348](assets\image-20240411145903348.png)

应用程序产生了读取请求

GFS客户端翻译请求并将其发送到主服务器

主服务器使用chunk handle和replica locations进行响应

客户端选择“最近”的位置并发送请求

块服务器发送请求的数据到客户端

客户端将数据转发给应用程序

### 写入文件

![image-20240411145945096](assets\image-20240411145945096.png)

1. 应用程序发起请求
2. GFS客户端翻译请求并将其发送给master
3. Master使用chunk handle和replca locations响应
4. 客户端将写数据推送到所有位置。数据是
  存储在chunkserver的内部buffer

![image-20240411150417228](assets\image-20240411150417228.png)



5. Client sends write command to primary
6. Primary决定数据突变的序列顺序并按此顺序写入数据块

7. Primary向secondary和告诉它们执行写操作。

![image-20240411150455928](assets\image-20240411150455928.png)

8. 次要服务器响应主要服务器

9. Primary响应客户机

![image-20240411150507079](assets\image-20240411150507079.png)

## 容错性

### 失败了怎么办

- rewrite
- 块不是按位相同的（Use checksum to skip inconsistent file regions）
- master检测chunk server的“heartbeat”
- master减少dead chunk server上所有块的副本计数主复制其他地方丢失的副本

### 特点

**High availability **

Data integrity

## 

## Limitations

Assumes write-once, read-many workloads 

Assumes a modest number of large files: small files can create hot spots on 

chunkservers if many clients accessing the same file









