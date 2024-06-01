# 启动 history

`mr-jobhistory-daemon.sh start historyserver`

# 浏览器查看

`http://192.168.0.201:19888/jobhistory/logs`

### 在/tmp 目录下创建名为 spark-events 的文件夹

### 查看 yarn 的日志信息

`yarn logs -applicationId application_1651646376490_0004`

# 计算 Pi 的值

```sh
spark-submit --master yarn --deploy-mode  client --class org.apache.spark.examples.SparkPi /home/spark/examples/jars/spark-examples_2.12-2.4.2.jar
```

# 将 spark 目录下的 jars 上传到 hdfs

# spark 上的 spark-env.sh 配置

```sh
export JAVA_HOME=/home/jdk
export HADOOP_HOME=/home/hadoop
export HADOOP_CONF_DIR=/home/hadoop/etc/hadoop
export SPARK_MASTER_IP=master
export SPARK_WORKER_MEMORY=1024m
export SPARK_EXECUTOR_MEMORY=1024m
export SPARK_DRIVER_MEMORY=1024m
export SPARK_WORKER_CORES=1     #作业使用的cpu内核数量
export YARN_CONF_DIR=/home/hadoop/etc/hadoop
# 配置spark历史日志存储地址，并且使得历史记录自动清理
spark_HISTORY_OPTS="-Dspark.history.fs.logDirectory=hdfs://master:9000/spark_Log/ -Dspark.history.fs.cleaner.enabled=true"
#配置spark提交任务的端口和worker的参数
SPARK_MASTER_PORT=7077
SPARK_MASTER_WEBUI_PORT=8080
```

# spark-defaults.conf

```sh
spark.eventLog.enabled                  true #是否开启日志
spark.eventLog.compress                 false #是否压缩日志
spark.eventLog.dir                      hdfs://master:9000/spark_Log  #日志存储路径
spark.yarn.historyServer.address        master:18080 #历史记录访问的url
spark.yarn.jars                         hdfs://master:9000/jars/*  #将spark的jar上传到hdfs
```
