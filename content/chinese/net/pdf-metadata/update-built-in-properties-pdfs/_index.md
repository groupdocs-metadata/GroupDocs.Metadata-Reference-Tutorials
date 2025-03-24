---
title: 使用 .NET 更新 PDF 中的内置属性
linktitle: 使用 .NET 更新 PDF 中的内置属性
second_title: GroupDocs.元数据 .NET API
description: 了解如何使用 C# 和 GroupDocs.Metadata for .NET 更新 PDF 文档属性。以编程方式修改作者、标题、关键字等。
weight: 15
url: /zh/net/pdf-metadata/update-built-in-properties-pdfs/
---
## 介绍
在本教程中，我们将学习如何使用 GroupDocs.Metadata for .NET 更新 PDF 文档的内置属性。该库提供了一组强大的工具来操作各种文档格式中的元数据。我们将逐步完成使用 C# 修改 PDF 文件中的作者、标题、创建日期、关键字、创建者和制作者等属性的必要步骤。
## 先决条件
在我们开始之前，请确保您已具备以下条件：
-  GroupDocs.Metadata for .NET 库：从以下位置下载库[这里](https://releases.groupdocs.com/metadata/net/).
- Visual Studio：安装 Visual Studio 以编写和执行 C# 代码。
- 对 C# 的基本了解：建议熟悉 C# 编程语言。

## 导入命名空间
首先在 C# 项目中包含必要的命名空间：
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## 第 1 步：初始化元数据对象
首先初始化一个`Metadata`带有 PDF 文件路径的对象：
```csharp
using (Metadata metadata = new Metadata("Your Input File Path"))
{
    //您的代码将放在此处
}
```
## 步骤 2：访问 PDF 根包
接下来，使用以下方法检索 PDF 专用的根包`GetRootPackage<PdfRootPackage>()`：
```csharp
var root = metadata.GetRootPackage<PdfRootPackage>();
```
## 步骤 3：更新文档属性
现在，在`PdfRootPackage`：
```csharp
root.DocumentProperties.Author = "New Author Name";
root.DocumentProperties.CreatedDate = DateTime.Now;
root.DocumentProperties.Title = "New Document Title";
root.DocumentProperties.Keywords = "keyword1, keyword2";
root.DocumentProperties.Creator = "Document Creator";
root.DocumentProperties.Producer = "Document Producer";
```
## 步骤 4：保存更改
修改属性后，将更改保存回 PDF 文件：
```csharp
metadata.Save("Your Output File Path");
```
## 步骤 5：检索更新的属性
要验证更改，请重新加载元数据并检索更新的属性：
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

## 结论
在本教程中，我们探讨了如何利用 GroupDocs.Metadata for .NET 以编程方式更新 PDF 文档的内置属性。通过遵循概述的步骤，您可以使用 C# 高效地管理和修改 PDF 文件中的元数据。请随意探索 GroupDocs.Metadata 提供的更多功能和能力，以实现全面的元数据操作。

## 常见问题解答
### 问：.NET 的 GroupDocs.Metadata 是什么？
答：GroupDocs.Metadata for .NET 是一个库，允许开发人员以编程方式读取、编辑、删除和操作各种文档格式的元数据。
### 问：在哪里可以找到 .NET 的 GroupDocs.Metadata 文档？
答：您可以访问文档[这里](https://tutorials.groupdocs.com/metadata/net/).
### 问：如何下载适用于 .NET 的 GroupDocs.Metadata？
答：您可以从以下网址下载 GroupDocs.Metadata for .NET[此链接](https://releases.groupdocs.com/metadata/net/).
### 问：有免费试用吗？
答：是的，您可以获得免费试用版[这里](https://releases.groupdocs.com/).
### 问：在哪里可以获得 .NET 的 GroupDocs.Metadata 支持？
答：如需支持，请访问 GroupDocs.Metadata 论坛[这里](https://forum.groupdocs.com/c/metadata/14).