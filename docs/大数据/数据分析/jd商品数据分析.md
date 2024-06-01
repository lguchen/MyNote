### 1、获取评论前五的商品，对比价格信息进行数据可视化
hive数据库中创建表

```hive
create table jd_comment like jd_data;

insert into table jd_comment select name,price,comment,shop from jd_data  order by comment desc limit 5;
```

mysql数据库中创建表

```mysql
create table jd_price like jd_data;
```

导入mysql数据库

```bash
sqoop export --connect  "jdbc:mysql://192.168.80.10:3306/jd?useUnicode=true&characterEncoding=utf-8" --username root --password root --table jd_price  --input-fields-terminated-by  '\t' --export-dir  /user/hive/warehouse/jd.db/jd_price/*
```

### 2、统计不同店铺的数量，通过店铺数量进行降序排序取前五

hive建表

```hive
create table shop_cnt(shop string, cnt int) row format delimited fields terminated by ',';
```

插入表

```hive
insert into table shop_cnt select shop,count(*) as cnt from jd_data group by shop having shop is not null and shop !="" order by cnt desc;
```

mysql建表

```mysql
create table shop_cnt ('shop' varchar(255) DEFAULT NULL,'cnt' int(255) DEFAULT NULL)；
```

导入mysql

```bash
sqoop export --connect  "jdbc:mysql://192.168.80.10:3306/jd?useUnicode=true&characterEncoding=utf-8" --username root --password root --table shop_cnt  --input-fields-terminated-by  ',' --export-dir  /user/hive/warehouse/jd.db/shop_cnt/*
```

### 3、统计商品价格范围数量：<500低价， 500-2000中等，2001-3000较高，3000以上高价

hive创建表

```hive
create table jd_price_range(price_range string,cnt int) row format delimited fields terminated by ',';
```

插入

```hive
insert into table jd_price_range 
select '低价位' as price_range,count(*) as cnt from jd_data where price < 500
union all
select '中等价位' as price_range,count(*) as cnt from jd_data where price between 500 and 2000
union all
select '较高价位' as price_range,count(*) as cnt from jd_data where price between 2001 and 3000
union all 
select '高价位' as price_range,count(*) as cnt from jd_data where price > 3000;
```

mysql创建表

```mysql
create table jd_price_range ('price_range' varchar(255) default null,'cnt' int(255) default null);
```

导入mysql

```bash
sqoop export --connect  "jdbc:mysql://192.168.80.10:3306/jd?useUnicode=true&characterEncoding=utf-8" --username root --password root --table jd_price_range --input-fields-terminated-by  ',' --export-dir  /user/hive/warehouse/jd.db/jd_price_range/*
```



### 4、统计店铺数前五的商品数 ,"百丽"重复，算作一个

hive创建表

```
create table jd_brand(brand string,cnt int)row format delimited fields terminated by ',';
```

插入表

```hive
insert into table jd_brand select '安踏' as brand, count(*) as cnt from jd_data where name like '%安踏%';
union all
select '百丽' as brand, count(*) as cnt from jd_data where name like '%百丽%';
union all
select '阿迪达斯' as brand, count(*) as cnt from jd_data where name like '%阿迪达斯%';
union all
select 'TOPSPORTS' as brand, count(name)+count(shop) as cnt from jd_data where name like '%滔搏%' or shop like '%TOPSPORTS%';
```

mysql创建表

```mysql
create table jd_brand ('brand' varchar(255) default null,'cnt' int(255) default null);
```

导入mysql

```bash
sqoop export --connect  "jdbc:mysql://192.168.80.10:3306/jd?useUnicode=true&characterEncoding=utf-8" --username root --password root --table jd_brand --input-fields-terminated-by  ',' --export-dir  /user/hive/warehouse/jd.db/jd_brand/*
```

