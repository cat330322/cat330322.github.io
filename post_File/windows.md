### windows

```
###
netstat -o 4
netstat -ano | findstr 9014
tasklist
tasklist |findstr java.exe
taskkill /pid 4612 /f
tasklist /fi "pid gt 10000"
eq, ne, gt, lt, ge, le

###
netstat -ano |findstr "端口号"
tasklist |findstr "进程id号"
taskkill /f /t /im "进程id或者进程名称"
```