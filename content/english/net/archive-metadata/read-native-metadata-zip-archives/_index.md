---
title: Read Native Metadata Properties from ZIP Archives in .NET
linktitle: Read Native Metadata Properties from ZIP Archives in .NET
second_title: GroupDocs.Metadata .NET API
description: Learn how to extract metadata from ZIP archives using GroupDocs.Metadata for .NET. Explore step-by-step instructions for reading native properties.
weight: 13
url: /net/archive-metadata/read-native-metadata-zip-archives/
type: docs
---
# Read Native Metadata Properties from ZIP Archives in .NET

## Introduction
ZIP archives are commonly used to compress and bundle files together. When working with ZIP files in .NET applications, it's often necessary to extract metadata properties from these archives. In this tutorial, we'll explore how to use GroupDocs.Metadata for .NET to read native metadata properties from ZIP files step by step.
## Prerequisites
Before you begin, ensure you have the following:
- GroupDocs.Metadata for .NET library installed. You can download it [here](https://releases.groupdocs.com/metadata/net/).
- Basic knowledge of C# and .NET development environment.

## Import Namespaces
Start by importing the necessary namespaces in your C# project:
```csharp
using GroupDocs.Formats.Archive;
using System;
using GroupDocs.Metadata;
using System.Text;
```
## Step 1: Initialize Metadata Object
First, create a `Metadata` object by providing the path to your ZIP file.
```csharp
using (Metadata metadata = new Metadata("Your Input File.zip"))
{
    // Access metadata extraction methods here
}
```
## Step 2: Access ZIP Root Package
Next, retrieve the root package for the ZIP file.
```csharp
var root = metadata.GetRootPackage<ZipRootPackage>();
```
## Step 3: Read ZIP Archive Properties
You can now access various properties of the ZIP archive, such as comment and total number of entries.
```csharp
Console.WriteLine(root.ZipPackage.Comment);
Console.WriteLine(root.ZipPackage.TotalEntries);
```
## Step 4: Iterate Through Files
Iterate through each file within the ZIP archive to access individual file metadata.
```csharp
foreach (var file in root.ZipPackage.Files)
{
    Console.WriteLine("File Name: " + file.Name);
    Console.WriteLine("Compressed Size: " + file.CompressedSize);
    Console.WriteLine("Compression Method: " + file.CompressionMethod);
    Console.WriteLine("File Flags: " + file.Flags);
    Console.WriteLine("Modification Date Time: " + file.ModificationDateTime);
    Console.WriteLine("Uncompressed Size: " + file.UncompressedSize);
    // Decode the file name if necessary
    var encoding = Encoding.UTF8;
    Console.WriteLine("Decoded File Name: " + encoding.GetString(file.RawName));
}
```

## Conclusion
In this tutorial, you learned how to utilize GroupDocs.Metadata for .NET to extract metadata properties from ZIP archives. This can be invaluable for applications dealing with compressed files, allowing you to access essential details embedded within each file.

## FAQ's
### What is GroupDocs.Metadata for .NET?
GroupDocs.Metadata for .NET is a powerful library that allows developers to read, write, and manipulate metadata associated with various file formats.
### How can I get a temporary license for GroupDocs.Metadata?
You can obtain a temporary license from [here](https://purchase.groupdocs.com/temporary-license/).
### Where can I find the complete documentation for GroupDocs.Metadata for .NET?
The documentation can be accessed [here](https://tutorials.groupdocs.com/metadata/net/).
### Can I try GroupDocs.Metadata for .NET for free?
Yes, you can download a free trial version [here](https://releases.groupdocs.com/).
### How can I get support or ask questions about GroupDocs.Metadata for .NET?
For support and discussions, visit the [GroupDocs.Metadata forum](https://forum.groupdocs.com/c/metadata/14).
