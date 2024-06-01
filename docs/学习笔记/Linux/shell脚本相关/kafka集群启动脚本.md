## 6、编写kafka集群操作脚本

```powershell
# 导入java环境
vim /etc/profile
# 添加如下内容(注意：填写自己的java安装目录)
export JAVA_HOME=/usr/java/jdk1.8.0_131
export CLASSPATH=.:${JAVA_HOME}/jre/lib/rt.jar:${JAVA_HOME}/lib/dt.jar:${JAVA_HOME}/lib/tools.jar
export PATH=$PATH:$JAVA_HOME/bin

cd /opt/module/kafka/bin
# 创建kafka启动脚本
vim kafka-cluster.sh
# 添加如下内容
#!/bin/bash
case $1 in
"start"){
	for i in hadoop1 hadoop2 hadoop3
	do 
		 echo -------------------------------- $i kafka 启动 ---------------------------
		ssh $i "source /etc/profile;/opt/module/kafka/bin/kafka-server-start.sh -daemon /opt/module/kafka/config/server.properties"
	done
}
;;
"stop"){
	for i in hadoop1 hadoop2 hadoop3
	do
		echo -------------------------------- $i kafka 停止 ---------------------------
		ssh $i "/opt/module/kafka/bin/kafka-server-stop.sh"
	done
}
;;
esac

# 保存退出后，修改执行权限
chmod +x ./kafka-cluster.sh
```

脚本命令说明：

```powershell
powershell复制代码启动kafka集群命令
./kafka-cluster.sh start

停止kafka集群命令
./kafka-cluster.sh stop
```