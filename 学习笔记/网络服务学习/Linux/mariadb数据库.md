# 初始化配置

```js
#数据库安全配置向导
mysql_secure_installation
#输入当前root用户密码，若没有则直接回车
Enter current password for root (enter for none):
#是否设置root用户密码，输入y标识设置root密码
Set root password? [Y/n] 
New password: 
Re-enter new password: 
Password updated successfully!
Reloading privilege tables..
 ... Success!
#是否删除匿名用户
Remove anonymous users? [Y/n] 
#是否禁止root用户远程连接
Disallow root login remotely? [Y/n] 
#是否删除测试数据库
Remove test database and access to it? [Y/n] 
#是否重新加载特权表
Reload privilege tables now? [Y/n] 

```

# 基本操作
```js
#使用root账户登录
[root@www ~]# mysql -u root -p 
Enter password:  //输入root密码
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 21
Server version: 10.3.9-MariaDB MariaDB Server

Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]> 

#登录数据库选项
-u 指定用户 -p 输入密码 -h 指定主机 -P 端口号



```

# 数据库中对库操作
```js
#查看所有库
MariaDB [(none)]> show databases;

#创建一个名为kylin_db1的数据库
MariaDB [(none)]> create database kylin_db1;

#删除一个名为kylin_db1的数据库
MariaDB [(none)]> drop database kylin_db1;

#切换到指定库
MariaDB [(none)]> use mysql;


```

# 数据库中对表的操作
```js
#查看当前库内的表
MariaDB [mysql]>show tables;

#查看指定表的结构
MariaDB [kylin_db1]> desc student_info;

#创建一个名为student_info的表
MariaDB [kylin_db1]> create table student_info(
    -> id int primary key not null auto_increment, 
    -> Name varchar(10) not null,
    -> Birthday datetime not null,
    -> Gender enum('male','female','X') not null default 'X', 
    -> Password varchar (200) not null);
+----------+---------------------------+------+-----+---------+----------------+
| Field    | Type                      | Null | Key | Default | Extra          |
+----------+---------------------------+------+-----+---------+----------------+
| id       | int(11)                   | NO   | PRI | NULL    | auto_increment |
| Name     | varchar(10)               | NO   |     | NULL    |                |
| Birthday | datetime                  | NO   |     | NULL    |                |
| Gender   | enum('male','female','X') | NO   |     | X       |                |
| Password | varchar(200)              | NO   |     | NULL    |                |
+----------+---------------------------+------+-----+---------+----------------+

#表格属性解释
not null //非空值
auto_increment //自增长，后面加上数字就是从当前数字开始增长
primary key //主键
enum ('x','x','x') //枚举指定内容
default ‘X’ //默认值为X
#在表中插入数据
insert into 表名 (字段名,字段名,..) values ('内容','内容'...);
#修改表中内容
MariaDB [kylin_db2]> update student_score set Yingyu='0' where id='20007';
#使用password函数为指定字符段加密
insert into 表名 (字段名,字段名,..) values ('内容',password('内容'));
#使用select索引查询表格内容
MariaDB [kylin_db1]> select * from 表名;
#修改表格字段类型
MariaDB [kylin_db2]> alter table 表名 modify 字段名 float (5,2)；
#添加字段
MariaDB [kylin_db1]> alter table 表名 add 字段名 varchar(10) not null;
#删除字段，当表内仅剩一个字段时该命令失败。
MariaDB [kylin_db1]> alter table 表名 drop 字段名;
#给表格添加内容，前面set是给指定列添加内容，后面where算是标识该行内容标志。
update 表名 set 字段名=‘内容’ where 字段名=‘内容’;
```



# 权限问题
```js
#允许指定用户指定网段访问所有数据库，并拥有授予其他用户权限的权限
MariaDB [(none)]> grant all privileges on *.* to 'root'@'192.168.200.%' identified by 'gRkTIhzD' with grant option;




```