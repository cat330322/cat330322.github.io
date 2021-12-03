create database how2java 创建数据库
===============

创建表模板
CREATE TABLE hero (
  id int(11) AUTO_INCREMENT,
  name varchar(30) ,
  hp float ,
  damage int(11) ,
  PRIMARY KEY (id)
)  DEFAULT CHARSET=utf8;

===============
插入记录
insert into hero values (null, '盖伦', 616, 100)

===============

select * from hero 查询所有数据

select count(*) from hero 统计表中有多少条数据

select * from hero limit 0,5 分页查询

=====================
update hero set hp = 818 where id = 1 修改表

========================
delete from hero where id = 1 删除数据