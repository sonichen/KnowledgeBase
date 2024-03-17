## 注册Github

到[Github](https://github.com/)根据提示注册一个账号

![image-20240317125702956](assets\image-20240317125702956.png)

通过邮箱验证账号

## 创建仓库

右上角创建仓库

![image-20240317125941390](assets\image-20240317125941390.png)



这里创建一个和账号同名的作为demo

![image-20240317130114418](assets\image-20240317130114418.png)

创建成功

![image-20240317130205804](assets\image-20240317130205804.png)

## 下载安装git

[下载地址](https://git-scm.com/downloads)

[window图文教程](https://zhuanlan.zhihu.com/p/443527549)

## 设置用户信息

```
git config --global user.name"xxx"
git config --global user.email"xxx@xx.xxx"
```



## 第一次提交

创建一个文件，写点东西。

准备配置git，提交这个文件到github。

初始化

```
git init
```

添加

```
#工作区-->暂存区
git add
 
#将工作区所有添加到暂存区
git add .
```

提交

```
#暂存区-->仓库
git commit
 
#将暂存区的提交并填写提交总结
git commit -m "first commit"
```

签名提交