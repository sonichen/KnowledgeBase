更新，下载高版本的Maven在后续程序运行中不匹配报错，下载3.6.3为宜

下载地址：[https://archive.apache.org/dist/maven/maven-3/3.6.3/binaries/](https://archive.apache.org/dist/maven/maven-3/3.6.3/binaries/)
![\[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-odqKNkew-1675574388734)(D:\Note\Note\学习笔记\开发\Java后端\Maven\assets\image-20230203151204246.png)\]](https://img-blog.csdnimg.cn/00584aceef83478fbe44799995b8ddbb.png)


配置步骤同下

## 1.下载安装包
下载网址：https://maven.apache.org/download.cgi
下载最新的maven
![\[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-pV9XAAEf-1675574388734)(D:\Note\Note\学习笔记\开发\Java后端\Maven\assets\image-20230203134801755.png)\]](https://img-blog.csdnimg.cn/ff2434dd8b1247b690ee3e68611a7a15.png)

下载后解压
 ![在这里插入图片描述](https://img-blog.csdnimg.cn/c8c56e3ce29d4d0a9e2934cbae157a43.png)




## 2.配置环境变量

系统变量
![在这里插入图片描述](https://img-blog.csdnimg.cn/0a249b2b22014f958e8d9dc7bb4178ef.png)


path中添加

```
%MAVEN_HOME%\bin
```

![\[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-vEIM9nYp-1675574388738)(D:\Note\Note\学习笔记\开发\Java后端\Maven\assets\image-20230203135953741-1675405065640-4.png)\]](https://img-blog.csdnimg.cn/88ee9a0e20d24140b721649e668794f1.png)



验证

![\[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-AECLr1x7-1675574388738)(D:\Note\Note\学习笔记\开发\Java后端\Maven\assets\image-20230203140046741.png)\]](https://img-blog.csdnimg.cn/6e3eee9922244eb5bb4787d22766e696.png)




## 3.修改配置文件

找到该文件

![在这里插入图片描述](https://img-blog.csdnimg.cn/d1d5705636f94c62bd727674f0f17038.png)


**修改本地仓库位置localRepository**

```
  <!-- localRepository
   | The path to the local repository maven will use to store artifacts.
   |
   | Default: ${user.home}/.m2/repository
  <localRepository>/path/to/local/repo</localRepository>
  -->
 <localRepository>D:\software\Environment\Maven\repository</localRepository>
```
添加国内镜像源

在`<mirrors>`标签下添加`<mirror>`，即国内镜像

```
    <mirror>
      <id>alimaven</id>
      <mirrorOf>central</mirrorOf>
      <name>aliyun maven</name>
      <url>https://maven.aliyun.com/nexus/content/groups/public</url>
  </mirror>
```

4.在IDEA里面配置maven

![\[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-BgR68IK2-1675574388740)(D:\Note\Note\学习笔记\开发\Java后端\Maven\assets\image-20230203142420447.png)\]](https://img-blog.csdnimg.cn/edbcc03a24c04a6d8f531e41e6377fb4.png)





