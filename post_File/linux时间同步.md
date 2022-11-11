date

```
date -s "20220509 8:56:00"  #yyyymmdd hh:mm:ss

hwclock --show

hwclock --systohc
```

```
chrony时间同步
vim /etc/chrony.conf
systemctl status chronyd -l
```



