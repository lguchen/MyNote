# scala环境变量
```javascript
export SCALA_HOME=/home/scala
export PATH=$PATH:$/SCALA_HOME/bin
```
# spark 环境变量
```javascript
export SPARK_HOME=/home/spark
export PATH=$PATH:$SPARK_HOME/bin:$SPARK_HOME/sbin
```	
# spark-env.sh
```javascript
export JAVA_HOME=/home/jdk
export SCALA_HOME=/home/scala
export HADOOP_HOME=/home/hadoop
export HADOOP_CONF_DIR=/home/hadoop/etc/hadoop
export SPARK_MASTER_IP=master
export SPARK_WORKER_MEMORY=1024m
export SPARK_EXECUTOR_MEMORY=1024m
export SPARK_DRIVER_MEMORY=1024m
export SPARK_WORKER_CORES=1     #作业使用的cpu内核数量
export SPARK_HOME=/home/spark
export SPARK_DIST_CLASSPATH=$(/home/hadoop/bin/hadoop classpath)

#配置yarn文件所在路径
YARN_CONF_DIR=/home/hadoop/etc/hadoop
#配置日志存储地址和日志的自动清理功能
spark_HISTORY_OPTS="-Dspark.history.fs.logDirectory=hdfs://master:9000/spark_Log/ -Dspark.history.fs.cleaner.enabled=true"
```
```
vi log4j.properties
 INFO改成WARN
```
# spark-defaults.conf
```javascript
spark.master spark://master:7077
spark.eventLog.enabled		true #是否开启日志
spark.eventLog.dir			hdfs://master:9000/spark_Log
spark.yarn.historyServer.address	master:10000
spark.yarn.jars			hdfs://master:9000/jars/*	
```
# slaves
```
slave1
slave2
```
# 避免和hadoop启动冲突
```
将start-all.sh改成start-spark-all.sh
stop-all.sh改成stop-spark-all.sh
```