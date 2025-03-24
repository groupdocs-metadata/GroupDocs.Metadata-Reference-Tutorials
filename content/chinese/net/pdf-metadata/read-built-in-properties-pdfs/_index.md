---
title: 从 .NET 中的 PDF 读取内置属性
linktitle: 从 .NET 中的 PDF 读取内置属性
second_title: GroupDocs.元数据 .NET API
description: 了解如何使用 GroupDocs.Metadata 在 .NET 中读取 PDF 元数据。使用 C# 代码访问作者姓名、创建日期、主题等。
weight: 10
url: /zh/net/pdf-metadata/read-built-in-properties-pdfs/
---

# 从 .NET 中的 PDF 读取内置属性

## 介绍
在本教程中，我们将探讨如何利用 GroupDocs.Metadata for .NET 从 PDF 文件读取内置属性。 GroupDocs.Metadata 是一个功能强大的库，允许开发人员处理与各种文档格式相关的元数据，包括 PDF、Microsoft Office 文档、图像等。通过使用此库，您可以轻松访问和操作 PDF 文件中嵌入的元数据属性，例如作者姓名、创建日期、主题等。
## 先决条件
在深入学习本教程之前，请确保您具备以下先决条件：
- Visual Studio：确保您的计算机上安装了 Visual Studio。
-  GroupDocs.Metadata for .NET：从以下位置下载并安装 GroupDocs.Metadata for .NET[这里](https://releases.groupdocs.com/metadata/net/).
- C#基础知识：熟悉 C# 编程语言和 .NET 框架。

## 导入命名空间
首先将必要的命名空间添加到您的 C# 项目中：
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## 第 1 步：加载 PDF 元数据
首先，加载 PDF 文件并使用 GroupDocs.Metadata 提取其元数据：
```csharp
using (Metadata metadata = new Metadata("YourInputFile.pdf"))
{
    //访问PDF文件的根包
    var root = metadata.GetRootPackage<PdfRootPackage>();
    //检索并显示内置属性
    Console.WriteLine("Author: " + root.DocumentProperties.Author);
    Console.WriteLine("Created Date: " + root.DocumentProperties.CreatedDate);
    Console.WriteLine("Subject: " + root.DocumentProperties.Subject);
    Console.WriteLine("Producer: " + root.DocumentProperties.Producer);
    Console.WriteLine("Keywords: " + root.DocumentProperties.Keywords);
    //可以类似地访问其他属性
    //...
}
```
除了读取元数据之外，GroupDocs.Metadata 还允许以编程方式对 PDF 文件进行编辑、删除或添加新的元数据属性等高级操作。这种灵活性支持对 .NET 应用程序中的文档元数据进行全面管理。
## 结论
在本教程中，我们介绍了如何利用 GroupDocs.Metadata for .NET 使用 C# 从 PDF 文件中提取内置属性。通过将该库集成到您的项目中，您可以无缝处理文档元数据操作，从而提供增强的文档管理功能。

## 常见问题解答
### GroupDocs.Metadata 可以与其他文档格式一起使用吗？
是的，GroupDocs.Metadata 支持各种文档格式，例如 DOCX、XLSX、PPTX、PDF、JPG、PNG 等。
### GroupDocs.Metadata 是否有免费试用版？
是的，您可以从以下网址免费试用 GroupDocs.Metadata[这里](https://releases.groupdocs.com/).
### 如何使用 GroupDocs.Metadata 修改元数据属性？
您可以通过访问相应的文档包并设置新值以编程方式修改元数据属性。
### GroupDocs.Metadata 是否支持 .NET Core？
是的，GroupDocs.Metadata 与 .NET Framework 和 .NET Core 兼容。
### 在哪里可以找到支持或询问与 GroupDocs.Metadata 相关的问题？
如需支持和讨论，请访问[GroupDocs.Metadata 论坛](https://forum.groupdocs.com/c/metadata/14).