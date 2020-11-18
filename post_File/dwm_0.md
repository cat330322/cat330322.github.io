dwm_0
---

https://mirrors.ustc.edu.cn/alpine/latest-stable/main

https://mirrors.ustc.edu.cn/alpine/latest-stable/community

---

setup-xorg-base 

dwm dmenu st

---

apk add xrandr

xrandr --output default --mode 1600x900 640x480

cvt命令 自定义分辨率模式

---

fc-match -a | less   查看系统字体

apk add font-noto-cjk 亚洲字体

Noto Sans CJK SC

---

fcitx

---

xsetroot --help

xsetroot -name "cxj"

apk add alacritty

---

apk add rofi

rofi -show run 

---

apk del git make gcc g++ libx11-dev libxft-dev libxinerama-dev ncurses dbus-x11 firefox-esr adwaita-gtk2-theme adwaita-icon-theme ttf-dejavu

---

vi .xinitrc
exec dwm

vi ~/.profile
startx

---
