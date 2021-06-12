mysql
---

sudo docker run -p 3306:3306 --name mysql -e MYSQL_ROOT_PASSWORD=xx -d mysql:5.7

mysql -h 127.0.0.1 -uroot -p123456

mysql -h 127.0.0.1 -P 3306 -uroot -p123456

mysql> use mysql;

mysql> show databases;

sudo docker exec -it mysql bash

mysql -uroot -p123456

use wordpress;

show tables;

desc wp_users;

select *from wp_user;

UPDATE wp_users SET user_pass = MD5( '123456' ) WHERE user_login = 'admin';

修改加密规则

ALTER USER 'root'@'localhost' IDENTIFIED BY 'password' PASSWORD EXPIRE NEVER;

更新用户密码

 ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'passwordt';.

刷新权限

FLUSH PRIVILEGES;

重置密码

alter user 'root'@'localhost'  identified by '1234567';

---

一、导出数据库用mysqldump命令（注意mysql的安装路径，即此命令的路径）：

1、导出数据和表结构：
mysqldump -u用户名 -p密码 数据库名 > 数据库名.sql

/usr/local/mysql/bin/   mysqldump -uroot -p abc > abc.sql

敲回车后会提示输入密码

2、只导出表结构

mysqldump -u用户名 -p密码 -d 数据库名 > 数据库名.sql

/usr/local/mysql/bin/   mysqldump -uroot -p -d abc > abc.sql

注：/usr/local/mysql/bin/  --->  mysql的data目录

二、导入数据库

1、首先建空数据库

mysql>create database abc;

2、导入数据库

方法一：

（1）选择数据库

mysql>use abc;

（2）设置数据库编码

mysql>set names utf8;

（3）导入数据（注意sql文件的路径）

mysql>source /home/abc/abc.sql;

方法二：

mysql -u用户名 -p密码 数据库名 < 数据库名.sql

mysql -uabc_f -p abc < abc.sql