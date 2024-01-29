---
title: 3-SQL手工注入
updated: 2024-01-29T12:40:03.0000000+08:00
created: 2020-08-18T20:43:54.0000000+08:00
---

## 一、基本了解
1，
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>SQL注入-高危漏洞</p>
<p>危害：网站的数据库-拖库行为</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>xx网站用户信息被泄露--SQL注入漏洞</p>
<p>数据库里面存放的是网站信息（包括网站用户信息）</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>DVWA--SQL注入--用户信息</p>
<p>不是所有的网站都有SQL注入</p>
<p>漏扫软件--AWVS（慎用）</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
注（NISP一级和二级 校园版的CISP 证书可以当成项目的资质）
2，SQL注入的判断方法（and语句，true，false的判断）
| ?id=13和?id=13 and 1=1 | 得到结果是一样的   |
|------------------------|--------------------|
| ?id=13和?id=13 and 1=2 | 得到结果是不一样的 |
利用方式-sqlmap, 啊D，穿山甲--工具注入
手工注入--联合注入union--联合查询
联合注入之前--需要知道网站的数据表有几列

## 二、dvwa的low等级sql工具注入
![image1](../../assets/b5880d16e20c49bfbe29a87ca4558bf8.png)
## 三、网站案例
![image2](../../assets/610067b4da644562a9d1a7bb01d5cecd.png)

