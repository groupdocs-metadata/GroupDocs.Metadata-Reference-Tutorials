---
title: Read Built-In Properties from Diagrams in .NET
linktitle: Read Built-In Properties from Diagrams in .NET
second_title: GroupDocs.Metadata .NET API
description: Learn to extract metadata from diagram files in .NET using GroupDocs.Metadata. Enhance document management and analysis efficiently.
weight: 10
url: /net/diagram-metadata/read-built-in-properties-diagrams/
---

# Read Built-In Properties from Diagrams in .NET

## Introduction
In this tutorial, we'll delve into using GroupDocs.Metadata for .NET to read built-in properties from diagrams. GroupDocs.Metadata for .NET is a powerful library that enables developers to work with metadata associated with various document types, including diagrams, presentations, images, and more. Specifically, we'll focus on extracting metadata properties from diagram files using this library.
## Prerequisites
Before we begin, ensure you have the following prerequisites in place:
- Basic knowledge of C# and .NET development.
- Visual Studio IDE installed on your machine.
- GroupDocs.Metadata for .NET library. You can download it from [here](https://releases.groupdocs.com/metadata/net/).
- An input diagram file (e.g., .vsdx) to extract metadata from.

## Import Namespaces
Start by importing the necessary namespaces in your C# project to use GroupDocs.Metadata functionalities:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## Step 1: Load the Diagram File
Begin by loading the diagram file from which you want to extract metadata:
```csharp
using (Metadata metadata = new Metadata("YourDiagramFile.vsdx"))
{
    // Access the root package for diagrams
    var root = metadata.GetRootPackage<DiagramRootPackage>();
    // Now, you can access various document properties
    // Let's print some of the properties to the console
}
```
## Step 2: Access Built-In Properties
Once the diagram file is loaded, you can access its built-in properties through `DocumentProperties`:
```csharp
Console.WriteLine(root.DocumentProperties.Creator);
Console.WriteLine(root.DocumentProperties.Company);
Console.WriteLine(root.DocumentProperties.Keywords);
Console.WriteLine(root.DocumentProperties.Language);
Console.WriteLine(root.DocumentProperties.TimeCreated);
Console.WriteLine(root.DocumentProperties.Category);
```
## Step 3: Utilize Other Metadata Information
Apart from `DocumentProperties`, GroupDocs.Metadata provides access to other metadata properties specific to diagram files. For instance, you can access layers, pages, shapes, and much more depending on the diagram type.

## Conclusion
In this tutorial, we explored how to use GroupDocs.Metadata for .NET to read built-in properties from diagram files effortlessly. Leveraging this library, developers can efficiently manage and extract metadata associated with various document types in their .NET applications.

## FAQ's
### What types of diagram files are supported by GroupDocs.Metadata for .NET?
GroupDocs.Metadata for .NET supports a wide range of diagram file formats, including .vsdx, .vssx, .vstx, and more.
### Can I modify metadata properties using GroupDocs.Metadata for .NET?
Yes, you can not only read but also update and remove metadata properties using this library.
### Is there a trial version available for GroupDocs.Metadata for .NET?
Yes, you can access a free trial version [here](https://releases.groupdocs.com/).
### How can I get technical support for GroupDocs.Metadata for .NET?
For technical assistance, you can visit the [GroupDocs.Metadata forum](https://forum.groupdocs.com/c/metadata/14).
### Where can I purchase a license for GroupDocs.Metadata for .NET?
You can buy a license from [here](https://purchase.groupdocs.com/buy).
