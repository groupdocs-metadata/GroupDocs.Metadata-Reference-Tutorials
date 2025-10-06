---
title: 使用 .NET 更新电子表格中的内置属性
linktitle: 使用 .NET 更新电子表格中的内置属性
second_title: GroupDocs.元数据 .NET API
description: 了解如何使用 GroupDocs.Metadata for .NET 更新 Excel 文件中的内置元数据属性。使用C#修改作者、创建时间、公司等。
weight: 14
url: /zh/net/spreadsheet-metadata/update-built-in-properties-spreadsheets/
type: docs
---
# 使用 .NET 更新电子表格中的内置属性

## 介绍
在本教程中，我们将探索如何利用 GroupDocs.Metadata for .NET 来使用 C# 更新电子表格文件中的内置属性。 GroupDocs.Metadata 是一个功能强大的 API，允许开发人员从各种文件格式（包括电子表格）读取、编辑和删除元数据属性。我们将特别关注修改 Excel 文件中的作者、创建时间、公司、类别和关键字等属性。
## 先决条件
在开始之前，请确保您已准备好以下物品：
- Visual Studio：安装最新版本的 Visual Studio。
-  GroupDocs.Metadata for .NET：从[下载页面](https://releases.groupdocs.com/metadata/net/).
- 基本 C# 知识：了解 C# 编程语言和 .NET 框架。

## 导入命名空间
首先在 C# 项目中导入必要的命名空间：
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## 第 1 步：加载电子表格文件
首先，初始化一个`Metadata`通过加载输入电子表格文件来对象：
```csharp
using (Metadata metadata = new Metadata("YourInputFile.xlsx"))
{
    var root = metadata.GetRootPackage<SpreadsheetRootPackage>();
    //访问根目录中的文档属性
}
```
## 第 2 步：更新内置属性
通过以下方式访问内置文档属性`SpreadsheetRootPackage`并根据需要修改它们：
```csharp
root.DocumentProperties.Author = "YourAuthorName";
root.DocumentProperties.CreatedTime = DateTime.Now;
root.DocumentProperties.Company = "YourCompany";
root.DocumentProperties.Category = "YourCategory";
root.DocumentProperties.Keywords = "metadata, built-in, update";
```
确保替换占位符 (`YourAuthorName`, `YourCompany`, `YourCategory`以及您要为属性设置的实际值。
## 步骤 3：保存更改
更新属性后，将更改保存回电子表格文件：
```csharp
metadata.Save("YourInputFile.xlsx");
```

## 结论
在本教程中，我们演示了如何使用 GroupDocs.Metadata for .NET 以编程方式更新电子表格文件的内置属性。通过利用此 API，开发人员可以有效管理 Excel 文档中的元数据，从而增强数据组织和可访问性。

## 常见问题解答
### GroupDocs.Metadata 支持哪些文件格式？
GroupDocs.Metadata 支持多种文件格式，包括 Microsoft Office 文档、PDF、图像、音频文件等。
### 我可以从文件中检索现有的元数据属性吗？
是的，您可以使用 GroupDocs.Metadata 提取和读取元数据属性，例如作者、创建日期、关键字和自定义属性。
### GroupDocs.Metadata 是否与 .NET Core 兼容？
是的，GroupDocs.Metadata 与 .NET Framework 和 .NET Core 兼容。
### GroupDocs.Metadata 是否提供免费试用？
是的，您可以从以下位置下载 GroupDocs.Metadata 的免费试用版：[这里](https://releases.groupdocs.com/).
### 在哪里可以找到对 GroupDocs.Metadata 的支持？
如需支持和讨论，请访问[GroupDocs.Metadata 论坛](https://forum.groupdocs.com/c/metadata/14).