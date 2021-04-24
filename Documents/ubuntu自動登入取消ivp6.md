# ubuntu自動登入 取消ivp6
`sudo nano /lib/systemd/system/getty@.service`
ExecStart=-/sbin/agetty --autologin bigred --keep-baud 115200,38400,9600 %I $TERM
![](https://i.imgur.com/7qxKE4b.png)
取消ivp6
sudo nano /etc/sysctl.conf
新增net.ipv6.conf.all.disable_ipv6 = 1
sudo nano /etc/default/grub
改ipv6.disable = 1
![](https://i.imgur.com/iYkn4ht.png)
sudo nano /etc/default/grub
sudo update-grub
