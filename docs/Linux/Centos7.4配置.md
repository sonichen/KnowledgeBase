Reference：

https://blog.csdn.net/qq_39135287/article/details/83993574

## centos下载

官网：https://vault.centos.org

下载链接：[https://vault.centos.org/7.4.1708/isos/x86_64/](https://vault.centos.org/7.4.1708/isos/x86_64/)

下载[CentOS-7-x86_64-DVD-1708.torrent](https://vault.centos.org/7.4.1708/isos/x86_64/CentOS-7-x86_64-DVD-1708.torrent)

![image-20240131123645703](assets\image-20240131123645703.png)

用迅雷或者夸克解压该文件

![image-20240131111502734.png](assets\image-20240131111502734.png)

## 创建虚拟机

用**VMware Workstation Pro**

### 创建虚拟机

![image-20240131124405955](D:\Workplace\github\soni_notes\docs\Linux\assets\image-20240131124405955.png)

经典模式

![image-20240131124424545](D:\Workplace\github\soni_notes\docs\Linux\assets\image-20240131124424545.png)

稍后安装

![image-20240131124452326](D:\Workplace\github\soni_notes\docs\Linux\assets\image-20240131124452326.png)

选择版本

![image-20240131124517518](D:\Workplace\github\soni_notes\docs\Linux\assets\image-20240131124517518.png)

命名，选择存储位置

![image-20240131124654600](D:\Workplace\github\soni_notes\docs\Linux\assets\image-20240131124654600.png)

选择配置

![image-20240131124715385](D:\Workplace\github\soni_notes\docs\Linux\assets\image-20240131124715385.png)

完成

![image-20240131124730049](D:\Workplace\github\soni_notes\docs\Linux\assets\image-20240131124730049.png)

## **编辑虚拟机设置**

![image-20240131124804175](D:\Workplace\github\soni_notes\docs\Linux\assets\image-20240131124804175.png)

使用ISP文件**CentOS-7-x86_64-DVD-1708.iso**

![image-20240131125400170](D:\Workplace\github\soni_notes\docs\Linux\assets\image-20240131125400170.png)

使用默认的网络适配器

![image-20240131125437471](D:\Workplace\github\soni_notes\docs\Linux\assets\image-20240131125437471.png)

可以移除USP控制器，声卡，打印机来留出更多空间

![image-20240131134218873](D:\Workplace\github\soni_notes\docs\Linux\assets\image-20240131134218873.png)

![image-20240131125555896](D:\Workplace\github\soni_notes\docs\Linux\assets\image-20240131125555896.png)

## 开启虚拟机

按下“↑”键，选择Install CentOS 7，最后按下“Enter 键”

![image-20240131134754851](D:\Workplace\github\soni_notes\docs\Linux\assets\image-20240131134754851.png)

![image-20240131134820216](D:\Workplace\github\soni_notes\docs\Linux\assets\image-20240131134820216.png)

### 选择语言英语

![image-20240131125832832](D:\Workplace\github\soni_notes\docs\Linux\assets\image-20240131125832832.png)

### 配置date time

date time为上海，时间设置为电脑同步时间

![image-20240131125921902](D:\Workplace\github\soni_notes\docs\Linux\assets\image-20240131125921902.png)

![image-20240131130010072](D:\Workplace\github\soni_notes\docs\Linux\assets\image-20240131130010072.png)

### 设置软件选择

![image-20240131130118380](D:\Workplace\github\soni_notes\docs\Linux\assets\image-20240131130118380.png)

![image-20240131130050899](D:\Workplace\github\soni_notes\docs\Linux\assets\image-20240131130050899.png)

如果希望安装带有界面的CentOS，请在左边Base Environment中，选择Server with GUI(带图形用户界面的服务器)，默认为Minimal Install (最小安装)，提示：如果安装有界面版本的，在如下的第22步骤中的操作会有所不同 (安装有界面版本的其实用处不大，都是可以通过命令行来设置的)，这里我没有安装有界面版本的

### 设置安装位置

![image-20240131130215034](D:\Workplace\github\soni_notes\docs\Linux\assets\image-20240131130215034.png)

![image-20240131130233466](D:\Workplace\github\soni_notes\docs\Linux\assets\image-20240131130233466.png)

### 更改模式![image-20240131135025896](D:\Workplace\github\soni_notes\docs\Linux\assets\image-20240131135025896.png)

![image-20240131130304089](D:\Workplace\github\soni_notes\docs\Linux\assets\image-20240131130304089.png)

![image-20240131130344629](D:\Workplace\github\soni_notes\docs\Linux\assets\image-20240131130344629.png)

![image-20240131130421762](D:\Workplace\github\soni_notes\docs\Linux\assets\image-20240131130421762.png)

![image-20240131135114545](D:\Workplace\github\soni_notes\docs\Linux\assets\image-20240131135114545.png)

![image-20240131130441997](D:\Workplace\github\soni_notes\docs\Linux\assets\image-20240131130441997.png)

![image-20240131130507546](D:\Workplace\github\soni_notes\docs\Linux\assets\image-20240131130507546.png)

### 安装

![image-20240131130526955](D:\Workplace\github\soni_notes\docs\Linux\assets\image-20240131130526955.png)

### 设置密码

![image-20240131130603935](D:\Workplace\github\soni_notes\docs\Linux\assets\image-20240131130603935.png)

![image-20240131135152057](D:\Workplace\github\soni_notes\docs\Linux\assets\image-20240131135152057.png)

**等待安装完成，然后点击“Reboot”**

![image-20240131131407097](D:\Workplace\github\soni_notes\docs\Linux\assets\image-20240131131407097.png)

## 基本设置

登入虚拟机，默认账号root

![image-20240131131434600](D:\Workplace\github\soni_notes\docs\Linux\assets\image-20240131131434600.png)

### 配置IP地址，网关

#### 查看子网掩码和网关

点击虚拟网络编辑器

![image-20240131131013637](D:\Workplace\github\soni_notes\docs\Linux\assets\image-20240131131013637.png)

![image-20240131131046301](D:\Workplace\github\soni_notes\docs\Linux\assets\image-20240131131046301.png)

可以看到我的vmnet8网络下的子网掩码为255.255.255.0 和 网关为 192.168.68.2

#### 查看主机IP地址

![image-20240131131723377](D:\Workplace\github\soni_notes\docs\Linux\assets\image-20240131131723377.png)

可以看到我的 VMnet8下的IPv4 地址为 192.168.68.1，VMnet8下的IPv4地址与子网IP 和 网关也同处于192.168.68这个网段下，如果VMnet8下的IPv4地址与子网IP 和 网关不同处一个网段下，请修改VMnet8下的IPv4地址与子网IP 和 网关处于同一个网段下，最后一位默认为1即可

在设置虚拟机的IP地址时，需要保证虚拟机的IP地址 与 VMnet8下的IPv4地址处于同一个网段下，即：前面必须是192.168.68，这样虚拟机才能跟我们的本地电脑互相通信，最后一位数不相同即可，但是最后一位不能设置跟我们的子网IP、网关 和 VMnet8下的IPv4地址相同，即最后一位不能设置为0、2 和 1，例如虚拟机的IP地址可以设置为192.168.68.124 或者 192.168.68.168都是可以的

#### 配置

```
cd /etc/sysconfig/network-scripts/    //进入到network-scripts目录下  
 
vi ifcfg-ens32  //编辑配置文件 
 
//修改以下内容
BOOTPROTO=static  //启用静态IP地址
ONBOOT=yes      //开启自动启用网络连接
 
 
//添加以下内容
IPADDR=192.168.68.102    //设置IP地址
NETMASK=255.255.255.0   //子网掩码
GATEWAY=192.168.68.2   //设置网关
```



### **设置DNS地址**   

```
vi /etc/resolv.conf    //编辑 resolv.conf文件
 
nameserver 114.114.114.114   //添加DNS地址
 
 
 
可以添加多个DNS地址，格式为：
nameserver xxx1.xxx1.xxx1.xxx1
nameserver xxx2.xxx2.xxx2.xxx2
 
 
常用的DNS地址:
 
  阿里  223.5.5.5  或者  223.6.6.6
 
  谷歌  8.8.8.8
  
  国内移动、电信和联通通用的DNS  114.114.114.114
```

提示：如果是内网，配置上面的DNS地址有可能是访问不了外网的，在电脑右下角的网络图标中鼠标右键，选择打开"网络和Internet"设置，选择WLAN，然后在点击你连接的网络，查看网络信息

![image-20240131135840324](D:\Workplace\github\soni_notes\docs\Linux\assets\image-20240131135840324.png)

![image-20240131135912221](D:\Workplace\github\soni_notes\docs\Linux\assets\image-20240131135912221.png)





### **重启网络服务**

```
service network restart
```

![image-20240131140936108](D:\Workplace\github\soni_notes\docs\Linux\assets\image-20240131140936108.png)

### ping检查

#### 主机ping虚拟机

```
ping 192.168.68.102

正在 Ping 192.168.68.102 具有 32 字节的数据:
来自 192.168.68.102 的回复: 字节=32 时间<1ms TTL=64
来自 192.168.68.102 的回复: 字节=32 时间<1ms TTL=64
来自 192.168.68.102 的回复: 字节=32 时间<1ms TTL=64
来自 192.168.68.102 的回复: 字节=32 时间<1ms TTL=64

192.168.68.102 的 Ping 统计信息:
    数据包: 已发送 = 4，已接收 = 4，丢失 = 0 (0% 丢失)，
往返行程的估计时间(以毫秒为单位):
    最短 = 0ms，最长 = 0ms，平均 = 0ms
```



#### 虚拟机ping主机

![image-20240131141038274](D:\Workplace\github\soni_notes\docs\Linux\assets\image-20240131141038274.png)

**提示：如果ping不通本地电脑ip，请检查一下本地电脑的防火墙是否关闭**

#### **ping外网**

```java
ping -c3 www.baidu.com
```



### **永久关闭 firewalld防火墙**

```
systemctl stop firewalld.service  // 停止firewalld服务
 
systemctl disable firewalld.service // 开机禁用firewalld服务
 
iptables -L   //列出所有iptables规则
```

![image-20240131141149903](D:\Workplace\github\soni_notes\docs\Linux\assets\image-20240131141149903.png)

### **永久关闭SELinux防火墙**

![image-20240131141234389](D:\Workplace\github\soni_notes\docs\Linux\assets\image-20240131141234389.png)

```
vi /etc/sysconfig/selinux       //编辑selinux文件
 
SELINUX=disabled         //把文件中的SELINUX=enforcing 改成 SELINUX=disabled 即可
 
sestatus    //查看SELinux状态
```

获取当前selinux防火墙的安全策略

```java
sestatus
```

![image-20240131141307482](D:\Workplace\github\soni_notes\docs\Linux\assets\image-20240131141307482.png)

可以看到当前selinux防火墙的安全策略仍为enforcing，配置文件并未生效

 **重启命令“reboot”**

再去查看SELinux防火墙的状态，可以看到已经关闭了



**给/etc/rc.d/rc.local 文件设置 “x”可执行权限，最初设置默认是没有可执行权限的**

```html
chmod +x /etc/rc.d/rc.local     //设置可执行权限
```

**输入“halt”关机命令，关闭虚拟机，并拍摄快照，保存当前配置**

### 拍摄快着

![image-20240131133532158](D:\Workplace\github\soni_notes\docs\Linux\assets\image-20240131133532158.png)