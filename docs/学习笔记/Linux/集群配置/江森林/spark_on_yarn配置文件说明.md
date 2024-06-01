# core-site.xml

```javascript
<configuration>
  <property>
    <name>fs.defaultFS</name> #NN的URL
    <value>hdfs://master:9000</value>
  </property>
  <property>
    <name>hadoop.tmp.dir</name> #临时文件的储存路径(hdfs的存放物理路径)
    <value>/home/hadoop/tmp</value>
  </property>
</configuration>
```

# hdfs-site.xml

```javascript
#数据文件的副本数，SNN的web访问URL，NN的web访问URL
<configuration>
<property>
<name>dfs.replication</name>
<value>2</value>
</property>
#在所有的集群搭建中，若有该项，则会指定出SNN所在的节点和访问的web的URL，否则默认情况下，会在主NN所在的节点上创建SNN
<property>
<name>dfs.namenode.secondary.http-address</name>
<value>master:50090</value>
</property>
#在所有的集群搭建中，若有该项，则会指定出SNN所在的节点和访问的web的URL，否则默认情况下，会在主NN所在的节点上创建SNN
<property>
<name>dfs.namenode.http-address</name>
<value>master:50070</value>
</property>
</configuration>
```

## yarn-site.xml

```javascript
<configuration>
  <property>
    <name>yarn.nodemanager.aux-services</name>
    <value>mapreduce_shuffle</value>
  </property>
  <property>
    <name>yarn.resourcemanager.hostname</name>
    <value>master</value>
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

## mapred-site.xml

```javascript
<configuration>
  <property>
    <name>mapreduce.framework.name</name>
    <value>yarn</value>
  </property>
</configuration>
```
