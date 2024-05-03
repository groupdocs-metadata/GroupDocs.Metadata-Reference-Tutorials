---
title: Update Built-In Properties in PDFs using .NET
linktitle: Update Built-In Properties in PDFs using .NET
second_title: GroupDocs.Metadata .NET API
description: Learn how to update PDF document properties using C# and GroupDocs.Metadata for .NET. Modify author, title, keywords, and more programmatically.
type: docs
weight: 15
url: /net/pdf-metadata/update-built-in-properties-pdfs/
---
## Introduction
In this tutorial, we will learn how to use GroupDocs.Metadata for .NET to update built-in properties of PDF documents. This library provides a powerful set of tools to manipulate metadata within various document formats. We'll walk through the necessary steps to modify properties like author, title, creation date, keywords, creator, and producer in a PDF file using C#.
## Prerequisites
Before we begin, ensure you have the following in place:
- GroupDocs.Metadata for .NET Library: Download the library from [here](https://releases.groupdocs.com/metadata/net/).
- Visual Studio: Install Visual Studio to write and execute the C# code.
- Basic Understanding of C#: Familiarity with C# programming language is recommended.

## Import Namespaces
Start by including the necessary namespaces in your C# project:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## Step 1: Initialize Metadata Object
Begin by initializing a `Metadata` object with the path to your PDF file:
```csharp
using (Metadata metadata = new Metadata("Your Input File Path"))
{
    // Your code will go here
}
```
## Step 2: Access PDF Root Package
Next, retrieve the root package specifically for PDF using `GetRootPackage<PdfRootPackage>()`:
```csharp
var root = metadata.GetRootPackage<PdfRootPackage>();
```
## Step 3: Update Document Properties
Now, update the desired properties of the PDF document within the `PdfRootPackage`:
```csharp
root.DocumentProperties.Author = "New Author Name";
root.DocumentProperties.CreatedDate = DateTime.Now;
root.DocumentProperties.Title = "New Document Title";
root.DocumentProperties.Keywords = "keyword1, keyword2";
root.DocumentProperties.Creator = "Document Creator";
root.DocumentProperties.Producer = "Document Producer";
```
## Step 4: Save Changes
After modifying the properties, save the changes back to the PDF file:
```csharp
metadata.Save("Your Output File Path");
```
## Step 5: Retrieve Updated Properties
To verify the changes, reload the metadata and retrieve the updated properties:
```csharp
using (Metadata metadata = new Metadata("Your Output File Path"))
{
    var root = metadata.GetRootPackage<PdfRootPackage>();
    Console.WriteLine("Author: " + root.DocumentProperties.Author);
    Console.WriteLine("Created Date: " + root.DocumentProperties.CreatedDate);
    Console.WriteLine("Title: " + root.DocumentProperties.Title);
    Console.WriteLine("Keywords: " + root.DocumentProperties.Keywords);
    Console.WriteLine("Creator: " + root.DocumentProperties.Creator);
    Console.WriteLine("Producer: " + root.DocumentProperties.Producer);
}
```

## Conclusion
In this tutorial, we explored how to leverage GroupDocs.Metadata for .NET to update built-in properties of PDF documents programmatically. By following the outlined steps, you can efficiently manage and modify metadata within PDF files using C#. Feel free to explore more features and capabilities offered by GroupDocs.Metadata for comprehensive metadata manipulation.

## FAQ's
### Q: What is GroupDocs.Metadata for .NET?
A: GroupDocs.Metadata for .NET is a library that allows developers to read, edit, remove, and manipulate metadata in various document formats programmatically.
### Q: Where can I find the documentation for GroupDocs.Metadata for .NET?
A: You can access the documentation [here](https://reference.groupdocs.com/metadata/net/).
### Q: How can I download GroupDocs.Metadata for .NET?
A: You can download GroupDocs.Metadata for .NET from [this link](https://releases.groupdocs.com/metadata/net/).
### Q: Is there a free trial available?
A: Yes, you can get a free trial version [here](https://releases.groupdocs.com/).
### Q: Where can I get support for GroupDocs.Metadata for .NET?
A: For support, visit the GroupDocs.Metadata forum [here](https://forum.groupdocs.com/c/metadata/14).
