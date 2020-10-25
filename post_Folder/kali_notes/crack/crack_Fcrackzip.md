# crack_Fcrackzip
---

Fcrackzip是一款专门破解zip类型压缩文件密码的工具，工具小巧方便、破解速度快，能使用字典和指定字符集破解，适用于linux、mac osx 系统。


 apt-get install fcrackzip 


 fcrackzip –help 

使用命令 zip --password 12345 test.zip test 将test文件压缩为格式为zip的压缩文件，密码为 password 压缩文件名为 test.zip。



尝试使用暴力破解对这个zip文件进行破解。

使用命令 fcrackzip -b -c ‘1’ -l 1-6 -u test.zip ，-b(使用暴力破解方式)，-c ‘1’（密码中只有数字），-l（密码长度为1-6），-u（目标名称）


使用字典文件对其进行破解。

创建一个字典，将其命名为pwd。（字典文件在百度上面有很多现成的，也可以使用kali里面的字典生成软件生成字典，由于这里我在进行演示，所以随便输入了几个数字）

使用命令 fcrackzip -D -p /root/pwd -u test.zip 其中-D（使用字典破解），-p(字典路径)，-u（目标名称）

可以看到我们使用字典再次破解了这个压缩包密码。
