
agent
---

proxychains

sudo proxychains ping www.baidu.com

---

privoxy

修改配置文件/etc/privoxy/config

修改listen-address 127.0.0.1:11080

forward-socks5 / 127.0.0.1:11080 . 

forward baidu.com .

---

export http_proxy="127.0.0.1:8118"
export https_proxy="127.0.0.1:8118"
export ftp_proxy="127.0.0.1:8118"
