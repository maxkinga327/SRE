# Container 運作架構
###### tags: `Linux`
![](https://i.imgur.com/ZBVEwHx.png)
# Container 核心關鍵技術
![](https://i.imgur.com/GPaM5xH.png)

![](https://i.imgur.com/vm1N7CK.png)

# 檢視 ctn 虛擬主機的 Namespace
ls -l /proc/self/ns/

![](https://i.imgur.com/8VNY3L1.png)

# Isolating the Hostname 隔離主機名
![](https://i.imgur.com/WJu4z0B.png)
![](https://i.imgur.com/mW71SJg.png)
兩個電腦主機的Namespace ID不一樣，所以在裡面做變更並不會影響虛擬主機
# Isolating Process IDs 隔離進程ID
![](https://i.imgur.com/4pOdbXa.png)
sudo unshare --pid --fork sh
在沒加 --fork 的情況下 隔離的程序無法有子程序
![](https://i.imgur.com/jnySZv1.png)
![](https://i.imgur.com/p9AhpQj.png)
sudo unshare --pid --fork --mount-proc sh
在這container kill -9 1 無法刪除
限制root 不再是無所不能
![](https://i.imgur.com/6Vb32h1.png)
--mount-proc 這參數, 會將 sh 的 PID Namespace, 掛載到 ctn 的 /proc 目錄, 由以下命令, 得知 /proc 目錄被掛載二次
![](https://i.imgur.com/GPZGa49.png)
exit 會自動卸載 /proc 目錄的第二次掛載
# slirp4netns 建立虛擬網路
![](https://i.imgur.com/szmLAqo.png)
就有點類似以前的網路 網卡撥號→中華電信→上網
tap0(模擬網卡)→建立虛擬網路給container使用 無上網功能
→主機網卡
# 實做 slirp4netns
![](https://i.imgur.com/odA26ns.png)
![](https://i.imgur.com/6400Vh8.png)
創出一個網路空間 主機跟虛擬空間還是會顯示slirp 的程序
只是PID 不會相同
![](https://i.imgur.com/oGBlDOU.png)
sudo apk add slirp4netns 安裝
sudo modprobe tun 打開模組
`sudo slirp4netns --configure  --disable-host-loopback   --mtu=65520 18676 tap`
![](https://i.imgur.com/iG2nhqM.png)


![](https://i.imgur.com/BEA4q7v.png)

[註] 按 ctrl + c 可停止上面命令執行, unshare 終端機中的 tap0 網卡會自動移除 

![](https://i.imgur.com/pOlQlrh.png)
在unshare 終端機上產生一張tap0的網卡
可以藉由這張網卡進行上網

![](https://i.imgur.com/LkxuAC8.png)

# 準備 Chroot 檔案系統目錄
![](https://i.imgur.com/XKSmGQy.png)

# 準備 Container 電腦的系統檔案及目錄
![](https://i.imgur.com/EUUYg9v.png)
![](https://i.imgur.com/fx9lXJG.png)

cp /bin/sh  r2d2/rootfs/bin

cp /lib/ld-musl-x86_64.so.1  r2d2/rootfs/lib/

sudo chown -R root:root  r2d2/rootfs
chown設定檔案所有者和檔案關聯組
把r2d2/rootfs改成root
# Isolating Process IDs and chroot --隔離進程ID和chroot
![](https://i.imgur.com/FaU0UZn.png)
dir r2d2/rootfs/proc
條列檔案及目錄的命令行
sudo unshare --pid --fork --mount-proc --uts -R r2d2/rootfs sh
![](https://i.imgur.com/AY8Am4w.png)
# 加入 Linux 的系統命令集 (busybox)
![](https://i.imgur.com/SO9JLuD.png)
把主機內的busybox 加到r2d2/rootfs/bin
![](https://i.imgur.com/zuLP8Bx.png)
whoami無法顯示是因為這裡沒有passwd所以無法顯示
但其他指令安裝busybox 捷近檔後都可以顯示
![](https://i.imgur.com/Z8vQDBE.png)
# 準備 Overlay2 檔案系統目錄
![](https://i.imgur.com/sfBjD2q.png)
# 建立與使用 Overlay2 檔案系統
![](https://i.imgur.com/Cv0fckx.png)
現在看到的in_both.txt是在upper資料夾內的檔案
寫資料進去merged的話會存於upper
merged 會立即顯上從最上面看到的畫面
就像兩片幻燈片一樣從最上面可以看到兩片的所有內容
# 使用 Overlay2 檔案系統
![](https://i.imgur.com/gtONBcK.png)
![](https://i.imgur.com/jHVPbSU.png)
![](https://i.imgur.com/TIzQM8I.png)
![](https://i.imgur.com/EROmUOU.png)


