# init
---

ssh-keygen -t rsa 

---

deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal main restricted universe multiverse

deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-updates main restricted universe multiverse

deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-backports main restricted universe multiverse

deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-security main restricted universe multiverse

---

deb http://mirrors.tuna.tsinghua.edu.cn/kali kali-rolling main contrib non-free 

deb-src https://mirrors.tuna.tsinghua.edu.cn/kali kali-rolling main contrib non-free 

---

apt-get install fcitx 

apt-get install fcitx-googlepinyin

---

apt install locales

locale -a dpkg-reconfigure locales 

apt install xfonts-intl-chines

apt install ttf-wqy-microhei

reoot

---

vmware_

apt install open-vm-tools

apt install open-vm-tools-desktop

---

https use iso_yuan

sudo apt install apt-transport-https ca-certificates

---

common tools

mtr、tshark、htop

---

sudo pacman-mirrors -i -c China -m rank 

sudo pacman -Syy

pacman -S archlinux-keyring

/etc/pacman.conf

[archlinuxcn]

SigLevel = Optional TrustedOnly

Server = https://mirrors.tuna.tsinghua.edu.cn/archlinuxcn/$arch

sudo pacman -S archlinuxcn-keyring

virtualbox-about kernel

/sbin/rcvboxdrv setup

pacman -S fcitx-im fcitx-configtool fcitx-googlepinyin

---

tools

whireshark htop mtr 
