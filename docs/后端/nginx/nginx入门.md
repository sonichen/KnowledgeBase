## 引用

https://www.kuangstudy.com/bbs/1353634800149213186



note：

架构：没有什么是加一层解决不了的问题

## 问题产生

几个项目启动在不同的服务器上，用户要访问，就需要增加一个代理服务器了，通过代理服务器来帮我们转发和处理请求。（一个代理服务器来转发和控制其他服务器的请求）

我们需要加一层，进行反向代理

![image-20231013120749380](assets\image-20231013120749380.png)

这就是nginx

## 什么是Nginx？

Nginx (engine x) 是一个高性能的HTTP和反向代理web服务器，同时也提供了IMAP/POP3/SMTP服务。

其特点是占有内存少，并发能力强，事实上nginx的并发能力在同类型的网页服务器中表现较好

> 高性能：响应更快，并发更高
>
> 反向代理：转发和控制其他服务器的请求



## Nginx作用？

Http代理，反向代理：作为web服务器最常用的功能之一，尤其是反向代理。

什么是正向代理什么是反向代理？

 

正向代理帮助客户端请求数据，反向帮助服务端请求数据

正向代理，比如打游戏，挂VPN

![image-20231013121307549](assets\image-20231013121307549.png)

反向代理，比如，很多人每天访问百度

![image-20231013121315626](assets\image-20231013121315626.png)



Nginx提供的**负载均衡**策略有2种：内置策略和扩展策略。内置策略为轮询，加权轮询，Ip hash。

轮询

![image-20231013121459382](assets\image-20231013121459382.png)



加权轮询

工作会分给能力较强的服务器

 ![image-20231013121529260](assets\image-20231013121529260.png)



iphash对客户端请求的ip进行hash操作，然后根据hash结果将同一个客户端ip的请求分发给同一台服务器进行处理，可以解决session不共享的问题。

![image-20231013121552957](assets\image-20231013121552957.png)

动静分离，在我们的软件开发中，有些请求是需要后台处理的，有些请求是不需要经过后台处理的（如：css、html、jpg、js等等文件），这些不需要经过后台处理的文件称为静态文件。让动态网站里的动态网页根据一定规则把不变的资源和经常变的资源区分开来，动静资源做好了拆分以后，我们就可以根据静态资源的特点将其做缓存操作。提高资源响应的速度。

![image-20231013121613070](assets\image-20231013121613070.png)

## Nginx的安装

Windows安装

**1、下载nginx**

http://nginx.org/en/download.html 下载稳定版本。
以nginx/Windows-1.16.1为例，直接下载 nginx-1.16.1.zip。

**2、启动nginx**

打开cmd命令窗口，切换到nginx解压目录下，输入命令 `nginx.exe` ，回车即可

**3、检查nginx是否启动成功**

直接在浏览器地址栏输入网址 http://localhost:80 回车，出现以下页面说明启动成功！

**4、配置监听**

nginx的配置文件是conf目录下的nginx.conf，默认配置的nginx监听的端口为80，如果80端口被占用可以修改为未被占用的端口即可。

![img](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2021/01/25/kuangstudyf23105c4-b0b2-4e22-a1bf-b8098f40c144.png)

当我们修改了nginx的配置文件nginx.conf 时，不需要关闭nginx后重新启动nginx，只需要执行命令 `nginx -s reload` 即可让改动生效

**5、关闭nginx**

如果使用cmd命令窗口启动nginx， 关闭cmd窗口是不能结束nginx进程的，可使用两种方法关闭nginx

(1)输入nginx命令  `nginx -s stop`(快速停止nginx)  或  `nginx -s quit`(完整有序的停止nginx)

(2)使用taskkill   `taskkill /f /t /im nginx.exe`

```
taskkill是用来终止进程的，/f是强制终止 ./t终止指定的进程和任何由此启动的子进程。/im示指定的进程名称 .
```

linux下安装



## nginx常用命令

```
cd /usr/local/nginx/sbin/
./nginx  启动
./nginx -s stop  停止
./nginx -s quit  安全退出
./nginx -s reload  重新加载配置文件
ps aux|grep nginx  查看nginx进程
```



## 实战

在1235和1236端口跑一样的项目

目标：

现在启动了两个项目

有一个用户要访问项目，但是不能一会1235一会1236，所以加一层代理，用nginx加一层代理

让nginx帮我转发请求

![image-20231013152602307](assets\image-20231013152602307.png)



nginx.conf文件配置

```
# 全局配置

# 监听事件配置
events {
    worker_connections  1024;
}


http {
	# http全局配置
	upstream xxx{
		# 负载均衡配置
	}
   
	# 配置server服务
	
    server {
        listen       80;
        server_name  localhost;
		# 代理
		location /{
			// xxx    128.xxx
		}
		// www.kuangstudy.com/admin
		location /admin{
			// xxx      14
		}
    }
	
	server {
        listen       443;
        server_name  localhost;
		# 代理
		
		location /{
			// xxx
		}
    }

    # another virtual host using mix of IP-, name-, and port-based configuration
    #
    #server {
    #    listen       8000;
    #    listen       somename:8080;
    #    server_name  somename  alias  another.alias;

    #    location / {
    #        root   html;
    #        index  index.html index.htm;
    #    }
    #}


    # HTTPS server配置
    #
    #server {
    #    listen       443 ssl;
    #    server_name  localhost;
    #}

}
```



我们想通过80端口访问1235和1236









访问看看

先重新启动nginx

```
@cyj MINGW64 /d/software/DevelopTools/nginx-1.24.0/nginx-1.24.0
$ ./nginx -s reload
nginx: [error] OpenEvent("Global\ngx_reload_8316") failed (2: The system cannot find the file specified)
```



可能是nginx没有启动

```
@cyj MINGW64 /d/software/DevelopTools/nginx-1.24.0/nginx-1.24.0
$ ./nginx
```

重新加载

```
./nginx -s reload
```

访问80，成功

可以看到在根据权重轮询

![image-20231013172141051](assets\image-20231013172141051.png)



![image-20231013172408765](assets\image-20231013172408765.png)

补充：

动静分离

![image-20231013172425070](assets\image-20231013172425070.png)