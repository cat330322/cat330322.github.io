# ubuntu

---

useradd -m username1

usermod -a -G sudo username1

chsh -s /bin/bash usern

userdel -r usern

---

fcitx

sudo apt install fcitx

sudo apt install fcitx-googlepinyin 

按win键，输入input method，回车

选择fcitx

reboot

fcitx configuration

---

vi /etc/hosts

192.30.255.113 github.com

---
neofetch

screenfetch

---

sudo apt install apt-transport-https ca-certificates

---
20.10

deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ groovy main restricted universe multiverse

deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ groovy-updates main restricted universe multiverse

deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ groovy-backports main restricted universe multiverse

deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ groovy-security main restricted universe multiverse

---

apt-cache search 软件包名

apt-cache show 软件包名

---

sudo apt-get install ibus-pinyin

region&language

---

 sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192

---

apt install locales

locale -a dpkg-reconfigure locales 

apt install xfonts-intl-chines

apt install ttf-wqy-microhei

reoot

---

sudo apt-get update: 升级安装包相关的命令,刷新可安装的软件列表

sudo apt-get upgrade: 进行安装包的更新

sudo apt-get dist-upgrade: 除了拥有upgrade的全部功能外，dist-upgrade会比upgrade更智能地处理需要更新的软件包的依赖关系。

sudo do-release-upgrade: 进行系统版本的升级(Ubuntu版本的升级)，Ubuntu官方推荐的系统升级方式,若加参数-d还可以升级到开发版本,但会不稳定

sudo apt-get autoclean: 清理旧版本的软件缓存

sudo apt-get clean: 清理所有软件缓存

sudo apt-get autoremove: 删除系统不再使用的孤立软件

---

vmware_

apt install open-vm-tools

apt install open-vm-tools-desktop

---

archlinux

sudo pacman-mirrors -i -c China -m rank 

sudo pacman -Syy

pacman -S archlinux-keyring

/etc/pacman.conf

[archlinuxcn]

SigLevel = Optional TrustedOnly

Server = https://mirrors.tuna.tsinghua.edu.cn/archlinuxcn/$arch

sudo pacman -S archlinuxcn-keyring

---

virtualbox-about kernel

/sbin/rcvboxdrv setup

pacman -S fcitx-im fcitx-configtool fcitx-googlepinyin

---

tools

whireshark htop mtr 

Ngrok

---

kali-docker

apt-get update
 
apt-get install -y apt-transport-https ca-certificates
 
apt-get install dirmngr

curl -fsSL https://mirrors.tuna.tsinghua.edu.cn/docker-ce/linux/debian/gpg | sudo apt-key add -

echo 'deb https://mirrors.tuna.tsinghua.edu.cn/docker-ce/linux/debian/ buster stable' | sudo tee /etc/apt/sources.list.d/docker.list

apt-get update

apt install docker-ce

service docker start

apt install docker-compose

---

[root@host sbin]# echo $PATH

/usr/kerberos/sbin:/usr/kerberos/bin:/usr/local/bin:/usr/bin:/bin:/usr/X11R6/bin:/home/vurtne/bi

ln -s /usr/bin/lscpu /usr/local/bin/

[root@host home]# whereis fdisk

fdisk: /sbin/fdisk /usr/share/man/man8/fdisk.8.gz

ln -s /usr/sbin/* /usr/local/bin/

---

/etc/netplan/00-installer-config.yaml

network:

  ethernets:
  
    enp0s3:
    
      dhcp4: true
      
  version: 2

---

network:

  ethernets:
  
    enp0s3:
    
      dhcp4: true
      
    enp0s8:
    
      dhcp4: true
      
  version: 2

---

network:

  version: 2
  
  renderer: networkd
  
  ethernets:
  
    ens160:
    
     addresses:
     
       - 10.200.0.237/24
       
     gateway4: 10.200.0.1
     
     nameservers:


