---
title: 從 .NET 中的 MP3 檔案讀取歌詞標籤
linktitle: 從 .NET 中的 MP3 檔案讀取歌詞標籤
second_title: GroupDocs.元資料 .NET API
description: 了解如何使用 GroupDocs.Metadata for .NET 從 MP3 檔案中擷取歌詞標籤。請按照我們的逐步教學進行操作。
weight: 13
url: /zh-hant/net/audio-metadata/read-lyrics-tag-mp3/
---

# 從 .NET 中的 MP3 檔案讀取歌詞標籤

## 介紹
在本教學中，我們將學習如何使用 .NET 中的 GroupDocs.Metadata API 從 MP3 檔案中擷取和讀取歌詞標籤。 GroupDocs.Metadata 是一個功能強大的程式庫，可讓開發人員處理與各種檔案格式（包括 MP3 檔案）相關的元資料。透過執行這些步驟，您將能夠有效地檢索 MP3 檔案中嵌入的歌詞相關資訊。
## 先決條件
在我們開始之前，請確保您已設定以下先決條件：
- Visual Studio 安裝在您的電腦上。
- C# 程式語言的基礎知識。
- 用於 .NET 的 GroupDocs.Metadata 函式庫。你可以下載它[這裡](https://releases.groupdocs.com/metadata/net/).
- 存取包含歌詞標籤的 MP3 檔案以進行測試。

## 導入命名空間
首先，在 C# 專案中包含必要的命名空間：
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Formats.Audio;
```
## 第 1 步：載入 MP3 文件
首先初始化一個`Metadata`物件與您的輸入 MP3 檔案路徑：
```csharp
using (Metadata metadata = new Metadata("YourInputFile.mp3"))
{
    //取得MP3格式的根包
    var root = metadata.GetRootPackage<MP3RootPackage>();
```
## 第 2 步：訪問歌詞標籤
檢查 MP3 檔案是否包含 Lyrics3V2 標籤並檢索關聯資訊：
```csharp
    if (root.Lyrics3V2 != null)
    {
        //輸出特定標籤字段
        Console.WriteLine("Lyrics: " + root.Lyrics3V2.Lyrics);
        Console.WriteLine("Album: " + root.Lyrics3V2.Album);
        Console.WriteLine("Artist: " + root.Lyrics3V2.Artist);
        Console.WriteLine("Track: " + root.Lyrics3V2.Track);
```
## 第 3 步：循環遍歷所有標籤字段
或者，您可以循環遍歷 Lyrics3V2 中的所有可用標籤欄位：
```csharp
        foreach (var field in root.Lyrics3V2.ToList())
        {
            Console.WriteLine("{0} = {1}", field.ID, field.Data);
        }
    }
}
```

## 結論
在本教學中，我們探討如何使用 GroupDocs.Metadata for .NET 從 MP3 檔案中擷取和讀取歌詞標籤。透過執行這些步驟，您可以有效地檢索 MP3 檔案中嵌入的與歌詞相關的元數據，以便進一步處理或在應用程式中顯示。

## 常見問題解答
### 我可以使用 GroupDocs.Metadata 修改或更新歌詞標籤嗎？
是的，GroupDocs.Metadata 允許您更新和修改 MP3 檔案中的元數據，包括歌詞標籤。
### GroupDocs.Metadata 是否支援除 MP3 之外的其他音訊格式？
是的，GroupDocs.Metadata 支援多種音訊和視訊格式以進行元資料提取和操作。
### 在哪裡可以找到有關 GroupDocs.Metadata 的更詳細文件？
您可以存取完整的文檔[這裡](https://tutorials.groupdocs.com/metadata/net/).
### GroupDocs.Metadata 是否有免費試用版？
是的，您可以獲得免費試用版[這裡](https://releases.groupdocs.com/).
### 如何獲得 GroupDocs.Metadata 的技術支援？
如需技術協助，您可以造訪 GroupDocs.Metadata 支援論壇[這裡](https://forum.groupdocs.com/c/metadata/14).