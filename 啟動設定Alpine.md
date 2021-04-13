# 啟動設定Alpine
###### tags: `安裝手冊`
* 建立使用者帳號
輸入:`adduser "帳號"` 
輸入完再輸入兩次自訂密碼即可建立

---
* 檢查網路 
![](https://i.imgur.com/MQps7xF.jpg)
網路不通安裝與連線無法使用，一定要先檢查
可使用 `ping -c 2 8.8.8.8` 來測試看看網路是否有通。 (-c 2 ping次數2次)

---
* 安裝 套件
輸入`apk add` ...
後面可自己決定要安裝什麼
實用的例如:undate nano.sudo.bash

---
* 自行設定 ip
輸入`nano /etc/network/interfaces`
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static "從DHCP改成static"
    address "自行設定"
    netmask "自行設定"
    gateway "自行設定"
```
設定完輸入 `ifconfig or ip addr` 兩個選一可察看是否設定成功

---
