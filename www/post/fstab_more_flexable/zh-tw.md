由於樹梅派上的小小32G隨身碟快要沒有辦法支撐系統資料，所以我就翻出一個沒有在用的隨身硬碟<br>
使用常用的硬碟當然要加到fstab中阿，不然每一次開機都要手動mount很麻煩餒，再加上我有看到網路上說fstab中最好是寫UUID不然硬碟位置重新排列會很更麻煩，於是我便跟著網路的說明做了下去...
<br>
然後就在下一次的開機過程中<br>
樹梅派打不開了😑😑<br>

當下的心急如焚，一心只想要讓裝置重新上線，不然我的窗簾就關不起來了(其實網頁掛掉沒有甚麼關係)，但是樹梅派開機失敗就會卡在那個機車的開機頁面，沒有辦法SSH過去。所以我又把micro hdmi線找出來，接上之後就是fstab UUID設定錯誤，但是也沒有辦法更改，我也不知道應該說甚麼😭😭<br>

### 解法
<ol>
<li>找上另一台可以用的電腦，接上樹梅派的開機碟(隨身碟或是SD卡)</li>
<li>修改cmdline.txt檔，在最後面接上 init=/bin/sh(圖一)</li>
<li>接回樹梅派開機，然後會進入奇怪的command line模式</li>
<li>重新掛載根目錄(取得編輯權限，不一定會一次成功) mount -o remount, w /</li>
<li>把/etc/fstab修成正常的模樣(如下)</li>
<li>再用另一台電腦把新增的 init=/bin/sh去掉</li>
<li>然後樹梅派就復活了</li>
</ol>

### 更有容錯空間的fstab寫法
```bash
UUID=123456 /mnt/usb auto defaults,noatime,nofail 0 0
```
這樣就算失敗也不會卡在開機頁面\n而我也順道把UUID改成PARTUUID就正常許多了

### UUID及PARTUUID怎麼看？
利用 blkid 工具，所以我是先用 blkid輸出資料到一個文件中<br>
再用vim從文件貼到fstab中<br>
像這樣：
```bash
sudo blkid >> tmp.txt
sudo vim tmp.txt #取出磁碟UUID
sudo vim /etc/fstab # 新增磁碟
```


###### Tues Feb 9 2021 08:00:00 GMT+0800 (Taipei Standard Time)