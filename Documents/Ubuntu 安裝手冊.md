# Ubuntu 安裝手冊
###### tags: `安裝手冊`

---
選取English,這裡沒有中文選項
![](https://i.imgur.com/fw5Wxzp.png)

---
台灣預設都是使用美式鍵盤，選擇English(US)
![](https://i.imgur.com/2pKE4VD.png)

---
ens33為Ubuntu Server的網卡名稱，虛擬機IP位址為DHCPv4給的
![](https://i.imgur.com/1Qioy6m.png)

---
Proxy address為
公司內部使用者只允許透過一個地址(網路終端)去連網，是大單位、或是很保護資安的公司才會需要設定。
![](https://i.imgur.com/aNSG9E5.png)

---
Canonical跟各地公司合作，將Ubuntu對外發行的版本，備份在合作公司伺服器上，以便附近使用者使用。
![](https://i.imgur.com/1OKJO1P.png)

---
用整個硬碟，避免檔案被切割便於管理。LVM，Logical Volume Manager，為整合多個實體partition 在一起，讓這些partitions 看起來就像是一個磁碟。若預想到日後空間不足，可點此選項。
![](https://i.imgur.com/F86weaT.png)

---

何謂ESP?EFI?
ESP為開機或顯示錯誤的緩衝區
EFI取代傳統BIOS介面，並且拋去BIOS需要長時間的自檢問題，讓硬體初始化和引導系統變快速簡潔。而EFI在微軟的支持下可以使用2.2TB以上啟動硬碟(Intel的則是2.1TB以上) ，BIOS在大容量硬碟如果沒有借助第三方軟體就只能當數據硬碟使用。Linux 在MBR中有2.2TB限制，大於2.2TB時就需要GUID分區表(GPT)結構，系統安裝的時候會使用get的切割方式(MBR是主啟動磁區，最大容量為2.1TB。GPT支援硬碟容量18EB，最大支援128個分區)
![](https://i.imgur.com/54CTUcU.png)

---
依據每個人電腦規格不同，這裡也會不相同  點選後會再做確認
點選Continus
![](https://i.imgur.com/H3eMlXA.png)

---
設定帳號密碼
Username是帳號名稱
Username只能輸入0到9跟小寫英文字母
第二個電腦名稱
![](https://i.imgur.com/YDH8FwF.png)

---
是否安裝OpenSSH
如果需要遠端連線就需要在此設定，這邊的打叉代表確認安裝喔!
![](https://i.imgur.com/tyOi1wA.png)

---
安裝Linux 套件
此為snap安裝，它徹底解決Linux依賴性的問題，也更擁有更佳穩定和安全特性。
依照每個人的個人需求安裝。
![](https://i.imgur.com/LuZnBN3.png)

---
等待安裝，安裝完成，點選reboot
![](https://i.imgur.com/OTy5Buu.png)

---
等待開機
跑完後按Enter
![](https://i.imgur.com/e092pCA.png)
