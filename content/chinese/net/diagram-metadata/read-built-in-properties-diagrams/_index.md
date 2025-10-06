---
title: 从 .NET 中的图表读取内置属性
linktitle: 从 .NET 中的图表读取内置属性
second_title: GroupDocs.元数据 .NET API
description: 学习使用 GroupDocs.Metadata 从 .NET 中的图表文件中提取元数据。有效增强文档管理和分析。
weight: 10
url: /zh/net/diagram-metadata/read-built-in-properties-diagrams/
type: docs
---
# 从 .NET 中的图表读取内置属性

## 介绍
在本教程中，我们将深入研究使用 GroupDocs.Metadata for .NET 从图表中读取内置属性。 GroupDocs.Metadata for .NET 是一个功能强大的库，使开发人员能够处理与各种文档类型相关的元数据，包括图表、演示文稿、图像等。具体来说，我们将重点关注使用此库从图表文件中提取元数据属性。
## 先决条件
在我们开始之前，请确保您具备以下先决条件：
- C# 和 .NET 开发的基础知识。
- 您的计算机上安装了 Visual Studio IDE。
-  .NET 库的 GroupDocs.Metadata。您可以从以下位置下载：[这里](https://releases.groupdocs.com/metadata/net/).
- 用于从中提取元数据的输入图文件（例如.vsdx）。

## 导入命名空间
首先在 C# 项目中导入必要的命名空间以使用 GroupDocs.Metadata 功能：
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## 第 1 步：加载图表文件
首先加载要从中提取元数据的图表文件：
```csharp
using (Metadata metadata = new Metadata("YourDiagramFile.vsdx"))
{
    //访问图表的根包
    var root = metadata.GetRootPackage<DiagramRootPackage>();
    //现在，您可以访问各种文档属性
    //让我们将一些属性打印到控制台
}
```
## 第 2 步：访问内置属性
加载图表文件后，您可以通过以下方式访问其内置属性`DocumentProperties`：
```csharp
Console.WriteLine(root.DocumentProperties.Creator);
Console.WriteLine(root.DocumentProperties.Company);
Console.WriteLine(root.DocumentProperties.Keywords);
Console.WriteLine(root.DocumentProperties.Language);
Console.WriteLine(root.DocumentProperties.TimeCreated);
Console.WriteLine(root.DocumentProperties.Category);
```
## 第 3 步：利用其他元数据信息
除了`DocumentProperties`、GroupDocs.Metadata 提供对特定于图表文件的其他元数据属性的访问。例如，您可以根据图表类型访问图层、页面、形状等。

## 结论
在本教程中，我们探索了如何使用 GroupDocs.Metadata for .NET 轻松地从图表文件中读取内置属性。利用该库，开发人员可以有效地管理和提取与其 .NET 应用程序中的各种文档类型相关的元数据。

## 常见问题解答
### GroupDocs.Metadata for .NET 支持哪些类型的图表文件？
GroupDocs.Metadata for .NET 支持多种图表文件格式，包括 .vsdx、.vssx、.vstx 等。
### 我可以使用 GroupDocs.Metadata for .NET 修改元数据属性吗？
是的，您不仅可以使用此库读取还可以更新和删除元数据属性。
### GroupDocs.Metadata for .NET 有试用版吗？
是的，您可以访问免费试用版[这里](https://releases.groupdocs.com/).
### 如何获得 GroupDocs.Metadata for .NET 的技术支持？
如需技术帮助，您可以访问[GroupDocs.Metadata 论坛](https://forum.groupdocs.com/c/metadata/14).
### 我可以在哪里购买 GroupDocs.Metadata for .NET 的许可证？
您可以从购买许可证[这里](https://purchase.groupdocs.com/buy).