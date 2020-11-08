ufw

---

ufw enable/disable:打开/关闭ufw

ufw status：查看已经定义的ufw规则

ufw default allow/deny:外来访问默认允许/拒绝

ufw allow/deny 20：允许/拒绝 访问20端口,20后可跟/tcp或/udp，表示tcp或udp封包。

ufw allow/deny servicename:ufw从/etc/services中找到对应service的端口，进行过滤。

ufw allow proto tcp from 10.0.1.0/10 to 本机ip port 25:允许自10.0.1.0/10的tcp封包访问本机的25端口。

ufw delete allow/deny 20:删除以前定义的"允许/拒绝访问20端口"的规则
