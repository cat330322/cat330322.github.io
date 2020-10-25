# osscan-Dnmap
---

一、Dnmap是什么？和Nmap啥区别？ Dnmap是一个用python编写的分布式扫描的nmap扫描框架，它提供强大的网络扫描功能。但在很多渗透场景中，需要渗透测试人员从多个终端发起扫描任务，从而实现快速扫描大型网络，或规避IP限制等安全策略，在这种场景下使用Nmap就有它的局限性了，而dnmap就是为了满足这种分布式需求而设计的。 Dnmap是一个分布式扫描工具，采用C/S结构。用户在服务器端指定要执行的扫描命令列表，客户端则读取命令进行扫描，并将扫描结果提交给服务器。这样，可以实现多人协作扫描的效果，这就是Dnmap的使用场景以及和普通Nmap的区别！

 二、Dnmap支持参数有哪些？ 第一部分：Dnmap_client参数： -s，--server-ip dnmap服务器的IP地址。 -p，--server-port dnmap服务器端口。 Dnmap端口默认为46001 -a，--alias你的名字别名，所以我们可以给你信任你的帮助。可选择 -d，--debug调试。 -m，-max-rate强制nmaps命令最多使用这个速率。有用的减缓nmap。添加--max-rate参数。 第二部分：dnmap_server参数： -f，--nmap-commands Nmap命令文件 -p， - 端口我们侦听连接的TCP端口。 -L，--log文件日志文件。默认为 /var/log/dnmap_server.conf。 -l，--log级日志级别。默认为信息。 -v，--verbose_level详细级别。提供1到5之间的数字。默认值为1.级别0表示安静。 -t，--client-timeout在标记客户端离线之前，我们应该等待多少时间。我们还记得它的价值观，以防万一它回来了。 -s，--sort字段来排序静态值。您可以选择：Alias，#Commands，UpTime，RunCmdXMin，AvrCmdXMin，Status -P，--pem-file pem文件用于TLS连接。默认情况下，我们在当前目录中使用随服务器提供的server.pem文件。

 三、Dnmap如何进行实战使用？ 1、证书文件生成 因为dnmap自带的用于TLS的pem文件证书过于老旧，得重新生成一个pem证书，客户端才能正常和服务器进行连接通信。 openssl req -newkey rsa:2048 -new -nodes -x509 -days 3650 -keyout key.pem -out server.pem 2、将新生成的私钥重定向或追加到server.pem证书后面 cat key.pem >> server.pem 3、创建nmap命令文件 Vim nmap.txt 4、使用dnmap_server文件启动dnmap的服务端 dnmap_server -f nmap.txt -P server.pem -f 要执行的nmap命令的文件 -P 用于TLS连接的server.pem 5、使用dnmap_client文件启动dnmap多个客户端 dnmap_client -s 192.168.1.53 -s dnmap的服务器地址 -p dnmap服务器的端口号，默认是46001 6、前往nmap_results目录查看执行结果 ls nmap_results/

