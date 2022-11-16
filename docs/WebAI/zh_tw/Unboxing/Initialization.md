# 初始化設定 ( 第一次使用請看這裡 )

Web:AI 開發板的韌體中使用了 2 種晶片，分別是主晶片 ( K210 ) 和 Wi-Fi 晶片 ( ESP8285 )。
第一次使用 Web:AI 開發板之前，需要先設定 Wi-Fi 及對晶片做韌體更新，將開發板升級到最新版本，才能順利使用最全面的功能。

#### 設定頁面：[Wi-Fi 設定頁面](https://webai.webduino.io) ( 需要透過電腦的 Chrome 瀏覽器開啟 )

## 教學影片

歡迎參考下方教學影片：

<iframe src="https://www.youtube.com/embed/ZSGkZUQQXcI" allowfullscreen width="100%" style="aspect-ratio:728/410;border:none " ></iframe>

## 教學步驟：Wi-Fi 設定

當拿到 Web:AI 開發板後，只要按照步驟教學或上方影片一步步操作，就可以完成初始化設定囉！

1. 首先使用電腦打開 Chrome 瀏覽器進入 [Wi-Fi 設定頁面](https://webai.webduino.io)。

    > 如果 Chrome 版本低於 89，需要先將瀏覽器更新到最新版本！

2. 將 Web:AI 開發板透過 USB 傳輸線連接到電腦。

3. 按下「點擊開始設定」。
    ![](../assets/images/upload_02a4681ffc6dfd1aa921e27afe17f2f5.png)

4. 點擊「開始連接」。

    ![](../assets/images/upload_792d00f7981cf19f3ffad15bf3930abf.png)

5. 選擇連接 Web:AI 的 USB，點擊「連接」。

    ![](../assets/images/upload_4892028c07de2478564d8705933f5580.png)

6. 電腦連接上 Web:AI 後會出現開發板的 Device ID 和現在的韌體版本。

    ![](../assets/images/upload_44766cf13211c94964896050340ceb25.jpg)


7. 在 Wi-Fi 連線畫面，選擇 Wi-Fi 並輸入密碼，按下「儲存連線」。

    ![](../assets/images/upload_ddcfed56e5b16ca8494e8c37dc6b9bed.jpg)

8. 成功完成設定 Wi-Fi！

    ![](../assets/images/upload_4938d84b09b19e6ff298bb8808661543.jpg)

> 如果需要進行韌體更新，再接著進行下方步驟。

## 教學步驟：更新韌體

1. 設定完 Wi-Fi 後，如果畫面有「已有新版本，點擊更新」，代表有新版本可以更新。

   點擊「更新韌體」。

    ![](../assets/images/upload_417de60a4f044c3973890328c1ce6987.png)

2. 等待韌體更新，開發板螢幕會顯示更新進度，期間內請勿斷開與 USB 線的連接。

    ![](../assets/images/upload_73e353a9e9a08eb82c1884c0b2c8bba2.png)
    ![](../assets/images/upload_d1a8539e1deef8d0c520d7bfc5fb2b0e.png)

3. 更新完成後，重新開機就可以開始使用 Web:AI 了！

    ![](../assets/images/upload_8dbf16901021d914270ba5134b478694.png)

## 小提醒

- 當開發板畫面呈現與下圖 **相同** 時，才能在 Wi-Fi 設定頁面進行初始化設定。

    ![](../assets/images/upload_9c75be672cbd440d6ee3fdb4f04b77c9.png)

- 想要再次設定 Wi-Fi 時，請先將開發板 [回復預設狀態](https://bpi-steam.com/WebAI/zh_tw/Unboxing/Mode.html#%E5%9B%9E%E5%BE%A9%E9%A0%90%E8%A8%AD%E7%8B%80%E6%85%8B)，當開發板顯示和上圖相同就可以進行設定。

- 若使用上述步驟卻無法更新韌體，可以參考：[安裝版更新韌體](https://bpi-steam.com/WebAI/zh_tw/Unboxing/Update.html) 來完成設定！

- 如果設定頁面文字顯示為「網路：人工智能」，如下圖，代表 Chrome 瀏覽器有經過網頁自動翻譯。網頁自動翻譯會造成 Wi-Fi 設定出錯，需要將語言設定回「英文」並重新整理才能正常使用。

    ![](../assets/images/upload_f35bd1f701c2304cac254c885f1ef660.jpg)

    ![](../assets/images/upload_698b723317d3f9e955ac643af178d3fe.jpg)
