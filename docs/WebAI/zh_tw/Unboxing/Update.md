# 安裝版更新韌體

Web:AI 開發板的韌體中使用了 2 種晶片，分別是主晶片 ( K210 ) 和 Wi-Fi 晶片 ( ESP8285 )。

第一次使用 Web:AI 開發板之前，需要先對晶片做韌體更新，將開發板升級到最新版本，才能順利使用最全面的功能。

#### 連結：[Web:AI 安裝版](https://drive.google.com/file/d/1m4qGyWGae-2yytYrSorrJKaP-XBBarHR/view)

![](../assets/images/upload_d8caf85eb964dda018799fe2f9b8476d.png)

## 教學影片

歡迎參考下方教學影片：

<iframe src="https://www.youtube.com/embed/vl6XY0iCCuM" allowfullscreen width="100%" style="aspect-ratio:728/410;border:none " ></iframe>

## 透過 Web:AI 安裝版 進行韌體更新

1. 首先下載 [Web:AI 安裝版](https://drive.google.com/file/d/1m4qGyWGae-2yytYrSorrJKaP-XBBarHR/view)。

2. 下載後點擊執行，安裝完成後就可以開啟 Web:AI 安裝版了。

    ![](../assets/images/upload_4c0c19b4782014407c134e49323fa2f4.png)

    - 開啟 Web:AI 安裝版，可以看到視窗最上方顯示「正在搜尋裝置...」，代表並未連接上開發板。

        ![](../assets/images/upload_6e38bcc632aad5ef625c43833b4cd579.png)

    - 透過 USB 線將 Web:AI 開發板連接上電腦，當 Web:AI 安裝版視窗顯示「已偵測到裝置」，代表成功讀取到開發板資訊。

        ![](../assets/images/upload_01d95577c2800de0b1686ecf195a160d.png)

3. 偵測到裝置後，點擊左上角「工具」>「更新韌體」，開始進行主晶片韌體更新，視窗上方會顯示目前更新進度。

    ![](../assets/images/upload_7ba6a2e5f255c8ec78d61b4937d64f06.png)

    :::danger
    回復原廠韌體時，請勿按下 Reset 按鈕及拔除電源！
    :::

4. 韌體更新完成後，開發板會重新開機。這時 LCD 螢幕畫面如下圖，需要進一步完成 Wi-Fi 設定才能開始使用。

    ![](../assets/images/upload_cffca67e2ed07221bf1445851c16c967.png)

> 完成韌體更新後，歡迎參考 [初始化設定 ( 第一次使用請看這裡 )](https://bpi-steam.com/WebAI/zh/Unboxing/Initialization.html) 來完成 Wi-Fi 設定。