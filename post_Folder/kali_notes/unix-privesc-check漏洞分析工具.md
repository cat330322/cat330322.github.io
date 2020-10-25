# unix-privesc-check漏洞分析工具
---

一、unix-privesc-check是什么？ 它是一款Kali Linux自带的提权漏洞检测工具。它是一个Shell文件，可以检测系统的错误配置，以发现可以用于提权的漏洞。该工具适用于安全审计、渗透测试和系统维护等使用场景。它可以检测与权限相关的各类文件的读写权限，如认证相关文件、重要配置文件、交换区文件、cron job文件、设备文件、其他用户的家目录、正在执行的文件等等。如果发现可以利用的漏洞，就会给出提示warning。

 二、unix-privesc-check扫描特别说明？ unix-privesc-check并不会检测所有提权漏洞的潜在情况。它只是快速进行检测，并以简洁的方式给出提权漏洞相关的建议，大大减少用户在文件权限检测方面的枯燥工作的量。

 三、unix-privesc-check使用效果如何？ 此工具效果还可以，但只能以标准或详细模式来扫描本地，不能远程扫描服务器。因为使用这个工具前，你需要先有权限进入别人的服务器，再去运行unix-privesc-check 四、unix-privesc-check怎么使用？【选择不同漏洞扫描模式】 用法: unix-privesc-check { standard | detailed } 举例：unix-privesc-check standard unix-privesc-check detailed

