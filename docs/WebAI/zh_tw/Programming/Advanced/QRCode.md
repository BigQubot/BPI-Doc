# 掃描條碼

Web:AI 具備條碼掃描功能，能夠透過開發板上的鏡頭偵測條碼，並將條碼內容顯示在螢幕上。

## 照相畫面

「拍攝照片」積木可以使用鏡頭拍攝一次畫面，配合「無限重複」積木就可以達成照相鏡頭的效果。

![](../../assets/images/upload_e5f0e28421cf299a02c56d80badc8485.png)

另外也可以使用「變數」積木替拍攝照片命名，透過命名來做出更多變化。

![](../../assets/images/upload_2630972dadc38129eb09e64e7d262658.png)

> 以上兩種積木組合方式執行後會達到相同的結果，差別在於若是要做出更多應用變化，就需要搭配「變數」積木的命名。

### 畫面上畫文字

Web:AI 能夠在螢幕畫面或圖片上顯示文字，這時就需要搭配「圖片上畫文字」積木。

> 請特別注意，「圖片上畫文字」積木需要放在「LCD 顯示圖片」積木之前！

![](../../assets/images/upload_d4fc3f4eca1a16281c9aade6bb111715.png)

## 讀取圖片的 QRcode

「讀取圖片的 QRcode」積木能夠讀取圖片上的     QRcode 資訊，並透過「LCD 螢幕」積木顯示出來。

![](../../assets/images/upload_fffaf7ffa609a3acfc3f5e733a88c047.png)


## 範例：QRcode 掃描

1. 使用「變數」積木將拍攝照片命名為「畫面」。 

    ![](../../assets/images/upload_2faf10807186f50299cd8d55f2d87f65.png)

2. 使用「圖片上畫文字」積木，填入「畫面」及「讀取圖片的 QRcode」積木，代表在畫面上顯示 QRcode 的資訊。

    ![](../../assets/images/upload_0c662efb60008d34d600fcfcc2e91587.png)

3. 放入「LCD 顯示圖片」積木，設定為「畫面」。

    ![](../../assets/images/upload_247a402fccd1886ecd12846df20cd917.png)

4. 前面步驟完成後代表能夠掃描一次 QRcode，為了能夠不斷掃瞄，在最外層放入「無限重複」積木。

    ![](../../assets/images/upload_bf87cd1a75b15fbf75bc21d972fb1b25.png)

5. 完成後按下執行，使用 Web:AI 的鏡頭掃描 QRcode，就可以看到螢幕顯示 QRcode 資訊了。

   ![](../../assets/images/upload_d393959c360f2933fa83169f9791d172.png)

    ![](../../assets/images/upload_dc36ceb0e810940ce6371095d09c5a09.png)
