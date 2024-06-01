# Hive高级知识进阶

一、常用的查询函数
1、Like 和 RLike用法
2、Group By 语句
3、Having 语句
4、Join 语句
5、排序
6、分区（Distribute By）
7、Cluster By
二、常用内置函数
1、NVL：空字段赋值
2、CASE WHEN THEN ELSE END
3、行转列
4、列转行
5、窗口函数（开窗函数）
三、自定义函数
1、自定义函数分类
2、编程步骤
以下是本篇文章正文内容，如有错误麻烦请指出。 谢谢 ！！！

一、常用的查询函数
1、Like 和 RLike用法
 1. Like
（1）使用 LIKE 运算选择类似的值；
（2）选择条件可以包含字符或数字；

```hive
 % 代表零个或多个字符(任意个字符)。
 _ 代表一个字符。
示例如下 
 select * from emp where ename LIKE 'A%';   # 查找名字以 A 开头的员工信息
 select * from emp where ename LIKE '_A%';  # 查找名字中第二个字母为 A 的员工信息
```

RLIKE
（1）RLIKE 子句是 Hive 中这个功能的一个扩展，其可以通过 Java 的**正则表达式**这个更强大的语言来指定匹配条件。

```
 # 示例
 select * from emp where ename RLIKE '[A]';  # 查找名字中带有 A 的员工信息
```



2、Group By 语句
 GROUP BY 语句通常会和聚合函数一起使用，按照一个或者多个列队结果进行分组，然后对每个组执行聚合操作。
3、Having 语句
 Having 与 Where不同点

（1）where 后不能跟聚合函数，因为where执行顺序大于聚合函数。
（2）where 子句的作用是在对查询结果进行分组前，将不符合where条件的行去掉，即在分组之前过滤数据，条件中不能包含聚组函数，使用where条件显示特定的行。
（3）having 子句的作用是筛选满足条件的组，即在分组之后过滤数据，条件中经常包含聚组函数，使用having 条件显示特定的组，也可以使用多个分组标准进行分组。

（4）where 后面不能写分组函数（可以在where前面写），而 Having 后面可以使用分组函数。

```hive
select deptno, avg(sal) from emp group by deptno; 
select deptno, avg(sal) from emp where id > 100 group by deptno;  # where前面写group by
```

（5）having 只用于 group by 分组统计语句。

```hive
select deptno, avg(sal) avg_sal from emp group by deptno having avg_sal > 2000;
```


4、Join 语句

 1. 内连接
只有进行连接的两个表中都存在与连接条件相匹配的数据才会被保留下来。

```hive
select e.empno, e.ename, d.deptno from emp e join dept d on e.deptno = d.deptno;
```

 2. 左外连接
JOIN 操作符左边表中符合 WHERE 子句的所有记录将会被返回。

```hive
select e.empno, e.ename, d.deptno from emp e left join dept d on e.deptno = d.deptno;
```


 3. 右外连接
JOIN 操作符右边表中符合 WHERE 子句的所有记录将会被返回。

```
select e.empno, e.ename, d.deptno from emp e right join dept d on e.deptno = d.deptno;
```

  4. 满外连接将会返回所有表中符合 WHERE 语句条件的所有记录。如果任一表的指定字段没有符合条件的值的话，那么就使用 NULL 值替代。

```hive
select e.empno, e.ename, d.deptno from emp e full join dept d on e.deptno = d.deptno;
```


5、排序

 1. 全局排序（Order By）
Order By：全局排序，只有一个 Reducer

 2. 每个 Reduce 内部排序（Sort By）
（1）Sort By： 对于大规模的数据集 order by 的效率非常低。在很多情况下，并不需要全局排序，此时可以使用 Sort by。
（2）Sort by 为每个 reducer 产生一个排序文件。每个 Reducer 内部进行排序，对全局结果集来说不是排序

6、分区（Distribute By）
Distribute By： 在有些情况下，我们需要控制某个特定行应该到哪个 Reducer，通常是为了进行后续的聚集操作,Distribute by 子句可以做这件事。
Distribute by 类似 MR 中 Partition（自定义分区），进行分区，结合 Sort by 使用。
对于 Distribute by 进行测试，一定要分配多个 Reduce 进行处理，否则无法看到 Distribute by 的效果。

```
# Distribute by 的分区规则是根据分区字段的 Hash 码与 Reduce 的个数进行模除后，余数相同的分到一个区。
# Hive 要求 DISTRIBUTE BY 语句要写在 SORT BY 语句之前。
# 示例：
set mapreduce.job.reduces=3;
insert overwrite local directory '/opt/module/data/distribute-result' select * from emp distribute by deptno sort by empno desc;
```


7、Cluster By
当 Distribute by 和 Sort by 字段相同时，可以使用 Cluster by 方式。
Cluster by 除了具有 Distribute by 的功能外还兼具 Sort by 的功能。但是排序只能是升序排序，不能指定排序规则为 ASC 或者 DESC。

```hive
# 示例：如下是一样的效果
select * from emp cluster by deptno;
select * from emp distribute by deptno sort by deptno;
```

二、常用内置函数
1、NVL：空字段赋值
NVL： 给值为 NULL 的数据赋值，它的格式是 NVL( value，default_value)。它的功能是如果 value 为 NULL，则 NVL 函数返回 default_value 的值，否则返回 value 的值，如果两个参数都为 NULL ，则返回 NULL。

2、CASE WHEN THEN ELSE END
```hive
# 示例
select dept_id,
	sum(case sex when '男' then 1 else 0 end) male_count,
	sum(case sex when '女' then 1 else 0 end) female_count
from emp_sex 
	group by dept_id;
```


3、行转列
 CONCAT(string A/col, string B/col…)：
返回输入字符串连接后的结果，支持任意个输入字符串。

 CONCAT_WS(separator, str1, str2,…)：
它是一个特殊形式的 CONCAT()。第一个参数是剩余参数间的分隔符。分隔符可以是与剩余参数一样的字符串。如果分隔符是 NULL，返回值也将为 NULL。这个函数会跳过分隔符参数后的任何 NULL 和空字符串。分隔符将被加到被连接的字符串之间;
注意: CONCAT_WS must be "string or array

```hive
# 示例

CONCAT_WS("|",col1, col2)   # 输出结果是：字段值之间以竖线“|”分割
```


 COLLECT_SET(col)：
函数只接受基本数据类型，它的主要作用是将某字段的值进行去重汇总，产生 Array 类型字段。

```
# 示例
CONCAT_WS("|",collect_set(name))   # name字段值去重之后，以竖线“|”分割，输出字符串
```

4、列转行
EXPLODE(col)： 将 hive 一列中复杂的 Array 或者 Map 结构拆分成多行。
LATERAL VIEW
用法： LATERAL VIEW udtf(expression) tableAlias AS columnAlias
解释： 用于和 split, explode 等 UDTF 一起使用，它能够将一列数据拆成多行数据，在此基础上可以对拆分后的数据进行聚合。

4、列转行
EXPLODE(col)： 将 hive 一列中复杂的 Array 或者 Map 结构拆分成多行。
LATERAL VIEW
用法： LATERAL VIEW udtf(expression) tableAlias AS columnAlias
解释： 用于和 split, explode 等 UDTF 一起使用，它能够将一列数据拆成多行数据，在此基础上可以对拆分后的数据进行聚合。

```hive
# 示例：
SELECT 
	movie, 
	category_name
FROM movie_info
	lateral VIEW explode(split(category,",")) movie_info_tmp AS category_name;
# 说明：lateral VIEW outer explode(split(category,",")) movie_info_tmp AS category_name
# 少了一个 outer 的主要区别，它会把数组中为“NULL”的值过滤掉
```


5、窗口函数（开窗函数）
 OVER()：
指定分析函数工作的数据窗口大小，这个数据窗口大小可能会随着行的变化而变化。

```
# CURRENT ROW：当前行
# n PRECEDING：往前 n 行数据
# n FOLLOWING：往后 n 行数据
# UNBOUNDED：起点，
	UNBOUNDED PRECEDING 表示从前面的起点，
	UNBOUNDED FOLLOWING 表示到后面的终点
# LAG(col,n,default_val)：往前第 n 行数据
# LEAD(col,n, default_val)：往后第 n 行数据
# NTILE(n)：把有序窗口的行分发到指定数据的组中，各个组有编号，编号从 1 开始，对于每一行，NTILE 返回此行所属的组的编号。
# 注意：n 必须为 int 类型。
```


```hive

	# 示例：
	# 创建 hive 表并导入数据
	create table business(
		name string,
		orderdate string,
		cost int
	) ROW FORMAT DELIMITED FIELDS TERMINATED BY ',';
	load data local inpath "/opt/module/data/business.txt" into table business;
# （1） 查询在 2017 年 4 月份购买过的顾客及总人数
	select name,count(*) over () 
	from business
		where substring(orderdate,1,7) = '2017-04'
		group by name; 
#（2） 查询顾客的购买明细及月购买总额
	select name,
		orderdate,
		cost,
		sum(cost) over(partition by month(orderdate)) 
	from business;
#（3） 将每个顾客的 cost 按照日期进行累加
	select name,orderdate,cost,
		sum(cost) over() as sample1,--所有行相加
		sum(cost) over(partition by name) as sample2,--按 name 分组，组内数据相加
		sum(cost) over(partition by name order by orderdate) as sample3,--按 name分组，组内数据累加
		sum(cost) over(partition by name order by orderdate rows 
			between UNBOUNDED PRECEDING and current row ) as sample4 ,--和 sample3 一样,由起点到当前行的聚合
		sum(cost) over(partition by name order by orderdate rows 
			between 1 PRECEDING and current row) as sample5, --当前行和前面一行做聚合
		sum(cost) over(partition by name order by orderdate rows 
		between 1 PRECEDING AND 1 FOLLOWING ) as sample6,--当前行和前边一行及后面一行
		sum(cost) over(partition by name order by orderdate rows 
		between current row and UNBOUNDED FOLLOWING ) as sample7 --当前行及后面所有行
	from business; 

# rows 必须跟在 order by 子句之后，对排序的结果进行限制，使用固定的行数来限制分区中的数据行数量

#（4） 查看顾客上次的购买时间
	select name,orderdate,cost,
		lag(orderdate,1,'1900-01-01') over(partition by name order by orderdate ) as time1, 
		lag(orderdate,2) over (partition by name order by orderdate) as time2 
	from business; 
#（5） 查询前 20%时间的订单信息
	select * 
	from (select name,orderdate,cost, 
	 		ntile(5) over(order by orderdate) sorted
	 	  from business) t
	where sorted = 1;
```


 Rank:
RANK() 排序相同时会重复，总数不会变;
DENSE_RANK() 排序相同时会重复，总数会减少;
ROW_NUMBER() 会根据顺序计算。



	# 示例：
	select name,
		subject,
		score,
		rank() over(partition by subject order by score desc) rp,
		dense_rank() over(partition by subject order by score desc) drp,
		row_number() over(partition by subject order by score desc) rmp
	from score;

三、自定义函数
1、自定义函数分类
 UDF（User-Defined-Function）
一进一出
 UDAF（User-Defined Aggregation Function）
聚集函数，多进一出
类似于：count/max/min
 UDTF（User-Defined Table-Generating Functions）
一进多出
如 lateral view explode()
2、编程步骤
（1）继承 Hive 提供的类

```
org.apache.hadoop.hive.ql.udf.generic.GenericUDF
org.apache.hadoop.hive.ql.udf.generic.GenericUDTF;
```


（2）实现类中的抽象方法
（3）在 hive 的命令行窗口创建函数

```hive
# 添加 jar
add jar linux_jar_path
# 创建 function
create [temporary] function [dbname.]function_name AS class_name;
```

（4）在 hive 的命令行窗口删除函数

```hive
drop [temporary] function [if exists] [dbname.]function_name;
```

