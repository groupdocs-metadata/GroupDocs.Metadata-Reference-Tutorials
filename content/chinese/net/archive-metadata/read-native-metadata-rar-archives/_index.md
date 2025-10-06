---
title: 在 .NET 中从 RAR 档案读取本机元数据属性
linktitle: 在 .NET 中从 RAR 档案读取本机元数据属性
second_title: GroupDocs.元数据 .NET API
description: 了解如何使用 C# 中的 GroupDocs.Metadata for .NET 从 RAR 档案中提取元数据属性。轻松探索文件详细信息。
weight: 10
url: /zh/net/archive-metadata/read-native-metadata-rar-archives/
type: docs
---
# 在 .NET 中从 RAR 档案读取本机元数据属性

## 介绍
RAR（Roshal Archive）是一种用于数据压缩和归档的流行文件格式。在 .NET 应用程序中处理 RAR 文件时，通常需要读取和提取嵌入在这些档案中的元数据属性。本教程将指导您完成利用 GroupDocs.Metadata for .NET 访问和提取 RAR 档案中的原生元数据属性的过程。
## 先决条件

开始之前，请确保您满足以下先决条件：
- 对 C# 编程语言有基本的了解。
- 您的开发机器上安装了 Visual Studio。
- 已安装 GroupDocs.Metadata for .NET 库（请参阅[下载链接](https://releases.groupdocs.com/metadata/net/)）。
- 访问 RAR 存档文件以进行测试。

## 导入命名空间
首先，将必要的命名空间导入到你的 C# 项目中：
```csharp
using GroupDocs.Formats.Archive;
using System;
using GroupDocs.Metadata;
using System.Text;
```

## 步骤 1：加载 RAR 档案
首先，初始化一个`Metadata`通过加载 RAR 存档文件来获取对象：
```csharp
using (Metadata metadata = new Metadata("YourZipFile.rar"))
{
    var root = metadata.GetRootPackage<RarRootPackage>();
```
## 第 2 步：访问 RAR 存档中的总条目数
检索 RAR 档案中的条目总数（文件/文件夹）：
```csharp
Console.WriteLine(root.RarPackage.TotalEntries);
```
## 步骤 3：遍历存档中的文件
循环遍历 RAR 存档中的每个文件以访问特定的元数据属性：
```csharp
foreach (var file in root.RarPackage.Files)
{
    Console.WriteLine(file.Name);
    Console.WriteLine(file.CompressedSize);
    Console.WriteLine(file.ModificationDateTime);
    Console.WriteLine(file.UncompressedSize);
}
```

## 结论
在本教程中，您学习了如何使用 GroupDocs.Metadata for .NET 从 RAR 档案中提取元数据属性。此库简化了访问和利用嵌入在各种文件格式中的元数据的过程，增强了 .NET 应用程序的功能。

## 常见问题解答
### .NET 的 GroupDocs.Metadata 是什么？
GroupDocs.Metadata for .NET 是一个功能强大的库，允许开发人员处理各种文件格式的元数据，包括 RAR 等档案。
### 如何获取 .NET 的 GroupDocs.Metadata 临时许可证？
您可以从[这里](https://purchase.groupdocs.com/temporary-license/).
### GroupDocs.Metadata 除了支持 RAR 之外还支持其他存档格式吗？
是的，GroupDocs.Metadata 支持多种存档格式，包括 ZIP、TAR 和 7z。
### 我可以使用此库修改元数据属性并在 RAR 存档中更新它们吗？
是的，GroupDocs.Metadata 允许您更新、删除元数据属性以及将元数据属性添加到支持的文件格式。
### 在哪里可以找到有关 GroupDocs.Metadata 的其他帮助或支持？
参观[GroupDocs.Metadata 论坛](https://forum.groupdocs.com/c/metadata/14)以获得社区支持和讨论。