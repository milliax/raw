隨著時間的演進，Microsoft 重新開發了Visual Stuio Code 擺脫了 Visual Studio的肥胖臃腫，其輕便及跨平台的特性，使的他廣為流傳。不知道你是否有用過Arduino IDE ，除了介面非常陽春之外，他還沒有內建自動選字的功能<br>
蛤？你說Arduino IDE沒有自動選字？(可是連dev C++都有ㄝ)<br>
那我們就把Arduino IDE跟有intelliSence 的Visual Studio Code 並在一起ㄅ

### 需要的軟體或功能
Arduino IDE： 用於當作visual studio code的編譯器[載點](https://www.arduino.cc/en/software)<br>
Visual Studio Code： [今天的主角](https://code.visualstudio.com)<br>
VS code Arduino 擴充元件： 在 VS code 中的商城安裝

### 設定編輯環境
首先，打開VS code 然後按下 ctrl + , ，進入設定頁面<br>
在 Extention 中找到 Arduino Configuration 並在 Arduino Path 中填入你Arduino IDE安裝的位置

windows： C:\\Program Files (x86)\\Arduino<br>
mac： 我沒有所以我不知道<br>
linux： 就解壓縮的地方

這樣VS code就可以透過 Arduino IDE 編譯了!!!<br>
接下來建立Arduino檔案，在每一次建立檔案時，按下F1<br>
並輸入
```bash
>Arduino: Initialize
```
如此他就會跳出提示，第一次他會安裝VS code必要的檔案，然後就跳掉<br>
所以可能需要再次輸入上個指令

往後只要進入到*.ino的檔案時，由上角就會出現上傳及驗證的按鈕<br>
下方則是序列埠及Arduino機型設置
<br>
<br>
這樣輕鬆幾個步驟就可以有進階版的Arduino編譯器了