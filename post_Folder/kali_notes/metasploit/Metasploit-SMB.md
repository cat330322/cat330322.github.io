# Metasploit-SMB
--

nmap -p 445 192.168.78.160 //Win7主机的445端口扫描

msfconsole

search smb_version

use auxiliary/scanner/smb/smb_version

show options

set rhosts 192.168.78.160

run
