---
title: Read Custom Properties from Spreadsheets in .NET
linktitle: Read Custom Properties from Spreadsheets in .NET
second_title: GroupDocs.Metadata .NET API
description: Learn how to extract custom properties from spreadsheets using GroupDocs.Metadata for .NET. Enhance metadata manipulation in your .NET applications.
weight: 11
url: /net/spreadsheet-metadata/read-custom-properties-spreadsheets/
type: docs
---
# Read Custom Properties from Spreadsheets in .NET

## Introduction
In this tutorial, we'll explore how to extract custom properties from spreadsheets using GroupDocs.Metadata for .NET. GroupDocs.Metadata is a powerful library that enables developers to read, edit, and manipulate metadata properties in various file formats, including spreadsheets.
## Prerequisites
Before we begin, ensure you have the following:
- Visual Studio installed on your machine.
- GroupDocs.Metadata for .NET library. You can download it [here](https://releases.groupdocs.com/metadata/net/).
- Basic knowledge of C# programming and .NET development.

## Import Namespaces
Start by importing the necessary namespaces in your C# project:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
using GroupDocs.Tagging;
```
## Step 1: Load the Spreadsheet File
Begin by loading the target spreadsheet file using GroupDocs.Metadata:
```csharp
using (Metadata metadata = new Metadata("YourInputFile.xlsx"))
{
    var root = metadata.GetRootPackage<SpreadsheetRootPackage>();
```
## Step 2: Retrieve Custom Properties
Next, retrieve custom properties from the spreadsheet excluding built-in properties:
```csharp
var customProperties = root.DocumentProperties.FindProperties(p => !p.Tags.Contains(Tags.Document.BuiltIn));
foreach (var property in customProperties)
{
    Console.WriteLine("{0} = {1}", property.Name, property.Value);
}
```
## Step 3: Extract Content Type Properties (Optional)
Optionally, extract content type properties from the spreadsheet:
```csharp
foreach (var contentTypeProperty in root.DocumentProperties.ContentTypeProperties.ToList())
{
    Console.WriteLine("{0}, {1} = {2}", contentTypeProperty.SpreadsheetPropertyType, contentTypeProperty.Name, contentTypeProperty.SpreadsheetPropertyValue);
}
```

## Conclusion
In this tutorial, we've learned how to use GroupDocs.Metadata for .NET to read custom properties from spreadsheets. This library provides extensive capabilities for metadata manipulation, offering flexibility and control over document properties.

## FAQ's
### Can I modify custom properties using GroupDocs.Metadata for .NET?
Yes, GroupDocs.Metadata allows you to modify, add, or remove custom properties within supported file formats.
### Which spreadsheet formats are supported by GroupDocs.Metadata for .NET?
GroupDocs.Metadata supports a wide range of spreadsheet formats, including XLSX, XLS, ODS, and more.
### Is GroupDocs.Metadata suitable for large-scale document processing?
Yes, GroupDocs.Metadata is optimized for performance and can handle large files efficiently.
### Where can I get support for GroupDocs.Metadata related queries?
You can find support and engage with the community at [GroupDocs.Metadata forum](https://forum.groupdocs.com/c/metadata/14).
### Can I try GroupDocs.Metadata before purchasing?
Yes, you can download a free trial version from [here](https://releases.groupdocs.com/).
