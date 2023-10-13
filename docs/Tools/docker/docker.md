## 引用

[1] https://docker.easydoc.net/doc/81170005/cCewZWoN/lTKfePfP

## Docker 简介和安装

### Docker 是什么

Docker 是一个应用打包、分发、部署的工具【一个轻量的虚拟机，它只虚拟你软件需要的运行环境，多余的一点都不要】

### 打包、分发、部署

**打包**：就是把你软件运行所需的依赖、第三方库、软件打包到一起，变成一个安装包
**分发**：你可以把你打包好的“安装包”上传到一个镜像仓库，其他人可以非常方便的获取和安装
**部署**：拿着“安装包”就可以一个命令运行起来你的应用，自动模拟出一摸一样的运行环境，不管是在 Windows/Mac/Linux。

### 安装

[最详细的ubuntu 安装 docker教程](https://blog.csdn.net/Tester_muller/article/details/131440306) (推)

[桌面版](https://www.docker.com/products/docker-desktop/)

[服务器](https://docs.docker.com/engine/install/#server)

##  Docker 快速安装软件

演示dockers安装redis和wordpress

到[docker](https://redis.io/)官网搜索要安装的软件

#### Redis

开发的时候不要安装latest，要安装stable

```
docker run -d -p 6379:6379 --name redis redis:latest
```



```shell
soni@soni-virtual-machine:~/Desktop$ docker run -d -p 6379:6379 --name redis redis:latest
Unable to find image 'redis:latest' locally
latest: Pulling from library/redis
a378f10b3218: Pull complete 
3c75410c1f8b: Pull complete 
667874757cc1: Pull complete 
7150b93d249d: Pull complete 
ed7c83735e28: Pull complete 
4f4fb700ef54: Pull complete 
3fa899a007ab: Pull complete 
Digest: sha256:cacfe1d34dad1b12708dedff1d20b3bb448b87df50ee770010e56eff0782c0cb
Status: Downloaded newer image for redis:latest
be5bccf204e73d097c8e86bfc8b2436d2ddc00bc5e5f14faa11bfd5f290ceadf

soni@soni-virtual-machine:~/Desktop$ docker run --name some-redis -d redis
e7552f6acbc689342b0b0ed4a82f48c098e06790701131dff7a924e62332e07b

soni@soni-virtual-machine:~/Desktop$ docker ps 
CONTAINER ID   IMAGE          COMMAND                  CREATED         STATUS         PORTS                                       NAMES
e7552f6acbc6   redis          "docker-entrypoint.s…"   3 minutes ago   Up 3 minutes   6379/tcp                                    some-redis
be5bccf204e7   redis:latest   "docker-entrypoint.s…"   5 minutes ago   Up 5 minutes   0.0.0.0:6379->6379/tcp, :::6379->6379/tcp   redis

soni@soni-virtual-machine:~/Desktop$ docker exec -it redis /bin/bash

root@be5bccf204e7:/data# redis-cli
127.0.0.1:6379> set test 1
OK
127.0.0.1:6379> 

```

#### wordpress

https://blog.csdn.net/weixin_43576565/article/details/131193855



## 制作自己的镜像

### 为自己的 Web 项目构建镜像

示例项目代码：https://github.com/gzyunke/test-docker
这是一个 Nodejs + Koa2 写的 Web 项目，提供了简单的两个演示页面。
软件依赖：[nodejs](https://nodejs.org/zh-cn/)
项目依赖库：koa、log4js、koa-router

### 编写 Dockerfile

```
FROM node:11
MAINTAINER easydoc.net

# 复制代码
ADD . /app

# 设置容器启动后的默认运行目录
WORKDIR /app

# 运行命令，安装依赖
# RUN 命令可以有多个，但是可以用 && 连接多个命令来减少层级。
# 例如 RUN npm install && cd /app && mkdir logs
RUN npm install --registry=https://registry.npm.taobao.org

# CMD 指令只能一个，是容器启动后执行的命令，算是程序的入口。
# 如果还需要运行其他命令可以用 && 连接，也可以写成一个shell脚本去执行。
# 例如 CMD cd /app && ./start.sh
CMD node app.js
```

[Dockerfile文档](https://docs.docker.com/engine/reference/builder/#run)

> 实用技巧：
> 如果你写 Dockerfile 时经常遇到一些运行错误，依赖错误等，你可以直接运行一个依赖的底，然后进入终端进行配置环境，成功后再把做过的步骤命令写道 Dockerfile 文件中，这样编写调试会快很多。
> 例如上面的底是`node:11`，我们可以运行`docker run -it -d node:11 bash`，跑起来后进入容器终端配置依赖的软件，然后尝试跑起来自己的软件，最后把所有做过的步骤写入到 Dockerfile 就好了。
> 掌握好这个技巧，你的 Dockerfile 文件编写起来就非常的得心应手了。

### Build 为镜像（安装包）和运行

编译 `docker build -t test:v1 .`

> `-t` 设置镜像名字和版本号
> 命令参考：https://docs.docker.com/engine/reference/commandline/build/

查看镜像列表

```shell
soni@soni-virtual-machine:~/Desktop/workplace/test-docker$ docker images
REPOSITORY    TAG       IMAGE ID       CREATED         SIZE
test          v1        b2ebfe1e9dad   3 minutes ago   913MB
redis         latest    5b0542ad1e77   5 weeks ago     138MB
hello-world   latest    9c7a54a9a43c   5 months ago    13.3kB

```

已经出现了test镜像



运行 `docker run -p 8080:8080 --name test-hello test:v1`

> `-p` 映射容器内端口到宿主机
> `--name` 容器名字
> `-d` 后台运行
> 命令参考文档：https://docs.docker.com/engine/reference/run/

```shell
soni@soni-virtual-machine:~/Desktop/workplace/test-docker$ docker run -p 8080:8080 --name test-hello test:v1
[2023-10-13T03:03:06.910] [INFO] app - Server started successfully and listened on 8080
http://localhost:8080

```

成功

### 更多相关命令

`docker ps` 查看当前运行中的容器
`docker images` 查看镜像列表
`docker rm container-id` 删除指定 id 的容器
`docker stop/start container-id` 停止/启动指定 id 的容器
`docker rmi image-id` 删除指定 id 的镜像
`docker volume ls` 查看 volume 列表
`docker network ls` 查看网络列表



## 目录挂载

### 现存问题

- 使用 Docker 运行后，我们**改了项目代码不会立刻生效，需要重新`build`和`run`，很是麻烦**。
- **容器里面产生的数据**，例如 log 文件，**数据库备份文件，容器删除后就丢失了**。

**目录挂载解决以上问题**



### 几种挂载方式

- `bind mount` 直接把宿主机目录映射到容器内，适合挂代码目录和配置文件。可挂到多个容器上
- `volume` 由容器创建和管理，创建在宿主机，所以删除容器不会丢失，官方推荐，更高效，Linux 文件系统，适合存储数据库数据。可挂到多个容器上
- `tmpfs mount` 适合存储临时文件，存宿主机内存中。不可多容器共享。



### 挂载演示

```
bind mount` 方式用绝对路径 `-v D:/code:/app
volume` 方式，只需要一个名字 `-v db-data:/app
```

示例：
`docker run -p 8080:8080 --name test-hello -v D:/code:/app -d test:v1`

> 注意！
> 因为挂载后，容器里的代码就会替换为你本机的代码了，如果你代码目录没有`node_modules`目录，你需要在代码目录执行下`npm install --registry=https://registry.npm.taobao.org`确保依赖库都已经安装，否则可能会提示“Error: Cannot find module ‘koa’”
> 如果你的电脑没有安装 [nodejs](https://nodejs.org/en/)，你需要安装一下才能执行上面的命令。



## 多容器通信



项目往往都不是独立运行的，需要数据库、缓存这些东西配合运作。
把前面的 Web 项目增加一个 Redis 依赖，多跑一个 Redis 容器，演示如何多容器之间的通信。



### 创建虚拟网络

要想多容器之间互通，从 Web 容器访问 Redis 容器，我们只需要把他们放到同个网络中就可以了。

文档参考：https://docs.docker.com/engine/reference/commandline/network/

### 演示

```shell
soni@soni-virtual-machine:~/Desktop/workplace$ docker images
REPOSITORY    TAG       IMAGE ID       CREATED          SIZE
test          v1        b2ebfe1e9dad   20 minutes ago   913MB
redis         latest    5b0542ad1e77   5 weeks ago      138MB
hello-world   latest    9c7a54a9a43c   5 months ago     13.3kB

```



##### 创建一个名为`test-net`的网络：

```shell
docker network create test-net
```

```
soni@soni-virtual-machine:~/Desktop/workplace$ docker network create test-net
c6305e648668f71b39d76aca4f8e467fe6f5587a71c63987ed2f095abd27d97a

```



##### 在 `test-net` 网络中运行redis，别名`redis`

```
docker run -d --name redis --network test-net --network-alias redis redis:latest
```

容器重合问题，删除容器

```shell
soni@soni-virtual-machine:~/Desktop/workplace$ docker run -d --name redis --network test-net --network-alias redis redis:latest
docker: Error response from daemon: Conflict. The container name "/redis" is already in use by container "be5bccf204e73d097c8e86bfc8b2436d2ddc00bc5e5f14faa11bfd5f290ceadf". You have to remove (or rename) that container to be able to reuse that name.
See 'docker run --help'.

soni@soni-virtual-machine:~/Desktop/workplace$ docker rm -f redis 
redis


soni@soni-virtual-machine:~/Desktop/workplace$ docker run -d --name redis --network test-net --network-alias redis redis:latest
33f597f026487a79097c946e342b658ed79c809c1184c4a57c95e9a9e52ec477
soni@soni-virtual-machine:~/Desktop/workplace$ 


```



##### 修改代码中访问`redis`的地址为网络别名

app.js

![image.png](https://sjwx.easydoc.xyz/46901064/files/kv98rfvb.png)

##### 运行 Web 项目，使用同个网络

```
docker run -p 8081:8080 --name test -v /home/soni/Desktop/workplace/app --network test-net -d test:v1

```

遇到问题

解决：换端口，删除test

```shell
soni@soni-virtual-machine:~/Desktop/workplace/test-docker$ docker run -p 8080:8080 --name test -v /home/soni/Desktop/workplace/app --network test-net -d test:v1
9dff5ff4edcdb87d9092fd34dccb64a2287af164c041a2c5a94dd8320a5dfb31
docker: Error response from daemon: driver failed programming external connectivity on endpoint test (433a295b88d2ec22b204e4163b36f4d67fd1cedf9c09484bd13ce9625d5276b8): Bind for 0.0.0.0:8080 failed: port is already allocated.
soni@soni-virtual-machine:~/Desktop/workplace/test-docker$ docker run -p 8081:8080 --name test -v /home/soni/Desktop/workplace/app --network test-net -d test:v1
docker: Error response from daemon: Conflict. The container name "/test" is already in use by container "9dff5ff4edcdb87d9092fd34dccb64a2287af164c041a2c5a94dd8320a5dfb31". You have to remove (or rename) that container to be able to reuse that name.
See 'docker run --help'.
soni@soni-virtual-machine:~/Desktop/workplace/test-docker$ docker rm -f test
test
soni@soni-virtual-machine:~/Desktop/workplace/test-docker$ docker run -p 8081:8080 --name test -v /home/soni/Desktop/workplace/app --network test-net -d test:v1
fae4812078d2f332085d267af4e1c752f45baaeda53666027dc7205636cf0ec4

```



##### 查看数据

`http://localhost:8081/redis`
容器终端查看数据是否一致





## Docker-Compose

### 现存问题

在上节，我们运行了两个容器：Web 项目 + Redis
如果项目依赖更多的第三方软件，我们需要管理的容器就更加多，每个都要单独配置运行，指定网络。
**使用 docker-compose 把项目的多个服务集合到一起，一键运行**。



### 安装

[docker-compose教程（安装，使用, 快速入门](https://blog.csdn.net/pushiqiang/article/details/78682323)

从[github](https://so.csdn.net/so/search?q=github&spm=1001.2101.3001.7020)上下载docker-compose二进制文件安装

```
sudo curl -L https://github.com/docker/compose/releases/download/v2.21.0/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
```

添加可执行权限

```
sudo chmod +x /usr/local/bin/docker-compose
```

测试安装结果

```
 docker-compose --version
```



### 编写脚本

要把项目依赖的多个服务集合到一起，我们需要编写一个`docker-compose.yml`文件，描述依赖哪些服务
参考文档：https://docs.docker.com/compose/

services: 标识依赖哪些项目

在这里，我们依赖app和redis

```
version: "3.7"

services:
  app:
    build: ./
    ports:
      - 80:8080
    volumes:
      - ./:/app
    environment:
      - TZ=Asia/Shanghai
  redis:
    image: redis:5.0.13
    volumes:
      - redis:/data
    environment:
      - TZ=Asia/Shanghai

volumes:
  redis:
```

> 容器默认时间不是北京时间，增加 TZ=Asia/Shanghai 可以改为北京时间

### 跑起来

在`docker-compose.yml` 文件所在目录，执行：`docker-compose up`就可以跑起来了。



## 发布和部署

[文章](https://docker.easydoc.net/doc/81170005/cCewZWoN/UlEl1cy7)

## 备份和迁移数据

[文章](https://docker.easydoc.net/doc/81170005/cCewZWoN/XQEqNjiu)