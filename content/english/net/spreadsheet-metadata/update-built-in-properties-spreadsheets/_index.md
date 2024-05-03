---
title: Update Built-In Properties in Spreadsheets using .NET
linktitle: Update Built-In Properties in Spreadsheets using .NET
second_title: GroupDocs.Metadata .NET API
description: Learn how to update built-in metadata properties in Excel files using GroupDocs.Metadata for .NET. Modify author, creation time, company, and more with C#.
type: docs
weight: 14
url: /net/spreadsheet-metadata/update-built-in-properties-spreadsheets/
---
## Introduction
In this tutorial, we will explore how to utilize GroupDocs.Metadata for .NET to update built-in properties in spreadsheet files using C#. GroupDocs.Metadata is a powerful API that allows developers to read, edit, and remove metadata properties from various file formats, including spreadsheets. We'll focus specifically on modifying properties like author, creation time, company, category, and keywords within Excel files.
## Prerequisites
Before we begin, ensure you have the following:
- Visual Studio: Install the latest version of Visual Studio.
- GroupDocs.Metadata for .NET: Download and install GroupDocs.Metadata for .NET from the [download page](https://releases.groupdocs.com/metadata/net/).
- Basic C# Knowledge: Understanding of C# programming language and .NET framework.

## Import Namespaces
Begin by importing the necessary namespaces in your C# project:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## Step 1: Load the Spreadsheet File
First, initialize a `Metadata` object by loading the input spreadsheet file:
```csharp
using (Metadata metadata = new Metadata("YourInputFile.xlsx"))
{
    var root = metadata.GetRootPackage<SpreadsheetRootPackage>();
    // Access document properties within root
}
```
## Step 2: Update Built-In Properties
Access the built-in document properties through the `SpreadsheetRootPackage` and modify them as needed:
```csharp
root.DocumentProperties.Author = "YourAuthorName";
root.DocumentProperties.CreatedTime = DateTime.Now;
root.DocumentProperties.Company = "YourCompany";
root.DocumentProperties.Category = "YourCategory";
root.DocumentProperties.Keywords = "metadata, built-in, update";
```
Ensure to replace placeholders (`YourAuthorName`, `YourCompany`, `YourCategory`) with actual values you want to set for the properties.
## Step 3: Save Changes
After updating the properties, save the changes back to the spreadsheet file:
```csharp
metadata.Save("YourInputFile.xlsx");
```

## Conclusion
In this tutorial, we've demonstrated how to use GroupDocs.Metadata for .NET to update built-in properties of spreadsheet files programmatically. By leveraging this API, developers can efficiently manage metadata within Excel documents, enhancing data organization and accessibility.

## FAQ's
### What file formats does GroupDocs.Metadata support?
GroupDocs.Metadata supports a wide range of file formats, including Microsoft Office documents, PDFs, images, audio files, and more.
### Can I retrieve existing metadata properties from files?
Yes, you can extract and read metadata properties such as author, creation date, keywords, and custom properties using GroupDocs.Metadata.
### Is GroupDocs.Metadata compatible with .NET Core?
Yes, GroupDocs.Metadata is compatible with both .NET Framework and .NET Core.
### Does GroupDocs.Metadata provide a free trial?
Yes, you can download a free trial of GroupDocs.Metadata from [here](https://releases.groupdocs.com/).
### Where can I find support for GroupDocs.Metadata?
For support and discussions, visit the [GroupDocs.Metadata forum](https://forum.groupdocs.com/c/metadata/14).
