# MySQL基本操作

```sql


#数据库的操作
#查看所有库
SHOW DATABASES;
#创建库
CREATE DATABASE IF NOT EXISTS mytest;
#使用库
USE mytest;
#删除库
DROP DATABASE mytest;


#表操作
#查看库里所有表
SHOW TABLES;
#创建表
CREATE TABLE IF NOT EXISTS users(
id INT,
username VARCHAR(100),
groupname VARCHAR(50),
tel VARCHAR(100),
birth DATETIME
);
CREATE TABLE IF NOT EXISTS t_group (
id INT,
groupname VARCHAR(100),
leader VARCHAR(50)
);
#查看表结构 
DESC users;
#删除表
DROP TABLE users;


#增删改查
#增加
#增加单个数据
INSERT INTO users(id,username,tel,birth) VALUES(133,"路人33","1234567890","2001-07-05 11:12:12");
INSERT INTO users VALUES(3,"李3","121212","2312-07-05 11:12:12");
#增加多个数据
INSERT INTO users VALUES(3,"李四","141212890","2021-07-05 11:12:12"),(4,"王五","1234412190","1995-07-05 11:12:12");


#删除
DELETE FROM users WHERE users.username="李四";


#更新
UPDATE users SET users.username="赵六" WHERE users.id=2;

#查询
#基础查询
#查询表中的所有数据
SELECT * FROM users;
#查询指定字段的数据
SELECT id,username FROM users;
#as 假名
SELECT id AS "ID号",username AS "用户名" FROM users;
#去重
SELECT DISTINCT username FROM users;


#排序查询 asc默认升序，desc降序
SELECT * FROM users ORDER BY id;
SELECT * FROM users ORDER BY id DESC;
#多列查询,第一列相同的情况下针对第二列排序
SELECT * FROM users ORDER BY username,id DESC;

#分页查询 limit m offset n  m表示m条数据，n表示第n页开始
SELECT * FROM users LIMIT 2 OFFSET 0;
SELECT * FROM users LIMIT 2 OFFSET 2;


#条件查询where
SELECT * FROM users WHERE users.username="张三";
SELECT * FROM users WHERE users.username IS NOT NULL;
#或 IN
SELECT * FROM users WHERE users.username IN ("张三","路人");
#between
SELECT * FROM users WHERE users.id BETWEEN 1 AND 3;
#like 
SELECT * FROM users WHERE users.username LIKE "%路人%";
#count(1) 计数
SELECT COUNT(*)  FROM users;

#分组group by
SELECT groupname,COUNT(*) FROM users GROUP BY groupname;

#连接查询
SELECT `t_group`.leader AS "组长",`users`.username AS "组员"
FROM `t_group`
RIGHT JOIN `users`
ON `users`.`groupname`=`t_group`.`groupname`;

```

