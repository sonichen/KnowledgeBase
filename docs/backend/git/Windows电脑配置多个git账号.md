转载：https://blog.csdn.net/q13554515812/article/details/83506172

## 移除全局配置

查看全局配置

```
git config --list
```

![image-20240317113533769](assets\image-20240317113533769.png)

移除全局配置

```
# 移除全局配置账户
git config --global --unset user.name
# 移除全局配置邮箱
git config --global --unset user.email
# 移除全局密码
git config --global --unset user.password
```

检查是否移除成功

```
#查看全局用户名
git config --global user.name
# 查看全局邮箱
git config --global user.email
# 查看全局密码
git config --global user.password
```

## 连接Github

我已经配置了账号1，现在配置账号2，步骤一样的。

### 生成该用户ssh key

```
ssh-keygen -t rsa -C "邮箱"
```

![image-20240317115229696](assets\image-20240317115229696.png)

C:\Users\用户名\\.ssh目录下

![image-20240317115457759](assets\image-20240317115457759.png)

### Github验证

Github页面，Setting->SSH and GPG Keys

把pub内容放进来

![image-20240317115739620](assets\image-20240317115739620.png)

### 测试

测试该用户的SSH密钥是否生效：

```
ssh -T git@github.com -i 文件名字
```

![image-20240317120340864](assets\image-20240317120340864.png)

因为系统默认只读取id_rsa，为了让ssh识别新的私钥，可以使用ssh-agent手动添加私钥：

```
ssh-agent bash
ssh-add ~/.ssh/文件名
```

### 配置config

在.ssh目录下创建一个config件，每个账号配置一个Host节点

```
Host    　　主机别名
HostName　　服务器真实地址
IdentityFile　　私钥文件路径
PreferredAuthentications　　认证方式
User　　用户名
```

```
# 配置user1 
Host user1.github.com
HostName github.com
IdentityFile C:\\Users\\lingh\\.ssh\\id_rsa
PreferredAuthentications publickey
User user1

# 配置user2
Host user2.github.com
HostName github.com
IdentityFile C:\\Users\\lingh\\.ssh\\id_rsa2
PreferredAuthentications publickey
User user2

```

测试是否生效

```
ssh -T git@用户名.github.com
```

![image-20240317121424271](assets\image-20240317121424271.png)

## 项目配置

为各仓库单独配置用户名和邮箱

```
git config user.name "user1"
git config user.email "user1@email.com"
```

如果原先使用HTTPS通信，则需要修改远程仓库地址

```
git remote rm origin
git remote add origin git@user1.github.com:xxx/xxxxx.git
```

