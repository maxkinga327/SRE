# 建置DHCP server
$ sudo apk update
$ sudo apk add dhcp
編寫DHCP server設定檔

```
#!/bin/bash
subnet 172.30.32.0 netmask 255.255.224.0 {
  option domain-name "right.io";
  option domain-name-servers 172.30.63.254, 8.8.8.8;
  option routers 172.30.63.254;
  range 172.30.48.0 172.30.63.249;
}
```
subnet 該區網段 32+16 48
doamin -name-severs  從哪裡進去
routers 從哪裡進去
range dhcp 範圍 

啟動DHCP server
$ sudo rc-update add dhcpd

$ sudo rc-service dhcpd start

用戶端取得網路參數的流程：
用戶端利用廣播封包發送搜索 DHCP 伺服器的封包
伺服器端提供用戶端網路相關的租約以供選擇
用戶端選擇 DHCP 伺服器提供的網路參數租約，並回報伺服器
伺服器端記錄該次租約行為，並回報用戶端其確認的回應封包資訊


![](https://i.imgur.com/6m1IXj7.png)


![](https://i.imgur.com/BiKETKp.png)


![](https://i.imgur.com/jVBRmG1.png)


![](https://i.imgur.com/ztmwBn6.png)

