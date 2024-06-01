## yarn-site.xml

```xml
<configuration>
<property>
 <name>yarn.resourcemanager.hostname</name>
 <value>master</value>
</property>
<property>
 <name>yarn.nodemanager.aux-services</name>
 <value>mapreduce_shuffle</value>
</property>
<property>
 <name>yarn.nodemanager.resource.memory-mb</name>
 <value>20480</value>
</property>
<property>
 <name>yarn.scheduler.minimun-allocation-mb</name>
 <value>20480</value>
</property>
<property>
 <name>yarn.nodemanager.vmem-pmem-ration</name>
 <value>2.1</value>
</property>
<property>
 <name>yarn.nodemanager.pmem-check-enabled</name>
 <value>false</value>
</property>
<property>
 <name>yarn.nodemanager.vmem-check-enabled</name>
 <value>false</value>
</property>
</configuration>
```

## hdfs-site.xml

```xml
<configuration>
<property>
 <name>dfs.replication</name>
 <value>2</value>
</property>
<property>
 <name>dfs.namenode.http-address</name>
 <value>master:50070</value>
</property>
<property>
 <name>dfs.namenode.secondary.http-address</name>
 <value>master:50090</value>
</property>
</configuration>
```

## mapred-site.xml

```xml
<configuration>
<property>
 <name>mapreduce.framework.name</name>
 <value>yarn</value>
</property>
</configuration>
```

## core-site.xml

```xml
<configuration>
<property>
 <name>fs.defaultFS</name>
 <value>hdfs://master:9000</value>
</property>
</configuration>
```

## spark-env.sh

```sh
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
export YARN_CONF_DIR=/home/hadoop/etc/hadoop

export SPARK_CLASSPATH=/home/spark/jars/mysql-connector-java-5.1.40-bin.jar
SPARK_MASTER_PORT=7077
SPARK_MASTER_WEBUI_PORT=8080
```

## spark-defaults.conf

```xml
spark.master spark://master:7077
spark.eventLog.compress                 false
```
