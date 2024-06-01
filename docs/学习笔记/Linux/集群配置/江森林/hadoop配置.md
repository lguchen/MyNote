# hadoop集群配置搭建（伪分布式和完全分布式）

- **hadoop-env.sh 配置jdk路径**

  ```sh
  export JAVA_HOME=/usr/local/src/jdk
  ```

  

- **core-site.xml**

```xml
<configuration>
  <property>
    <name>fs.defaultFS</name>
    <value>hdfs://master:9000</value>
  </property>
  <property>
 	<name>io.file.buffer.size</name> # 设置缓存的大小,以byte为单位
 	<value>131072</value>
  </property>
  <property>
 	<name>hadoop.tmp.dir</name> # 临时文件目录
 	<value>/home/hadoop/tmp</value>
  </property>
</configuration>
```

- **hdfs-site.xml 伪分布式将数据副本数改为1**

```xml
<configuration>
  <property>
 	<name>dfs.namenode.name.dir</name> # 保存FsImage镜像的目录
 	<value>/home/hadoop/dfs/name</value>
  </property>
  <property>
 	<name>dfs.datanode.data.dir</name> # 存放HDFS文件系统数据文件的目录，存放hadoop的数据节点datanode里的多个数据块
 	<value>/home/hadoop/dfs/data</value>
  </property>
  <property>
    <name>dfs.replication</name>
    <value>3</value> #数据副本数
  </property>
</configuration>
```

- **yarn-site.xml**

```xml
<configuration>
  <property>
    <description>Whether to enable log aggregation</description>
    <name>yarn.log-aggregation-enable</name> # 开启日志功能
    <value>true</value>
  </property>
  <property>
    <name>yarn.log.server.url</name>
    <value>http://master:19888/jobhistory/logs</value> # web日志访问路径
  </property>
  <property>
    <name>yarn.resourcemanager.hostname</name> # 设置resourcemanager所在主机
    <value>master</value>
  </property>
    <!--固定写法-->
  <property>
    <name>yarn.nodemanager.aux-services</name>
    <value>mapreduce_shuffle</value>
  </property>
    <!--运行 MapReduce 任务时，可能会报错:找不到或无法加载主类
解决办法:
1.命令行执行: hadoop classpath
2.将 1 中命令执行后出现的结果，复制到下面的 value 中去，重启集群即可
-->
<property>
 <name>yarn.application.classpath</name>
 <value>输入刚才返回的 hadoop classpath 中的路径</value>
</property>
</configuration>
```

- **mapred-site.xml**

```xml
<configuration>
    <!--固定写法-->
  <property>
    <name>mapreduce.framework.name</name>
    <value>yarn</value>
  </property>
  <!--配置历史服务器访问地址-->
  <property>
    <name>mapreduce.jobhistory.address</name>
    <value>master:10020</value>
  </property>
  <property>
    <name>mapreduce.jobhistory.webapp.address</name>
    <value>master:19888</value>
  </property>
</configuration>
```

- **slaves  伪分布式不需要修改这个**

```
slave1
slave2
```

## 伪分布式

 **配置文件的修改和完全分布一样，只需要将 core-site.xml 中的主机映射名修改为伪分布的主机名，以及将 hdfs-site.xml 中的副本数量修改为 1 ，同时也要注意修改 slaves ，只保留当前伪分布主机名即可
格式化 namenode
启动集群
测试是否跑通 Mapper 程序**

## ResourceManager相关配置参数（yarn-site.xml文件）

**`（1） yarn.resourcemanager.address`**

参数解释：`ResourceManager` 对客户端暴露的地址。客户端通过该地址向RM提交应用程序，杀死应用程序等。

默认值：${yarn.resourcemanager.hostname}:8032

例：

```xml
<property>
 <name>yarn.resourcemanager.address</name>
 <value>master:8032</value>
</property>
```



**`（2） yarn.resourcemanager.scheduler.address`**

参数解释：`ResourceManager` 对ApplicationMaster暴露的访问地址。ApplicationMaster通过该地址向RM申请资源、释放资源等。

默认值：${yarn.resourcemanager.hostname}:8030

**`（3） yarn.resourcemanager.resource-tracker.address`**

参数解释：`ResourceManager` 对NodeManager暴露的地址.。NodeManager通过该地址向RM汇报心跳，领取任务等。

默认值：${yarn.resourcemanager.hostname}:8031

**`（4） yarn.resourcemanager.admin.address`**

参数解释：`ResourceManager` 对管理员暴露的访问地址。管理员通过该地址向RM发送管理命令等。

默认值：${yarn.resourcemanager.hostname}:8033

**`（5） yarn.resourcemanager.webapp.address`**

参数解释：`ResourceManager`对外web ui地址。用户可通过该地址在浏览器中查看集群各类信息。

默认值：${yarn.resourcemanager.hostname}:8088

**`（6） yarn.resourcemanager.scheduler.class`**

参数解释：`启用的资源调度器主类`。目前可用的有FIFO、Capacity Scheduler和Fair Scheduler。

默认值：

org.apache.hadoop.yarn.server.resourcemanager.scheduler.capacity.CapacityScheduler

**`（7） yarn.resourcemanager.resource-tracker.client.thread-count`**

参数解释：`处理来自``NodeManager``的``RPC``请求的``Handler``数目`。

默认值：50

**`（8） yarn.resourcemanager.scheduler.client.thread-count`**

参数解释：`处理来自``ApplicationMaster``的``RPC``请求的``Handler``数目`。

默认值：50

**`（9） yarn.scheduler.minimum-allocation-mb/ yarn.scheduler.maximum-allocation-mb`**

参数解释：单个可申请的最小/最大内存资源量。比如设置为1024和3072，则运行MapRedce作业时，每个Task最少可申请1024MB内存，最多可申请3072MB内存。

默认值：1024/8192

**`（10） yarn.scheduler.minimum-allocation-vcores / yarn.scheduler.maximum-allocation-vcores`**

参数解释：单个可申请的最小/最大虚拟CPU个数。比如设置为1和4，则运行MapRedce作业时，每个Task最少可申请1个虚拟CPU，最多可申请4个虚拟CPU。什么是虚拟CPU，可阅读我的这篇文章：[“YARN 资源调度器剖析”。](http://dongxicheng.org/mapreduce-nextgen/yarnmrv2-resource-manager-resource-manager/)

默认值：1/32

**`（11） yarn.resourcemanager.nodes.include-path` /`yarn.resourcemanager.nodes.exclude-path`**

参数解释：NodeManager黑白名单。如果发现若干个NodeManager存在问题，比如故障率很高，任务运行失败率高，则可以将之加入黑名单中。注意，这两个配置参数可以动态生效。（调用一个refresh命令即可）

默认值：“”

**`（12） yarn.resourcemanager.nodemanagers.heartbeat-interval-ms`**
