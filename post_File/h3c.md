# h3c
---

###transceiver

display transceiver diagnosis interface Ten-GigabitEthernet 

display transceiver interface Ten-GigabitEthernet

display lldp neighbor-information lis

---

###config-tftp

tftp 172.17.254.1 get 

startup saved-configuration startup.cfg 

dir /all //命令查看设备的配置文件。

backup startup-configuration to 192.168.125.149 aaa.cfg或tftp 192.168.125.149 put h3c.cfg aaa.cfg 备份配置文件

使用restore startup-configuration from 192.168.125.149 aaa.cfg或tftp 192.168.125.149 get aaa.cfg 恢复配置文件

使用dis startup命令，查看下一次启动所使用的配置命令

删除startup.cfg文件，使用reset recycle-bin命令清空回收站，

reset save-configuration命令彻底删除设备保存的启动配置。


restore startup-configuration from 192.168.1.2 tiyukantai.cfg


删除startup.cfg文件，使用reset recycle-bin命令清空回收站，


startup saved-configurationcfg tiyukantai.cfg

---

display link-aggregation verbose Bridge-Aggregation xx

---

console

sys

user-interface aux 0

authentication-mode password

set authentication password simp co

---

###wlan

wlan rename-ap old new

wlan auto-ap enable 

wlan auto-persistent enable

dis wlan client mac xxx-xxx-xx

display ip interface biref查看vlan分配的地址段

display wlan ap-group brief

display ip routing-table 127.0.0.1

display wlan ap all radio 查看ap信道和功率

display wlaln ap all adress查看ap的IP和MAC地址

display wlan client ap 查看单个ap下关联的用户数

display wlan statistics radio 查看单个radio的数据流状态

display wlan statistics client all 查看单个用户数据统计

display wlan app-model all 查看AC支持的AP信息

display wlan radio-policy查看radio策略参数

display wlan rrm 查看无线资源管理配置

display wlan service-template查看wlan服务模板参数

display clock 查看系统时间

display brief interface 查看所有接口信息

display vlan all 查看所有vlan信息

display vlan static 查看vlan的详细信息

display dhcp server ip-in-use all查看用户地址池已经分配出去的地址

---

h3c 


dis ll nei list

dis arp

dis lldp local information

dispaly irf

display clock

display environment 温度

display logbuffer 日志信息

display device 单板运行状态

display cpu-usage 查看cpu状态

display ip interface brief  查看ip

display interface brief 查看接口状态

display version 查看设备版本

display license 查看license信息

display power 查看电源信息

display fan 查看风扇信息

dispaly ntp status 查看ntp服务器

display vlan 查看vlan

dispaly vrrp brief 查看vrrp主备信息

display device manuinfo 序列号

display ip routing 查看路由表

display ospf peer 查看ospf邻居

dis transceiver interface Ten-GigabitEthernet 查看光模块接口

display saved-configuration 查看保存的配置信息

display ip route-table 查看路由表

display mac-address 查看MAC地址表

display controllers （物理信息）

display diag 全部采集信息

序列号 display device man

dis device manuinfo

dis int 端口名  查看端口

dis device pic 查看子卡

dis trapbuffer 查看重要告警

dis access-user username 账号 verbose  查看宽带账号速率

dis interface brief 查看端口摘要，流量，误码等

dis ip-pool pool-usage domain 地址池类型  查看地址池

dis version slot 板卡号 查看板卡信息，重启时间

dis ip int brief 查看接口IP地址

reset  counters interface 端口 清除CRC误码

dis memory-usage slot X 查看bras板卡内存情况

dis max-onlineusers slot X 查看bras板卡流量

display ip routing-table 　　　　　　　　　　路由信息

display port trunk                        查看参与trunk的端口

display stp root　　　　　　　　　　　　　　　 查看stp根

display stp brief                         查看stp简单信息

display stp abnormal                      查看是否有非正常端口

display vrrp statistics                   查看主备用状态

display link-aggregation summary          查看链路聚合组的情况

reset counters interface G0/0/1           清理接口CRC错包

 display current-configuration | include vlan

 display logbuffer | include SEHLL | include VTY

 display history-command

关闭当前用户的分屏显示功能。screen-length disable

显示设备作为Telnet客户端的相关配置信息 display telnet client

flow-control流量控制

 telnet 1.1.1.2 source ip 1.1.1.1 设备作为Telnet客户端时，指定发送的Telnet报文的源IP地址为1.1.1.1。

 telnet client source ip 1.1.1.1

display alarm命令用来显示设备硬件的告警信息。

display mac-address命令用来显示MAC地址表信息。

display ip interface brief命令用来显示三层接口与IP相关的简要信息。

display fib 命令用来显示FIB表项的信息。

display route-static routing-table命令用来显示静态路由表信息。


