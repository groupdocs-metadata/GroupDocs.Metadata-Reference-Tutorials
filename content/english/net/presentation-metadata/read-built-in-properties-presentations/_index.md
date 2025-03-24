---
title: Read Built-In Properties from Presentations in .NET
linktitle: Read Built-In Properties from Presentations in .NET
second_title: GroupDocs.Metadata .NET API
description: Learn how to extract built-in properties from presentations using GroupDocs.Metadata for .NET in this comprehensive tutorial.
weight: 10
url: /net/presentation-metadata/read-built-in-properties-presentations/
---

# Read Built-In Properties from Presentations in .NET

## Introduction
In the realm of .NET development, managing and extracting metadata from various file formats like presentations is crucial. GroupDocs.Metadata for .NET offers a powerful solution to handle metadata tasks efficiently. This tutorial will delve into reading built-in properties from presentations using GroupDocs.Metadata for .NET. By the end, you'll have a clear understanding of how to leverage this library for extracting essential metadata from presentation files.
## Prerequisites
Before diving into this tutorial, ensure you have the following set up:
- Visual Studio installed on your machine.
- Basic knowledge of C# programming and .NET development.
- GroupDocs.Metadata for .NET library downloaded and installed. You can obtain it [here](https://releases.groupdocs.com/metadata/net/).

## Import Namespaces
Firstly, import the necessary namespaces in your C# project to use GroupDocs.Metadata functionalities.
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## Step 1: Load Presentation File
Begin by loading the presentation file from which you want to extract metadata using GroupDocs.Metadata.
```csharp
using (Metadata metadata = new Metadata("YourInputFile.pptx"))
{
    // Your code goes here
}
```
## Step 2: Access Presentation Metadata
Once the presentation file is loaded, you can access its root package and then retrieve document properties like author, creation date, company, and more.
```csharp
var root = metadata.GetRootPackage<PresentationRootPackage>();
Console.WriteLine(root.DocumentProperties.Author);
Console.WriteLine(root.DocumentProperties.CreatedTime);
Console.WriteLine(root.DocumentProperties.Company);
Console.WriteLine(root.DocumentProperties.Category);
Console.WriteLine(root.DocumentProperties.Keywords);
Console.WriteLine(root.DocumentProperties.LastPrintedDate);
Console.WriteLine(root.DocumentProperties.NameOfApplication);
// Add more properties as needed
```
## Step 3: Execute and Display Metadata
Execute the above code within the context of the using statement to ensure the metadata is properly accessed and displayed.

## Conclusion
In this tutorial, we've explored how to read built-in properties from presentations using GroupDocs.Metadata for .NET. Leveraging this library simplifies the process of working with metadata in presentation files, providing developers with powerful tools for managing document properties efficiently.

## FAQ's
### Is GroupDocs.Metadata for .NET compatible with different presentation formats?
Yes, GroupDocs.Metadata for .NET supports various presentation formats like PPTX, PPT, and more.
### Can I modify or update metadata using GroupDocs.Metadata for .NET?
Absolutely, you can modify, update, and remove metadata properties using this library.
### Where can I find detailed documentation for GroupDocs.Metadata for .NET?
You can refer to the documentation [here](https://tutorials.groupdocs.com/metadata/net/) for comprehensive information.
### How can I obtain a temporary license for GroupDocs.Metadata for .NET?
You can acquire a temporary license [here](https://purchase.groupdocs.com/temporary-license/) for evaluation purposes.
### Where can I seek assistance or ask questions related to GroupDocs.Metadata for .NET?
Visit the [GroupDocs.Metadata forum](https://forum.groupdocs.com/c/metadata/14) for community support and discussions.
