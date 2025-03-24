---
title: 使用 .NET 更新電子表格中的內建屬性
linktitle: 使用 .NET 更新電子表格中的內建屬性
second_title: GroupDocs.元資料 .NET API
description: 了解如何使用 GroupDocs.Metadata for .NET 更新 Excel 檔案中的內建元資料屬性。使用C#修改作者、創建時間、公司等。
weight: 14
url: /zh-hant/net/spreadsheet-metadata/update-built-in-properties-spreadsheets/
---
## 介紹
在本教程中，我們將探索如何利用 GroupDocs.Metadata for .NET 來使用 C# 更新電子表格檔案中的內建屬性。 GroupDocs.Metadata 是一個功能強大的 API，允許開發人員從各種文件格式（包括電子表格）讀取、編輯和刪除元資料屬性。我們將特別關注修改 Excel 檔案中的作者、建立時間、公司、類別和關鍵字等屬性。
## 先決條件
在我們開始之前，請確保您具備以下條件：
- Visual Studio：安裝最新版本的 Visual Studio。
-  GroupDocs.Metadata for .NET：從下列位置下載並安裝 GroupDocs.Metadata for .NET[下載頁面](https://releases.groupdocs.com/metadata/net/).
- 基本 C# 知識：了解 C# 程式語言和 .NET 架構。

## 導入命名空間
首先在 C# 專案中導入必要的命名空間：
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## 第 1 步：載入電子表格文件
首先，初始化一個`Metadata`透過載入輸入電子表格檔案來物件：
```csharp
using (Metadata metadata = new Metadata("YourInputFile.xlsx"))
{
    var root = metadata.GetRootPackage<SpreadsheetRootPackage>();
    //存取根目錄中的文件屬性
}
```
## 第 2 步：更新內建屬性
透過以下方式存取內建文件屬性`SpreadsheetRootPackage`並根據需要修改它們：
```csharp
root.DocumentProperties.Author = "YourAuthorName";
root.DocumentProperties.CreatedTime = DateTime.Now;
root.DocumentProperties.Company = "YourCompany";
root.DocumentProperties.Category = "YourCategory";
root.DocumentProperties.Keywords = "metadata, built-in, update";
```
確保替換佔位符 (`YourAuthorName`, `YourCompany`, `YourCategory`以及您要為屬性設定的實際值。
## 第 3 步：儲存更改
更新屬性後，將變更儲存回電子表格檔案：
```csharp
metadata.Save("YourInputFile.xlsx");
```

## 結論
在本教學中，我們示範如何使用 GroupDocs.Metadata for .NET 以程式設計方式更新電子表格檔案的內建屬性。透過利用此 API，開發人員可以有效管理 Excel 文件中的元數據，從而增強資料組織和可存取性。

## 常見問題解答
### GroupDocs.Metadata 支援哪些文件格式？
GroupDocs.Metadata 支援多種文件格式，包括 Microsoft Office 文件、PDF、圖像、音訊檔案等。
### 我可以從文件中檢索現有的元資料屬性嗎？
是的，您可以使用 GroupDocs.Metadata 來提取和讀取元資料屬性，例如作者、建立日期、關鍵字和自訂屬性。
### GroupDocs.Metadata 與 .NET Core 相容嗎？
是的，GroupDocs.Metadata 與 .NET Framework 和 .NET Core 也相容。
### GroupDocs.Metadata 是否提供免費試用？
是的，您可以從以下位置下載 GroupDocs.Metadata 的免費試用版：[這裡](https://releases.groupdocs.com/).
### 在哪裡可以找到對 GroupDocs.Metadata 的支援？
如需支援和討論，請訪問[GroupDocs.元資料論壇](https://forum.groupdocs.com/c/metadata/14).