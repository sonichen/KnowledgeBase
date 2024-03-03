---
title: jar包双击执行
updated: 2020-09-21T17:44:54.0000000+08:00
created: 2020-09-20T15:12:40.0000000+08:00
---

如何制作可以双击执行的jar包呢？
1，将多个类封装到了一个包(package)中。
2，定义一个jar包的配置信息。
定义一个文件a.txt 。文件内容内容为：

Main-Class:(空格)包名.类名(回车)
3，打jar包。
jar -cvfm my.jar a.txt 包名
4，通过winrar程序进行验证，查看该jar的配置文件中是否有自定义的配置信息。

5，通过工具--文件夹选项--文件类型--jar类型文件，通过高级，定义该jar类型文件的打开动作的关联程序。
jdk\bin\javaw.exe -jar

6，双击试试
## 演示
1，
![image1](../../../assets/1ce0d1ef220340c49b9f0d2f5cb78840.png)

![image2](../../../assets/7d4655974e744755b89b16017ca6c023.png)

![image3](../../../assets/e9ab50a6797545239e117125aa7c0571.png)

![image4](../../../assets/39d589ea06b34dac96bd96a2a78155ea.png)

![image5](../../../assets/73c4c9b7b5fa4d5db91395a4e955aaa1.png)
打开失败

![image6](../../../assets/ceda1275e1ef4010b168bab229c5ee35.png)

![image7](../../../assets/ba9e28817f01462aabc26d4dac6e7fac.png)

![image8](../../../assets/483bc862d56e4a2c9648e5dae26d8595.png)

此时
![image9](../../../assets/c768da4169b540c4a52f3c3aea114f70.png)

还是无法使用？
必须在本地注册才能使用jar
![image10](../../../assets/e857ba93576347fdb2ed18bf477e7e35.png)

