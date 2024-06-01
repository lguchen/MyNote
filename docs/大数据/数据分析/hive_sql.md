#### hive数据分析相关操作

1. 去除某个字段中为空值的行

   ```
   insert overwrite table 表名 select * from jd where 空值所在字段名 is not null;
   ```

   