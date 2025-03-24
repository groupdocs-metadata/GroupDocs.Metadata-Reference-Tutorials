---
title: 從 .NET 圖表中讀取內建屬性
linktitle: 從 .NET 圖表中讀取內建屬性
second_title: GroupDocs.元資料 .NET API
description: 了解使用 GroupDocs.Metadata 從 .NET 中的圖表檔案中提取元資料。有效增強文件管理和分析。
weight: 10
url: /zh-hant/net/diagram-metadata/read-built-in-properties-diagrams/
---
## 介紹
在本教程中，我們將深入研究使用 GroupDocs.Metadata for .NET 從圖表中讀取內建屬性。 GroupDocs.Metadata for .NET 是一個功能強大的程式庫，使開發人員能夠處理與各種文件類型相關的元數據，包括圖表、簡報、圖像等。具體來說，我們將重點關注使用此庫從圖表檔案中提取元資料屬性。
## 先決條件
在我們開始之前，請確保您具備以下先決條件：
- C# 和 .NET 開發的基礎知識。
- 您的電腦上安裝了 Visual Studio IDE。
-  .NET 函式庫的 GroupDocs.Metadata。您可以從以下位置下載：[這裡](https://releases.groupdocs.com/metadata/net/).
- 用於從中提取元資料的輸入圖檔（例如.vsdx）。

## 導入命名空間
首先在 C# 專案中匯入必要的命名空間以使用 GroupDocs.Metadata 功能：
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## 第 1 步：載入圖表文件
首先載入要從中提取元資料的圖表檔案：
```csharp
using (Metadata metadata = new Metadata("YourDiagramFile.vsdx"))
{
    //訪問圖表的根包
    var root = metadata.GetRootPackage<DiagramRootPackage>();
    //現在，您可以存取各種文件屬性
    //讓我們將一些屬性列印到控制台
}
```
## 第 2 步：存取內建屬性
載入圖表檔案後，您可以透過以下方式存取其內建屬性`DocumentProperties`：
```csharp
Console.WriteLine(root.DocumentProperties.Creator);
Console.WriteLine(root.DocumentProperties.Company);
Console.WriteLine(root.DocumentProperties.Keywords);
Console.WriteLine(root.DocumentProperties.Language);
Console.WriteLine(root.DocumentProperties.TimeCreated);
Console.WriteLine(root.DocumentProperties.Category);
```
## 第 3 步：利用其他元資料資訊
除了`DocumentProperties`、GroupDocs.Metadata 提供對特定於圖表檔案的其他元資料屬性的存取。例如，您可以根據圖表類型存取圖層、頁面、形狀等。

## 結論
在本教學中，我們探索如何使用 GroupDocs.Metadata for .NET 輕鬆地從圖表檔案讀取內建屬性。利用該程式庫，開發人員可以有效地管理和提取與其 .NET 應用程式中的各種文件類型相關的元資料。

## 常見問題解答
### GroupDocs.Metadata for .NET 支援哪些類型的圖表檔案？
GroupDocs.Metadata for .NET 支援多種圖表檔案格式，包括 .vsdx、.vssx、.vstx 等。
### 我可以使用 GroupDocs.Metadata for .NET 修改元資料屬性嗎？
是的，您不僅可以使用此程式庫讀取還可以更新和刪除元資料屬性。
### GroupDocs.Metadata for .NET 是否有試用版？
是的，您可以存取免費試用版[這裡](https://releases.groupdocs.com/).
### 如何獲得 GroupDocs.Metadata for .NET 的技術支援？
如需技術協助，您可以訪問[GroupDocs.元資料論壇](https://forum.groupdocs.com/c/metadata/14).
### 在哪裡可以購買 GroupDocs.Metadata for .NET 的許可證？
您可以從以下位置購買許可證[這裡](https://purchase.groupdocs.com/buy).