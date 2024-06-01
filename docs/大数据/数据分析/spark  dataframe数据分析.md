### 代码

```scala
package analysis

import org.apache.spark.sql.functions.col
import org.apache.spark.sql.types.StringType
import org.apache.spark.sql.{SQLContext, SparkSession}
import org.apache.spark.{SparkConf, SparkContext}

import java.util.Properties

object test {
  def main(args: Array[String]): Unit = {
    val conf = new SparkConf().setAppName("spark").setMaster("local[*]")
    val sc = new SparkContext(conf)

    val spark = SparkSession.builder.master("local[*]").appName("spark").getOrCreate();
    spark.sparkContext.setLogLevel("WARN")
    val properties = new Properties()
    properties.setProperty("user", "root")
    properties.setProperty("password", "123456")
    val url = "jdbc:mysql://localhost:3306/job?characterEncoding=utf8&useSSL=false"
    val df = spark.read.jdbc(url, "jobinfo", properties).toDF()

    df.withColumn("address", df("address").cast(StringType))
      .withColumn("company_name", df("company_name").cast(StringType))
      .withColumn("job_name", df("job_name").cast(StringType))
      .withColumn("experience", df("experience").cast(StringType))
      .withColumn("education", df("education").cast(StringType))
      .withColumn("salary", df("salary").cast(StringType))

    val out_of_repeat = df.dropDuplicates(Seq("address", "company_name", "job_name")) //按字段去除重复值
    //    out_of_repeat.show(10)
//    out_of_repeat.coalesce(1).write.option("header", "true").csv("E:\\project\\spark\\data\\norepeat")

    val edu_label = out_of_repeat.groupBy("education").count()
    edu_label.show(10)

  }
}

```

