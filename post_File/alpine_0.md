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

apk u