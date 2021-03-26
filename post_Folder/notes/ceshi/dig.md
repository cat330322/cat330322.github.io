#dig
---

查询域名信息
$ dig  qq.com
dig 命令默认的输出信息可以分为 5 个部分。

第一部分显示 dig 命令的版本和输入的参数。

第二部分显示服务返回的一些技术详情，比较重要的是 status。如果 status 的值为 NOERROR 则说明本次查询成功结束。

第三部分中的 "QUESTION SECTION" 显示我们要查询的域名。

第四部分的 "ANSWER SECTION" 是查询到的结果。

第五部分则是本次查询的一些统计信息，比如用了多长时间，查询了哪个 DNS 服务器，在什么时间进行的查询等等。

查询CName记录

$ dig qq.com CNAME
从指定的 DNS 服务器上查询
$ dig qq.com CNAME @8.8.8.8
如果不指定 DNS 服务器，dig 会依次使用 /etc/resolv.conf 里的地址作为 DNS 服务器：

控制显示结果
$ dig +short qq.com
跟踪整个查询过程
$ dig +trace qq.com
查询域的MX记录
$ dig qq.com MX
查询域的TTL记录
$ dig qq.com TTL
仅查询答案部分
$ dig qq.com +nocomments +noquestion +noauthority +noadditional +nostats
反向查询

$ dig -x 8.8.8.8 +short
