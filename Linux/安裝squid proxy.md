# 安裝squid proxy

Proxy Server
代理伺服器（Proxy），是一種重要的電腦資安功能，也是特殊的網路服務，允許用戶端透過它與另一個網路服務進行非直接的連線，也稱「網路代理」。代理伺服器有利於保障網路安全，防止攻擊。

代理伺服器（proxy server）設置的兩個主要目的：加強網路安全及提升網路使用效率。 

$ sudo apk update
$ sudo apk add squid
啟動squid
$ sudo rc-service squid start
#查看squid運行狀態
$ sudo rc-service squid status
#讓squid開機自動執行
$ sudo rc-update add squid

檔案 /etc/squid/squid.conf
squid的修改全都在這個檔案裡所以很重要
#備分
~$ cp /etc/squid/squid.conf /etc/squid/squid.conf.bk
#修改完檔案後可以用以下指令套用
~$ squid -k reconfigure


```
acl mysurfers srcdomain .example.com   
#mysurfers 定義為來自 .example.com 中的所有使用者 (由 IP 的反向查閱確定)。
acl teachers src 192.168.1.0/255.255.255.0   
#teachers 定義為 IP 位址以 192.168.1. 開頭的電腦的使用者。
acl students src 192.168.7.0-192.168.9.0/255.255.255.0 
#students 定義為 IP 位址以 192.168.7.、192.168.8. 或 192.168.9. 開頭的電腦的使用者。
acl lunch time MTWHF 12:00-15:00 
 #lunch 定義為星期一至星期五的中午到下午 3 點之間的某個時間
acl dropfb dstdomain .facebook.com 
#控制不能去的目標網站的主機名稱

```

http_access deny localhost
http_access allow teachers
#允許teachers 使用proxy的http連線功能
http_access allow students lunch
#允許students 使用proxy的http連線功能，但限定在lunch時間
http_access deny all
