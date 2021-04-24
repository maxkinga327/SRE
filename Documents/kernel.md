# kernel

電腦系統的kernel
kernel space 要有root權限

![](https://i.imgur.com/I5oRG97.jpg)


**Kernel Space**
即Linux kernel的運作空間. 基本上, 只要是CPU可以管的硬體, kernel space的程式就可以透過machine code來操作該硬體. 所以我們可以認為kernel space可以執行比user space更高權限的動作.
**User Space**
即user process的運作空間. 基本上是比較受限的, 除了一些沒有傷害的行為之外, 基本上都不能做. 若需要在user space調用系統資源(如I/O作業), 則必須通過system call.
shell 例:car unzip
APP 例: http busybox

![](https://i.imgur.com/hF2QdJr.png)


![](https://i.imgur.com/9fPoJHa.gif)
此圖最重要3大功能 偽裝 防火牆 虛擬IP
B路徑須設定路油表


`sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE`

`sudo iptables -t nat -A POSTROUTING  ! -d 10.233.0.0/24 -o eth0 -j MASQUERADE`

10.233.0.0/24 以外的全部偽裝

-t table -A Append to chain
-o output -j jump -d destination

sudo iptables -I INPUT -s 10.233.0.129 -j DROP

sudo iptables -t nat -F  sudo iptables -F 
-F 刪除設定



https://serverfault.com/