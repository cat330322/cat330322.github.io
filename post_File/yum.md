yum

---

自动搜索最快镜像插件：yum install yum-fastestmirror

安装yum图形窗口插件：yum install yumex

查看可能批量安装的列表：yum grouplist
安装

　　yum install              #全部安装
　　
　　yum install package1     #安装指定的安装包package1
　　
　　yum groupinsall group1   #安装程序组group1

　　yum update               #全部更新
　　
　　yum update package1      #更新指定程序包package1
　　
　　yum check-update         #检查可更新的程序
　　
　　yum upgrade package1     #升级指定程序包package1
　　
　　yum groupupdate group1   #升级程序组group1

　　yum info package1      #显示安装包信息package1
　　
　　yum list               #显示所有已经安装和可以安装的程序包
　　
　　yum list package1      #显示指定程序包安装情况package1
　　
　　yum groupinfo group1   #显示程序组group1信息yum search string 根据关键字string查找安装包

　　yum remove &#124; erase package1   #删除程序包package1
　　
　　yum groupremove group1             #删除程序组group1
　　
　　yum deplist package1               #查看程序package1依赖情况

　　yum clean packages       #清除缓存目录下的软件包
　　
　　yum clean headers        #清除缓存目录下的 headers
　　
　　yum clean oldheaders     #清除缓存目录下旧的 headers
