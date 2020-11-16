alpine_0
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

rc-update add docker boot #增加一个服务

rc-update del docker boot #删除一个服务

rc-service sshd start #启动一个服务

rc-service sshd stop  #停止一个服务

rc-service sshd restart  #重启一个服务

openrc single #更改为single运行级
