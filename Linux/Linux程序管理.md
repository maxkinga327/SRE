# Linux程序管理
###### tags: `Linux`
# 1. 認識程序與程式(process &program)
 ![](https://i.imgur.com/5hwXdvf.jpg)
程式 program 一定要有執行權限 chmod +x
執行程式→載入記憶體→procsee
process ID =PID

---
# 2. 顯示程序資訊
sudo apk add procps 安裝全功能PS命令
ls -al/bin |grep ps →驗證
sudo nano /etc/profile 程式任何帳號登入都會執行
下面新增
alias ps='ps -eo user,pid,cmd,%mem,%cpu ’
alias dir=‘ls -alh’
alias ping=‘ping -c 4’
`ps -eo user,pid,cmd,%mem,%cpu | head -n 5`
![](https://i.imgur.com/QOhnafc.jpg)

`ps -eo user,pid,cmd,%mem,%cpu --sort=-%mem | head -n 6`
![](https://i.imgur.com/JoHBLZK.jpg)
`ps -eo user,pid,cmd,%mem,%cpu --sort=-%cpu | head -n 5`
![](https://i.imgur.com/fUXWNuj.jpg)
ps -aux 所有程序的執行者
top 效能分析工具 1 cpu 切換 q 離開
# 3. 子程序與父程序: $$與 $PPID

`echo 'xxx' > 檔名.sh ; chmod +X 檔名.sh`
process 有父子關係
pstree -ph init(1)第1個 alpine
        systemd(1)第1個 ubuntu
![](https://i.imgur.com/xYDckqr.jpg)
echo $$ 自己 $PPID 爸爸
# 4. 程式與環境變數
程式變數不可繼承
![](https://i.imgur.com/c2VcwmB.jpg)
PLACE 帶變數  所以最後會顯示
![](https://i.imgur.com/Wk73DgQ.jpg)

stty XX undef  susp=ctrl+z  intr+ctrl+c
kill -9 強迫 kill -2 正常中斷
10.用 $ nice -n 改變程序優先順序
優先順序高: openssh mariadb 伺服器
nice -n  19友好度加優先減

uname -r kernel 版本
現在流行的系統 centos 防火牆高於ubuntu 內建seccomp
