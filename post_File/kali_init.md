# kali_init
---

ssh-keygen -t rsa 

---
deb http://mirrors.tuna.tsinghua.edu.cn/kali kali-rolling main contrib non-free 

deb-src https://mirrors.tuna.tsinghua.edu.cn/kali kali-rolling main contrib non-free 

---

apt-get install fcitx 
apt-get install fcitx-googlepinyin

Emacs markdown

---

新版本乱码问题

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

#https use iso_yuan

sudo apt install apt-transport-https ca-certificates

---

# common tools

mtr、tshark、htop
