---
title: 從 .NET 中的電子表格讀取內建屬性
linktitle: 從 .NET 中的電子表格讀取內建屬性
second_title: GroupDocs.元資料 .NET API
description: 了解如何使用 GroupDocs.Metadata 從 .NET 中的電子表格中提取元數據，從而增強應用程式中的文件管理和組織。
type: docs
weight: 10
url: /zh-hant/net/spreadsheet-metadata/read-built-in-properties-spreadsheets/
---
## 介紹
在本教程中，我們將深入研究如何利用 GroupDocs.Metadata for .NET 高效管理和從電子表格中提取元資料。 GroupDocs.Metadata for .NET 是一個功能強大的 API，使開發人員能夠使用嵌入各種文件格式的元數據，包括電子表格、簡報、文件、圖像等。本指南特別關注使用 C# 從電子表格檔案中提取內建屬性。
## 先決條件
在開始之前，請確保您具備以下先決條件：
- 開發環境：Visual Studio 或任何 C# 相容 IDE。
-  GroupDocs.Metadata for .NET 程式庫：從下列位置下載並安裝該程式庫：[網站](https://releases.groupdocs.com/metadata/net/).
- 輸入檔案：準備一個要從中提取元資料的範例電子表格檔案（例如 Excel）。

## 導入命名空間
首先匯入必要的命名空間以存取 C# 專案中的 GroupDocs.Metadata 功能。
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## 第 1 步：初始化元資料並檢索電子表格根包
首先初始化`Metadata`物件與您的輸入檔案路徑。然後，取得電子表格特定的根包。
```csharp
using (Metadata metadata = new Metadata("YourInputFile.xlsx"))
{
    var root = metadata.GetRootPackage<SpreadsheetRootPackage>();
    
    //存取和檢索內建屬性
}
```
## 第 2 步：存取內建屬性
獲得根包後，您可以使用以下命令存取電子表格檔案的各種內建屬性`DocumentProperties`.
### 步驟2.1：訪問作者屬性
檢索電子表格的作者（創建者）。
```csharp
Console.WriteLine(root.DocumentProperties.Author);
```
### 步驟2.2：存取建立時間屬性
取得電子表格的建立時間戳記。
```csharp
Console.WriteLine(root.DocumentProperties.CreatedTime);
```
### 步驟 2.3：訪問公司財產
取得與電子表格關聯的公司名稱。
```csharp
Console.WriteLine(root.DocumentProperties.Company);
```
### 步驟2.4：存取類別屬性
取得電子表格的類別資訊。
```csharp
Console.WriteLine(root.DocumentProperties.Category);
```
### 步驟2.5：存取關鍵字屬性
檢索與電子表格關聯的關鍵字。
```csharp
Console.WriteLine(root.DocumentProperties.Keywords);
```
### 步驟2.6：存取語言屬性
檢索電子表格中使用的語言。
```csharp
Console.WriteLine(root.DocumentProperties.Language);
```
### 步驟2.7：存取內容類型屬性
取得電子表格的內容類型或 MIME 類型。
```csharp
Console.WriteLine(root.DocumentProperties.ContentType);
```

## 結論
在本教程中，我們探討如何使用 GroupDocs.Metadata for .NET 使用 C# 從電子表格檔案中提取內建屬性。透過執行這些步驟，您可以將元資料管理無縫整合到 .NET 應用程式中，從而增強檔案組織和檢索功能。

## 常見問題解答
### GroupDocs.Metadata for .NET 是否與各種文件格式相容？
是的，GroupDocs.Metadata 支援多種文件格式，包括電子表格、文件、簡報、圖像等。
### 我可以使用 GroupDocs.Metadata for .NET 修改元資料嗎？
是的，您不僅可以使用此 API 讀取元數據，還可以編輯、更新和刪除元數據。
### 在哪裡可以找到 GroupDocs.Metadata for .NET 的詳細文件？
詳細文件可參見[.NET 文件的 GroupDocs.Metadata](https://reference.groupdocs.com/metadata/net/).
### 我如何獲得用於測試目的的臨時許可證？
您可以向以下機構申請臨時許可證[這裡](https://purchase.groupdocs.com/temporary-license/).
### 是否有 GroupDocs.Metadata 支援的社群論壇？
是的，您可以訪問[GroupDocs.元資料論壇](https://forum.groupdocs.com/c/metadata/14)以獲得社區支持和討論。