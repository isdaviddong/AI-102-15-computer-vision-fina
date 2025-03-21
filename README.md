# 電腦視覺影像分析專案

本專案示範如何使用 Azure Computer Vision 服務進行影像分析，包含影像描述、物件偵測、名人辨識、地標辨識等功能。

## 功能說明

1. 影像分析 (AnalyzeImage)
   - 自動生成影像描述
   - 影像標籤辨識
   - 影像分類
   - 地標辨識
   - 名人辨識
   - 品牌識別
   - 物件偵測與標註
   - 內容分級評估

2. 縮圖生成 (GetThumbnail)
   - 自動生成指定大小的影像縮圖

## 程式碼解析

### 主程式結構
```csharp
static async Task Main(string[] args)
```
- 從 appsettings.json 讀取 Azure 認證設定
- 設定預設影像檔案或接受命令列參數
- 初始化 Computer Vision 客戶端
- 執行影像分析與縮圖生成

### 影像分析功能
```csharp
static async Task AnalyzeImage(string imageFile)
```
包含以下分析項目：
- 影像描述生成：自動產生影像內容的文字描述
- 標籤識別：辨識影像中的關鍵元素
- 分類系統：將影像歸類到預定義類別
- 地標/名人辨識：識別知名地標或公眾人物
- 品牌識別：辨識商業品牌標誌
- 物件偵測：標示影像中物件的位置
- 內容分級：評估影像的成人內容程度

### 縮圖生成功能
```csharp
static async Task GetThumbnail(string imageFile)
```
- 將原始影像轉換為 100x100 像素的縮圖
- 保持原始比例
- 儲存為 PNG 格式

## 使用方式

1. 設定 Azure 認證：
   - 在 appsettings.json 中設定 CognitiveServicesEndpoint 和 CognitiveServiceKey

2. 執行程式：
   ```bash
   dotnet run [圖片路徑]
   ```
   若未指定圖片路徑，將使用預設圖片 "images/building.jpg"

3. 輸出結果：
   - 分析結果將顯示在控制台
   - 物件偵測結果將儲存為 "objects.jpg"
   - 縮圖將儲存為 "thumbnail.png"

## 相依套件

- Microsoft.Azure.CognitiveServices.Vision.ComputerVision
- System.Drawing
- Microsoft.Extensions.Configuration
