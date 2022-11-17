### SQL

```
###MYSQL
INSERT INTO test_tbl(user_name, user_job, submit_date) VALUES(dd, dd, NOW());
```

```
###Redis
设置redis密码，config set requirepass 123456
MongoDB做主存储，Redis缓存部分
```

```
命令
--select表查询
select * FROM EMP;
select * from dept;
select deptno,dname from dept;

--查询所有员工的名称，工资，所在部门的编号
select * from emp;
select ename, sal,deptno from emp;
select deptno,dname,loc from dept;
select dname ,deptno ,loc from dept;
--去重复记录
select ename,deptno from emp;
--查询存在员工的部门编号
select deptno from emp;
--去重 distinct
select distinct deptno from emp;
--查询所有员工名称，以及员工所在部门编号
select distinct ename,deptno from emp;
--列取别名
--查询员工姓名，工资
select ename,sal from emp;
select ename 姓名,sal 工资 from emp;
select ename as 姓名,sal 工资 from emp;
--排序 order by
select ename,sal from emp;
--查询所有员工姓名 工资，降序排序
select ename , sal from emp order by sal desc;
select ename , sal from emp order by sal asc;
--查询所有员工姓名，工资，所在部门编号	，按照部门编号升序排序，同一部门的员工，安装工资降序
select ename,sal,deptno from emp order by deptno asc,sal desc;
--查询用户姓名，工资,1 ,伪列
select ename,sal ,1 from emp;
--查询用户姓名，月工资，年薪（月薪*12）伪列
select ename,sal ,sal*12 from emp;
select ename,sal,sal*12 as 年薪 from emp;
--查询员工姓名 工资 提成 月收入 工资+提成
select * from emp;
select ename,sal,comm,sal+comm 月收入 from emp;
--nvl(exp1,res)处理空
select ename,sal,comm,sal+nvl(comm,0) 月收入 from emp;
--排序
--按照员工的工资进行排序
select * from emp order by sal;
--查询员工的信息，并且按照提成升序排序
select * from emp order by comm desc;
--nulls first | nulls last
select * from emp order by comm desc nulls last;
select ename from emp;
--拼接符
select ename ,ename||'a'  别名 from emp;
--null
select ename,comm,ename || comm test  from emp;
--计算999*666 虚表的使用
select 999*666 from dual;
--简单查询 所有的行记录 某一些（指定，全部）字段
--去重
--别名
--伪列
--排序
--null 当null进行算数运算结果为null
--字符串拼接||
--null 
--nulls first   ，null last
select distinct  查询字段1 别名, 查询字段2 as 别名，表达式 别名  from 数据来源 order by 排序字段 desc|asc;
--语法
select …… from …… order by;
--解析顺序
--1）from
--2）select
--3）order by
--查询员工的姓名，员工的工资 别名 为工资 并且将结果集按照工资降序排序；
select * from emp;
select ename,sal 工资 from emp order by 工资 desc;
--条件查询
elect 查询内容 from 数据来源 where 行记录条件;
--查询班级所有男同学信息
select 同学信息 from 学生信息表 where 性别=男;
--解析过程
--1）学生信息表
--2）判断性别为男
--3）根据判断，记录中指定信息，满足select进行存放结果集
--查询10部门员工信息
select * from emp where deptno = 10;
--查询名称 smith员工信息
--!= <> ^= 不等于
select * from emp where ename <> 'SMITH';
select * from emp where deptno <> 10;
--查询2000以上工资员工信息
select  * from emp where sal>= 2000;
--bewtten ..an 之间
select * from emp where  sal between 2000 and 4000;
--in 查询在10部门或者20部门的员工信息
select * from emp where deptno in(10,20);
--查询工资大于1500 并且在20部门的员工信息
select * from emp where sal>1500 and deptno =20;
--between and
--查询工资1500-3000 员工信息
select * from emp where sal between 1500 and 3000;
select * from emp where sal>1500 and sal<3000;
--查询出20部门的员工，以及工资大于1500的员工信息
select * from emp where deptno=20 or sal>1500;
--not 取反
--查询不在20部门的员工信息
select * from emp where deptno!=20;
select * from emp where not deptno = 20;
--查询不在20部门，而且工资也不大于1500员工信息
select * from emp where deptno!=20 and sal<1500;
--查询出所有可能获得奖金的员工信息，查询出奖金不为空的员工信息
select * from emp where comm is not null;
select * from emp where not comm is null;
--查询出所有不可能获得奖金的员工信息，查询奖金为空
select * from emp where comm is null;
--nvl()为空时给一个特定值
select nvl(null,100) from 	dual;
--查询获取到的奖金的员工信息，查询奖金大于0的员工信息
select * from emp where comm>0;
--查询所有奖金小于等于0
select * from emp where comm<=0 ;
--当某个人奖金为null ，奖金设置为0
select * from emp where nvl(comm,0)<=0;
--查询名字为Smith员工信息
select * from emp where ename = 'SMITH';
--查询名称中包含s
select * from emp where ename like '%S%';
--查询JOB字段中包含有‘A‘的员工新
select * from emp where JOB like '%A%';
--查询名称以A开头的员工信息
select * from emp where ename like 'A%';
--查询名称当中第二个字母为大写A员工信息
select * from emp where ename like '_A%';
--查询倒数第二字母I
select * from emp where ename like '%I_';
--查询员工包含%员工信息
select * from emp;
select * from emp  where ename like '%a%%' escape('a');
--查询员工包含a%的信息
select * from emp where ename like '%aaa%%' escape('a');
--查询包含% _的员工信息
select * from emp where like '%a%%a_%' escape('a');
--添加记录 emp 插入
insert into emp (empno ,ename ,job,deptno) values(1111,'a%b_cd','aaa',20);
commit;
--从v查询所有部门信息
select * from dept;
select * from emp;
--销售部的员工信息
select * from emp where deptno = (select deptno from dept where dname = 'SALES');
select * from emp where deptno = 30;
--查询工资等级为2员工信息
select * from salgrade;
select * from emp where sal between (select losal from SALGRADE where GRADE = 2) and (select HISAL from SALGRADE where GRADE = 2);
--查询所有员工的姓名和工种
select ename, job from emp;
-- 员工姓名工种一起显示
select ename ||job namejob from emp;
--concat(x,y)
select concat(ename,job) namejob from emp;
--找子串
select instr('helloworld','e') from dual;
--查看所有员工的姓名是否包含A，如果包含，显示位置
select ename ,instr(ename,'A') from emp;
--假设有一个字符串'helloworld'找出1
select instr('helloworld','l',1,3)from dual;
--显示字符串长度
select LENGTH('hello') from dual;
--每个员工名称，由几个字符组成
select ename,length(ename) from emp;
--查看10部门的员工姓名的长度
select ename,deptno,length(ename) from emp where deptno=10;
--查看10部门，长度升序
select ename,deptno,length(ename) from emp where deptno=10 order by LENGTH(ename);
--转大小写，英文字母
select ename,sal,deptno ,lower(ename) lowerNanem from emp where deptno = 20;
select ename,sal,deptno ,lower(ename) lowerNanem ,upper(ename) uperName from emp where deptno = 20;
--去除字符串左边空格
select ltrim('  abc abc  ') || 'a' from dual;
select rtrim('  abc  abc   ')  || 'a'  from dual;
--去除字符串两边空格
select rtrim(ltrim('  abc  abc'))||'a'  from dual;
select concat(rtrim(ltrim(' abc abc ')),'a') from dual;
select ltrim('aaaa123456bbbb','aaa') from dual;
select rtrim(ltrim('aaaa123456bbbb','aaa') ,'bbb') from dual ;
--替换
select replace('a123b456c7','a','-') from dual;
select replace('a123b45a6c7','a','-') from dual;
---替换部分
select substr('abc',2,2) from dual;
--显示所有员工姓氏
select ename,substr(ename,1,1) from emp;
--显示所有员工3 4 字符
select ename,substr(ename,3,2) from emp;
--显示最后一个字符
select ename,substr(ename,LENGTH(ename),1) from emp;
--获取当前系统的日期
select sysdate from dual;
select CURRENT_DATE from dual;
--获取当前系统后一天的时间
select sysdate+21 from dual;
--查询所有员工的转正日期，3个月的试用期
select empno,ename,hiredate ,ADD_MONTHS(HIREDATE,-3)from emp;
--查看当前这个月最后一天
select last_day(SYSDATE) from dual;
--查看每个员工入职最后一天
select LAST_DAY(HIREDATE) 最后一天,HIREDATE from emp;
--查询每个员工工作到现在，一共几个月的班
select sysdate,HIREDATE,MONTHS_BETWEEN(SYSDATE, HIREDATE) from emp;
select sysdate,HIREDATE,MONTHS_BETWEEN(HIREDATE,SYSDATE ) from emp;
--获取当前时间点下一个星期几是什么时候
select next_day(sysdate,'1')from dual;
--查看每个员工上班，录用时间的下一个星期入职
select HIREDATE,NEXT_day(HIREDATE,'1') 入职时间 from emp;
--tochar(date，charFormat)日期转字符
select HIREDATE from emp;
 select TO_CHAR(HIREDATE,'mm"月"dd"日"yyyy"年"') from emp;
 --to_date(chars,charformat)数据转日期
 --1990/01/01
 select TO_DATE('1990/01/01','yyyy/mm/dd')+4 from dual;
 --to_number()其他类型转数字
 select '11'+1 from dual;
 select to_number('11')+1 from emp;
 select TO_NUMBER('11','xx') from dual;
 --avg() sum() min() max() count()
 select * from emp;
 delete from emp where empno= '1111';
 commit;
 --count()统计本公司的人数
 select count(empno) from emp; 
--max最大值，求所有员工最快金额
select max(sal) from emp;
select * from emp order by sal desc;
--min()最小值
select min(sal) from emp;
--sum()求和一个月公司需要发多少工资
select sum(sal) from emp;
--avg()求平均
select avg(sal) from  emp;
--统计10部门员工人数 count(empno) where deptno=10
select  * from emp where deptno=10;
select count(empno) from emp  where deptno=10;
select sum(sal) from emp where deptno=20;
select max(sal) from emp where deptno=20;
--统计整个员工数 null 不统计
select count(empno) from emp;
select * from emp;
select count(comm) from emp;
--统计有几个部门里面有员工,去重统计
select count(DISTINCT deptno) from emp;
--统计整个公司有几个部门
select count(deptno) from dept;
--统计记录数
select count(*) from emp;
select count(*) from dept;
select max(comm) from emp;
select min(comm) from emp;
--求出所有员工平均奖金
select avg(comm) from emp; 
select * from emp;
select sum(comm)/count(*) form emp;
select sum(comm) from emp;
select count(*) from emp;
select count(nvl(comm,0)) from emp; 
select deptno,avg(sal) from emp GROUP BY deptno;
--求出每个工作 job对应平均工资
select job,avg(sal) from emp group by job;
-- 求出有员工每个部门员工数,分组
select deptno,count(*) from emp GROUP BY deptno;
--查看平均工资大于2000部门的编号和平均工资
select deptno,avg(sal) from emp GROUP BY deptno HAVING AVG(sal)>2000;
-- 查看部门的人数大于3人的部门编号和人数
select count(*) ,deptno from emp GROUP BY DEPTNO HAVING count(*) >3;
--只统计工资大于2000的员工，，员工数量2以上的部门
select deptno,count(*) from emp where sal>2000 GROUP by deptno HAVING count(*)>=2;
-- from where GROUP BY HAVING select
--rownum是对每一个结果集的每一条记录编号，从1开始
select ename ,sal,DEPTNO ，rownum from emp;
select ename,sal,deptno ,rownum from emp where  deptno=30;
--进行分页，每页5条记录
select ename,sal,deptno ,rownum from emp where rownum<=5;
--查询第二页
select ename ,sal ,deptno, rownum from emp where rownum<=10 and rownum >5;
--查询所有员工信息，伪劣rownum
select ename,sal,deptno,rownum from emp;
--将查询出来结果集作为临时数据来源
select * from (select ename,sal,deptno,rownum rw from emp) where  rw>5 and rw<10;
--查询第二页
select ename,sal,deptno,rw,rownum from （select ename,sal,deptno,rownum rw from emp) where rw>5 and rw<=10;
--查询员工信息 姓名工资按照工资降序,实现分页
--第一页3条记录
select ename,sal,deptno,r1  ,rownum  r2 from (select ename ,sal,deptno ,rownum r1 from emp ORDER by sal desc);
select ename,sal,deptno,r1,r2 from(select ename,sal,deptno,r1  ,rownum  r2 from (select ename ,sal,deptno ,rownum r1 from emp ORDER by sal desc)) where r2 >3 and r2<=6;
--准备数据
create table copy as select * from dept;
select * from copy ORDER BY deptno;
select deptno,dname,loc,rowid from copy order by deptno;
insert into copy select  * from dept;commit;
--将所有相同保留一份
--将数据进行分组，重复分组
select min(rowid) from copy GROUP BY DEPTNO,DNAME,loc;
select * from copy WHERE ROWID not in (select min(rowid) from copy GROUP BY DEPTNO,DNAME,loc
);
delete from copy WHERE rowid not in (select min(rowid) from copy GROUP BY DEPTNO,DNAME,loc
);
select * from copy;
select * from emp;
select * from dept;
select * from salgrade;
select * from emp e;
--查询emp表和dept表当中的数据
select * from emp e,dept d  where 1=1 ORDER by empno;
--等值连接，查询每一个员工信息和所在部门信息
select * from emp e,dept d where e.DEPTNO=d.DEPTNO;
--查询出每一个有员工存在的部门信息，和部门人数
select count(*),DEPTNO from emp GROUP BY DEPTNO;
select * from dept d ,(select count(*),DEPTNO from emp GROUP BY DEPTNO) c
where d.DEPTNO=c.DEPTNO;
--等值连接
--查询每一个员工姓名，工资金额，入职时间，对应工资等级
select  * from SALGRADE;
select * from emp;
select ename,sal,HIREDATE,GRADE from emp e ,SALGRADE s where e.sal BETWEEN losal and HISAL;
--查询每一个部门信息和和部门人数
select * from dept;
select * from emp;
select count(*),DEPTNO from emp GROUP BY DEPTNO;
select * from dept d ,(select count(*),deptno from emp GROUP BY deptno) c WHERE d.DEPTNO=c.DEPTNO;
--外连接 主表，主要主表记录都要出现在结果
--查看每一个部门信息，对应员工数
select * from dept d,(select count(*),deptno from emp GROUP BY DEPTNO) c WHERE d.DEPTNO=c.DEPTno
(+);
select d.DEPTNO,DNAME,loc,nvl(cc,0) from dept d ,(select count(*) cc,deptno from emp GROUP BY DEPTNO)c where d.DEPTNO=c.DEPTNO(+);
--列出每一个有上级员工信息和上级信息
--列出所有有上级员工及其上级信息
select * from emp;
select * from emp e ,emp m  where e.mgr = m.empno(+);
select * from emp;
--查询每一个有上级存在的员工自己的信息和上级的信息
select * from emp e ,emp m where e.mgr=m.empno;
--99标准 笛卡尔积 cross join
select * from dept cross join emp;
--naturn join，所有员工名称 编号 所属部门编号 部门名称
select ename ，empno，deptno，dname from emp natural join dept;
--join using同名列
select ename,empno,deptno,dname  from emp  join dept using(deptno);

--查询10部门的员工名称，部门编号，部门名称
select ename,deptno,dname from emp NATURAL join dept where DEPTNO=10;
select ename,deptno,dname from emp join dept using(deptno) where DEPTNO=10;
--join on查询所有员工
select ename,empno,e.deptno,dname from emp e join dept d on e.DEPTNO=d.DEPTNO;
--姓名工资 工资等级 部门编号
select ename,sal,deptno,GRADE from emp e join SALGRADE s on sal BETWEEN LOSAL and HISAL; 
--姓名 工资 等级 部门名称 30部门
select ename ,sal,e.deptno,GRADE,dname from  emp e join dept d on e.DEPTNO=d.DEPTNO join SALGRADE on e.sal BETWEEN LOSAL and HISAL where e.DEPTNO = 30 ;
--outer join 查看每一个员工编号 名称 上级编号，上级名称
select e.empno 员工编号 ,e.ENAME 员工名称,e.mgr 上级编号,m.ENAME 上级名称 from emp e left 
join emp m on e.mgr =m.EMPNO;
---92 99
--92 
select  ...from  table1,table2 where table1.xx=table2.xx and table1.xx=1;
--92外连接
select  ...from  table1,table2 where table1.xx=table2.xx(+);
--99
select ...from table1 cross join  table2  where...;
select ...from table1 natural join  table2  where...;
select ...from table1  join  table2 using (同名) where...;
select ...from table1  join  table2 on 连接条件 where...;
--99外连接
select  ...from  table1 left  join  table2  on 连接条件 where;
select  ...from  table1 right  join  table2  on 连接条件 where;
--全连接 
select  ...from  table1  full join  table2  on 连接条件 where;
--集合并集
select 'a','b' from  dual UNION select 'c','d' from  dual UNION select 'a','b' from  dual;
--union all全并集
select 'a','b' from  dual union all select 'c','d' from  dual union all select 'a','b' from  dual;
--交集
（select 'a','b' from  dual UNION select 'b','d' from  dual ）INTERSECT （select 'a','c' from  dual union select 'a','b' from  dual）;
--差集，相减
（select 'a','b' from  dual UNION select 'b','d' from  dual	)minus （select 'a','c' from  dual union select 'a','b' from  dual）;
--创建新表
create table tb_user(num char(10));
--从其他表拷贝结构
create table 表内名 as select  字段列表 from 已有表 where 1!=1;
--修改表名
select * from tb_user;
rename tb_user to tb_txt_new
--修改列名
alter table tb_user  rename column num to num1; 
--修改字段类型
alter table tb_user MODIFY(num1 char(20));
--添加列
alter table tb_user add class1 char(30);
--删除列
alter table tb_user drop COLUMN class1;
--删除表
drop table tb_user;
--约束，创建表同时
create table tb_user(
	userid number(5) primary key,
	username VARCHAR2(30) CHECK(LENGTH(username)BETWEEN 4 and 20) not null,
	userpwd VARCHAR2(30) not null check(LENGTH(userpwd) BETWEEN 4 and 18),
	age number(3) DEFAULT(18) CHECK(age>=18),
	gender char(3) DEFAULT('男') CHECK(gender in ('男','女')),
	email VARCHAR2(30) UNIQUE,
	regtime date DEFAULT(SYSDATE)
)

create table  tb_txt(
	txtid number(5) primary key,
	title VARCHAR2(30) not null CHECK(LENGTH(title)>=4 and LENGTH(title)<=30),
	txt VARCHAR2(1024),
	pubtime date DEFAULT(sysdate),
	userid NUMBER(5) references tb_user(userid) on  DELETE set null
)
--创建表同时，创建约束
create table tb_user(
	userid number(5),
	username VARCHAR2(30) constraint nn_user_name  not null,
	userpwd VARCHAR2(30) constraint nn_user_pwd  not null,
	age number(3) DEFAULT(18),
	gender char(3) DEFAULT('男'),
	email VARCHAR2(30),
	regtime date DEFAULT(SYSDATE),
	constraint pk_user_id primary key(userid),
	constraint ck_user_name CHECK(LENGTH(username) BETWEEN 4 and 20),
	constraint ck_user_pwd CHECK(LENGTH(userpwd) BETWEEN 4 and 18),
	constraint ck_user_age CHECK(age>=18),
	constraint ck_user_gender CHECK(gender in ('男','女')),
	constraint ck_user_email UNIQUE(email)
)

drop table tb_txt;
drop table tb_user;

create table  tb_txt(
	txtid number(5) ,
	title VARCHAR2(32) constraint nn_txt_title not null,
	txt VARCHAR2(1024),
	pubtime date DEFAULT(sysdate),
	userid NUMBER(5) ,
	constraint pk_txt_id primary key(txtid),
	constraint ck_txt_title CHECK(LENGTH(title)>=4 and LENGTH(title)<=30),
	constraint fk_txt_user_id foreign key(userid)  references tb_user(userid) on  DELETE set null
)

--insert  update delete
insert into tb_user  VALUES
(1012,'marry','123123',18,'女','1243@qq.com',TO_DATE('1990-1-1','yyyy-mm-dd'));
commit;
select * from tb_user;
--创建表同时添加记录
create table temp as select empno, ename ,deptno ,sal  from emp;
select * from  temp;
--创建表
 create  table temp1 as select * from temp where 1!=1;
 select * from temp1;
 insert into temp1 VALUES(1111,'lisa',30,90);
 commit;
 --从其他表拷贝数据
insert into temp1 VALUE(select * from temp where deptno=30);
 commit;
 --从其他表拷贝数据emp
 insert into temp1 VALUE(select empno,ename,deptno,sal from emp where deptno=20);
 commit;
 --指定列的方式添加记录
 insert into tb_user(userid,regtime, username,userpwd,email,gender,age) VALUES(10002,TO_DATE('1990-1-1','yyyy-mm-dd'),'tomi','111111','11@qq.com','男'，19);
 commit;
 select * from tb_user;
 --查询添加到表中
insert into tb_user(userid,username,userpwd,regtime) (select empno,ename,ename,HIREDATE from emp where deptno = 10 );
--插入一条记录到tb_txt当中
--外键 从表，被参考的表，主表
insert into tb_txt VALUES(000001,'tit2','dedw',TO_DATE('1990-2-2','yyyy-mm-dd'),10001);
 select * from tb_txt;
--update
update tb_txt set txt='aaa' where txtid=1;
commit;
select * from tb_txt;
--一个字段一个字段修改
update tb_txt set txt='bbbb' ,userid= 1011	where txtid=1;
--先列出通过查询字句设定
update tb_txt set(txt,userid)= (select 'ccccc',1011 from dual)	where txtid=2;
update tb_txt set title='title0' where 1=1;
--delete
delete from tb_user where userid ='1011';
select * from tb_user;
delete from tb_user where userid<10000;
select * from tb_txt;
```

```
创建用户
切换到oracle用户下 
su -l oracle
使用sysdba账户登录： 
sqlplus / as sysdba
语法：CREATE USER 用户名 IDENTIFIED BY 密码; 
CREATE  USER testDatabase IDENTIFIED BY testDatabase;

将刚创建的用户解锁/锁住
ALTER USER 用户名 ACCOUNT UNLOCK/LOCK
##用户解锁
alter user testDatabase account unlock;
##用户锁住
alter user testDatabase account lock;

授予新登陆的用户创建权限:登录权限
grant create session to testDatabase;

注意：权限表
create session to test：登陆权限
create table to test创建表权限
create insert any table  to test插入表权限
create unlimited tablespace to test 插入表权限
create user to test 授权可以创建用户权限
create view  to test 视图权限
create procedure
grant create user to scott;  //授权给scott创建用户的权限
grant alter user to scott; //授权给scott改变用户的权限
grant drop user to scott;  //授权给scott删除用户的权限

授予新创建的用户数据库管理员权限
语法：CRANT DBA TO 用户名;
grant dba to testDatabase;

切换到新创建的用户登陆
语法：CONNECT 用户名/密码
connect testDatabase/testDatabase;

删除用户
语法：DROP USER 用户名
drop user testDatabase
DROP USER TEST CASCADE；

修改用户
alter user 用户名 password expire

登陆后立即改密码
alter user 用户名 account unlock
ALTER   USER  SCOTT  IDENTIFIED  BY  LION;  //改变scott用户的密码

```

	SELECT * FROM 
	select * from all_viewst;
	create public database link；
	create public database link hehe connect to 123 identified by 123 using 'link';


```
#shitu 
CREATE [OR REPLACE] [FORCE|NOFORCE] VIEW view_name
select * from CESHI00001
SELECT t1.emp_id, t1.emp_name, t2.dept_name
FROM employees AS t1 LEFT JOIN departments AS t2
ON t1.dept_id = t2.dept_id;
```

```
oracle创建用户赋予访问某一视图的权限
创建用户
```





