---
title: 從 .NET 中的 RAR 檔案讀取本機元資料屬性
linktitle: 從 .NET 中的 RAR 檔案讀取本機元資料屬性
second_title: GroupDocs.元資料 .NET API
description: 了解如何使用 C# 中的 GroupDocs.Metadata for .NET 從 RAR 檔案中擷取元資料屬性。輕鬆探索文件詳細資訊。
weight: 10
url: /zh-hant/net/archive-metadata/read-native-metadata-rar-archives/
---

# 從 .NET 中的 RAR 檔案讀取本機元資料屬性

## 介紹
RAR（Roshal Archive）是一種用於資料壓縮和歸檔的熱門檔案格式。在 .NET 應用程式中使用 RAR 檔案時，通常需要讀取和提取這些檔案中嵌入的元資料屬性。本教學將引導您完成使用 GroupDocs.Metadata for .NET 從 RAR 檔案中存取和擷取本機元資料屬性的過程。
## 先決條件

在開始之前，請確保您具備以下先決條件：
- 對 C# 程式語言有基本了解。
- Visual Studio 安裝在您的開發電腦上。
- 安裝了 .NET 程式庫的 GroupDocs.Metadata（請參閱[下載連結](https://releases.groupdocs.com/metadata/net/)）。
- 出於測試目的存取 RAR 存檔檔案。

## 導入命名空間
首先，將必要的命名空間匯入到您的 C# 專案中：
```csharp
using GroupDocs.Formats.Archive;
using System;
using GroupDocs.Metadata;
using System.Text;
```

## 第 1 步：載入 RAR 存檔
首先，初始化一個`Metadata`透過載入 RAR 存檔檔案來取得物件：
```csharp
using (Metadata metadata = new Metadata("YourZipFile.rar"))
{
    var root = metadata.GetRootPackage<RarRootPackage>();
```
## 第 2 步：存取 RAR 檔案中的全部條目
檢索 RAR 存檔中的條目（檔案/資料夾）總數：
```csharp
Console.WriteLine(root.RarPackage.TotalEntries);
```
## 第 3 步：遍歷存檔中的文件
循環遍歷 RAR 存檔中的每個檔案以存取特定的元資料屬性：
```csharp
foreach (var file in root.RarPackage.Files)
{
    Console.WriteLine(file.Name);
    Console.WriteLine(file.CompressedSize);
    Console.WriteLine(file.ModificationDateTime);
    Console.WriteLine(file.UncompressedSize);
}
```

## 結論
在本教學中，您學習如何使用 GroupDocs.Metadata for .NET 從 RAR 檔案中擷取元資料屬性。該程式庫簡化了存取和利用嵌入在各種文件格式中的元資料的過程，從而增強了 .NET 應用程式的功能。

## 常見問題解答
### 什麼是 .NET 的 GroupDocs.Metadata？
GroupDocs.Metadata for .NET 是一個功能強大的程式庫，允許開發人員處理各種文件格式的元數據，包括 RAR 等存檔。
### 如何取得 GroupDocs.Metadata for .NET 的臨時授權？
您可以從以下地址取得臨時許可證[這裡](https://purchase.groupdocs.com/temporary-license/).
### GroupDocs.Metadata 是否支援 RAR 之外的其他存檔格式？
是的，GroupDocs.Metadata 支援多種存檔格式，包括 ZIP、TAR 和 7z。
### 我可以使用此庫修改元資料屬性並在 RAR 檔案中更新它們嗎？
是的，GroupDocs.Metadata 允許您更新、刪除元資料屬性以及將元資料屬性新增至支援的檔案格式。
### 在哪裡可以找到有關 GroupDocs.Metadata 的其他協助或支援？
參觀[GroupDocs.元資料論壇](https://forum.groupdocs.com/c/metadata/14)以獲得社區支持和討論。