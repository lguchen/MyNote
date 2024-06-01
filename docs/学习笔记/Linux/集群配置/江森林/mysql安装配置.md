## 安装步骤

1. 解压 mysql 安装包并改名
2. 查看并删除自带的数据库

- rpm -qa | grep mariadb
- rpm -e 包名 --nodeps

3. 配置环境变量<br>

- vi /etc/profile
  ```
  MYSQL_HOME=/home/mysql
  PATH=$PATH:$MYSQL_HOME/bin
  ```

4. 创建用户和组名为 mysql

- groupadd mysql
- useradd -r -g mysql mysql

5. 在 mysql 目录中创建 data 文件用于存放数据库数据<br>

- mkdir /home/mysql/data

6. 把 mysql 所属用户和组改成 mysql<br>

- chown -R mysql:mysql /home/mysql

7. 初始化 mysql,将初始化后的密码复制下来<br>

- mysqld --initialize --user=mysql --basedir=/home/mysql --datadir=/home/mysql/data

8. 修改/etc/my.cnf，自己新建

```
   [mysqld]
   basedir=/home/mysql
   datadir=/home/mysql/data
   port=3306
```

9. 启动 mysql 服务

- /home/mysql/support-files/mysql.server start

10. 使用初始化密码登录 mysql 并修改密码

- mysql -u root -p
  - 修改密码
  - set password=password('密码')

11. 开放远程访问权限（在 mysql 里面执行）

```
- grant all privileges on *.* to 'root'@'%' identified by '数据库密码';
- grant all privileges on *.* to 'root'@'master' identified by '数据库密码';
- flush privileges;
```

12. 作为服务自启动<br>
    把 mysql.server 复制到/etc/init.d/mysql

    - cp /home/mysql/support-files/mysql.server /etc/init.d/mysql
    - chmod +x /etc/init.d/mysql #给执行权限
    - chkconfig --add mysql
    - chkconfig --list
