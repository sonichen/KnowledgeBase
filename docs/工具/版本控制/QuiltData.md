---
title: Quilt Data
date: 2023-08-19 23:15:10
permalink: /pages/3d3613/
---

## 简介

Quilt Data是一个**数据版本控制**和**数据包管理**的工具和平台。它的目标是帮助用户有效地管理、版本控制和共享数据集。

## 功能特性

- Quilt Data允许用户将数据集打包为可重复和可共享的数据包。这些数据包可以包含各种类型的数据，包括结构化数据、图像、文本等。用户可以使用Quilt Data的命令行界面或Python API将数据包上传到Quilt Data平台上的数据仓库中。一旦数据包被上传到Quilt Data平台，用户可以通过版本控制系统对其进行管理和追踪。
- Quilt Data使用数据哈希算法来跟踪数据包的更改，并确保数据的一致性和可追溯性。
- Quilt Data还提供了一个Web界面，用户可以通过该界面浏览和搜索（支持SQL，ElasticSearch）数据包，查看数据包的元数据和版本历史，并与团队成员共享数据包。
- Quilt 数据包统一了数据和元数据。Quilt 数据包是可复现、可发现和可信任的数据集，存储在 Blob 存储中。数据包清单包括元数据和主要数据的物理键。所有数据包的元数据和数据都存储在S3 存储桶中。一部分数据包级别的元数据和 S3 对象内容被发送到由 Quilt 管理的 ElasticSearch 集群中。所有 Quilt 数据包清单都可以通过 AWS Athena 使用 SQL 进行访问。

## 工作设计

### Quilt Package

Quilt Data 将数据集表示为数据包（package）。package包括一个用于唯一标识包内容的哈希，以及一个数据清单。

清单被序列化为一个包含条目的文件，清单条目是以下形式的元组：(LOGICAL_KEY, PHYSICAL_KEYS, HASH, METADATA)

  LOGICAL_KEY逻辑键是用户可见的友好名称，比如 “README.md”。

  PHYSICAL_KEYS物理键是指磁盘上的字节或S3中的字节的完全限定路径。

  Hash哈希是物理键内容的摘要，通常是 SHA-256。

  METADATA元数据是一个字典，可以包含用户定义的元数据键，如边界框、标签或溯源信息（例如，{"algorithm_version": "4.4.1"} 表示给定文件的创建方式）。

例子

```json
  {
    "logical_key": "annotations/captions_train2017.json",
    "physical_keys": [
      "s3://quilt-ml-data/data/raw/annotations/captions_train2017.json?versionId=UtzkAN8FP4irtroeN9bfYP1yKzX7ko3G"
    ],
    "size": 91865115,
    "hash": {
      "type": "SHA256",
      "value": "4b62086319480e0739ef390d04084515defb9c213ff13605a036061e33314317"
    },
    "meta": {}
  }
```

数据包清单存储在注册表中。Quilt 支持本地磁盘和 Amazon S3 存储桶作为注册表。注册表既可以存储清单，也可以存储主要数据。

 

### 版本控制  

存储桶就是分支。在 Quilt 中，S3 存储桶类似于 git 中的分支。每个存储桶都是一个独立的注册表，用于存储一个或多个数据包。随着数据和模式的改进，可以将一个数据包推广到新的存储桶，表示其数据质量提高。

Quilt版本控制与S3对象版本控制有何关联？ Quilt包是在S3对象版本控制之上的一层抽象。对象版本控制跟踪对单个文件的更改，而Quilt包引用了一组文件，并为该组文件分配了一个唯一的版本。 强烈建议在将Quilt包推送到S3存储桶时启用对象版本控制。对象版本控制确保跟踪每个对象的变更，并提供一定的防止删除的保护。

## 工作流程

 

## 优缺点

QUILT的优点：

- 允许轻松进行数据版本控制。
- 其Python接口使得将数据版本控制集成到机器学习流水线代码中变得简单。
- 它与Amazon S3存储服务紧密集成，因此在上传数据时，您的数据将保持完全安全！

QUILT的缺点：

- 它是一个相对较新的工具，不像其他一些数据版本控制工具（如DVC）那样受欢迎，因此关于如何使用它的文档有限，并且在线资源相对较少，如果遇到问题，可能无法找到太多帮助。
- 它要求您拥有AWS账户（AWS S3会收取存储大量数据的费用）。
- Python接口并未完全开发完善，某些功能不够完美。例如，当您推送一个新包时，有时候它不会更新包的哈希值，除非您清除本地缓存，这可能会变得相当繁琐。

## Reference

Quilt Data. (n.d.). Quilt Documentation. Retrieved from https://docs.quiltdata.com
