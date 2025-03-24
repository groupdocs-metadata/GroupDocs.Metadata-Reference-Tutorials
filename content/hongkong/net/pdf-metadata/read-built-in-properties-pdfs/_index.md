---
title: 從 .NET 中的 PDF 讀取內建屬性
linktitle: 從 .NET 中的 PDF 讀取內建屬性
second_title: GroupDocs.元資料 .NET API
description: 了解如何使用 GroupDocs.Metadata 在 .NET 中讀取 PDF 元資料。使用 C# 代碼存取作者姓名、建立日期、主題等。
weight: 10
url: /zh-hant/net/pdf-metadata/read-built-in-properties-pdfs/
---

# 從 .NET 中的 PDF 讀取內建屬性

## 介紹
在本教學中，我們將探討如何利用 GroupDocs.Metadata for .NET 從 PDF 檔案讀取內建屬性。 GroupDocs.Metadata 是一個功能強大的程式庫，可讓開發人員處理與各種文件格式相關的元數據，包括 PDF、Microsoft Office 文件、圖像等。透過使用此程式庫，您可以輕鬆存取和操作 PDF 文件中嵌入的元資料屬性，例如作者姓名、建立日期、主題等。
## 先決條件
在深入學習本教程之前，請確保您具備以下先決條件：
- Visual Studio：確保您的電腦上安裝了 Visual Studio。
-  GroupDocs.Metadata for .NET：從下列位置下載並安裝 GroupDocs.Metadata for .NET[這裡](https://releases.groupdocs.com/metadata/net/).
- C#基礎：熟悉C#程式語言和.NET架構。

## 導入命名空間
首先將必要的命名空間加入您的 C# 專案：
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## 第 1 步：載入 PDF 元數據
首先，載入 PDF 文件並使用 GroupDocs.Metadata 提取其元資料：
```csharp
using (Metadata metadata = new Metadata("YourInputFile.pdf"))
{
    //訪問PDF文件的根包
    var root = metadata.GetRootPackage<PdfRootPackage>();
    //檢索並顯示內建屬性
    Console.WriteLine("Author: " + root.DocumentProperties.Author);
    Console.WriteLine("Created Date: " + root.DocumentProperties.CreatedDate);
    Console.WriteLine("Subject: " + root.DocumentProperties.Subject);
    Console.WriteLine("Producer: " + root.DocumentProperties.Producer);
    Console.WriteLine("Keywords: " + root.DocumentProperties.Keywords);
    //可以類似地存取其他屬性
    //……
}
```
除了讀取元資料之外，GroupDocs.Metadata 還允許以程式設計方式對 PDF 檔案進行編輯、刪除或新增新的元資料屬性等進階操作。這種靈活性支援對 .NET 應用程式中的文件元資料進行全面管理。
## 結論
在本教學中，我們介紹如何利用 GroupDocs.Metadata for .NET 使用 C# 從 PDF 檔案中提取內建屬性。透過將該程式庫整合到您的專案中，您可以無縫處理文件元資料操作，從而提供增強的文件管理功能。

## 常見問題解答
### GroupDocs.Metadata 可以與其他文件格式一起使用嗎？
是的，GroupDocs.Metadata 支援各種文件格式，例如 DOCX、XLSX、PPTX、PDF、JPG、PNG 等。
### GroupDocs.Metadata 是否有免費試用版？
是的，您可以存取 GroupDocs.Metadata 的免費試用版[這裡](https://releases.groupdocs.com/).
### 如何使用 GroupDocs.Metadata 修改元資料屬性？
您可以透過存取相應的文檔包並設定新值以程式設計方式修改元資料屬性。
### GroupDocs.Metadata 是否支援 .NET Core？
是的，GroupDocs.Metadata 與 .NET Framework 和 .NET Core 也相容。
### 在哪裡可以找到與 GroupDocs.Metadata 相關的支援或提出問題？
如需支援和討論，請訪問[GroupDocs.元資料論壇](https://forum.groupdocs.com/c/metadata/14).