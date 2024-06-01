1. 拷贝 hive 配置文件 hive-site.xml 到 spark/conf 目录下

2. 拷贝 mysql 驱动到 spark/jars

3. 在 spark 的配置文件中：spark-env.sh 配置 mysql 驱动

   - export SPARK_CLASSPATH=/opt/modules/spark/jars/mysql-connector-java- 5.1.40-bin.jar

4. 启动 mysql

5. 启动 hive 的 metastore 服务

   - hive --service metastore &    修改日志界别 log4j.properties

6. 启动 spark 集群

7. 访问 spark-sql

# DataFrame 相关数据操作

## 启动 scala 交互

spark-shell --master yarn

spark.sql("select \* from luo.test").show #查看从 hive 中创建的表数据

1. 定义 SQLContext

   - val sql=new org.apache.spark.sql.SQLContext(sc);

2. 创建 DataFrame

   - val df1=sql.read.load("/data/users.parquet")
   - val df2=sql.read.format("json").load("/data/employees.json")

3. 查看数据
   - df1.show()
   - df2.show()

## 从外部数据库导入数据

1. 在 mysql 数据库中新建数据库并创建表，将准备好的数据导入表中，如图所示
   ![XUCOnH.png](https://s1.ax1x.com/2022/06/03/XUCOnH.png)

2. 连接数据库
   - val url="jdbc:mysql://master/luo"
3. 创建 DataFrame
   - val df3=sql.read.format("jdbc").options(
   - Map("url"->url,
   - "user"->"root",
   - "password"->"1234",
   - "dbtable"->"test")).load()
