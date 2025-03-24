---
title: 从 .NET 中的 MP3 文件读取歌词标签
linktitle: 从 .NET 中的 MP3 文件读取歌词标签
second_title: GroupDocs.元数据 .NET API
description: 了解如何使用 GroupDocs.Metadata for .NET 从 MP3 文件中提取歌词标签。请按照我们的分步教程进行操作。
weight: 13
url: /zh/net/audio-metadata/read-lyrics-tag-mp3/
---
## 介绍
在本教程中，我们将学习如何使用 .NET 中的 GroupDocs.Metadata API 从 MP3 文件中提取和读取歌词标签。 GroupDocs.Metadata 是一个功能强大的库，允许开发人员处理与各种文件格式（包括 MP3 文件）相关的元数据。通过执行这些步骤，您将能够有效地检索 MP3 文件中嵌入的歌词相关信息。
## 先决条件
在我们开始之前，请确保您已设置以下先决条件：
- 您的机器上安装了 Visual Studio。
- C# 编程语言的基础知识。
- 用于 .NET 的 GroupDocs.Metadata 库。你可以下载它[这里](https://releases.groupdocs.com/metadata/net/).
- 访问包含歌词标签的 MP3 文件以进行测试。

## 导入命名空间
首先，在 C# 项目中包含必要的命名空间：
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Formats.Audio;
```
## 第 1 步：加载 MP3 文件
首先初始化一个`Metadata`对象与您的输入 MP3 文件路径：
```csharp
using (Metadata metadata = new Metadata("YourInputFile.mp3"))
{
    //获取MP3格式的根包
    var root = metadata.GetRootPackage<MP3RootPackage>();
```
## 第 2 步：访问歌词标签
检查 MP3 文件是否包含 Lyrics3V2 标签并检索关联信息：
```csharp
    if (root.Lyrics3V2 != null)
    {
        //输出特定标签字段
        Console.WriteLine("Lyrics: " + root.Lyrics3V2.Lyrics);
        Console.WriteLine("Album: " + root.Lyrics3V2.Album);
        Console.WriteLine("Artist: " + root.Lyrics3V2.Artist);
        Console.WriteLine("Track: " + root.Lyrics3V2.Track);
```
## 第 3 步：循环遍历所有标签字段
或者，您可以循环遍历 Lyrics3V2 中的所有可用标签字段：
```csharp
        foreach (var field in root.Lyrics3V2.ToList())
        {
            Console.WriteLine("{0} = {1}", field.ID, field.Data);
        }
    }
}
```

## 结论
在本教程中，我们探讨了如何使用 GroupDocs.Metadata for .NET 从 MP3 文件中提取和读取歌词标签。通过执行这些步骤，您可以有效地检索 MP3 文件中嵌入的与歌词相关的元数据，以便进一步处理或在应用程序中显示。

## 常见问题解答
### 我可以使用 GroupDocs.Metadata 修改或更新歌词标签吗？
是的，GroupDocs.Metadata 允许您更新和修改 MP3 文件中的元数据，包括歌词标签。
### GroupDocs.Metadata 是否支持除 MP3 之外的其他音频格式？
是的，GroupDocs.Metadata 支持多种音频和视频格式以进行元数据提取和操作。
### 在哪里可以找到有关 GroupDocs.Metadata 的更详细文档？
您可以访问完整的文档[这里](https://tutorials.groupdocs.com/metadata/net/).
### GroupDocs.Metadata 是否有免费试用版？
是的，您可以获得免费试用版[这里](https://releases.groupdocs.com/).
### 如何获得 GroupDocs.Metadata 的技术支持？
如需技术帮助，您可以访问 GroupDocs.Metadata 支持论坛[这里](https://forum.groupdocs.com/c/metadata/14).