# hive-site.xml

```bash
<configuration>
  <property>
    <name>hive.metastore.warehouse.dir</name>
    <value>/data/hive</value>
  </property>
  <property>
    <name>hive.metastore.local</name>
    <value>false</value>
  </property>
  <property>
    <name>java.jdo.option.ConnectionURL</name>
    <value>
      jdbc:mysql://master:3306/hive？createDatabaseIfNotExist=true&amp;useSSL=false
    </value>
  </property>
  <property>
    <name>javax.jdo.option.ConnectionDriverName</name>
    <value>com.mysql.jdbc.Driver</value>
  </property>
  <property>
    <name>javax.jdo.option.ConnectionUserName</name>
    <value>root</value>
  </property>
  <property>
    <name>javax.jdo.option.ConnectionPassword</name>
    <value>1234</value>
  </property>
</configuration>
```

![XUCbcD.jpg](https://s1.ax1x.com/2022/06/03/XUCbcD.jpg)
