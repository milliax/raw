### 前言
Minecraft是一款老少咸宜的好遊戲，但是要讓遊戲變得更好玩，就要跟朋友一起玩，於是我便犧牲了我的電腦以跟同學一起玩Minecraft😥😥，獨樂樂不如眾樂樂嘛(其實我只是想要把同學推下去)

### 事前準備
準備一台電腦，什麼作業系統都可以，linux最佳

### 著手安裝-Linux
```bash
1. sudo apt update
2. sudo apt install default-jre #(1.16版本以前)
```
接著到minecraft官網下載server.jar

之後就可以執行拉：
```bash
java -Xmx1G -Xms1G -jar server.jar nogui
```
如果記憶體不夠可以自己調整<br>
Server配置
建議：<br>
![minimum_requirements](https://raw.sivir.pw/www/photo/3b019ef6695785ae3c21aeb16d32db2f5c7f6365.png)
<br>

### 正言 --- 待補

### 續
但是每次都要開伺服器都要打這麼一大串真的非常的不方便<br>
所以我就把它存在sh檔中，順便用tmux執行，這樣就可以做其他的事(在windows中還可以直接按叉叉，他一樣會繼續執行)

```bash
# run_minecraft.sh
/bin/sh
cd Minecraft_Server/
tmux new-session -s mine-java sudo java -Xms2G -Xmx4G -jar server.jar nogui
```
最後
```bash
sudo chmod +x run_minecraft.sh
```
之後只需要執行sh黨就可以執行了