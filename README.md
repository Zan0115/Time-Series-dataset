# Time-series circula knitting dataset, 
週期針織布數據集第一版
----台灣中央大學智慧軟體系統實驗室

## 週期針織布數據集第一版介紹
週期針織布數據集第一版由台灣中央大學智慧軟體系統實驗室整理並開源, 共三種針織布類型。該數據集共包含訓練樣本圖像5422張，測試樣本圖像67835張，圖像的分辨率分為800x640及400x320兩種。

## 資料集特性
### 裁切線特性
為了幫助在生產後進行精確的裁剪，**圓形針織機** 會在固定的位置設置兩條漏針來形成 **裁切線 (Cutline)**。這些裁切線本身是設計中的一部分，用於引導布匹的裁剪，並非織物缺陷。然而，這些裁切線在外觀上與一些常見的缺陷（如垂直線缺陷 v-line）非常相似，因此在進行實時缺陷檢測時，區分這些裁切線與真正的缺陷是一個關鍵挑戰。

![img_3.png](img_3.png)
defect-free 樣本圖

### 光照特性
由於相機沒有感光元件, 拍攝的影像容易受到光照條件的影響。由於相機只能捕捉灰度信息而無法分辨顏色, 同一布匹在不同光照下呈現不同的色階，因此在進行實時缺陷檢測時，能正確的在不同色階下區分正常以及瑕疵圖片是第二個挑戰。
![img_5.png](img_5.png)

### 週期特性
在不同資料集中，圖片的週期可能也不同。所謂週期指的是兩次裁切線出現間隔的圖片個數，在週期針織布數據集
中這個值從130~500都有涵蓋。

以週期60為例：
![img_7.png](img_7.png)

### 瑕疵特性
在週期針織布數據集中包含了各式各樣的瑕疵類型，包含一般常見的線型、點型，或是中型破洞瑕疵，另外還有比較罕見的大型瑕疵與和裁切線在同一張圖片的瑕疵。
![img_6.png](img_6.png)

瑕疵樣本圖

## 資料集結構
資料集中包括三種不同的針織織物紋理，分別標示為 Texture 1，Texture 2 和 Texture 3三類花型：
![img_10.png](img_10.png)

## 訓練和測試數據集劃分
每個花型包含了一個訓練資料集跟數個測試資料集，下方表格中提供了每個花型詳細的訓練和測試數據集劃分：

### Texture 1 資料總表：

| 訓練/測試 | 資料集名稱             |週期  |光照(灰度)   |正常樣本數    |異常樣本數     |裁切線樣本數    |總共樣本數   | 備註                 |
|------------|---------------------|------|------------|-------------|--------------|----------------|-----------|----------------------|
| train      | 243_2_0407          | 170  | 30         | 1733        | 0            | 74             | 1807      |                      |
| test       | 243_2_0411          | 170  | 30         | 1732        | 0            | 75             | 1807      |                      |
| test       | 243_2_0411_2        | X    | 30         | 0           | 352          | 13500          | 13852     | 都是裁切線/瑕疵       |
| test       | 1129_02_00          | 130  | 70         | 191         | 121          | 68             | 380       |不是連續資料           |
| test       | 243_1_20210318_1    | 170  | 110        | 15749       | 0            | 682            | 16431     |                      |
| test       | 243_1_20210318_2    | 170  | 110        | 17838       | 0            | 682            | 18520     |                      |
| test       | 1065_1              | 500  | 100        | 213         | 198          | 213            | 624       | 週期特別大            |
| test       | 243_1_00            | 170  | 110        | 173         | 173          | 278            | 624       | 不是連續資料          |
| test       | 1065_1_00           | X    | 110        | 0           | 404          | 237            | 641       | 不是連續資料          |
| test       | 1129_1_0407_01      | 130  | 70         | 16          | 0            | 14             | 30        |                      |
| test       | 1129_1_0407_02      | 230  | 90         | 144         | 0            | 215            | 359       |                      |
| test       | 1129_1_0407_03      | 230  | 90         | 987         | 0            | 494            | 1481      |                      |
| **總計**   |                     |      |            | **41219**   | **1087**     | **15618**      | **57924** |                      |

### Texture 2 資料總表：

| 訓練/測試   | 資料集名稱    |週期    |光照(灰度)     |正常樣本數       |異常樣本數         |裁切線樣本數      |總共樣本數       | 備註 |
| ---------- | ------------ | ------ | ------------ | -------------- | ----------------- | --------------- | ------------- | ---- |
| train      | 839\_1\_0706 | 170    | 170          | 1727           | 0                 | 81              | 1808          |      |
| test       | 839\_2       | 170    | 70           | 498            | 0                 | 21              | 519           |      |
| test       | 839\_1\_0705 | 170    | 170          | 455            | 0                 | 18              | 473           |      |
| test       | 839\_1\_0712 | 170    | 170          | 1733           | 0                 | 74              | 1807          |      |
| **總計**    |              |        |              | **4413**       | **0**             | **194**         | **4607**      |      |

### Texture 3 資料總表：

| 訓練/測試   | 資料集名稱         |週期    |光照(灰度)     |正常樣本數       |異常樣本數         |裁切線樣本數       |總共樣本數      | 備註                  |
| ---------- | ----------------- | ------ | ------------ | -------------- | ----------------- | --------------- | ------------- | ---------------------- |
| train      | 1480\_1\_0728\_25 | 200    | 170          | 1729           | 0                 | 78              | 1807          |                        |
| test       | 1480\_2\_1        | 130    | 40           | 291            | 0                 | 12              | 303           |                        |
| test       | 1480\_2\_0812     | 130    | 40           | 1549           | 0                 | 73              | 1622          |                        |
| test       | 1480\_2\_0906     | 130    | 40           | 1461           | 0                 | 65              | 1526          |                        |
| test       | 1480\_2\_2        | 230    | 40           | 4099           | 0                 | 191             | 4290          | 週期變動很大            |
| test       | 1480\_1\_0728\_15 | 300    | 170          | 1052           | 75                | 51              | 1178          |                        |
| **總計**   |                   |        |              | **10181**      | **75**            | **402**         | **10726**     |                        |

## 文件結構
週期針織布數據集CKD-1文件夾中，包含 Texture 1，Texture 2 和 Texture 3三類布匹型號。
這三類別分别放置於三個文件夾，依次命名為Texture 1，Texture 2，Texture 3，總結構如圖所示。
![img_8.png](img_8.png)

每種針織布類型的數據集文件包含訓練集train和測試集test兩个子文件夾。其中，訓練集為無缺陷樣本和週期出現cutline樣本,放置於defect-free文件夾, 對應標記缺陷區域放置於groundtruth；
測試集為週期出現樣本circular及標記缺陷區域的groundtruth, 裡面包含defect-free, 週期出現cutline以及有缺陷樣本defect。以Texture 1 為例，它的文件結構圖如下圖所示。

![img_9.png](img_9.png)


## 下載

稍後公佈
