### ubuntu

```
###
useradd -m username1
usermod -a -G sudo username1
chsh -s /bin/bash usern
userdel -r usern

### hwclock
date -s "20140225 20:16:00"  #yyyymmdd hh:mm:ss
hwclock --show
hwclock --systohc

###fcitx
sudo apt install fcitx
sudo apt install fcitx-googlepinyin 
按win键，输入input method，回车
选择fcitx
reboot
fcitx configuration

###vi /etc/hosts
192.30.255.113 github.com

###
neofetch
screenfetch

###sudo apt install apt-transport-https ca-certificates

###21.04
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ hirsute main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ hirsute-updates main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ hirsute-backports main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ hirsute-security main restricted universe multiverse

### 
apt-cache search 软件包名
apt-cache show 软件包名

###
sudo apt-get install ibus-pinyin
region&language
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192

###
apt install locales
locale -a dpkg-reconfigure locales 
apt install xfonts-intl-chines
apt install ttf-wqy-microhei
reoot

###
vmware
apt install open-vm-tools
apt install open-vm-tools-desktop

###
virtualbox-about kernel
/sbin/rcvboxdrv setup
pacman -S fcitx-im fcitx-configtool fcitx-googlepinyin

###
sudo vi /etc/netplan/00-installer-config.yaml
network:
ethernets:

###
ens33:     #配置的网卡的名称
addresses: [192.168.31.215/24]    #配置的静态ip地址和掩码
dhcp4: no    #关闭DHCP，如果需要打开DHCP则写yes
optional: true 
gateway4: 192.168.31.1    #网关地址
nameservers:
addresses: [192.168.31.1,114.114.114.114]    #DNS服务器地址，多个DNS服务器地址需要用英文逗号分隔开

###
version: 2
renderer: networkd    
#指定后端采用systemd-networkd或者Network Manager，可不填写则默认使用systemd-workd

###tools
wireshark htop mtr 
Ngrok

###tmux
tmux new -s session-name
tmux detach
tmux ls
tmux list-session
tmux attach -t 0 使用会话编号
tmux attach -t session-name 使用会话名称
tmux kill-session -t 0 使用会话编号
tmux kill-session -t session-name 使用会话名称
tmux switch -t 0 使用会话编号
tmux switch -t session-name 使用会话名称
tmux rename-session -t 0 new-name
Ctrl+b d：分离当前会话。
Ctrl+b s：列出所有会话。
Ctrl+b $：重命名当前会话。
新建会话tmux new -s my_session。
在 Tmux 窗口运行所需的程序。
按下快捷键Ctrl+b d将会话分离。
下次使用时，重新连接到会话tmux attach-session -t my_session。
tmux split-window 划分上下两个窗格
划分左右两个窗格  tmux split-window -h
Ctrl+b %：划分左右两个窗格。
Ctrl+b "：划分上下两个窗格。
Ctrl+b arrow key：光标切换到其他窗格。arrow key是指向要切换到的窗格的方向键，比如切换到下方窗格，就按方向键↓。
Ctrl+b ;：光标切换到上一个窗格。
Ctrl+b o：光标切换到下一个窗格。
Ctrl+b {：当前窗格与上一个窗格交换位置。
Ctrl+b }：当前窗格与下一个窗格交换位置。
Ctrl+b Ctrl+o：所有窗格向前移动一个位置，第一个窗格变成最后一个窗格。
Ctrl+b Alt+o：所有窗格向后移动一个位置，最后一个窗格变成第一个窗格。
Ctrl+b x：关闭当前窗格。
Ctrl+b !：将当前窗格拆分为一个独立窗口。
Ctrl+b z：当前窗格全屏显示，再使用一次会变回原来大小。
Ctrl+b Ctrl+<arrow key>：按箭头方向调整窗格大小。
Ctrl+b q：显示窗格编号。

###lvm分区
umount /home 如果提示无法卸载，因为有进程占用/home，使用如下命令来终止占用进程
fuser -m /home 
如果依然无法卸载，使用以下命令：
[root@localhost home]# umount -l /home
PV->VG->LV
8e类型来使他们可用于LVM
30=uefi
pvcreate /dev/sdb# 创建为物理卷
pvdisplay 
pvremove /dev/sdb1 
vgcreate data /dev/sdb1
vgextend data /dev/sdb2  # 将新增的物理卷添加到已有的逻辑卷组中
vgremove  data 
lvcreate -l +100%FREE -n lvdata data
lvresize -L 200M /dev/volume-group1/lv1 
lvextend -l +100%FREE /dev/mapper/data-lvdata
e2fsck -f /dev/volume-group1/lv1  检查磁盘错误
resize2fs  /dev/mapper/data-lvdata  #更新磁盘 定义
resize2fs -p /dev/mapper/VolGroup-lv_home 100G #重定义大小
lvremove 
mkfs.ext4 /dev/volume-group1/lv1
mkdir /lvm-mount
mount /dev/mapper/lv1 /data

##### iptables
iptables -I INPUT -s 【IP】 -p tcp --dport  【端口】】  -j ACCEPT
```