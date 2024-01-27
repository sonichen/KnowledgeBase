## 基础语法

### 查询Select

#### 全表查询

```
select * from student;
```

#### 选择查询

```
select name,age from student
```

#### 别名

```
select name as 学生姓名, age as 学生年龄 from student
```

#### 常量和运算

```
select name, score, score*2 as double_score from student
```

### 条件查询Where

```
select name,score
from student
where name="鱼皮"
```

### 运算符

```
select name, age
from student
where name!="热dog"
```

### 空值

is null空值

is not null非空值

```
select name,age,score 
from student
where age is not null
```



### 模糊查询 like

like 

not like

```
select name,score 
from student
where name not like "%李%"
```



### 逻辑运算

```
select
  name,
  score
from
  student
where
  name like "%李%"
  or score > 500
```

### 去重distinct

```
select distinct
  class_id,
  exam_num
from
  student
```

### 排序

从名为 `student` 的数据表中选择出学生姓名（name）、年龄（age）和成绩（score），首先按照成绩从大到小排序，如果成绩相同，则按照年龄从小到大排序。

```
select
  name,
  age,
  score
from
  student
order by
  score desc,
  age asc
```

### 截断和偏移limit

limit x: 一次获取x条

limit x,y: 从第x-1条开始获取y条

请编写一条 SQL 查询语句，从名为 `student` 的数据表中选择学生姓名（name）和年龄（age），按照年龄从小到大排序，从第 2 条数据开始、截取 3 个学生的信息。

```
select
  name,
  age
from
  student
order by
  age asc
limit
  1, 3
```

### 条件分支

假设有一个学生表 `student`，包含以下字段：`name`（姓名）、`age`（年龄）。请你编写一个 SQL 查询，将学生按照年龄划分为三个年龄等级（age_level）：60 岁以上为 "老同学"，20 岁以上（不包括 60 岁以上）为 "年轻"，20 岁及以下、以及没有年龄信息为 "小同学"。

返回结果应包含学生的姓名（name）和年龄等级（age_level），并按姓名升序排序。

```
CASE WHEN (条件1) THEN 结果1
	   WHEN (条件2) THEN 结果2
	   ...
	   ELSE 其他结果 END

```



```
select
  name,
  case
    when (age > 60) then "老同学"
    when (age < 20 or age is null) then "小同学"
    else "年轻"
  end as age_level
from
  student
order by
  name asc;
```

## 函数

### 时间函数

常用的时间函数有：

- DATE：获取当前日期
- DATETIME：获取当前日期时间
- TIME：获取当前时间

![image-20240127102301800](assets\image-20240127102301800.png)

```
-- 获取当前日期
SELECT DATE() AS current_date;

-- 获取当前日期时间
SELECT DATETIME() AS current_datetime;

-- 获取当前时间
SELECT TIME() AS current_time;
```

### 字符串处理

```
UPPER()
LENGTH()
LOWER()


```

```
select id,name,UPPER(name) as upper_name from student
where name="热dog"
```

### 聚合函数

常见的聚合函数包括：

- COUNT：计算指定列的行数或非空值的数量。
- SUM：计算指定列的数值之和。
- AVG：计算指定列的数值平均值。
- MAX：找出指定列的最大值。
- MIN：找出指定列的最小值。

```
select
  sum(score) as total_score,
  avg(score) as avg_score,
  max(score) as max_score,
  min(score) as min_score
from
  student
```

## 分组聚合

### 单字段分组

某个学校可以按照班级将学生分组，并对每个班级进行统计。查看每个班级有多少学生、每个班级的平均成绩。这样我们就能够对学校各班的学生情况有一个整体的了解，而不是单纯看个别学生的信息。

在 SQL 中，通常使用 `GROUP BY` 关键字对数据进行分组

假设有一个学生表 `student`，包含以下字段：`id`（学号）、`name`（姓名）、`class_id`（班级编号）、`score`（成绩）。请你编写一个 SQL 查询，统计学生表中的班级编号（class_id）和每个班级的平均成绩（avg_score）

```
select
  class_id,
  avg(score) as avg_score
from
  student
group by
  class_id
```

### 多字段分组

多字段分组查询表中 **每个客户** 购买的 **每种商品** 的总金额，相当于按照客户编号和商品编号分组：

```
-- 查询每个用户购买的每种商品的总金额，按照客户编号和商品编号分组
SELECT customer_id, product_id, SUM(amount) AS total_amount
FROM orders
GROUP BY customer_id, product_id;
```

假设有一个学生表 `student`，包含以下字段：`id`（学号）、`name`（姓名）、`class_id`（班级编号）、`exam_num`（考试次数）、`score`（成绩）。请你编写一个 SQL 查询，统计学生表中的班级编号（class_id），考试次数（exam_num）和每个班级每次考试的总学生人数（total_num）。

```
select
  class_id,
  exam_num,
  count(*) as total_num
from
  student
group by
  class_id,
  exam_num
```

### having子句

在 SQL 中，HAVING 子句用于在分组聚合后对分组进行过滤。它允许我们对分组后的结果进行条件筛选，只保留满足特定条件的分组。

HAVING 子句与条件查询 WHERE 子句的区别在于，WHERE 子句用于在 **分组之前** 进行过滤，而 HAVING 子句用于在 **分组之后** 进行过滤。

假设有一个学生表 `student`，包含以下字段：`id`（学号）、`name`（姓名）、`class_id`（班级编号）、`score`（成绩）。请你编写一个 SQL 查询，统计学生表中班级的总成绩超过 150 分的班级编号（class_id）和总成绩（total_score）。

```
select
  class_id,
  sum(score) as total_score
from
  student
group by
  class_id
having
  sum(score) > 150
```

### 关联查询 - cross join

在 SQL 中，关联查询是一种用于联合多个数据表中的数据的查询方式。

其中，`CROSS JOIN` 是一种简单的关联查询，不需要任何条件来匹配行，它直接将左表的 **每一行** 与右表的 **每一行** 进行组合，返回的结果是两个表的笛卡尔积。



假设有一个学生表 `student` ，包含以下字段：id（学号）、name（姓名）、age（年龄）、class_id（班级编号）；还有一个班级表 `class` ，包含以下字段：id（班级编号）、name（班级名称）。

请你编写一个 SQL 查询，将学生表和班级表的所有行组合在一起，并返回学生姓名（student_name）、学生年龄（student_age）、班级编号（class_id）以及班级名称（class_name）。

```
select s.name as student_name, s.age as student_age,s.class_id,c.name as class_name
from student s
cross join class c
```

### 关联查询 - inner join

它根据两个表之间的关联条件，将满足条件的行组合在一起。

注意，INNER JOIN 只返回两个表中满足关联条件的交集部分，即在两个表中都存在的匹配行。



假设有一个学生表 `student`，包含以下字段：`id`（学号）、`name`（姓名）、`age`（年龄）、`class_id`（班级编号）。还有一个班级表 `class`，包含以下字段：`id`（班级编号）、`name`（班级名称）、`level`（班级级别）。

请你编写一个 SQL 查询，根据学生表和班级表之间的班级编号进行匹配，返回学生姓名（`student_name`）、学生年龄（`student_age`）、班级编号（`class_id`）、班级名称（`class_name`）、班级级别（`class_level`）。

```
select s.name as student_name,s.age as student_age,s.class_id,c.name as class_name,c.level as class_level
from student s
join class c on c.id=s.class_id
```

### 关联查询 - outer join

在 SQL 中，OUTER JOIN 是一种关联查询方式，它根据指定的关联条件，将两个表中满足条件的行组合在一起，并 **包含没有匹配的行** 。

在 OUTER JOIN 中，包括 LEFT OUTER JOIN 和 RIGHT OUTER JOIN 两种类型，它们分别表示查询左表和右表的所有行（即使没有被匹配），再加上满足条件的交集部分。



```
select s.name as student_name,s.age as student_age,s.class_id,c.name as class_name,c.level as class_level
from student s
left join class c on c.id=s.class_id
```

### 子查询

子查询是指在一个查询语句内部 **嵌套** 另一个完整的查询语句，内层查询被称为子查询。子查询可以用于获取更复杂的查询结果或者用于过滤数据。

当执行包含子查询的查询语句时，数据库引擎会首先执行子查询，然后将其结果作为条件或数据源来执行外层查询。

打个比方，子查询就像是在一个盒子中的盒子，外层查询是大盒子，内层查询是小盒子。执行查询时，我们首先打开小盒子获取结果，然后将小盒子的结果放到大盒子中继续处理。



假设有一个学生表 `student`，包含以下字段：`id`（学号）、`name`（姓名）、`age`（年龄）、`score`（分数）、`class_id`（班级编号）。还有一个班级表 `class`，包含以下字段：`id`（班级编号）、`name`（班级名称）



请你编写一个 SQL 查询，使用子查询的方式来获取存在对应班级的学生的所有数据，返回学生姓名（`name`）、分数（`score`）、班级编号（`class_id`）字段。

```
select
  s.name,
  s.score,
  s.class_id
from
  student s
where
  s.class_id in (
    select distinct
      id
    from
      class
  )
```

### 子查询 - exists

子查询中的一种特殊类型是 "exists" 子查询，用于检查主查询的结果集是否存在满足条件的记录，它返回布尔值（True 或 False），而不返回实际的数据。

和 exists 相对的是 not exists，用于查找不满足存在条件的记录。



题目

假设有一个学生表 `student`，包含以下字段：`id`（学号）、`name`（姓名）、`age`（年龄）、`score`（分数）、`class_id`（班级编号）。还有一个班级表 `class`，包含以下字段：`id`（班级编号）、`name`（班级名称）。

请你编写一个 SQL 查询，使用 exists 子查询的方式来获取 **不存在对应班级的** 学生的所有数据，返回学生姓名（`name`）、年龄（`age`）、班级编号（`class_id`）字段。

```
select
  s.name,
  s.age,
  s.class_id
from
  student s
where
  not exists (
    select distinct
      id
    from
      class
    where
      class.id = s.class_id
  )
```

# 查询进阶 - 组合查询
