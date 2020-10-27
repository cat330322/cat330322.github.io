# SQL
---

BBQSQL 盲注工具

一、什么是SQL注入？ SQL注入是将恶意的SQL语句插入到表单、URL链接或者页面请求的内容中，并最终让后端数据库插入执行，使得黑客能够得以控制WEB服务器的操作，这就是SQL注入攻击！在渗透过程中，后端服务器往往会回显一些报错信息，黑客能很好的利用这些信息，决定下一步的渗透操作！ 

二、什么是SQL盲注？ 盲注，Blind SQL Injection，整个渗透过程类似一个盲目的过程，抹黑求索的过程。 在SQL注入攻击过程中，如果后端不反馈具体的错误信息，抑或是只给出一个模糊的反馈，如输入数据有误或者空白页面。黑客往往会仔细检查攻击行为中的间接信息，以获取额外的可利用的渗透线索，这种情况下的注入就被称为SQL盲注。

 三、如何使用Kali Linux进行SQL盲注？ SQL注入分为手动注入和工具注入，手动注入对渗透人员要求较高，往往需要反复进行大量注入操作，每次都需要重复设置配置项，构建新的SQL语句等，大量的重复操作，导致渗透效率低下。为了改变现状，Kali Linux提供了一个SQL盲注工具BBQSQL，它是一种用Pyhthon写的SQL盲注框架，使用它可以很好的帮助我们进行半自动化的渗透盲注！  BBQSQL是半自动工具，渗透人员可以方便地将各项参数进行预先设置，每次测试，只需要修改一项，就可以执行一次测试，从而避免重复项目的设置。它也自带一个直观的UI用户界面，使设置攻击更容易。

 四、BBQSQL有什么特征？ 1、 利用SQL盲注漏洞 2、 半自动 3、 与数据库无关 4、 多功能 5、利用两种搜索技术（二元搜索和按频次搜索） 6、 并发的HTTP请求 7、 配置导入/导出 8、 自定义的Hooks 9、速度快 五、如何使用BBQSQL？ 使用BBQSQL需要为它提供满足条件的请求信息，如下： 1、 URL 2、 HTTP方法 3、 标题 4、 Cookies 5、 编码方法 6、 重定向方式 7、 文件夹 8、 HTTP认证 9、代理

---
# Sqlmap


数据库注入1、工具注入2、手动注入

Sqlmap是一个自动化的SQL注入利器，其主要功能是扫描、发现并利用给定的URL的SQL注入漏洞，进行数据库注入攻击。

支持如MySQL, Oracle, PostgreSQL, Microsoft SQL Server, Microsoft Access, IBM DB2, SQLite, Firebird, Sybase和SAP MaxDB等数据库。

Sqlmap支持五种不同的注入模式： 1、基于布尔的盲注，即可以根据返回页面判断条件真假的注入。 2、基于时间的盲注，即不能根据页面返回内容判断任何信息，用条件语句查看时间延迟语句是否执行（即页面返回时间是否增加）来判断。 3、基于报错注入，即页面会返回错误信息，或者把注入的语句的结果直接返回在页面中。 4、联合查询注入，可以使用union的情况下的注入。 5、堆查询注入，可以同时执行多条语句的执行时的注入。

Sqlmap常用用法【Kali自带】

 1、对url进行检测，判断是否存在SQL注入 sqlmap -u "url" --batch 

2.获取数据库 a、获取全部数据库 sqlmap -u URL --dbs --batch b、获取当前数据库 sqlmap -u URL --current-db --batch 

3、获取当前数据库里所有表 sqlmap -u URL -D (数据库) --tables --batch

4、获取表的字段 python sqlmap.py -u URL -D (数据库) -T users --columns --batch

 5、dump字段内容 sqlmap -u URL -D (数据库) -T users -C "password,username" --dump --batch 如果字段内容多的话可以再加上如 --start 1 --stop 100 这样就取1-100条数据 --dump 可以换成 --dump-all则导出全部的内容