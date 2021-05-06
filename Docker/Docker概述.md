# Docker 軟體貨櫃
###### tags: `Docker`
![](https://i.imgur.com/wx4Pyic.jpg)
Docker的功用是解決Human errors人為錯誤
Docker 啟動需用到linux核心模組圖示左邊6項
sever中包括有圖示右邊3項
cluster叢集 可透過k8s自動化管理下面的電腦
由於自動化的管理，可減少人為錯誤的發生，達到系統穩定的目的
![](https://i.imgur.com/etpVhOm.png)
隔離出一個獨立的電腦container擁有自己的APP跟bins/libs相依檔 並藉由核心模組達到擁有獨立的目錄.網路.CPU.記憶體,網路.子程序.電腦名稱.使用者

![](https://i.imgur.com/Kv2B1F8.png)
背景程序  Docker daemon
提供一種一種高階命令，讓使用者可以理解的語言

# RunC
只會負責產生containerd
runc 符合OCI 規範的CLI工具 TCP/IP規範
runc 是以 golang 撰寫的函示庫
設定檔跟rootfs 給container使用
RunC 並不是只包含 Linux Namespace 及 chroot, 它還包含 CGroup

runc 命令內定執行帳號為 root, 而 rootfs 目錄的 Owner 是 bigred, 所以需將 rootfs 目錄的 owner 改為 root
`sudo chown root:root -R rootfs/`

Config.json是Container 設定檔 OCI組織設定
config.json設定檔中 nano config.json 
# 產生 OCI 標準的 Container 設定檔
$ runc spec
$ nano config.json 

設定 Container 檔案系統可讀寫 
Readonly 從ture 改成false 可讀可寫

# 建立 bb8 Container (啟用 Namespace)
![](https://i.imgur.com/qFxblIE.png)
sudo runc run bb8   會去找config.json抓資料

# 保護 Linux Kernel 系統目錄
![](https://i.imgur.com/VeTxbEs.png)

proc來源就是kernel
Seccomp 用來保護kernel

# 題目
1.請問透過 RunC 建立 Container 電腦, 需準備那些內容 ?
檔案系統目錄 跟 Config.json
Container 設定檔
2.請問 bb8 Container 電腦系統中, 所啟動的 sh 程序, 在 Host (ALP) 系統中, 是不是只是一個程序 (Process) ?
作業系統裡的process YES
3.請問 bb8 Container , 有開機程序嗎 ?NO 共用一個kernel 開機程序在kernel裡面

# containerd
負責管理container的一生
![](https://i.imgur.com/wVPSRyY.png)
IMAGE高手已經處理好的rootfs，下載下來使用
由這個ctr命令對containerd下達命令
檔案系統目錄 跟 Config.json 再經由runc開啟containerd
Containerd 原生管理命令 - ctr

# 安裝與啟動 Containerd
![](https://i.imgur.com/SfrOI4W.png)

# Containerd 原生管理命令 - ctr
![](https://i.imgur.com/nab0jC0.png)
創造container 名為b1
-tty虛擬終端機
每個終端機裡面run 貝殼程式
架設好containerd使用不再需要安裝軟體


# Docker
![](https://i.imgur.com/xoI0K8z.png)


安裝Docker就會一起安裝containerd runc
設定 Docker Daemon 自動啟動
$ sudo rc-update add docker boot

將 bigred 帳號加入 docker 群組後, 就不需使用 sudo 命令執行 docker
$ sudo addgroup bigred docker

重新開機 (一定要執行)
$ sudo  reboot

# 檢視 Docker 運作資訊
![](https://i.imgur.com/pZXPT2K.png)
docker info 顯示 Docker 版本
Server Version: 20.10.6
年.月.修改次數  修改次數越多越穩定
沒有任何 Container 執行時, 只有 dockerd 及 containerd 這二個 Daemon 在運作
 

# 檢視 Docker 運作資訊 - 執行 Container

![](https://i.imgur.com/HgoM7Tw.png)
Docker run 產生 container
Image 就是rootfs
-d 這台電腦可以背景執行
--rm指令就是離開container後自動被刪除

 OCI是一個組織 制定container的標準