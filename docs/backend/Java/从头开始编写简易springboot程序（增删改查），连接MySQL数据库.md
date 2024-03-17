# 1.创建项目
选择创建项目
![在这里插入图片描述](https://img-blog.csdnimg.cn/f55973a09ce948e3bce1e09b4f0bb96c.png)![在这里插入图片描述](https://img-blog.csdnimg.cn/46ccb6244d3a4985b8ef59f3724a215a.png)![在这里插入图片描述](https://img-blog.csdnimg.cn/c86826720ad34f479a6e8e946ff23c71.png)
可以删除没用的文件，简化目录
![在这里插入图片描述](https://img-blog.csdnimg.cn/a13a1580e0df439aa661d9ac293f217e.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/6187f6489d4a47c59ef24609f510d891.png)
可能会出现JDK未定义问题
![在这里插入图片描述](https://img-blog.csdnimg.cn/be01ebdf562b458e803b78fa83e72634.png)根据提示选择JDK即可

检查配置
![在这里插入图片描述](https://img-blog.csdnimg.cn/1ffdca4b05854a95a902c081908b2a1a.png)
检查maven设置
![在这里插入图片描述](https://img-blog.csdnimg.cn/83aebc672311419a9739506859a906f1.png)
检查java版本设置
![在这里插入图片描述](https://img-blog.csdnimg.cn/aa059f683ce743a8bbe04f550a523d82.png)
![在这里插入图片描述](https://img-blog.csdnimg.cn/8ad66c2e50c2414f89a273118f8e9579.png)
![在这里插入图片描述](https://img-blog.csdnimg.cn/0e1e12da62414a63a7fbd1fe06bd484f.png)
右键运行
![在这里插入图片描述](https://img-blog.csdnimg.cn/44e845ef9f2a49f4971b92fb4e0216e9.png)![在这里插入图片描述](https://img-blog.csdnimg.cn/27100be312b64657aedcdec7c6438c29.png)
运行成功

# 2.编写简单的增删改查
设计数据库

```sql
/*
SQLyog Ultimate v12.09 (64 bit)
MySQL - 8.0.32 : Database - shop
*********************************************************************
*/

/*!40101 SET NAMES utf8 */;

/*!40101 SET SQL_MODE=''*/;

/*!40014 SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 */;
/*!40014 SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 */;
/*!40101 SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' */;
/*!40111 SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0 */;
CREATE DATABASE /*!32312 IF NOT EXISTS*/`shop` /*!40100 DEFAULT CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci */ /*!80016 DEFAULT ENCRYPTION='N' */;

USE `shop`;

/*Table structure for table `store` */

DROP TABLE IF EXISTS `store`;

CREATE TABLE `store` (
  `id` bigint NOT NULL AUTO_INCREMENT COMMENT 'id',
  `store_name` varchar(50) DEFAULT NULL COMMENT '店铺名称',
  `desc` text COMMENT '描述',
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

/*Data for the table `store` */

/*!40101 SET SQL_MODE=@OLD_SQL_MODE */;
/*!40014 SET FOREIGN_KEY_CHECKS=@OLD_FOREIGN_KEY_CHECKS */;
/*!40014 SET UNIQUE_CHECKS=@OLD_UNIQUE_CHECKS */;
/*!40111 SET SQL_NOTES=@OLD_SQL_NOTES */;

```

![在这里插入图片描述](https://img-blog.csdnimg.cn/a9cc4601f3ad4350abbf5638e4583597.png)

项目目录结构
![在这里插入图片描述](https://img-blog.csdnimg.cn/6eec02ad6eac43bf800ca8646c5c3a3a.png)
(1)构建实体类

```java
package com.cyj.shopmanagement.pojo;

import com.baomidou.mybatisplus.annotation.IdType;
import com.baomidou.mybatisplus.annotation.Version;
import com.baomidou.mybatisplus.annotation.TableId;
import java.io.Serializable;
import io.swagger.annotations.ApiModel;
import io.swagger.annotations.ApiModelProperty;
import lombok.Data;
import lombok.EqualsAndHashCode;
import lombok.experimental.Accessors;

/**
 * <p>
 * 
 * </p>
 *
 * @author cyj
 * @since 2023-02-05
 */
@Data
@EqualsAndHashCode(callSuper = false)
@Accessors(chain = true)
@ApiModel(value="Store对象", description="")
public class Store implements Serializable {

    private static final long serialVersionUID = 1L;

    @ApiModelProperty(value = "id")
    @TableId(value = "id", type = IdType.AUTO)
    private Long id;

    @ApiModelProperty(value = "店铺名称")
    private String storeName;

    @ApiModelProperty(value = "描述")
    private String desc;


}

```
(2)创建mapper

```java
package com.cyj.shopmanagement.mapper;

import com.cyj.shopmanagement.pojo.Store;
import com.baomidou.mybatisplus.core.mapper.BaseMapper;
import org.springframework.stereotype.Repository;

/**
 * <p>
 *  Mapper 接口
 * </p>
 *
 * @author cyj
 * @since 2023-02-05
 */
@Repository
public interface StoreMapper extends BaseMapper<Store> {

}

```
没写完




