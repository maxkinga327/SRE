# Linux 開機流程
###### tags: `Linux`
![](https://i.imgur.com/R1uUEDe.jpg)

# 1. BIOS 
開機時做硬體裝置自我檢測pst
會去找第一個可開機的裝置的第一個磁區MBR
# 2. MBR  磁碟分割表
硬碟的第一個磁區(可以開機的裝置)
大小 512 Bytes 446 Bytes
儲存開機管理程式（Boot Loader）
4 個 16 Bytes 儲存磁區分割表
2 Bytes 儲存檢查標誌
446 + (4*16) + 2 = 512
尋找bootloader
![](https://i.imgur.com/0DihcgV.png)

GPT磁碟分割表
![](https://i.imgur.com/6nVu6hV.png)


GPT把磁區使用(LBA)一個有 512 Bite 共有128個主要磁區
LBA 2-33 用來當作儲存磁碟分割資訊
後面當作備份
為什麼有128個磁區
(33-2+1(32個LBA))*512(Bite)/128(一個partition需要128個bite) =128(個磁區)

# 3. Boot Loader 
從硬碟開機 找到作業系統的kernel
MBR中的開機管理程式，負責載入(kernel)到記憶體並移交控制權給 Linux 核心(kernel)
syslinux isolinux grub2 會取選擇其中一個
 光硬碟     光碟     硬碟
載入init & boot 到記憶體裡面


# 4. kernel
當Kernel初始化時,會檢查I/O裝置(cpu,ram,人機介面)
會將檢查資訊載入initram
掛載上來會先載入initram /proc /dev
init在任何linux都是壓縮過的檔案
解壓縮init到記憶體裡面(記憶體讀取比硬碟快)讀取initrd


# 5. init
第一個開機程式:system.d 
Damon背景  
(sshd dhcpsever
busybox裡的httpwebsever )
login 前景
(帳號密碼)

# 6. user/passwd
登入後第一個執行的 /etc/profile
設定alias 設定開機顯示網卡IP位置→
/bin/bash or sh (/etc/passwd)帳號使用哪個自己決定→
$ 工作環境
1.home directory 2.environment ($USER $IP 自己做的 從profile裡面 $PATH) echo $PATH 清除export PATH= 恢復 exit which 套件位置
每個帳號都有個家/home/帳號

# 7. File system 
1.permission
r→ls.cat.head.tail
w→mkdir.touch.rm.rm -r
x→cd ~~source~~
2.setuid.setgid.skicky

setuid
使用 setuid 權限的可執行文件的例子是 passwd，我們可以使用該程序更改登錄密碼。我們可以通過使用 ls 命令來驗證

setuid 位對目錄沒有影響

setgid
setgid （設置組 ID）位對文件和目錄都有影響。在第一個例子中，具有 setgid 位設置的文件在執行時，不是以啟動它的用戶所屬組的權限運行，而是以擁有該文件的組運行。換句話說，進程的 gid 與文件的 gid 相同。
當在一個目錄上使用時，setgid 位與一般的行為不同，它使得在所述目錄內創建的文件，不屬於創建者所屬的組，而是屬於父目錄所屬的組。這個功能通常用於文件共享（目錄所屬組中的所有用戶都可以修改文件）

目錄所有者、組和其他用戶對該目錄具有完全的權限（讀、寫和執行）。sticky 位在可執行位上用 t 來標識。同樣，小寫的 t 表示可執行權限 x也被設置了，否則你會看到一個大寫字母 T。


sticky 位的工作方式有所不同：它對文件沒有影響，但當它在目錄上使用時，所述目錄中的所有文件只能由其所有者刪除或移動。一個典型的例子是 /tmp 目錄，通常系統中的所有用戶都對這個目錄有寫權限。所以，設置 sticky 位使用戶不能刪除其他用戶的文件：

setuid、setgid 和 sticky 位分別由數值 4、2 和 1 表示
例如，如果我們要在目錄上設置 setgid 位，我們可以運行：
$ chmod 2775 test



3.umask
umask 的用法與 chmod 相反, chmod 是在 “000” 上面 “增加” 權限, 而 umask 則是在 “666” 基礎上 “減少” 檔案權限; 及在 “777” 基礎上 “減少” 目錄權限。這個講法可能有點混亂, 看看實際例子更易明白, 
例如:umask 022 上面用 umask 設定預設權限為 022, 
即預設檔案權限設定為 644, 因為 [666 – 022 = 644]; 及預設目錄權限設定為 755, 因為 [777 – 022 = 755].
# 8. Process
![](https://i.imgur.com/17hH2y1.jpg)
# 9. Network
IP private up 
GW 上網的出口
routing
iptable
DNS
