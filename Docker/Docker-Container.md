# Docker-Container
###### tags: `Docker`
# Docker 命令運作圖 
![](https://i.imgur.com/RjpWXwW.png)

backup.tar
用於企業內部使用由於大企業禁止上網無法備份於光片中心只能將光碟檔打包存於隨身碟在傳至要使用其的電腦

Dockerfile
用來製作可以記錄下來以免忘記改什麼東西

1.Docker pull 下載光碟片(docker image)拉到images
2.產生container
3.Commit 燒光碟存於 images
4.將燒好的光碟推送至光片中心

# 搜尋與下載 Docker Image
![](https://i.imgur.com/XzRzRlZ.png)

# 建立與執行軟體貨櫃 (Container) 主機
![](https://i.imgur.com/yvsqRDW.png)

# 管理軟體貨櫃 (Container) 主機
![](https://i.imgur.com/PXlHaZf.png)

# 管理軟體貨櫃 (Container) 主機
![](https://i.imgur.com/BRX6j2f.png)

# 討論
![](https://i.imgur.com/voIOPep.png)

docker run --rm –-privileged --name=b3 -it busybox
加priivilged把這台container 的 capabilities 全部套用上去
不建議使用

# 建立 Alpine 軟體貨櫃主機
![](https://i.imgur.com/gZdxs7U.png)

# 建立 Busybox Httpd 網站伺服器
![](https://i.imgur.com/o2Jd1Rk.png)

# 製作 a1 image 並上載至 Docker HUB
![](https://i.imgur.com/8MVJTgO.png)

# 使用自製 a1 image 
![](https://i.imgur.com/RRAkwxB.png)

# 重建 n1 Container 並設定自動啟動
![](https://i.imgur.com/PilgQR4.png)

# Application Container 記憶體管理
![](https://i.imgur.com/wPRwMuw.png)

![](https://i.imgur.com/WbbhFYL.png)
發現需求不符可增加可減少
Scale up在這一台實體主機
運算字元可以上上下下
Scale out k8s來做
水平擴充(左左右右)
擴充其他container

# Application Container CPU 管理
![](https://i.imgur.com/a3y4NiG.png)

# Application Container IO 管理
![](https://i.imgur.com/6a24gLW.png)


