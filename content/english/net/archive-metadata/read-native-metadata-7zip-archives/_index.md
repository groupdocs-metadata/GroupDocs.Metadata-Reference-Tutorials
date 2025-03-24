---
title: Read Native Metadata Properties from 7Zip Archives in .NET
linktitle: Read Native Metadata Properties from 7Zip Archives in .NET
second_title: GroupDocs.Metadata .NET API
description: Learn how to read native metadata properties from 7Zip archives using GroupDocs.Metadata for .NET. Enhance your .NET application's data management capabilities.
weight: 11
url: /net/archive-metadata/read-native-metadata-7zip-archives/
---

# Read Native Metadata Properties from 7Zip Archives in .NET

## Introduction
In the realm of .NET development, managing metadata—such as document properties, file information, and tags—is crucial for efficient data organization and retrieval. GroupDocs.Metadata for .NET provides a powerful toolkit for accessing and manipulating metadata within various file formats. This tutorial focuses on harnessing the capabilities of GroupDocs.Metadata to read native metadata properties from 7Zip archives in .NET. 
## Prerequisites
Before diving into this tutorial, ensure you have the following prerequisites set up:
- Visual Studio installed on your machine.
- Basic understanding of C# programming language.
- GroupDocs.Metadata for .NET library downloaded and tutorialsd in your project.

## Import Namespaces
Start by importing the necessary namespaces for utilizing GroupDocs.Metadata within your C# project.
```csharp
using GroupDocs.Metadata.Common;
using GroupDocs.Metadata.Options;
using GroupDocs.Formats.Archive;
using System;
using GroupDocs.Metadata;
using System.Text;
```
## Step 1: Load the 7Zip Archive
Begin by loading the 7Zip archive file into a `Metadata` object from GroupDocs.Metadata.
```csharp
using (Metadata metadata = new Metadata("YourZipFile.zip"))
{
    // Code to read metadata will go here
}
```
## Step 2: Access 7Zip Metadata Properties
Inside the `using` block, retrieve the root package of the 7Zip archive to access its properties.
```csharp
var root = metadata.GetRootPackage<SevenZipRootPackage>();
```
## Step 3: Display Total Entries
Retrieve and display the total number of entries (files and directories) within the 7Zip archive.
```csharp
Console.WriteLine(root.SevenZipPackage.TotalEntries);
```
## Step 4: Iterate Through Files
Iterate through each file in the 7Zip archive to access individual file metadata.
```csharp
foreach (var file in root.SevenZipPackage.Files)
{
    Console.WriteLine(file.Name);
    Console.WriteLine(file.CompressedSize);
    Console.WriteLine(file.ModificationDateTime);
    Console.WriteLine(file.UncompressedSize);
}
```

## Conclusion
In this tutorial, we explored how to utilize GroupDocs.Metadata for .NET to read native metadata properties from 7Zip archives. By following these steps, you can effectively extract and utilize metadata information embedded within your archive files, enhancing your .NET applications' capabilities.

## FAQ's
### Can I modify metadata properties using GroupDocs.Metadata for .NET?
Yes, GroupDocs.Metadata provides robust capabilities to edit, remove, and add metadata properties across various file formats.
### Is GroupDocs.Metadata compatible with other archive formats like RAR or TAR?
Yes, GroupDocs.Metadata supports a wide range of archive formats, including RAR, TAR, and ZIP, among others.
### Where can I find detailed documentation for GroupDocs.Metadata for .NET?
You can access the documentation [here](https://tutorials.groupdocs.com/metadata/net/).
### How do I obtain a temporary license for GroupDocs.Metadata?
You can acquire a temporary license [here](https://purchase.groupdocs.com/temporary-license/).
### Does GroupDocs.Metadata offer support for troubleshooting and inquiries?
Yes, you can seek assistance and engage with the community on the [GroupDocs.Metadata forum](https://forum.groupdocs.com/c/metadata/14).
