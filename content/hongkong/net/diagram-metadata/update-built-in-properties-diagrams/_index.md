---
title: 使用 .NET 更新圖表中的內建屬性
linktitle: 使用 .NET 更新圖表中的內建屬性
second_title: GroupDocs.元資料 .NET API
description: 了解如何使用 GroupDocs.Metadata for .NET 更新圖表中的內建屬性。使用程式碼範例無縫修改元資料。
weight: 14
url: /zh-hant/net/diagram-metadata/update-built-in-properties-diagrams/
type: docs
---
# 使用 .NET 更新圖表中的內建屬性

## 介紹
在本教學中，我們將探討如何使用 GroupDocs.Metadata for .NET 更新圖表中的內建屬性。該庫允許您操作各種文件格式（包括圖表）中的元資料。我們將介紹先決條件、必要的命名空間，並提供帶有程式碼範例的逐步指南，以有效更新這些屬性。

## 先決條件

在開始之前，請確保您具備以下條件：

- Visual Studio：安裝在您的電腦上。
- GroupDocs.Metadata for .NET：下載並新增為專案的參考。
- C#基礎知識：了解C#程式語言。

## 導入命名空間

首先匯入必要的命名空間以存取 GroupDocs.Metadata 庫功能：

```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```

讓我們將使用 GroupDocs.Metadata 更新圖表中內建屬性的過程分解為多個步驟：

## 第 1 步：初始化元資料對象

首先初始化一個`Metadata`帶有輸入圖檔案路徑的物件：

```csharp
using (Metadata metadata = new Metadata("Your Input File"))
{
    var root = metadata.GetRootPackage<DiagramRootPackage>();
```

## 第 2 步：更新文檔屬性

現在，存取並修改圖表所需的內建屬性：

```csharp
root.DocumentProperties.Creator = "test author";
root.DocumentProperties.TimeCreated = DateTime.Now;
root.DocumentProperties.Company = "GroupDocs";
root.DocumentProperties.Category = "test category";
root.DocumentProperties.Keywords = "metadata, built-in, update";
```

您可以設定屬性，例如`Creator`, `TimeCreated`, `Company`, `Category`, `Keywords`等等，根據您的要求。

## 第 3 步：儲存更改

最後，將更新的元資料儲存回圖表檔案：

```csharp
metadata.Save("Your Input File");
```

## 結論

透過執行這些步驟，您可以使用 GroupDocs.Metadata for .NET 來有效地更新圖表中的內建屬性。這種方法使您能夠無縫管理元數據，確保準確且相關的資訊與您的圖表檔案相關聯。


## 常見問題解答

### Q：除了內建元資料屬性之外，我還可以修改其他元資料屬性嗎？
答：是的，GroupDocs.Metadata for .NET 支援編輯各種元資料屬性，例如 EXIF、IPTC、XMP 和自訂屬性。

### Q：購買前是否有試用版可供測試？
答：是的，您可以從以下位置下載免費試用版：[這裡](https://releases.groupdocs.com/).

### Q：如何獲得 GroupDocs.Metadata for .NET 的技術支援？
答：您可以訪問[GroupDocs.元資料論壇](https://forum.groupdocs.com/c/metadata/14)尋求幫助。

### Q：在哪裡可以找到 GroupDocs.Metadata for .NET 的詳細文件？
答：參考綜合[文件](https://tutorials.groupdocs.com/metadata/net/)以獲得深入指導。

### Q：我可以購買臨時許可證用於短期使用嗎？
答：是的，您可以從以下機構獲得臨時許可證：[這裡](https://purchase.groupdocs.com/temporary-license/).