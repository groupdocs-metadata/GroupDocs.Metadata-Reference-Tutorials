---
title: Read Native Metadata Properties from RAR Archives in .NET
linktitle: Read Native Metadata Properties from RAR Archives in .NET
second_title: GroupDocs.Metadata .NET API
description: Learn how to extract metadata properties from RAR archives using GroupDocs.Metadata for .NET in C#. Explore file details effortlessly.
weight: 10
url: /net/archive-metadata/read-native-metadata-rar-archives/
---
## Introduction
RAR (Roshal Archive) is a popular file format used for data compression and archiving. When working with RAR files in .NET applications, it's often necessary to read and extract metadata properties embedded within these archives. This tutorial will guide you through the process of utilizing GroupDocs.Metadata for .NET to access and extract native metadata properties from RAR archives.
## Prerequisites

Before you begin, ensure you have the following prerequisites:
- Basic understanding of C# programming language.
- Visual Studio installed on your development machine.
- GroupDocs.Metadata for .NET library installed (refer to [download link](https://releases.groupdocs.com/metadata/net/)).
- Access to a RAR archive file for testing purposes.

## Import Namespaces
To get started, import the necessary namespaces into your C# project:
```csharp
using GroupDocs.Formats.Archive;
using System;
using GroupDocs.Metadata;
using System.Text;
```

## Step 1: Load the RAR Archive
First, initialize a `Metadata` object by loading your RAR archive file:
```csharp
using (Metadata metadata = new Metadata("YourZipFile.rar"))
{
    var root = metadata.GetRootPackage<RarRootPackage>();
```
## Step 2: Access Total Entries in RAR Archive
Retrieve the total number of entries (files/folders) within the RAR archive:
```csharp
Console.WriteLine(root.RarPackage.TotalEntries);
```
## Step 3: Iterate Through Files in the Archive
Loop through each file within the RAR archive to access specific metadata properties:
```csharp
foreach (var file in root.RarPackage.Files)
{
    Console.WriteLine(file.Name);
    Console.WriteLine(file.CompressedSize);
    Console.WriteLine(file.ModificationDateTime);
    Console.WriteLine(file.UncompressedSize);
}
```

## Conclusion
In this tutorial, you've learned how to extract metadata properties from RAR archives using GroupDocs.Metadata for .NET. This library simplifies the process of accessing and utilizing metadata embedded within various file formats, enhancing the capabilities of your .NET applications.

## FAQ's
### What is GroupDocs.Metadata for .NET?
GroupDocs.Metadata for .NET is a powerful library that allows developers to work with metadata in various file formats, including archives like RAR.
### How can I obtain a temporary license for GroupDocs.Metadata for .NET?
You can obtain a temporary license from [here](https://purchase.groupdocs.com/temporary-license/).
### Does GroupDocs.Metadata support other archive formats apart from RAR?
Yes, GroupDocs.Metadata supports a wide range of archive formats, including ZIP, TAR, and 7z.
### Can I modify metadata properties and update them within the RAR archive using this library?
Yes, GroupDocs.Metadata allows you to update, remove, and add metadata properties to supported file formats.
### Where can I find additional help or support for GroupDocs.Metadata?
Visit the [GroupDocs.Metadata forum](https://forum.groupdocs.com/c/metadata/14) for community support and discussions.
