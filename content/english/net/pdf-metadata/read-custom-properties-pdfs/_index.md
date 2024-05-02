---
title: Read Custom Properties from PDFs in .NET
linktitle: Read Custom Properties from PDFs in .NET
second_title: GroupDocs.Metadata .NET API
description: Learn how to extract custom properties from PDFs using GroupDocs.Metadata for .NET. Dive into document metadata management with C#.
type: docs
weight: 11
url: /net/pdf-metadata/read-custom-properties-pdfs/
---
## Introduction
In the realm of .NET development, managing metadata within documents is crucial for organizing and extracting valuable information. GroupDocs.Metadata for .NET offers powerful tools to read custom properties from PDFs, enabling developers to efficiently access and utilize document metadata. This tutorial will guide you through the process of leveraging GroupDocs.Metadata to retrieve custom properties from PDF files using C#.
## Prerequisites
Before diving into this tutorial, ensure you have the following:
- Basic understanding of C# programming language.
- Visual Studio installed on your system.
- GroupDocs.Metadata for .NET library installed. You can download it [here](https://releases.groupdocs.com/metadata/net/).
- Access to a PDF file containing custom properties for testing.

## Import Namespaces
Begin by importing the necessary namespaces into your C# project:
```csharp
using System;
using Formats.Document;
using Tagging;
```
## Step 1: Load the PDF File
To start, load the PDF file containing the custom properties using GroupDocs.Metadata:
```csharp
using (Metadata metadata = new Metadata("YourInputFile.pdf"))
{
    var root = metadata.GetRootPackage<PdfRootPackage>();
    // Code for retrieving custom properties will go here.
}
```
Replace `"YourInputFile.pdf"` with the path to your PDF file.
## Step 2: Retrieve Custom Properties
Next, access and display the custom properties from the PDF document:
```csharp
var customProperties = root.DocumentProperties.FindProperties(p => !p.Tags.Contains(Tags.Document.BuiltIn));
foreach (var property in customProperties)
{
    Console.WriteLine("{0} = {1}", property.Name, property.Value);
}
```
This code snippet retrieves all non-built-in custom properties from the PDF document and prints their names and values to the console.

## Conclusion
In this tutorial, we explored how to utilize GroupDocs.Metadata for .NET to read custom properties from PDF documents using C#. By following the outlined steps, you can efficiently integrate metadata management into your .NET applications, enhancing document processing capabilities.

## FAQ's
### Can I modify custom properties using GroupDocs.Metadata?
Yes, GroupDocs.Metadata allows you to edit, remove, or add custom properties to various document formats.
### Does GroupDocs.Metadata support other file formats besides PDF?
Yes, GroupDocs.Metadata supports a wide range of file formats including Word documents, Excel spreadsheets, PowerPoint presentations, images, and more.
### Where can I find further documentation and support for GroupDocs.Metadata?
Refer to the [documentation](https://reference.groupdocs.com/metadata/net/) for comprehensive information. For additional support, visit the [GroupDocs.Metadata forum](https://forum.groupdocs.com/c/metadata/14).
### Is there a free trial available for GroupDocs.Metadata?
Yes, you can get a [free trial](https://releases.groupdocs.com/) to explore the features of GroupDocs.Metadata.
### How can I purchase a license for GroupDocs.Metadata?
Visit the [purchase page](https://purchase.groupdocs.com/buy) to acquire a license. Temporary licenses are also available [here](https://purchase.groupdocs.com/temporary-license/).
