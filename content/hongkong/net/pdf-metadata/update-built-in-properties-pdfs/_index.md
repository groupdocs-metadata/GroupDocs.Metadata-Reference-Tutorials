---
title: 使用 .NET 更新 PDF 中的內建屬性
linktitle: 使用 .NET 更新 PDF 中的內建屬性
second_title: GroupDocs.元資料 .NET API
description: 了解如何使用 C# 和 GroupDocs.Metadata for .NET 更新 PDF 文件屬性。以程式方式修改作者、標題、關鍵字等。
type: docs
weight: 15
url: /zh-hant/net/pdf-metadata/update-built-in-properties-pdfs/
---
## 介紹
在本教學中，我們將學習如何使用 GroupDocs.Metadata for .NET 更新 PDF 文件的內建屬性。該庫提供了一組強大的工具來操作各種文件格式中的元資料。我們將逐步完成使用 C# 修改 PDF 檔案中的作者、標題、建立日期、關鍵字、建立者和製作者等屬性的必要步驟。
## 先決條件
在我們開始之前，請確保您已具備以下條件：
-  GroupDocs.Metadata for .NET 函式庫：從下列位置下載函式庫[這裡](https://releases.groupdocs.com/metadata/net/).
- Visual Studio：安裝 Visual Studio 以編寫和執行 C# 程式碼。
- 對 C# 的基本了解：建議熟悉 C# 程式語言。

## 導入命名空間
首先在您的 C# 專案中包含必要的命名空間：
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## 第 1 步：初始化元資料對象
首先初始化一個`Metadata`包含 PDF 檔案路徑的物件：
```csharp
using (Metadata metadata = new Metadata("Your Input File Path"))
{
    //您的程式碼將位於此處
}
```
## 第2步：訪問PDF根包
接下來，使用以下命令檢索專門用於 PDF 的根包`GetRootPackage<PdfRootPackage>()`：
```csharp
var root = metadata.GetRootPackage<PdfRootPackage>();
```
## 步驟 3：更新文件屬性
現在，更新 PDF 文件所需的屬性`PdfRootPackage`：
```csharp
root.DocumentProperties.Author = "New Author Name";
root.DocumentProperties.CreatedDate = DateTime.Now;
root.DocumentProperties.Title = "New Document Title";
root.DocumentProperties.Keywords = "keyword1, keyword2";
root.DocumentProperties.Creator = "Document Creator";
root.DocumentProperties.Producer = "Document Producer";
```
## 第 4 步：儲存更改
修改屬性後，將變更儲存回 PDF 檔案：
```csharp
metadata.Save("Your Output File Path");
```
## 第 5 步：檢索更新的屬性
若要驗證更改，請重新載入元資料並檢索更新的屬性：
```csharp
using (Metadata metadata = new Metadata("Your Output File Path"))
{
    var root = metadata.GetRootPackage<PdfRootPackage>();
    Console.WriteLine("Author: " + root.DocumentProperties.Author);
    Console.WriteLine("Created Date: " + root.DocumentProperties.CreatedDate);
    Console.WriteLine("Title: " + root.DocumentProperties.Title);
    Console.WriteLine("Keywords: " + root.DocumentProperties.Keywords);
    Console.WriteLine("Creator: " + root.DocumentProperties.Creator);
    Console.WriteLine("Producer: " + root.DocumentProperties.Producer);
}
```

## 結論
在本教學中，我們探討如何利用 GroupDocs.Metadata for .NET 以程式設計方式更新 PDF 文件的內建屬性。透過遵循概述的步驟，您可以使用 C# 有效地管理和修改 PDF 文件中的元資料。請隨意探索 GroupDocs.Metadata 提供的更多特性和功能，以進行全面的元資料操作。

## 常見問題解答
### Q：什麼是 .NET 的 GroupDocs.Metadata？
答：GroupDocs.Metadata for .NET 是一個函式庫，允許開發人員以程式設計方式讀取、編輯、刪除和操作各種文件格式的元資料。
### Q：在哪裡可以找到 GroupDocs.Metadata for .NET 的文檔？
答：您可以存取文檔[這裡](https://reference.groupdocs.com/metadata/net/).
### Q：如何下載 .NET 的 GroupDocs.Metadata？
答：您可以從以下位置下載 GroupDocs.Metadata for .NET[這個連結](https://releases.groupdocs.com/metadata/net/).
### Q：有免費試用嗎？
答：是的，您可以獲得免費試用版[這裡](https://releases.groupdocs.com/).
### Q：在哪裡可以獲得 GroupDocs.Metadata for .NET 支援？
答：如需支持，請造訪 GroupDocs.Metadata 論壇[這裡](https://forum.groupdocs.com/c/metadata/14).