## spark DataFrame正则表达式
注意 在spark中使用正则的时候，需要时时刻刻加上转义自符

```
'\'需要使用'\\',例如'\w'需要使用'\\w'
```


正则表达式，使用的库在sql.funtions 下，如导入split和regexp_extract

```
import org.apache.spark.sql.functions.{regexp_extract,split}
```

1. split
   split 切分字符串
   可通过下面的，形如udf函数实现

```scala
val splitFunc=udf((arg:String)=>{arg.split(',|[| ')[0]})  //0 是切分之后的索引
```


也可使用

```scala
var data1 = data.withColumn(colName, split(col(colName), pattern=',|[| ')(0))
```



2. regexp_extract
   regexp_extract(string subject, string pattern, int index) 将字符串subject按照pattern正则表达式的规则拆分，返回index指定的字符

   例子：匹配至少有两个非数字的gid

```scala
val data=fake_data.select(regexp_extract(fake_data("gid"),"^\\d{2}",0).alias("gid"))
```



3. like & rlike的区别

   - like：
     %：匹配零个及多个任意字符
     _：与任意单字符匹配
     []：匹配一个范围
     [^]：排除一个范围
     ESCAPE 关键字定义转义符 WHERE ColumnA LIKE ‘%5/%%’ ESCAPE ‘/’
     like不是正则，而是通配符

   - rlike
     rlike是正则，正则的写法与java一样。’‘需要使用’\’,例如’\w’需要使用’\w’
     A rlike ‘\d+’ 匹配一个或多个数字， not A rlike ‘\d+’ 匹配非数字

## 正则替换实例

```scala
    import spark.implicits._ //使用 $ 符号需要加入这个 
// salary_min 和salary_max为生成新字段
    val salary_reg = out_of_repeat
      .withColumn("salary", regexp_replace($"salary", "千", "000"))
      .withColumn("salary", regexp_replace($"salary", "万", "0000"))
      .withColumn("salary_min", split($"salary", "-")(0))
      .withColumn("salary_max", split($"salary", "-")(1)).show(5)
```

如果您的数据中既有包含“千”又有包含“万”且**有小数点**的情况，您可以使用正则表达式来替换这些值。以下是示例代码：

```
import org.apache.spark.sql.functions.{regexp_replace, expr}
    import spark.implicits._ //使用 $ 符号需要加入这个

    //正则表达式替换 “千”和“万”
    val replaced_df = out_of_repeat
      .withColumn("salary", regexp_replace($"salary", "千", ""))
      .withColumn("salary", regexp_replace($"salary", "万", ""))
      //将结果分别乘1000 和10000
      .withColumn("salary_min", split($"salary", "-")(0)*1000)
      .withColumn("salary_max", split($"salary", "-")(1)*10000)
      //删除salary字段并赋值为薪资范围内的平均值
      .drop("salary")
      .withColumn("salary",($"salary_min"+$"salary_max")/2).show(20)


```

在这个示例代码中，我们使用正则表达式来匹配包含“千”和“万”的数据，并将它们替换为对应的数值。我们还使用了expr函数来拆分salary字段，并使用cast函数将其转换为double类型。最后，我们使用select函数和avg函数计算平均值，并使用show函数显示结果。

## 数据类型转换

```scala
 val replaced_df = out_of_repeat .withColumn("salary",col("salary").cast(DoubleType))
```

## udf函数

```scala
import org.apache.spark.sql.functions.regexp_extract

// 读取数据
val df = spark.read.format("csv").option("header", "true").load("path/to/your/file.csv")

// 通过正则表达式提取“室数”信息
val pattern = "(\\d+)[室|卧]".r
val extract = udf((s: String) => pattern.findFirstIn(s).getOrElse(""))

val result = df.withColumn("room_num", extract($"type"))

// 输出结果
result.show()
```

