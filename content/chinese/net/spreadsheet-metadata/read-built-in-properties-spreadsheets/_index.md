---
title: 从 .NET 中的电子表格读取内置属性
linktitle: 从 .NET 中的电子表格读取内置属性
second_title: GroupDocs.元数据 .NET API
description: 了解如何使用 GroupDocs.Metadata 从 .NET 中的电子表格中提取元数据，增强应用程序中的文档管理和组织。
weight: 10
url: /zh/net/spreadsheet-metadata/read-built-in-properties-spreadsheets/
type: docs
---
# 从 .NET 中的电子表格读取内置属性

## 介绍
在本教程中，我们将深入研究如何利用 GroupDocs.Metadata for .NET 高效管理和从电子表格中提取元数据。 GroupDocs.Metadata for .NET 是一个功能强大的 API，使开发人员能够使用嵌入各种文件格式的元数据，包括电子表格、演示文稿、文档、图像等。本指南特别关注使用 C# 从电子表格文件中提取内置属性。
## 先决条件
在开始之前，请确保您具备以下先决条件：
- 开发环境：Visual Studio 或任何 C# 兼容 IDE。
-  GroupDocs.Metadata for .NET 库：从[网站](https://releases.groupdocs.com/metadata/net/).
- 输入文件：准备一个要从中提取元数据的示例电子表格文件（例如 Excel）。

## 导入命名空间
首先导入必要的命名空间以访问 C# 项目中的 GroupDocs.Metadata 功能。
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## 第 1 步：初始化元数据并检索电子表格根包
首先初始化`Metadata`对象与您的输入文件路径。然后，获取电子表格特定的根包。
```csharp
using (Metadata metadata = new Metadata("YourInputFile.xlsx"))
{
    var root = metadata.GetRootPackage<SpreadsheetRootPackage>();
    
    //访问和检索内置属性
}
```
## 第 2 步：访问内置属性
获得根包后，您可以使用以下命令访问电子表格文件的各种内置属性`DocumentProperties`.
### 步骤2.1：访问作者属性
检索电子表格的作者（创建者）。
```csharp
Console.WriteLine(root.DocumentProperties.Author);
```
### 步骤2.2：访问创建时间属性
获取电子表格的创建时间戳。
```csharp
Console.WriteLine(root.DocumentProperties.CreatedTime);
```
### 步骤 2.3：访问公司财产
获取与电子表格关联的公司名称。
```csharp
Console.WriteLine(root.DocumentProperties.Company);
```
### 步骤2.4：访问类别属性
获取电子表格的类别信息。
```csharp
Console.WriteLine(root.DocumentProperties.Category);
```
### 步骤2.5：访问关键字属性
检索与电子表格关联的关键字。
```csharp
Console.WriteLine(root.DocumentProperties.Keywords);
```
### 步骤2.6：访问语言属性
检索电子表格中使用的语言。
```csharp
Console.WriteLine(root.DocumentProperties.Language);
```
### 步骤2.7：访问内容类型属性
获取电子表格的内容类型或 MIME 类型。
```csharp
Console.WriteLine(root.DocumentProperties.ContentType);
```

## 结论
在本教程中，我们探讨了如何使用 GroupDocs.Metadata for .NET 通过 C# 从电子表格文件中提取内置属性。通过遵循这些步骤，您可以将元数据管理无缝集成到 .NET 应用程序中，从而增强文件组织和检索功能。

## 常见问题解答
### .NET 的 GroupDocs.Metadata 是否兼容各种文件格式？
是的，GroupDocs.Metadata 支持多种文件格式，包括电子表格、文档、演示文稿、图像等。
### 我可以使用 GroupDocs.Metadata for .NET 修改元数据吗？
是的，您不仅可以使用此 API 读取元数据，还可以编辑、更新和删除元数据。
### 在哪里可以找到有关 .NET 的 GroupDocs.Metadata 的详细文档？
详细文档可参见[.NET 文档的 GroupDocs.Metadata](https://tutorials.groupdocs.com/metadata/net/).
### 我如何才能获得用于测试目的的临时许可证？
您可以从申请临时许可证[这里](https://purchase.groupdocs.com/temporary-license/).
### 是否有一个 GroupDocs.Metadata 支持的社区论坛？
是的，您可以访问[GroupDocs.Metadata 论坛](https://forum.groupdocs.com/c/metadata/14)以获得社区支持和讨论。