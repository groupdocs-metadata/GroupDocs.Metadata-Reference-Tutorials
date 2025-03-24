---
title: Read Built-In Properties from PDFs in .NET
linktitle: Read Built-In Properties from PDFs in .NET
second_title: GroupDocs.Metadata .NET API
description: Learn how to read PDF metadata in .NET using GroupDocs.Metadata. Access author names, creation dates, subjects, and more with C# code.
weight: 10
url: /net/pdf-metadata/read-built-in-properties-pdfs/
---

# Read Built-In Properties from PDFs in .NET

## Introduction
In this tutorial, we will explore how to leverage GroupDocs.Metadata for .NET to read built-in properties from PDF files. GroupDocs.Metadata is a powerful library that allows developers to work with metadata associated with various document formats, including PDFs, Microsoft Office documents, images, and more. By using this library, you can easily access and manipulate metadata attributes embedded within PDF files, such as author names, creation dates, subjects, and more.
## Prerequisites
Before diving into this tutorial, ensure you have the following prerequisites:
- Visual Studio: Make sure you have Visual Studio installed on your machine.
- GroupDocs.Metadata for .NET: Download and install GroupDocs.Metadata for .NET from [here](https://releases.groupdocs.com/metadata/net/).
- Basic Knowledge of C#: Familiarity with C# programming language and .NET framework.

## Import Namespaces
Begin by adding the necessary namespaces to your C# project:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## Step 1: Load PDF Metadata
First, load the PDF file and extract its metadata using GroupDocs.Metadata:
```csharp
using (Metadata metadata = new Metadata("YourInputFile.pdf"))
{
    // Access the root package of the PDF file
    var root = metadata.GetRootPackage<PdfRootPackage>();
    // Retrieve and display built-in properties
    Console.WriteLine("Author: " + root.DocumentProperties.Author);
    Console.WriteLine("Created Date: " + root.DocumentProperties.CreatedDate);
    Console.WriteLine("Subject: " + root.DocumentProperties.Subject);
    Console.WriteLine("Producer: " + root.DocumentProperties.Producer);
    Console.WriteLine("Keywords: " + root.DocumentProperties.Keywords);
    // Additional properties can be accessed similarly
    // ...
}
```
Beyond reading metadata, GroupDocs.Metadata allows for advanced operations like editing, removing, or adding new metadata properties to PDF files programmatically. This flexibility enables comprehensive management of document metadata within your .NET applications.
## Conclusion
In this tutorial, we've covered how to utilize GroupDocs.Metadata for .NET to extract built-in properties from PDF files using C#. By integrating this library into your projects, you can seamlessly handle document metadata operations, providing enhanced document management capabilities.

## FAQ's
### Can GroupDocs.Metadata work with other document formats?
Yes, GroupDocs.Metadata supports various document formats such as DOCX, XLSX, PPTX, PDF, JPG, PNG, and more.
### Is there a free trial available for GroupDocs.Metadata?
Yes, you can access a free trial of GroupDocs.Metadata from [here](https://releases.groupdocs.com/).
### How can I modify metadata properties using GroupDocs.Metadata?
You can modify metadata properties programmatically by accessing the corresponding document package and setting new values.
### Does GroupDocs.Metadata support .NET Core?
Yes, GroupDocs.Metadata is compatible with both .NET Framework and .NET Core.
### Where can I find support or ask questions related to GroupDocs.Metadata?
For support and discussions, visit the [GroupDocs.Metadata forum](https://forum.groupdocs.com/c/metadata/14).
