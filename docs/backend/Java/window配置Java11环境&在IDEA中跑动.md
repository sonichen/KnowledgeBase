window11配置Java11环境
# 1.下载安装包
下载网址：[https://www.oracle.com/java/technologies/javase/jdk11-archive-downloads.html](https://www.oracle.com/java/technologies/javase/jdk11-archive-downloads.html)
 ![在这里插入图片描述](https://img-blog.csdnimg.cn/cba925c4abc44504b6c7303431150604.png)
![在这里插入图片描述](https://img-blog.csdnimg.cn/6298cb0fa8714e768a8224cbaeee9894.png)
一路下一步（最好更改路径
![在这里插入图片描述](https://img-blog.csdnimg.cn/88b5da0bf31a4a269de5de34f554b01f.png)
![在这里插入图片描述](https://img-blog.csdnimg.cn/5770e4baee574d90be9e9b510712edb0.png)



验证

![\[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-NJaXnSuT-1675573852011)(D:\Note\Note\学习笔记\开发\Java后端\Java\assets\image-20230203131444855.png)\]](https://img-blog.csdnimg.cn/4062e3de9bc14fc29a49beab3b584bfd.png)


安装成功

# 2.配置环境变量

系统变量中配置

Java_Home

![\[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-tXr4H9Bq-1675573852012)(D:\Note\Note\学习笔记\开发\Java后端\Java\assets\image-20230203131650775.png)\]](https://img-blog.csdnimg.cn/f644456ca61947898a9ecfd8389cde99.png)


添加path

```
%Java_Home%\bin
```

保存并确定后

CLASSPATH 配置(无大影响)

```
变量名：CLASSPATH
变量值：.;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar;
```

验证
![在这里插入图片描述](https://img-blog.csdnimg.cn/8bf6060671064f93ae159d06fbf9a9cf.png)


成功

# 3.IDEA中跑Java程序
新建项目中
![在这里插入图片描述](https://img-blog.csdnimg.cn/b22af1c768e342efabff6039fffb1949.png)


![在这里插入图片描述](https://img-blog.csdnimg.cn/8fdbdeaee6d04048b312668edca844fb.png)

成功

