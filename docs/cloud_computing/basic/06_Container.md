# Container Virtualization

## 为什么需要container？

Configure once, run anything

## VM vs Contrainers

![image-20240411181010660](assets\image-20240411181010660.png)

## 容器实现 

利用 Linux 内核机制 

- namespace：每个进程资源隔离 
- cgroups：管理进程组的资源 
-  seccomp：限制可用系统调用 
- capabilities：限制可用特权 
- CRIU：检查点/恢复（带有内核支持）

## What names must be virtualized?

- Process IDs 
  - 容器内部的 top 命令仅显示其中运行的进程 
  - 容器外部的 top 命令可能显示容器内的进程，但具有不同的进程 ID 
- File names 
  - 容器内的进程可能对挂载的文件系统有有限的不同视图 
  - 文件名可能解析为不同的名称 - 容器外的一些文件名可能被删除 
- User names 
  - 容器可能具有不同角色的不同用户 
  - 容器内的 root 用户不应与容器外的 root 用户相同 
- Host name and IP addresses 
  - 容器内的进程在执行网络操作时可能使用不同的主机名和 IP 地址

## Docker

![image-20240411181632043](assets\image-20240411181632043.png)

 ![image-20240411181648201](assets\image-20240411181648201.png)