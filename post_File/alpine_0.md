# alpine_0
---

root

setup-alpine

cn

vi /etc/ssh/sshd_config

sed -i 's/dl-cdn.alpinelinux.org/mirrors.tuna.tsinghua.edu.cn/g' /etc/apk/repositories

---

sed -i 's/dl-cdn.alpinelinux.org/mirrors.ustc.edu.cn/g' /etc/apk/repositories

---
/etc/apk/repositories

https://mirrors.ustc.edu.cn/alpine/latest-stable/main

https://mirrors.ustc.edu.cn/alpine/latest-stable/community


---

rc-status

rc-update add docker boot #开机启动增加一个服务

rc-update del docker boot #删除一个服务

rc-service sshd start #启动一个服务

rc-service sshd stop  #停止一个服务

rc-service sshd restart  #重启一个服务

openrc single #更改为single运行级

---

apk add ttf-dejavu 中文字体

neofetch 

screenfetch

fc-cache -f 字体缓存

fc-list 字体列表

fc-match -a 字体查看

---

apk add 下载

apk del openssh openntp vim 删除

apk update #更新最新本地镜像源

apk upgrade #升级软件

apk add --upgrade busybox #指定升级部分软件包

apk search #查找所有可用软件包

apk search -v #查找所有可用软件包及其描述内容

apk search -v 'acf*' #通过软件包名称查找软件包

apk search -v -d 'docker' #通过描述文件查找特定的软件包

apk info #列出所有已安装的软件包

apk info -a zlib #显示完整的软件包信息

apk info --who-owns /sbin/lbu #显示指定文件属于的包
