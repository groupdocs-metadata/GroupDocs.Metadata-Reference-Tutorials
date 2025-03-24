---
title: 使用 .NET 更新 MP3 文件中的歌词标签
linktitle: 使用 .NET 更新 MP3 文件中的歌词标签
second_title: GroupDocs.元数据 .NET API
description: 了解如何使用 GroupDocs.Metadata for .NET 以编程方式更新 MP3 文件元数据，包括歌词、艺术家和专辑详细信息。
weight: 21
url: /zh/net/audio-metadata/update-lyrics-tag-mp3/
---
## 介绍
在本教程中，我们将演示如何使用 GroupDocs.Metadata for .NET 库以编程方式更新 MP3 文件中的歌词标签。此过程涉及访问和修改 MP3 文件的元数据，特别是针对歌词信息。
## 先决条件
在开始之前，请确保您具备以下条件：
- C# 编程基础知识。
- 您的机器上安装了 Visual Studio。
- 已安装 GroupDocs.Metadata for .NET 库（请参阅[下载链接](https://releases.groupdocs.com/metadata/net/)）。
- 用于测试目的的 MP3 文件。

## 导入命名空间
首先将必要的命名空间导入到您的 C# 项目中：
```csharp
using GroupDocs.Formats.Audio;
using System;
using GroupDocs.Metadata;
```
## 第 1 步：加载 MP3 文件
首先，将 MP3 文件加载到`Metadata`使用 GroupDocs.Metadata 的对象：
```csharp
using (Metadata metadata = new Metadata("path_to_your_mp3_file.mp3"))
{
    var root = metadata.GetRootPackage<MP3RootPackage>();
    //访问 Lyrics3V2 标签
    if (root.Lyrics3V2 == null)
    {
        root.Lyrics3V2 = new LyricsTag();
    }
```
## 第2步：更新歌词信息
接下来，更新歌词信息以及其他相关详细信息，例如艺术家、专辑和曲目：
```csharp
    root.Lyrics3V2.Lyrics = "[00:01]Test lyrics";
    root.Lyrics3V2.Artist = "test artist";
    root.Lyrics3V2.Album = "test album";
    root.Lyrics3V2.Track = "test track";
```
## 第 3 步：添加自定义字段（可选）
或者，您可以向标记添加自定义字段：
```csharp
    root.Lyrics3V2.Set(new LyricsField("ABC", "custom value"));
```
## 步骤 4：保存更改
最后，将修改后的元数据保存回 MP3 文件：
```csharp
    metadata.Save("path_to_your_output_file.mp3");
}
```

## 结论
在本教程中，我们探讨了如何使用 GroupDocs.Metadata for .NET 更新 MP3 文件中的歌词标签。通过遵循概述的步骤，您可以以编程方式有效地管理和修改 MP3 文件中的元数据。

## 常见问题解答
### 我可以使用 GroupDocs.Metadata for .NET 更新除歌词之外的其他元数据吗？
是的，GroupDocs.Metadata for .NET 允许您处理不同文件格式的各种类型的元数据。
### .NET 的 GroupDocs.Metadata 是否与 .NET Core 兼容？
是的，该库同时支持 .NET Framework 和 .NET Core。
### GroupDocs.Metadata for .NET 是否需要许可证才能用于商业用途？
是的，你可以从[群组文档](https://purchase.groupdocs.com/buy)用于商业用途。
### 如何获得支持或询问与 GroupDocs.Metadata for .NET 相关的问题？
您可以访问[GroupDocs.Metadata 论坛](https://forum.groupdocs.com/c/metadata/14)寻求支持和讨论。
### 我可以免费试用 .NET 的 GroupDocs.Metadata 吗？
是的，你可以得到一个[免费试用](https://releases.groupdocs.com/)探索其特征。