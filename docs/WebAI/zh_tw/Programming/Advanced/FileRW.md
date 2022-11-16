# 檔案讀寫

Web:AI 檔案讀寫功能能夠將鏡頭拍攝的圖片存入，並透過 LCD 螢幕顯示的功能將儲存的圖片展示出來。透過檔案讀寫功能，可以讓 Web:AI 開發板實現照相機、自拍等影像應用。

> 更多相關應用，可以參考：[LCD 顯示圖片](https://bpi-steam.com/WebAI/zh_tw/Programming/WebAI/LCD.html#LCD-%E9%A1%AF%E7%A4%BA%E5%9C%96%E7%89%87)。

## 寫入檔案

「寫入檔案」積木可以將鏡頭捕捉到的影像儲存在開發板記憶體中，再配合其它積木展示。

![](../../assets/images/upload_0467957e1aab1208df0cc8fb9732b98a.png)

## 圖片 ( 檔案 )

「圖片 ( 檔案 )」積木要使用的圖片，能夠根據圖檔的名稱加以讀取並使用。

![](../../assets/images/upload_9844d06a3efc96392cd124fc7b783432.png)

## 範例：自拍照相

1. 先設定拍照狀態，使用「無限重複」積木讓開發板保持在拍照狀態。

    ![](../../assets/images/upload_71ff8223a0f878a61c8e80c7fb05d899.png)

2. 使用「變數 show」來表示相機的狀態，開發板一開始會保持在拍照狀態。
 
   ![](../../assets/images/upload_5c5a38e6240f641e002335da3812879c.png)

    - 真：展示拍攝的照片
    - 假：拍照狀態

3. 設定當 L 按鈕按下，會拍攝照片，並同時顯示「儲存中...」和「完成」。

   ![](../../assets/images/upload_1f2b11380cf2372c9ca3672bd50efa3f.png)

4. 設定當 R 按鈕按下，會顯示拍攝的照片。

    ![](../../assets/images/upload_d7494a77b30b1496ed4d98822662f13e.png)

5. 設定當 R 按鈕放開，「變數 show」為**假**，回到拍照狀態。

    ![](../../assets/images/upload_90628981c80e3f7c9dde48fdf506bfe6.png)

6. 完成後開始執行，按下開發板 L 按鈕拍照，按下 R 按鈕展示。

    ![](../../assets/images/upload_4926d849dc1ccd16171bfbe981df306f.png)

![](../../assets/images/upload_137463eb3594996be60e6b4514feba5e.gif)
