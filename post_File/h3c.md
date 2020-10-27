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

