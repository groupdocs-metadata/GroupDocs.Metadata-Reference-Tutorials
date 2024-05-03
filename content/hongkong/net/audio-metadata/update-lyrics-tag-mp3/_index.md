---
title: 使用 .NET 更新 MP3 檔案中的歌詞標籤
linktitle: 使用 .NET 更新 MP3 檔案中的歌詞標籤
second_title: GroupDocs.元資料 .NET API
description: 了解如何使用 GroupDocs.Metadata for .NET 以程式設計方式更新 MP3 檔案元數據，包括歌詞、藝人和專輯詳細資訊。
type: docs
weight: 21
url: /zh-hant/net/audio-metadata/update-lyrics-tag-mp3/
---
## 介紹
在本教學中，我們將示範如何使用 GroupDocs.Metadata for .NET 函式庫以程式設計方式更新 MP3 檔案中的歌詞標籤。此過程涉及存取和修改 MP3 檔案的元數據，特別是針對歌詞資訊。
## 先決條件
在開始之前，請確保您具備以下條件：
- C# 程式設計基礎知識。
- Visual Studio 安裝在您的電腦上。
- 安裝了 .NET 程式庫的 GroupDocs.Metadata（請參閱[下載連結](https://releases.groupdocs.com/metadata/net/)）。
- 用於測試目的的 MP3 檔案。

## 導入命名空間
首先將必要的命名空間匯入到您的 C# 專案中：
```csharp
using GroupDocs.Formats.Audio;
using System;
using GroupDocs.Metadata;
```
## 第 1 步：載入 MP3 文件
首先，將 MP3 檔案載入到`Metadata`使用 GroupDocs.Metadata 的物件：
```csharp
using (Metadata metadata = new Metadata("path_to_your_mp3_file.mp3"))
{
    var root = metadata.GetRootPackage<MP3RootPackage>();
    //訪問 Lyrics3V2 標籤
    if (root.Lyrics3V2 == null)
    {
        root.Lyrics3V2 = new LyricsTag();
    }
```
## 步驟2：更新歌詞訊息
接下來，更新歌詞資訊以及其他相關詳細信息，例如藝術家、專輯和曲目：
```csharp
    root.Lyrics3V2.Lyrics = "[00:01]Test lyrics";
    root.Lyrics3V2.Artist = "test artist";
    root.Lyrics3V2.Album = "test album";
    root.Lyrics3V2.Track = "test track";
```
## 第 3 步：新增自訂欄位（可選）
或者，您可以向標記新增自訂欄位：
```csharp
    root.Lyrics3V2.Set(new LyricsField("ABC", "custom value"));
```
## 第 4 步：儲存更改
最後，將修改後的元資料保存回 MP3 檔案：
```csharp
    metadata.Save("path_to_your_output_file.mp3");
}
```

## 結論
在本教學中，我們探討如何使用 GroupDocs.Metadata for .NET 更新 MP3 檔案中的歌詞標籤。透過遵循概述的步驟，您可以以程式設計方式有效地管理和修改 MP3 檔案中的元資料。

## 常見問題解答
### 我可以使用 GroupDocs.Metadata for .NET 更新歌詞以外的其他元資料嗎？
是的，GroupDocs.Metadata for .NET 允許您使用不同文件格式的各種類型的元資料。
### GroupDocs.Metadata for .NET 是否與 .NET Core 相容？
是的，該程式庫支援 .NET Framework 和 .NET Core。
### GroupDocs.Metadata for .NET 是否需要商業用途許可證？
是的，您可以從以下位置取得許可證[集團文件](https://purchase.groupdocs.com/buy)用於商業用途。
### 我如何獲得與 GroupDocs.Metadata for .NET 相關的支援或提出問題？
您可以訪問[GroupDocs.元資料論壇](https://forum.groupdocs.com/c/metadata/14)以尋求支持和討論。
### 我可以免費試用 GroupDocs.Metadata for .NET 嗎？
是的，您可以獲得[免費試用](https://releases.groupdocs.com/)來探索它的特點。