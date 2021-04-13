# Alpine安裝手冊
###### tags: `安裝手冊`
**安裝過程使用問答方式,若回答想要反悔，只能透過 Ctrl + C 重來。**
* 登入帳號 預設帳號為root
![](https://i.imgur.com/uT0KVwt.jpg)


---
* 安裝 apline 輸入:setup-alpine
![](https://i.imgur.com/udJZaTw.jpg)
---
* 設定鍵盤配置與語系 兩個都是輸入: tw
![](https://i.imgur.com/rEQhaFX.jpg)
---
* 輸入電腦名稱 預設為localhost 可自行更改
![](https://i.imgur.com/FTMoG8P.jpg)
![](https://i.imgur.com/Aqa2SbP.jpg)
電腦名稱只能英文小寫.數字.符號-

---
* 設定網路卡
![](https://i.imgur.com/9Vm11y5.jpg)
選項1預設為第一個網卡eth0
選項2預設為DHCP 也行更改自訂IP

---
設定root密碼 可自訂
![](https://i.imgur.com/b0oV2FH.jpg)
需輸入兩次確認

---
* 設定地區
![](https://i.imgur.com/5F4Mk38.jpg)
設定Asia(亞洲) 下個選項Taipei(第一個字大寫)

---
* 設定 proxy 與 ntp
![](https://i.imgur.com/RBfCIyN.png)
選項1 使用預設 如有可自行設定
選項2 使用預設 chrony (網絡時間協議)

---
* 設定 lpine 與 ssh
![](https://i.imgur.com/yWgbkvz.jpg)
選項1  選項2使用預設 openssh

---
* 將Alpine安裝到硬碟
![](https://i.imgur.com/36kpLTk.jpg)
選項1 輸入sda
選項2 輸入sys 作為系統碟
選項3 清除硬碟(等於格式化)輸入y(yes)

---
完成後輸入`reboot`重啟




